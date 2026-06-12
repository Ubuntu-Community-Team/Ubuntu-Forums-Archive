---
title: "wow is not so smooth under wine as in windows"
date: 2006-12-22
forum: Gaming &amp; Leisure
---

### Post by ukasz20 on 2006-12-22
hi

i have installed al like in this [http://ubuntuforums.org/showthread.php?t=120615](http://ubuntuforums.org/showthread.php?t=120615)
i haven't compiled wine. just installed it from repo

my wow version is 2.0
the problem is that it is slow. it is breaking. 

do you have any ideas ?

---

### Post by raul_ on 2006-12-22
What are your system specifications? Check if you're running out of RAM or if your CPU usage is too high

---

### Post by ukasz20 on 2006-12-22
i have 1 gb of ram and amd 64 2500 real time clocking

---

### Post by AndersAA on 2006-12-22
[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)
look for "DisabledExtensions", and do what it says.  Improves performance on both ati and nvidia hardware.

also
mkdir -p Cache/WDB/enGB
in your wow directory.

---

### Post by ukasz20 on 2006-12-22
ok it is working :-D 

i have another issue. fonts and all what is written is not displaying correctly. in game is ok but for example when i was installing wow the letters of licence was a total mes

---

### Post by AndersAA on 2006-12-22
if it's ok ingame I wouldn't worry too much about it ;)

---

### Post by hikaricore on 2006-12-22
> **ukasz20 said:**
> ok it is working :-D 

i have another issue. fonts and all what is written is not displaying correctly. in game is ok but for example when i was installing wow the letters of licence was a total mes

eh the ELUA text for the installer is garbled for everyone, that's normal.

I saw it work once, I don't know why but it never happened again lol.

---

### Post by Sammi on 2006-12-22
I'm glad everything worked out for you :D

I would just like to point out that that was an old howto you were using. This one should hopefully be up to date and working:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by ukasz20 on 2006-12-26
hi i have a problem with wow. it freezes after some time of playing.

---

### Post by Sammi on 2006-12-29
It crashes without outputing any errors? 

I haven't experienced this problem before :-k

What are your system specs, cpu, ram, grafics card, etc?

---

### Post by ukasz20 on 2006-12-29
i have athlon 64 2800+ 1 gb of ram radeon 9500

i have experienced the same crash sheme on windows but i have reinstalled my drivers and under windows it is working

---

### Post by Sammi on 2006-12-29
Ok then you definatively should try to install new ATI drivers.

I recomend you try this guide first:
[http://wiki.cchtml.com/index.php/Ubu...allation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")

then:
[http://www.ubuntuforums.org/showthre...ighlight=fglrx]("http://www.ubuntuforums.org/showthread.php?t=305665&highlight=fglrx")

Automatix Bleeder also has an option for installing ATI drivers automaticly, but it may not be stable:
[http://www.getautomatix.com]("http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_Bleeder_.28only_on_Ubuntu_6.10_i386_as_of_now.29")

---

### Post by ukasz20 on 2007-01-01
ok thx it is working now.

but i know that i should be downloading patch to wow but the news site before launching game doesn't appear:neutral:
i have done the disable extentions option and it is much better now but i still see that the game isn't so smooth
same goes for the sound

maybe i am too demanding ...

---

### Post by Sammi on 2007-01-02
> **ukasz20 said:**
> ok thx it is working now.

but i know that i should be downloading patch to wow but the news site before launching game doesn't appear:neutral:
i have done the disable extentions option and it is much better now but i still see that the game isn't so smooth
same goes for the sound

maybe i am too demanding ...
Have you configured Wine to use OSS for sound instead of ALSA? You do this by running the command "winecfg" in a terminal.

If you are able tu run the game, then that means that you are up to date regarding patching, and therefor you should not be downloading any patch right now.


I believe that the "news site" you are referring to is another .exe file, which in turn launches the wow.exe for you. I'm not at my own computer right now, so I can't check, what this file is called, but you can try looking in your wow folder for a .exe file, that seems to fit the bill.

---

### Post by ukasz20 on 2007-01-02
yes  use oss 

under windows it is downloading a patch but i think that it is not important becouse i am playing the game

---

