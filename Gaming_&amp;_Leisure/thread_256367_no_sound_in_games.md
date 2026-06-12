---
title: "no sound in games"
date: 2006-09-12
forum: Gaming &amp; Leisure
---

### Post by Beanalby on 2006-09-12
Sound works for system sound effects, totem plays movie and music files, but all games I've tried (gtetrinet, emilia pinball, monkey bubble, etc.) have no sound.  I'm new to X troubleshooting, so I don't know what to look for.  Any advice?

---

### Post by Perfect Storm on 2006-09-13
See if this help: [http://ubuntuforums.org/showthread.php?t=254397](http://ubuntuforums.org/showthread.php?t=254397)

---

### Post by Beanalby on 2006-09-13
> **Artificial Intelligence said:**
> See if this help: [http://ubuntuforums.org/showthread.php?t=254397](http://ubuntuforums.org/showthread.php?t=254397)

Forgot to mention I'd tried that :)  Didn't do anything, as far as I can tell I didn't have any esd running (didn't see anyting in "ps aux | grep esd").

---

### Post by fatsheep on 2006-09-13
Are you using KDE/Kubuntu?  If so try this command:

> killall artsd

---

### Post by Beanalby on 2006-09-13
> **fatsheep said:**
> Are you using KDE/Kubuntu?

Nope, regular Ubuntu, fresh Dapper Drake install.  It's a Dell Inspiron 4000 laptop, I'll post some more details I can scrape up when I get home tonight.

---

### Post by fatsheep on 2006-09-13
You didn't turn off ESD in the sound options did you?  And are you sure your speakers are plugged in? ;)

---

### Post by Beanalby on 2006-09-13
> **fatsheep said:**
> You didn't turn off ESD in the sound options did you?

Nope, I haven't tweaked any sound options, don't even know what ones there are to tweak!

> **fatsheep said:**
> And are you sure your speakers are plugged in? ;)

Unless my speakers have deveoped their own power source that selectively plays audio in .ogg clips in Totem but not games, then yes my speakers are plugged in.  ;)

We're talking about internal speakers on a laptop.  They're definitely not muted and volume is turned up.  I can go from successfully playing audio in totem, to an unsuccessful game, back to successful totem.

---

### Post by fatsheep on 2006-09-13
That's really weird, I hope someone can help you find a solution because I am clueless.

---

### Post by Hhkmac on 2007-11-02
Hi All, thought I'd resurrect this old thread....  the above fix is no good for me either.

I have the exact same problem in my new install of Gutsy.  I was happily playing all manner of games with sound and good graphics (Radeon ATI X1300) and after the upgrade.... well... no sound at all... I get sound in Gweled...but no sound in anything else...... if that helps.

Amarok works fine, Ubuntu system sounds work fine, totem works fine (except if I scroll too fast through a movie it kicks me out!) everything else is fine..... but no sound in games... the kids keep getting shot up in all the FPS's.

After the install that only thing that I did in relation to sound drivers is I added mouse over playing of MP3s using this:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_get_Mouse_over_preview_of_MP3_files_working]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_get_Mouse_over_preview_of_MP3_files_working")

[PHP]
 How to get Mouse over preview of MP3 files working

sudo apt-get install mpg321
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install pulseaudio
sudo apt-get install pulseaudio-esound-compat
sudo apt-get install libasound2-plugins[/PHP]


and now no sound on games!!!  anyone able to help?  :confused:

Cheers in advance to the community!!

---

### Post by Crafty Kisses on 2007-11-02
> **Beanalby said:**
> Sound works for system sound effects, totem plays movie and music files, but all games I've tried (gtetrinet, emilia pinball, monkey bubble, etc.) have no sound.  I'm new to X troubleshooting, so I don't know what to look for.  Any advice?

Try posting the following output:
```
lspci
```
It could be a driver issue.

---

### Post by yongkailoon on 2007-11-02
I am having problems getting sound from native games ? Tried to disable ESD and still no sound from the native games. :(

---

### Post by yongkailoon on 2007-11-03
I am also having the same problem here where everything else has sound except for the native games. :(

---

### Post by Hhkmac on 2007-11-03
> **Codename said:**
> Try posting the following output:
```
lspci
```
It could be a driver issue.

[PHP]macdonald@macdonald-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:09.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
02:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]
02:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)
macdonald@macdonald-desktop:~$ [/PHP]

Here it is... anything jump out as wrong?

Cheers in advance once again.

---

### Post by autocrosser on 2007-11-04
> **Hhkmac said:**
> Hi All, thought I'd resurrect this old thread....  the above fix is no good for me either.

I have the exact same problem in my new install of Gutsy.  I was happily playing all manner of games with sound and good graphics (Radeon ATI X1300) and after the upgrade.... well... no sound at all... I get sound in Gweled...but no sound in anything else...... if that helps.

Amarok works fine, Ubuntu system sounds work fine, totem works fine (except if I scroll too fast through a movie it kicks me out!) everything else is fine..... but no sound in games... the kids keep getting shot up in all the FPS's.

After the install that only thing that I did in relation to sound drivers is I added mouse over playing of MP3s using this:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_get_Mouse_over_preview_of_MP3_files_working](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_get_Mouse_over_preview_of_MP3_files_working)

[php]
 How to get Mouse over preview of MP3 files working

sudo apt-get install mpg321
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install pulseaudio
sudo apt-get install pulseaudio-esound-compat
sudo apt-get install libasound2-plugins[/php]
and now no sound on games!!!  anyone able to help?  :confused:

Cheers in advance to the community!!

Your problem is with:
sudo apt-get install pulseaudio
sudo apt-get install pulseaudio-esound-compat

pulseaudio has problems with games--look thru this thread:
[http://ubuntuforums.org/showthread.php?t=601602&highlight=pulseaudio](http://ubuntuforums.org/showthread.php?t=601602&highlight=pulseaudio)

and there are several other threads about pulseaudio--it is MUCH better than Esound, but there are problems with output still....

---

### Post by Hhkmac on 2007-11-07
Thanks for the reply, but it did not work...

I must have done something else....

Just not sure what.

Is there another output that I can post to help with determining what is wrong?

Cheers

---

