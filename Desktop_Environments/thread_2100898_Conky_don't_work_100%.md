---
title: "Conky don't work 100%"
date: 2013-01-03
forum: Desktop Environments
---

### Post by scdragos on 2013-01-03
Ubuntu 12.04, on Dell Inspiron N5110 (Sandy Bridge technology).
For video card, I installed bumblebee.

My Conky is taken from Pinguy and multiplied in 4 sections: .conkyrc1, .conkyrc2, .conkyrc3 and .conkyrc4.
After loading the operating system, is so (.conkyrc2 missing):

[[IMG]http://i.imgur.com/TVXrjs.png[/IMG]]("http://imgur.com/TVXrj")

After log out and log in, is complete (appears .conkyrc2):

[[IMG]http://i.imgur.com/LyEbAs.png[/IMG]]("http://imgur.com/LyEbA")

My Conky is [here]("https://dl.dropbox.com/u/19391613/Conky_for_test.tar.gz") (7 hidden files).

Loaded from Terminal:

[[IMG]http://i.imgur.com/gSTFhs.png[/IMG]]("http://imgur.com/gSTFh")

Can find a solution for this problem? Thank you!

---

### Post by ajgreeny on 2013-01-03
I assume you are starting conky four separate times in the startup applications configuration with four commands ```
conky -c conkyrc1
```followed by conkyrc2 etc etc.

I wonder if it would help to add the -p option to the commands, ie pause for a few seconds, each one slightly different pause time, eg;-
conky -p 5 -c conkyrc1
conky -p 10 -c conkyrc2
conky -p 15 -c conkyrc3
etc.

---

### Post by stinkeye on 2013-01-03
If ajgreeny's solution doesn't work,
Run...
```
killall conky
```

Then```
conky -c ~/.conkyrc2
```
and paste the terminal output.

What version of conky are you using.
```
conky --version
```

---

### Post by scdragos on 2013-01-03
Thanks for the answers!

@ajgreeny

Conky start with script conky_start.sh
I replaced the contents of the script:
```
sleep 30
conky -c ~/.conkyrc1 &
conky -c ~/.conkyrc2 &
conky -c ~/.conkyrc3 &
conky -c ~/.conkyrc4
```

with:

```
sleep 30
conky -p 5 -c ~/.conkyrc1 &
conky -p 10 -c ~/.conkyrc2 &
conky -p 15 -c ~/.conkyrc3 &
conky -p 20 -c ~/.conkyrc4
```

No change in operation: .conkyrc2 does not charge.

@stinkeye

[[IMG]http://i.imgur.com/QlaBls.png[/IMG]](http://imgur.com/QlaBl)

Version of Conky is 1.8.1

```
dragos@office-pc:~$ conky --version
Conky 1.8.1 compiled Wed Dec 14 10:22:49 UTC 2011 for Linux 2.6.24-30-server (x86_64)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft
  * ARGB visual

 Music detection:
  * Audacious
  * MPD
  * MOC
  * XMMS2

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * Weather (METAR)
  * Weather (XOAP)
  * wireless
  * config-output
  * Imlib2
  * apcupsd
  * iostats
  * ncurses
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2
dragos@office-pc:~$ 

```

---

### Post by stinkeye on 2013-01-03
Does the conkyrc2 display when loaded by itself?

---

### Post by scdragos on 2013-01-03
Yes:

[[IMG]http://i.imgur.com/5eyvqs.png[/IMG]](http://imgur.com/5eyvq)

---

### Post by stinkeye on 2013-01-03
> **scdragos said:**
> Yes:

[[IMG]http://i.imgur.com/5eyvqs.png[/IMG]](http://imgur.com/5eyvq)

The version of conky in 12.04 had a few bugs.

Use this ppa to upgrade conky to see if it will fix...
```
sudo add-apt-repository ppa:vincent-c/conky
sudo apt-get update
sudo apt-get install conky-all
```

P.S. No need for sudo when running **killall conky**. The process is owned by you.

You can also try editing the lines in conkyrc2...
```
own_window_type [COLOR="Red"]override[/COLOR]
[COLOR="red"]#[/COLOR]own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

to
```
own_window_type [COLOR="red"]normal[/COLOR]
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```
making sure to remove the "[COLOR="red"]#[/COLOR]"

---

### Post by scdragos on 2013-01-03
I updated conky and after restarting the computer, display including .conkyrc2.

Thank you very much!

---

