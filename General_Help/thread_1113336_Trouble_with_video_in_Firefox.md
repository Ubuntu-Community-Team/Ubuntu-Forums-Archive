---
title: "Trouble with video in Firefox"
date: 2009-04-01
forum: General Help
---

### Post by toehead2 on 2009-04-01
I am having trouble viewing embedded video files with Firefox 3.0.8
When I am at a site that has embedded video files or streaming video for that matter, instead of the video file there is a grey box with a large play button, which when pushed hangs up firefox. Looking at the add-ons I have for Firefox I find a plug-in for [LIST]
Totem 2.22.1
VLC multimedia plug in
Windows Media Player Plug in
Windows Media Player Plug in 10
Shockwave Flash
Real Player 9
Quicktime 7.2.0
Quicktime6.0/7
Java 1.6.0_07.b06
Helix DNA Plug in
Gecko media player 0.6.0
Divx Browser 0.60
Divx Web Player 1.4.0.233
[/LIST]
Are there multiple instances of plug ins causing problems?

---

### Post by leonardo_neo on 2009-04-01
> **toehead2 said:**
> I am having trouble viewing embedded video files with Firefox 3.0.8
When I am at a site that has embedded video files or streaming video for that matter, instead of the video file there is a grey box with a large play button, which when pushed hangs up firefox. Looking at the add-ons I have for Firefox I find a plug-in for [LIST]
Totem 2.22.1
VLC multimedia plug in
Windows Media Player Plug in
Windows Media Player Plug in 10
Shockwave Flash
Real Player 9
Quicktime 7.2.0
Quicktime6.0/7
Java 1.6.0_07.b06
Helix DNA Plug in
Gecko media player 0.6.0
Divx Browser 0.60
Divx Web Player 1.4.0.233
[/LIST]
Are there multiple instances of plug ins causing problems?

Firefox is giving this trouble with flash for sometimes past now.

The fix is, remove the shockwave flash, and install adobe flash player. You will get the .deb file from adobe's website.

---

### Post by x C0MMAND0 x on 2009-04-01
I have ran into that problem before and this is what I have found. Run the following codes with all browsers CLOSED.

```

sudo apt-get purge flashplugin-nonfree
```

```
sudo apt-get install flashplugin-nonfree
```

```
sudo apt-get update
```

```
sudo apt-get upgrade

```
```

exit
```

This is a very simple solution, but it has always worked for me. I also have a 64 bit OS and have ran into the exact problem.

Good luck!

---

### Post by aeiah on 2009-04-01
you should run sudo apt-get update before installing the flash plugin again, not afterwards. you're updating your software source index so its useful to do this first. doing sudo apt-get upgrade will upgrade your ubuntu system and this may not be desirable, so i advise against doing this just for the sake of it.

---

### Post by markharding557 on 2009-04-01
> **leonardo_neo said:**
> Firefox is giving this trouble with flash for sometimes past now.

The fix is, remove the shockwave flash, and install adobe flash player. You will get the .deb file from adobe's website.

there is no need to go to adobies web site it is in ubuntu's repository either on it's own or part of ubuntu-restricted-extras

---

### Post by toehead2 on 2009-04-01
> **markharding557 said:**
> there is no need to go to adobies web site it is in ubuntu's repository either on it's own or part of ubuntu-restricted-extras

The ubuntu-restricted-extras, is this a repository? I don't see it in my list. Searching for flashplayer in Synaptic provides the flashplayer nonfree plugin which is installed but video playback still isn't there.

---

### Post by rausuar on 2009-04-01
> **toehead2 said:**
> The ubuntu-restricted-extras, is this a repository? I don't see it in my list. Searching for flashplayer in Synaptic provides the flashplayer nonfree plugin which is installed but video playback still isn't there.

Hi,

I had the same problem, and actually, posted a help request here in the forum... you can actually check to see the solutions... however, embedded videos are played mostly by the flash plugin, you can install it in synaptic, the package name is flashplugin-nonfree.  You can also install the player plugins, like mozilla-mplayer or mozilla-vlc.

In the other hand, try disabling, if you have them installed, the extensions blocking javascripts, like adblock plus...
 

I hope it helps...

---

