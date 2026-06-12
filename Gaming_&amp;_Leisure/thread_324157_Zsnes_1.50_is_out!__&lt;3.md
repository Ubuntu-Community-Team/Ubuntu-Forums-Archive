---
title: "Zsnes 1.50 is out!  &lt;3"
date: 2006-12-23
forum: Gaming &amp; Leisure
---

### Post by hikaricore on 2006-12-23
I presonally havn't had a chance to compile it myself but after reading
the change log, I'd imagine alot of other people wouldn't be so lazy.

hehe

Normally I'd post their changelog in my post, but errrmmm it's way to
long with this release.  Anyway I'm just passing along the info, here's
some linkies:

[Download Source]("http://prdownloads.sourceforge.net/zsnes/zsnes150src.tar.bz2") | [Changelog]("http://www.zsnes.com/index.php?page=news") | [LinuxEmu]("http://linuxemu.retrofaction.com/")

---

### Post by play0r on 2006-12-23
i just compiled it...
unfortunately if you play zsnes via netplay you won't be too pleased with this release.
although, if you play any of the games that received fixes in the changelog this is definately for you.
i'm personally waiting for the next release that has a functioning netplay feature (which should be out early in the new year i would assume), because i play a lot of street fighter 2 over the net.

ez,
play0r

---

### Post by bebop_tango on 2007-01-05
First, I downloaded a precompiled .deb package by madman2k:

[http://www.madman2k.net/files/zsnes_1.500-0ubuntu1_i386.deb]("http://www.madman2k.net/files/zsnes_1.500-0ubuntu1_i386.deb")

Almost everything is working wonders... the auto-patch bug was fixed, the FPS clocked in at 60/60 without openGL support... but the sound is buggy... just like v1.42 with the libsdl1.2debian-alsa package installed instead of libsdl1.2debian-oss or libsdl1.2debian-all. The thing is, I HAVE libsdl1.2debian-all properly installed...

Well, I tried to compile the source-code myself. It worked the exact same way...

Has anyone experienced the same thing...?

---

### Post by bebop_tango on 2007-01-05
Ha!

:) 

It's **buggy** with libsdl1.2debian-all but **works fine** with libsdl1.2debian-oss. This *should* have worked with either installed, though... hope it'll work on Feisty Fawn...

:mrgreen:

---

### Post by Josey on 2007-01-05
sweet :)

thanks for the .deb for us noobs :p

---

### Post by braveerudite on 2007-01-14
Yes, Thank you for compiling it for us Linux Noobs.  I hope they add this new release to the repo.

---

### Post by BoyOfDestiny on 2007-01-14
> **bebop_tango said:**
> Ha!

:) 

It's **buggy** with libsdl1.2debian-all but **works fine** with libsdl1.2debian-oss. This *should* have worked with either installed, though... hope it'll work on Feisty Fawn...

:mrgreen:

Hmm, I used 1.50 on edgy, now on feisty... What exactly is wrong with sound? 
Crackling/fuzzy? Try setting the samplerate to 48000hz.

If that doesn't do it, make a file called .asoundrc in your home dir.

stick this in it:
```
pcm.!default {
	type hw
	card 0
	}

	ctl.!default {
	type hw           
	card 0
        }
```

Then launch zsnes... Fixed?

---

### Post by braveerudite on 2007-01-14
> **BoyOfDestiny said:**
> Hmm, I used 1.50 on edgy, now on feisty... What exactly is wrong with sound? 
Crackling/fuzzy? Try setting the samplerate to 48000hz.

If that doesn't do it, make a file called .asoundrc in your home dir.

stick this in it:
```
pcm.!default {
	type hw
	card 0
	}

	ctl.!default {
	type hw           
	card 0
        }
```

Then launch zsnes... Fixed?

In the home folder?   Hu?   I don't want files all thrown around in my home folder.  I like to keep things nice and neat (in order)

Why in home folder?

Please forgive my noobness,but isn't this file supposed to be put where zSNES is installed?

---

### Post by BoyOfDestiny on 2007-01-15
> **braveerudite said:**
> In the home folder?   Hu?   I don't want files all thrown around in my home folder.  I like to keep things nice and neat (in order)

Why in home folder?

Please forgive my noobness,but isn't this file supposed to be put where zSNES is installed?

Hi. Only changing the samplerate is a zsnes setting (you can do it from zsnes's gui)

The file I suggested to create is for ALSA (advanced linux sound architecture)
it solved my problem of sound static in several apps...

As for your home folder, that's where all your personal settings are.

Open up nautilus, press ctrl + h (show/hide hidden files)

You'll see a bunch of folders and files

making the file .asoundrc
with that period in front, will make it hidden like the rest.
You will have zero clutter, and if it doesn't help. Just remove it. :)

FYI for zsnes settings, it's stored in the .zsnes folder in your home

Makes things easy for reinstall and for multiple users to keep your own settings. Rather than where zsnes is installed. 
Which you'd need root privileges to write to directly... it just means things are more secure with system wide apps separate. :)

---

### Post by braveerudite on 2007-01-15
> **BoyOfDestiny said:**
> Hi. Only changing the samplerate is a zsnes setting (you can do it from zsnes's gui)

The file I suggested to create is for ALSA (advanced linux sound architecture)
it solved my problem of sound static in several apps...

As for your home folder, that's where all your personal settings are.

Open up nautilus, press ctrl + h (show/hide hidden files)

You'll see a bunch of folders and files

making the file .asoundrc
with that period in front, will make it hidden like the rest.
You will have zero clutter, and if it doesn't help. Just remove it. :)

FYI for zsnes settings, it's stored in the .zsnes folder in your home

Makes things easy for reinstall and for multiple users to keep your own settings. Rather than where zsnes is installed. 
Which you'd need root privileges to write to directly... it just means things are more secure with system wide apps separate. :)

Thx man that is really good info. :)

---

### Post by hikaricore on 2007-01-15
> **BoyOfDestiny said:**
> Hmm, I used 1.50 on edgy, now on feisty... What exactly is wrong with sound? 
Crackling/fuzzy? Try setting the samplerate to 48000hz.

If that doesn't do it, make a file called .asoundrc in your home dir.

stick this in it:
```
pcm.!default {
	type hw
	card 0
	}

	ctl.!default {
	type hw           
	card 0
        }
```

Then launch zsnes... Fixed?

thanks for this, i'll be testing it out when I get home ^.^

---

### Post by braveerudite on 2007-01-15
I can confirm that this trick does work!  w00t

I'm not a coder, would anyone explain what the .asoundrc exacly did to fix it? (I like to learn new things)

The crt+h = Hide/See hidden files trick is awsome.  Thanks.

---

### Post by BoyOfDestiny on 2007-01-15
> **braveerudite said:**
> I can confirm that this trick does work!  w00t

I'm not a coder, would anyone explain what the .asoundrc exacly did to fix it? (I like to learn new things)

The crt+h = Hide/See hidden files trick is awsome.  Thanks.

Glad it worked for you.

From ALSA's home page:

"Why asoundrc?

What is it good for, why do I want one?

Neither the .asoundrc nor the asound.conf files are required for ALSA to work properly. Most applications will work without them. They are used to allow extra functionality, such as routing and sample-rate conversion, through the alsa-lib layer."

[http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php?company=Generic&card=Generic&chip=Generic&module=Generic](http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php?company=Generic&card=Generic&chip=Generic&module=Generic)

---

