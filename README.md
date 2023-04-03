# tap-googleads

`tap-googleads` is a Singer tap for GoogleAds.

This fork of `tap-googleads` will sync your GoogleAds data under the specified `customer_id`.

Built with the [Meltano Tap SDK](https://sdk.meltano.com) for Singer Taps.

## Installation

To install and use this tap with Meltano:

```bash
meltano add extractor tap-googleads
```

To use standalone, you can use the following:

```bash
pip install https://github.com/Matatika/tap-googleads.git
```


## Configuration

### Accepted Config Options

### This tap supports two sets of configs:

### Using Your Own Credentials

Settings required to run this tap.

- `oauth_credentials.client_id` (required)
- `oauth_credentials.client_secret` (required)
- `oauth_credentials.refresh_token` (required)
- `developer_token` (required)
- `customer_id` (required)
- `login_customer_id` (optional)
- `start_date` (optional)
- `end_date` (optional)

How to get these settings can be found in the following Google Ads documentation:

https://developers.google.com/adwords/api/docs/guides/authentication

https://developers.google.com/google-ads/api/docs/first-call/dev-token

If you have installed the tap you can run the following commands to see more information about the tap.
```bash
tap-googleads --about
```

### Proxy OAuth Credentials

To run the tap yourself It is highly recommended to use the [Using Your Own Credentials](#using-your-own-credentials) section listed above.

These settings for handling your credentials through a Proxy OAuth Server, these settings are used by default in a [Matatika](https://www.matatika.com/) workspace.

The benefit to using these settings in your [Matatika](https://www.matatika.com/) workspace is that you do not have to get or provide any of the OAuth credentials. All a user needs to do it allow the Matatika App permissions to access your GoogleAds data, and choose what `customer_id` you want to get data from.

All you need to provide in your [Matatika](https://www.matatika.com/) workspace are:
- Permissions for our app to access your google account through an OAuth screen
- `customer_id` (required)
- `start_date` (optional)
- `end_date` (optional)

These are not intended for a user to set manually, as such setting them could cause some config conflicts that will now allow the tap to work correctly.

Also set in by default in your [Matatika](https://www.matatika.com/) workspace environment:

- `oauth_credentials.client_id`
- `oauth_credentials_client_secret`
- `oauth_credentials.authorization_url`
- `oauth_credentials.scope`
- `oauth_credentials.access_token`
- `oauth_credentials.refresh_token`
- `oauth_credentials.refresh_proxy_url`


### Source Authentication and Authorization

## Usage

You can easily run `tap-googleads` by itself or in a pipeline using [Meltano](https://meltano.com/).

### Executing the Tap Directly

```bash
tap-googleads --version
tap-googleads --help
tap-googleads --config CONFIG --discover > ./catalog.json
```

## Developer Resources


### Initialize your Development Environment

```bash
pipx install poetry
poetry install
```

### Create and Run Tests

Create tests within the `tap_googleads/tests` subfolder and
  then run:

```bash
poetry run pytest
```

You can also test the `tap-googleads` CLI interface directly using `poetry run`:

```bash
poetry run tap-googleads --help
```

### Testing with [Meltano](https://www.meltano.com)

_**Note:** This tap will work in any Singer environment and does not require Meltano.
Examples here are for convenience and to streamline end-to-end orchestration scenarios._

Your project comes with a custom `meltano.yml` project file already created. Open the `meltano.yml` and follow any _"TODO"_ items listed in
the file.

Next, install Meltano (if you haven't already) and any needed plugins:

```bash
# Install meltano
pipx install meltano
# Initialize meltano within this directory
cd tap-googleads
meltano install
```

Now you can test and orchestrate using Meltano:

```bash
# Test invocation:
meltano invoke tap-googleads --version
# OR run a test `elt` pipeline:
meltano elt tap-googleads target-jsonl
```

### SDK Dev Guide

See the [dev guide](https://sdk.meltano.com/en/latest/dev_guide.html) for more instructions on how to use the SDK to 
develop your own taps and targets.
