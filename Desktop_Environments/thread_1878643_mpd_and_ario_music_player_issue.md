---
title: "mpd and ario music player issue"
date: 2011-11-10
forum: Desktop Environments
---

### Post by test006 on 2011-11-10
Hi,
On LAN i have headless server on which i have installed mpd. Server is running ubuntu server 11.10.
On my laptop i have installed ario music player so i can player music stored on the server streamed using mpd. With Ario i can connect to the server and i can see the all the mp3s on the server. The issue is when i go play the mp3 file it starts playing but i cannot hear any audio. I can see it paying since the time counter starts increasing....

Any ideas what might be issue?
Desktop is running kubuntu 11.10.

thanks

---

### Post by mcduck on 2011-11-10
Do you actually have some system to stream the sound from the MPD machine to your computer? The normal way to use MPD is to play the music *on the server*, and the clients are only used to control what's playing.

To actually hear the sound on the client system you'd need to use something like Icecast server (or perhaps Pulseaudio) to stream the sound to the client machine.

(of course if you just want to store the music files on the server and play them back on the client, then a normal network files share would be much simpler way to acchieve the same result ;))

---

### Post by test006 on 2011-11-10
> **mcduck said:**
> Do you actually have some system to stream the sound from the MPD machine to your computer? The normal way to use MPD is to play the music *on the server*, and the clients are only used to control what's playing.

To actually hear the sound on the client system you'd need to use something like Icecast server (or perhaps Pulseaudio) to stream the sound to the client machine.

(of course if you just want to store the music files on the server and play them back on the client, then a normal network files share would be much simpler way to acchieve the same result ;))

Yes i would like to stream the sound from the mpd server to my client PC and hear the sound on my client PC. I have configured the pulse audio in the mpd.conf file as shown below. Is this correct or do i need some more configuration.

audio_output {
        type            "pulse"
        name            "My Pulse Output"
#       server          "remote_server"         # optional
#       sink            "remote_server_sink"    # optional
}

---

### Post by mcduck on 2011-11-11
I've never even tried to get pulse streaming working myself, but as far as I can remember you'll also need to install tools for configuring Pulse's settings and to allow remote connections to the sound server. And of course you'll have to somehow configure the client machine to connect to the audio stream, as the MPD client is not going to do that for you (like I said, the main idea of using MPD is to play music on the server, not on the client).

---

### Post by pharnet on 2011-11-21
An alternative would be to create an HTTP output:

 audio_output {
	type		"httpd"
	name		"my-http"
	encoder		"vorbis"
	port		"8888"
	bitrate		"128"
	format		"44100:16:2"
}

Then use a client like vlc (or many other clients) and open network stream:

[http://ip.of.mpd.server:8888/mpd.ogg](http://ip.of.mpd.server:8888/mpd.ogg)

---

