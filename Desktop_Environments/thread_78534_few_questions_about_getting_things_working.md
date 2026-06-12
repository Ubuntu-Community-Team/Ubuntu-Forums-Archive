---
title: "few questions about getting things working"
date: 2005-10-18
forum: Desktop Environments
---

### Post by granite230 on 2005-10-18
Today I installed Breezy, I changed my sources.list to the one available on ubuntuguide.org and changed all the 'hoary's' to 'breezy's'. Everything seems to work except this part:

[I]## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted[/I]

So I disabled them. Then I moved on and installed all the applications I want using the hoary guide. Everything works fine except the following:

From the multimedia codecs:
**sudo apt-get install w32codecs: **
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

**sudo apt-get install libdivx4linux:**
E: Couldn't find package libdivx4linux

The dvd playback capability:
**sudo apt-get install libdvdcss2:**
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

I also installed the Mplayer plugin for Firefox but Firefox is trying to use the Totem plugin. How can I make Firefox use the Mplayer plugin?

---

### Post by hamil on 2005-10-18
About the plugin from Mplayer.

First you need to find out the name of the Totem plugin used by firefox. Type "about:plugins" in the adress bar. Find the name for the Totem plugin.
Search the computer for the plugin, it is located in the firefox plugin folder. Delete the Totem plugin, and it will use your Mplayer plugin instead.
Simple as that..
Finally I am able to watch some of my favourite programs online again.. :)

And about the w32 codecs, they are not available anymore, due to some legal stuff. 
If you add this line to your /etc/apt/sources.list
```
deb ftp://ftp.nerim.net/debian-marillat/ sarge main
```
You will be able to download the codec. But remember to remove this repositorie when you are done, since this is intended for use by Debian users...

---

### Post by hajk on 2005-10-18
I went through this on the weekend, and followed the instructions in the Ubuntu Wiki -- Documentation - Restricted formats. It's all there: w32codecs, dvd stuff, and much more. BTW, didn't install Mplayer, because Totem can play it all.:razz:

---

### Post by Abandon on 2005-10-18
One of the nicest things in Ubuntu 5.10 is the Help button. Click it..don' t be scared. Look inside and see all you need (and more) if you click on tje link called " Ubuntu 5.10 Starter Guide. Amazing..isn' t it? This is one hell of a distro!! :)

---

### Post by essexman on 2005-10-19
[quote=Abandon]One of the nicest things in Ubuntu 5.10 is the Help button. Click it..don' t be scared. Look inside and see all you need (and more) if you click on tje link called " Ubuntu 5.10 Starter Guide. Amazing..isn' t it? This is one hell of a distro!! :)[/quote]

But I am scared.

I touched it before, and I didn't like it.

I'm touching now.

Oh yes, your'e right, it's wonderful.

My mother always used to say: > Don't touch that, you don't know where it has been.

Well mum, it's been through massive development and it is safe to touch. In fact I  can see that it might well now be beneficial for me.

I might even touch it some more.

Thanks Abandon, it is amazing how things can, change.  Just because something wasn't good before, doesn't mean it isn't good now.

---

