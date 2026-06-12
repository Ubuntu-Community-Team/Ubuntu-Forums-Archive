---
title: "[SOLVED] The Mana World compile problem"
date: 2009-01-16
forum: Gaming &amp; Leisure
---

### Post by BobSongs on 2009-01-16
[SOLVED]

I'm running Ubuntu Ultimate, version 1.9 based on Hardy Heron.

I've checked the repositories for a game called TMW, or "The Mana World". Version 0.0.24.1-1 is available. However, it lacks a number of features I've come to know under Mac OS X 10.4.

So I tried compiling from source. It's a very small package: 1.2 MB. Available from Sourceforge (address: [http://downloads.sourceforge.net/themanaworld/tmw-0.0.27.tar.gz](http://downloads.sourceforge.net/themanaworld/tmw-0.0.27.tar.gz)).

Installed ahead of time, from source, was guichan-0.8.1 (source: [http://guichan.googlecode.com/files/guichan-0.8.1.tar.gz](http://guichan.googlecode.com/files/guichan-0.8.1.tar.gz)).

When compiling TMW 0.0.27, **configure** threw this error:

> checking for curl_global_init in -lcurl... no
configure: error:  *** Unable to find CURL library ([http://curl.haxx.se/](http://curl.haxx.se/))A search was done in Synaptic Package Manager. Synaptic says these packages are installed:

[LIST]
[*]libcurl3
[*]libcurl3-gnutls
[/LIST]

...and these are available:

[LIST]
[*]libcur3-dbg
[*]libcurl4-gnutls-dev
[*]libcurl4-openssl-dev
[*]libcurl-ocaml
[*]libcurl-ocaml-dev
[*]libflickcurl0
[*]libflickcurl0-dev
[/LIST]

Since compiling depends on the -dev files, I tried installing them. However, Synaptic gives this error message:

> libcurl-ocaml-dev:
Depends: libcurl4-gnutls-dev but it is not going to be installedWhile playing The Mana World, I encountered a player who said he successfully installed version 0.0.27 on Hardy Heron.

Any ideas how to get a -dev version of libcurl on Hardy?

---

### Post by Grant A. on 2009-01-16
I believe you ran the wrong installation script.

[http://forums.themanaworld.org/viewtopic.php?f=7&t=5498&p=47225#p47225]("http://forums.themanaworld.org/viewtopic.php?f=7&t=5498&p=47225#p47225")

That should solve your problem.

---

### Post by BobSongs on 2009-01-18
Well, the above solution did not work, due to the nature of the version of Hardy Heron.

As it was clearly detailed, I'm using Ubuntu Ultimate, 1.9, based on Hardy Heron.

It may have some dependencies already installed that standard Hardy does not. So trying to get conflicting libraries running is just not going to happen in this version.

However, I do have a solution. I installed Wine. I then set up Wine and made sure the sound worked. I then installed TMW, the Windows version. At first the game was very choppy. I unchecked OpenGL, started it again, and it ran as well in Wine as I've seen it run in Ubuntu, Windows or the Mac.

---

### Post by Ripfox on 2009-01-18
That is precisely why I do NOT use distros like "Ubuntu Ultimate" 

I can configure it myself, thank you :lolflag:

---

### Post by BobSongs on 2009-01-22
> **Ripfox said:**
> That is precisely why I do NOT use distros like "Ubuntu Ultimate" 

I can configure it myself, thank you :lolflag:
Well. I'm very happy for you, Ripfox.

[Offtopic rant ahead]
For those who come across this thread, I will say that I'm not a distro-hopper. My PC's a family PC. And though I enjoy installing applications and features, it is a slow process after a fresh installation, true? (Keeping in mind here that Ubuntu is released every 6 months and not every 5 years like Windows NT.)

And a fresh installation of the **Standard Ubuntu Distribution** means the PC is not immediately able to satisfy the needs of a bunch of impatient teenagers with whom I share a house.

If that were not the case, trust me: I'd be learning about Linux from the ground up with a far more challenging distro such as Gentoo or even DoItYourself Linux. And I would not cry if I couldn't get X working within the first few weeks.

We're all entitled to our opinions, even if they resemble pointless gloating. And as the creator of this thread, I believe I'm entitled to the last word.

:D

---

