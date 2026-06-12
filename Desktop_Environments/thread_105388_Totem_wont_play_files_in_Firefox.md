---
title: "Totem wont play files in Firefox"
date: 2005-12-18
forum: Desktop Environments
---

### Post by Rackerz on 2005-12-18
Im trying to play a video from vidnet.com but Totem keeps telling me it can't. Here's the errors i get.

> Totem could not play 'fd://0'.

There were no decoders found to handle the stream, you might need to install the corresponding plugins

---

### Post by rejean on 2005-12-18
Hi Rackerz!
Diddo for me! Not only that but if I go let's say to [http://www.cbc.ca/ns/]("http://www.cbc.ca/ns/") and I click on a sound only link I get the same message after a window pops-up from Win Media Player asking me if I use broadband or dial-up. Even worse I get the same message if I try to play an audio cd.
I know that in PCLinuxOS and Mandriva that I had to install MPlayer, and win 32-codecs, xine-win32, real-codecs from PLF and mplayer-plugins and xmms-alsa from Contrib but I cannot find them anywhere in Synaptic.
How do people watch a video or listen to some sound in Ubuntu is beyond me at the moment.

---

### Post by rejean on 2005-12-18
Hi again!
Just want to report on my progress. I went into Synaptic and Settings=> Repositories. I found 7 and clicked on each one at a time then on +Add and I checked the 4 entries, officially supported,restricted, Community and Non-free. Then I went into Not Installed and I found mozilla-player, mplayer and I went for wine as well, ( wine not! lol ). Once they were installed I tried a video from the link in my previous post but it didn't work. I tried an audio link and got the Totem message again. I went back into Synaptic did the same thing over but this time looked into All and I found RealPlayer, which I downloaded but during the install I was told it was either downloaded in the wrong place or the file was corrupted.
I will keep on trying.
P.S. I found some good info in the wiki:[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")
Good news Rackerz!!! It worked! I can see internet videos! And listen to a CD audio using Sound juicer! Go to the wiki and give it a try. Easy to follow.

---

### Post by aysiu on 2005-12-18
You could always [replace Totem with MPlayer](http://ubuntuforums.org/showthread.php?t=76946).

---

### Post by Rackerz on 2005-12-18
MPlayer always plays the movies in a very reduced quality. It's a shame really. I might give it go, thanks for the heads up guys!

---

