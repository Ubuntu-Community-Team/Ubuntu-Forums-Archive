---
title: "xserver problem"
date: 2009-03-17
forum: Desktop Environments
---

### Post by Froodolt on 2009-03-17
Hi all,

I screwed up my xserver settings, it's my fault, I know. 
My video-card is a RADEOM igp 345m.
After google-ing around, I somehow got xserver back on-line in low graphics mode.
The desktop effects didn't work any more, because apparently there were no drivers installed.
So I got Envy installed, but that says that it doesn't support my os.
Found a web page to install the ati drivers, via this forum.
But now my xserver jams on start-up again, I only get a very colourful screen, that's it.
Its not that I don't like colours, but I would very much like to see xserver working again!

Tried 'Dpkg -reconfigure xserver-xorg' but that doesn't work. 
' aticonfig –initial -f ' tells me something like no adapter found or something. (switching back and forward from windows xp to Ubuntu is dual boot so I cant recall exactly atm)
Tried a dozen other commands/scripts/stuff from forums/blogs but it doesn't work for me, or I am doing something very wrong.

I don't know what to do anymore, can someone help me solve my problem please?

Thanks in advance!! (very much!!)

---

### Post by overdrank on 2009-03-17
> **Froodolt said:**
> Hi all,

So I got Envy installed, but that says that it doesn't support my os.

Thanks in advance!! (very much!!)

Hi and what version of Ubuntu are you using?
Have you tried the xfix option when booting into recovery mode. Recovery mode is usually the second choice when booting from grub. Then when xfix is complete then you should be given the option to boot normally.

---

### Post by Froodolt on 2009-03-18
@overdrank,

Using Ubuntu 8.10.

Got EnvyNG installed now, now EnvyNG runs.
There is only 1 ATI driver I can chose to install, but thats not recommended by EnvyNG.

Why isn't there some way to reset everything back to default?
```
 Dpkg-reconfigure -phig xerver-xorg 
```
Didn't work.
xfix Didn't work for me either.

I almost don't dare to say:oops:, but I took my live-CD and made a fresh install.
I'm not gonna touch my graphic settings anymore, because I'm a bit scared of xserver now. :-#
Its in my nature to press every button, try all the packages and experiment with config-files, but when x goes bad.....8-[
I just don't have enough Linux/Ubuntu knowledge yet.:-\"

I'm very pleased with Ubuntu, besides my disrupted relationship with xserver...:cool:

Thanks anyway! :guitar:

---

### Post by overdrank on 2009-03-18
> **Froodolt said:**
> @overdrank,


```
 Dpkg-reconfigure -phig xerver-xorg 
```


The command is ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then restart x with ctrl, alt, backspace keys

---

### Post by Froodolt on 2009-03-18
Sorry, I forgot to post that I ran it as root.:oops:

When I had no x at all (only frozen colorful screen), I ran:
```
startx
```
to restart xserver when in recovery-mode.

Thanks! O:)

---

