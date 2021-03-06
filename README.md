# SpotaTweet

A real-time Spotify &amp; Twitter API mashup.

This web app filters the Twitter stream for #NowPlaying tweets, extracts track IDs from Spotify URLs, requests track data from the Spotify API, displays the embedded Tweet in the web browser and plays a preview. Implements Twitter statuses/filter stream and oEmbed API.

Inspired by [Serendipity](https://twitter.com/search?q=kcimc%20serendipity) by [@kcimc](https://twitter.com/kcimc), formerly a Spotify Media Artist in Residence.

![Screenshot](screenshot.png?raw=true "Screenshot")

## Installing and Running

Install [Node.js](https://nodejs.org/).

Clone GitHub repo:

```bash
git clone https://github.com/twitterdev/spotatweet.git
```

Create Twitter and Spotify Apps:

- Create a [Twitter application](https://developer.twitter.com/en/apps).
- Create a [Spotify application](https://developer.spotify.com/my-applications).

Create a `config.json` file using `config.sample.json` as a template. Fill in your Twitter & Spotify API Keys. You may also set the values in the `config.sample.json` file as environment variables for environments like Heroku and Glitch. Values set in the environment will override those set in the config file.

Install node module dependencies:

```bash
npm install
```

Run application:

```bash
npm start
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

A GET request to /nowplaying.json will return a Tweet object, additionally hydrated with a "spotify_track" object and a "oembed" object representing the latest #NowPlaying Tweet.

## Deploying

### Heroku

This application is already configured to run on [Heroku](https://www.heroku.com) and can be [deployed with Git](https://devcenter.heroku.com/articles/git).

Before deployment set your Heroku environment [config vars](https://devcenter.heroku.com/articles/config-vars) to mirror config.json.

On Heroku set NODE_ENV to "production."

### Glitch

You can also easily remix this project on [Glitch](https://glitch.com). Set the environment variables in the `.env` file.

[![Remix on Glitch](https://cdn.glitch.com/2703baf2-b643-4da7-ab91-7ee2a2d00b5b%2Fremix-button.svg)](https://glitch.com/edit/#!/import/github/twitterdev/spotatweet?TWITTER_CONSUMER_KEY=&TWITTER_CONSUMER_SECRET=&TWITTER_ACCESS_TOKEN=&TWITTER_ACCESS_TOKEN_SECRET=&SPOTIFY_CLIENT_ID=&SPOTIFY_CLIENT_SECRET=)

## Limitations

- A Spotify developer token only lasts for 3600 seconds (one hour), so the app will need to be restarted after that time.
- Web audio does not autoplay on mobile Safari and some other browsers

## Resources

- [Twitter statuses/filter stream](https://developer.twitter.com/en/docs/tweets/filter-realtime/api-reference/post-statuses-filter.html)
- [Twitter oEmbed](https://developer.twitter.com/en/docs/tweets/post-and-engage/api-reference/get-statuses-oembed.html)
- [Twitter Rate Limiting](https://developer.twitter.com/en/docs/basics/rate-limiting.html)
- [Spotify Web API](https://developer.spotify.com/web-api/)
