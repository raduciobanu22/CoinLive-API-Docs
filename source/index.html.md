---
title: CoinLive News API

toc_footers:
  - <a href='https://coinlive.io/contact'>Contact us to get access</a>

<!-- includes:
  - errors -->

search: true
---

# Introduction

Welcome to the CoinLive News API! We provide latest news from the crypto space, updated to the second. Our systems are constantly monitoring hundreds of sources like popular media outlets or social networks.
Human discretion is then applied to filter out the noise. The result is an institutional-level news feed targeted to a professional audience.

# Authentication

> Authorization example:

```shell
# Just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: Token token=<api_key>"
```

> Make sure to replace `<api_key>` with your API key.

CoinLive uses API keys to allow access to the API. You can send us an email at <a href="mailto:contact@coinlive.io">contact@coinlive.io</a> if you are interested in getting access and using our API.

CoinLive expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Token token=api_key`

<aside class="notice">
You must replace <code>api_key</code> with your personal API key.
</aside>

# Articles

## Get latest news articles

```shell
curl "http://api.coinlive.io/v1/articles"
  -H "Authorization: Token token=api_key"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "title": "A news article title",
    "content": "News body",
    "type": "news",
    "created_at": "2018-04-16T14:46:51.610Z",
    "updated_at": "2018-04-16T14:48:42.243Z",
    "slug": "a-news-article",
    "source_url": "https://example.com/a-news-article",
    "tags": [
        {
            "id": 1,
            "name": "BTC",
            "slug": "btc",
            "created_at": "2018-02-11T11:30:06.233Z",
            "updated_at": "2018-02-11T11:30:06.233Z",
            "icon_class": null,
            "priority": 1
        }
    ]
  },
  {
    "id": 2,
    "title": "Another news article",
    "content": "News body",
    "type": "news",
    "created_at": "2018-04-14T03:57:31.600Z",
    "updated_at": "2018-04-14T03:57:31.600Z",
    "slug": "another-one",
    "source_url": "https://example.com/another-news-article",
    "tags": [
      {
        "id": 101,
        "name": "BTC",
        "slug": "btc",
        "created_at": "2018-02-11T11:30:06.233Z",
        "updated_at": "2018-02-11T11:30:06.233Z",
        "icon_class": null,
        "priority": 1
      },
      {
        "id": 203,
        "name": "REC",
        "slug": "rec",
        "created_at": "2018-01-26T09:29:20.119Z",
        "updated_at": "2018-01-26T09:29:20.119Z",
        "icon_class": null,
        "priority": 3
      }
    ]
  },
]
```

This endpoint retrieves the latest news articles.

### HTTP Request

`GET http://api.coinlive.io/v1/articles`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
<code>limit</code> *optional* | 50 | Limit the returned results. Accepted range: 1 to 50.
<code>last_id</code> *optional* | null | Filters all articles published after the one provided.
<code>tags[]</code> *optional* | null| Filter articles using tags. This parameter should be provided as array. Accepted values are tags names. See the /tags endpoint.

<!-- <aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside> -->

# Tags

## Get the list of available tags

```shell
curl "http://api.coinlive.io/v1/tags"
  -H "Authorization: Token token=api_key"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 878,
        "name": "BTC",
        "slug": "btc",
        "created_at": "2018-02-17T08:41:44.113Z",
        "updated_at": "2018-02-20T15:45:52.479Z",
        "icon_class": null,
        "priority": 1
    },
    {
        "id": 2,
        "name": "LTC",
        "slug": "ltc",
        "created_at": "2018-01-25T10:12:06.734Z",
        "updated_at": "2018-02-20T15:45:52.479Z",
        "icon_class": null,
        "priority": 1
    },
    {
        "id": 14,
        "name": "ADA",
        "slug": "ada",
        "created_at": "2018-01-26T06:06:45.918Z",
        "updated_at": "2018-02-20T15:45:52.479Z",
        "icon_class": null,
        "priority": 1
    },
    ...
]
```

This endpoint retrieves the list of available tags.

### HTTP Request

`GET http://api.coinlive.io/v1/tags`
