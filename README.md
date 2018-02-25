# zoupcast
Icecast to JACK output over SSH

## Requirements

### Client

```sh
sudo apt install socat
```

### Server

```sh
sudo apt install php-http php-cli vlc-bin vlc-jack
```

TODO server side requires some weird scripts not yet included in this
repo. They should be published as well.

(Note: No HTTP server setup is needed!)

## Broadcasting

First, deliver your public key to server administrator.

Edit `~/.ssh/config` and add the following server entry:

```
Host broadcast
	hostname yourserver.example.com
	# You need this the following only if running ssh on non-standard port
	port 2222
	user broadcast
	identityfile /path/to/your/private_key
```

To run, you need local port number and ssh hostname:

```
client/zoupcast 8000 broadcast
```

Then, check if you have connection by navigating to
http://localhost:8000/ with your browser. If it shows instructions
page, then you have a remote connection!

Then open your Icecast client such as Mixxx and use the following
settings:

* Vorbis codec
* Use UTF-8 for metadata
* Rather high quality (>=160kbps)
* Any username and password
* Any mount point

Zoupcast can be started in advance and it doesn't interfere the
broadcast until you start streaming from the Icecast client.

Enjoy!
