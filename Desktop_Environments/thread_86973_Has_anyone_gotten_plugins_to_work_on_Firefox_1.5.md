---
title: "Has anyone gotten plugins to work on Firefox 1.5?"
date: 2005-11-06
forum: Desktop Environments
---

### Post by aysiu on 2005-11-06
All of my plugins worked on Firefox 1.0.7 (the original Ubuntu version--not the Mozilla .tar.gz). When I installed 1.5 from Mozilla, I symlinked the /usr/local/bin/firefox/plugins to point to /usr/lib/mozilla-firefox/plugins, but I couldn't get any plugins to work--not even Flash.

I tried installing Flash straight from the Macromedia website. Still no go. My plugins all work with Epiphany, though.

Here's the weird thing, too. My wife is using Firefox 1.5 on Mac OS X and *also* cannot get its plugins working. However, her plugins all work for Safari. 

Is this because of Firefox being a non-native app somehow? Are we doing anything wrong (if anyone happens to know the OS X fix as well, that'd be great, too--my wife doesn't like using Safari... and I don't dig Epiphany either).

---

### Post by bored2k on 2005-11-07
[list][*]I installed flash using Firefox's built in installer.
[*]I installed a working MPlayer plugin using the latest 3.11 version **not** on the repositories (I deleted totem's).
[*]I *think* mozilla-acroread works here.

---

### Post by bored2k on 2005-11-07
[list][*]I installed flash using Firefox's built in installer.
[*]I installed a working MPlayer plugin using the latest 3.11 version **not** on the repositories (I deleted totem's).
[*]I *think* mozilla-acroread works here.[/list]

---

### Post by aysiu on 2005-11-07
[QUOTE=bored2k]I installed flash using Firefox's built in installer.[/quote] What does this mean? I went to the [Mozilla plugin page](http://plugindoc.mozdev.org/linux.html#Flash) and when I click on the Flash plugin, it just sends me to the Macromedia page.

> 
I installed a working MPlayer plugin using the latest 3.11 version **not** on the repositories (I deleted totem's). I'll look for the latest one... is that in a Debian repository somewhere?

> 
I *think* mozilla-acroread works here.[/list] I'm not too worried about that. I open all PDFs externally anyway (not with plugins).

---

### Post by bored2k on 2005-11-07
1. [http://www.gamespot.com/](http://www.gamespot.com/) . You should get a bar telling you that since you don't have Flash installed, it will do it for you.
2. [ Mplayer Plugin 3.11]("http://www.ubuntuforums.org/showthread.php?t=75817&highlight=mplayer+plugin")

---

### Post by aysiu on 2005-11-07
[QUOTE=bored2k]1. [http://www.gamespot.com/](http://www.gamespot.com/) . You should get a bar telling you that since you don't have Flash installed, it will do it for you.[/quote] Nope. I just get a blank screen.

> 
2. [ Mplayer Plugin 3.11]("http://www.ubuntuforums.org/showthread.php?t=75817&highlight=mplayer+plugin") Well, I installed that, and now the MPlayer plugin doesn't work for Firefox *or* Epiphany. I appreciate you trying to help out. I think I may just stick with the *status quo*. This may not be worth the effort. I figured if there were an easy fix...

---

### Post by dto on 2005-11-07
I installed Firefox 1.5 to a directory under /home and just copied the various plugins (mplayer, real, flash) from the /plugins directory of the 1.0.7 install to the /plugins directory of my 1.5 install. Everything has worked for me.

---

### Post by aysiu on 2005-11-07
[QUOTE=dto]I installed Firefox 1.5 to a directory under /home and just copied the various plugins (mplayer, real, flash) from the /plugins directory of the 1.0.7 install to the /plugins directory of my 1.5 install. Everything has worked for me.[/QUOTE] Hm. So maybe symlinking isn't the way to do? Just plain copy them? I might give that a try.

**Edit**: Nope. Didn't work. Thanks for the suggestion, though.

---

### Post by briguy on 2005-11-07
Go to the /firefox/plugins/ directory where you installed 1.5 and do this:  

sudo ln -s /usr/lib/mozilla-firefox/plugins/* .

This will get your plugins going no problems.  In fact, flash works much better (audio doesn't drift).

---

### Post by dto on 2005-11-07
[QUOTE=aysiu]Hm. So maybe symlinking isn't the way to do? Just plain copy them? I might give that a try.

**Edit**: Nope. Didn't work. Thanks for the suggestion, though.[/QUOTE]

Hmm...that is strange. I've done that with all three of the machines that I have Breezy on. The only symlink I remember using was to the Java plugin.

---

### Post by manicka on 2005-11-07
The instructions on the wiki work flawlessly for me. Plugins working from first startup

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by dcherryholmes on 2005-11-23
I also followed the instructions on the wikki, and neither flash nor mplayer-mozilla are working anymore.

---

### Post by aysiu on 2006-01-07
I found the solution!

First of all, I thought it was a bit odd that I couldn't get Flash working on Firefox 1.5 on...

1. My wife's Mac OS X Powerbook
2. My Windows XP partition at home
3. My Ubuntu partition at home
4. My Windows XP computer at work

Something was *definitely* wrong.

I found out what it is by digging around the internet: **the Adblock extension**. Just disable obj-tabs. This solution works for OS X and Ubuntu. I haven't tried it in Windows yet.

---

