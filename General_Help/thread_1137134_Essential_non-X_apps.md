---
title: "Essential non-X apps?"
date: 2009-04-25
forum: General Help
---

### Post by Sente on 2009-04-25
I've embarked on a journey to try to do my basic computing on a basic cli install of Ubuntu 9.04.
I don't want to use X. Here are a couple things I've found so far:

emacs is a pretty cool program. I know that's supposed to be common knowledge in the GNU/Linux community, but having finally decided to sit down with the tutorial, I'm just starting to really appreciate its versatility.

lynx and elinks are a very different way to browse the web if you've only been exposed to browsing through gui browsers like firefox. It's not always easy to use on web pages designed for "modern" browsers, but it is pretty fun to change things up a bit!

The Linux Cookbook has been helpful as a reference for command-line utilities:
[http://dsl.org/cookbook/cookbook_toc.html](http://dsl.org/cookbook/cookbook_toc.html)

So my question to you is, what non-X applications/documentation have you found to be useful? Whether they be for productivity or fun, let's hear them!

---

### Post by oldos2er on 2009-04-25
mc, slrn, nano, wget, aptitude, etc.

---

### Post by RedSquirrel on 2009-04-25
Well, I prefer vim. :P

For docs, you might want to have a look at the guides at [http://tldp.org/](http://tldp.org/).

---

### Post by Sente on 2009-04-26
RedSquirrel- have yet to go there. I fear it was an exercise in discipline for me to sit down and actually go through the emacs tutorial. We'll see ;)

Here's a couple that I forgot about: mpg123 and ogg123

---

### Post by Nepherte on 2009-04-26
mpd, ncmpcpp, elinks, screen, rtorrent, vim, irssi, iftop, ssh, ...

---

### Post by SuperSonic4 on 2009-04-26
basics: nano, cp, mv, mount

web: wget, links, finch

audio: mocp, lame, pacpl, faac, faad, oggenc, cdparanoia

other: mkisofs (i think)

---

### Post by andrew.46 on 2009-04-27
Hi Sente,

> **Sente said:**
> So my question to you is, what non-X applications/documentation have you found to be useful? Whether they be for productivity or fun, let's hear them!

Such a setup would not be complete without mutt for email. I have written a guide that would at the very least get you started:

[Howto] Use Mutt with Gmail
[http://ubuntuforums.org/showthread.php?t=1021746](http://ubuntuforums.org/showthread.php?t=1021746)

All the best for your project,

Andrew

---

### Post by Sente on 2009-04-27
Sweet, thanks for the heads up andrew!

---

### Post by Sente on 2009-04-27
Another cool one... "pm-utils", with "pm-suspend" on can suspend from the command line.

---

### Post by Dr_Willis on 2009-04-27
Dont forget the following 

pastebinit - command-line pastebin client

unp - unpack (almost) everything with one command

mc - Midnight commander file manager. (a must)

screen - multiplexing terminal

vim-full - for you vim users. :)

renameutils -  several commands that make bulk renaming easy.

irssi - everyones fave console irc client. :popcorn:

---

### Post by Sente on 2009-04-27
> **Sente said:**
> Another cool one... "pm-utils", with "pm-suspend" on can suspend from the command line.
  Seems it suspends alright...but waking up is a little difficult!

---

### Post by Dr_Willis on 2009-04-27
Also for a web browser - at one time i recall there being one that could use a 'graphical' interface in the framebuffer enabled console.

If you are using the framebuffer enabled console that is..

I just cant remeber which one it was. :confused: 

And if you are going to try 'console only' you may want to check out the framebuffer console. It can make things much easier on the eyes.

---

### Post by Daisuke_Aramaki on 2009-04-27
elinks is one of the best cli web browsers. the rest of the things are already covered here i see. screen, dvtm, htop, mpd and ncmpc/pp, or moc, rtorrent have been mentioned already. for calendar, you can probably use calcurse. for videos, mplayer should be more than sufficient. but you need framebuffer enabled, and you can use the xf86-video-fbdev driver to watch videos on console. fbida is an image viewing utility that also runs in framebuffer. vim and emacs should do it as far as editors go.

as Dr_Willis says, framebuffer is the best way to use your console screen recognize your computer's native resolution, so that you don't have a problem with screen real estate. and if you install terminus fonts, you can use them without issues on a framebuffer console.

---

### Post by Simian Man on 2009-04-27
Many people don't know that vim can be used as a file browser - it can even browse tar balls.

---

### Post by kirsis on 2009-04-27
**screen** is essential for any serious CLI use, imo.

---

### Post by RedSquirrel on 2009-04-27
> **Dr_Willis said:**
> vim-full - for you vim users. 

I find the **vim** package is sufficient. **vim-full** pulls in a lot of gnome stuff since it is the equivalent of (that is, a transitional package to...) **vim-gnome**. 



> **Dr_Willis said:**
> Also for a web browser - at one time i recall there being one that could use a 'graphical' interface in the framebuffer enabled console.

If you are using the framebuffer enabled console that is..

I just cant remeber which one it was. :confused: 

links can do that with the '-g' option.

```
links -g
```

> **Dr_Willis said:**
> And if you are going to try 'console only' you may want to check out the framebuffer console. It can make things much easier on the eyes.

I agree, the framebuffer is nice. I just wanted to point out that on Ubuntu the framebuffer modules are blacklisted by default. See /etc/modprobe.d/blacklist-framebuffer.conf. It is possible to comment out the one you want to use (vesafb, for example).


Oh, and one more program I like is **abcde** - "**a** **b**etter **cd** **e**ncoder".

---

### Post by Sente on 2009-04-28
Thanks for all the ideas guys! Things are coming along quite nicely.

"links -g" on my system gives an error about not being compiled w/ fb support, but "links2 -g" works fine.

screen and mc really make things much easier!

---

### Post by Sente on 2009-04-28
iptraf seems to be pretty nice for monitoring network activity

---

