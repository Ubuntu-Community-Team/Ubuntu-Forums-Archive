---
title: "flash making firefox crash !"
date: 2006-07-11
forum: Desktop Environments
---

### Post by neoflight on 2006-07-11
i have the latest flash and FF installed...while watching google videos or other flash based applications...and if i try to pause or fast forward or click on another movie the firefox crashes...

then i have to explicitely kill several instances of FF manually....anyone has the same experience?

any solutions? today i reinstalled FF and flash....but the same problem...please let me know...thanks

---

### Post by Dr. Nick on 2006-07-12
how are you installing flash? The macromedia installer or from the dapper repos?

I have always had a few issues with the flash apps in synaptic, but none with the macromedia terminal install application version

---

### Post by neoflight on 2006-07-16
> **Dr. Nick said:**
> how are you installing flash? The macromedia installer or from the dapper repos?

I have always had a few issues with the flash apps in synaptic, but none with the macromedia terminal install application version



sorry for replying late....

i installed following the wiki.....

```
sudo apt-get install flashplugin-nonfree
sudo update-flashplugin
```
 when it crashes i observe there are atleast  3 instances of FF running....it is driving me crazy.....

is there anyother way to install? is it the same as the terminal install because it asks for stuff at the terminal while installing...
thanks

---

### Post by Dr. Nick on 2006-07-16
check to make sure you have no other flash stuff installed, check for these packages.

From syaptic package manager:
1) uninstall flashplugin-nonfree
2) uninstall libflash-mozplugin (this should also unistall libflash0c2)
3) uninstall libflash-swfplayer
and finally,
4) reinstall flashplugin-nonfree

I have heard that the flashplugin-nonfree just downloads the file from  macromedia and installs it, In theory this should work, but if not then remove it and go to a page in FF with flash and try to install the plugin from within FF, If it fails try the manual installation it mentions

---

### Post by jedsen on 2006-07-16
I've had this problem under Gentoo and Ubuntu. I think it's a problem with the port of Flash. If the problem itself exists in the flash binary, there's little or nothing we can do to fix it. Personally, I've uninstalled it from my system. [-(

---

### Post by gingibash on 2006-07-17
guys and girls, flash crashes when your X server uses 16bit color depth. it is a bug in flash. it works fine in 24bit. developers at macromedia said it will be fixed in next version due to be released next year :( until then either use 24bit or get rid of flash player, like i did.

---

### Post by matthewn on 2006-07-19
thanks, gingibash. DefaultDepth in /etc/X11/xorg.conf now at 24, and no more crashes. this wasn't a problem until a day or so ago, so I'd be interested to know what's gone wrong in the recent shower of updates, but for now, this works... damn you, macromedia!

---

### Post by Arisna on 2006-07-19
This seems to happen with many kinds of SVG content, not just Flash.  Also, the following command can also solve this problem on a per-session basis (i.e. run every time you log in or within the Firefox wrapper script):

```
export XLIB_SKIP_ARGB_VISUALS=1
```

---

### Post by jordilin on 2006-07-19
I had the same problem, and I downloaded and install the flash player provided by macromedia website. Problem solved ;-)

---

### Post by justinflavin on 2006-08-02
> **Dr. Nick said:**
> check to make sure you have no other flash stuff installed, check for these packages.

From syaptic package manager:
1) uninstall flashplugin-nonfree
2) uninstall libflash-mozplugin (this should also unistall libflash0c2)
3) uninstall libflash-swfplayer
and finally,
4) reinstall flashplugin-nonfree

I have heard that the flashplugin-nonfree just downloads the file from  macromedia and installs it, In theory this should work, but if not then remove it and go to a page in FF with flash and try to install the plugin from within FF, If it fails try the manual installation it mentions

thanks!  
this problem was bugging me , and the above solution worked.
and yes - flashplugin-nonfree does download the file from macromedia.

---

### Post by cantormath on 2006-08-02
use this
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

its probably a user-installation error.

---

### Post by justinflavin on 2006-08-02
> **cantormath said:**
> use this
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

its probably a user-installation error.

i've not used automatix - i just followed the dapper UbuntuGuide and manually added stuff via apt-get

The crashing has started again - this time on YouTube.

---

### Post by justinflavin on 2006-08-02
this worked for me
i added this:

export XLIB_SKIP_ARGB_VISUALS=1

to /usr/bin/firefox

(sudo pico /usr/bin/firefox )

i added it under the VARIABLES section near the top of the file:

## Variables
##
MOZ_DIST_BIN="/usr/lib/firefox"
MOZ_PROGRAM="${MOZ_DIST_BIN}/firefox-bin"
export XLIB_SKIP_ARGB_VISUALS=1

---

### Post by justinflavin on 2006-08-09
scrap that. its started crashing again , on youtube.com

i can play youtube videos just fine, but the minute i pause or stop it , firefox seizes up and i have to kill -9 it.

---

### Post by ubu-for on 2006-08-09
Have the same problem, especially with flash ads since Firefox 1.5.0.4!

---

### Post by someguyouknow on 2006-08-09
i had the same problem but it was due to a sound problem and i am unsure that my fix would help you......

---

### Post by Megatog615 on 2006-08-09
Could it be because of the new Firefox 1.5.0.5?

---

### Post by Dommel on 2006-08-19
I have the same problem with Youtube, the strange thing is Firefox only crashes when I let a youtube video which is linked to from another site finish playing.

If i exit or pause it before the end, no problems. Also watching videos on the youtube.com site itself is no problem at all.

---

### Post by Megatog615 on 2006-08-19
I have figured out the problem. If you have an .asoundrc file in your home directory, it causes this. Not sure what setting in the file does cause it, but I renamed it to .asoundrc.backup(to remove it from use), and it fixed the problem.

---

### Post by dr.drake on 2006-08-23
well, a quick fix for me was to install the firefox extension [flashblock]("https://addons.mozilla.org/firefox/433/"), which also solved the problem of too many annoying flash adds with blasting sound..
the problem remained, but was less noticable, because I still use sound in some flash based sites like myspace..

> **Megatog615 said:**
> I have figured out the problem. If you have an .asoundrc file in your home directory, it causes this. Not sure what setting in the file does cause it, but I renamed it to .asoundrc.backup(to remove it from use), and it fixed the problem.

Yes! actually .asoundrc has something to do with it.
I did a lot of searches and it might be a problem with this file, eventhough I did not have this file (yet). 
asoundrc is the config file for the alsa sound engine, the one you should use for firefox, I found [this thread]("http://www.ubuntuforums.org/showthread.php?t=204224&highlight=asoundrc") very helpful.
So I decided to just go for it and create this asoundrc file:
[QUOTE=henriet]Hello.

Here is what I've done on my computer. I hope it will be useful.

First, install alsa-oss
```
sudo apt-get install alsa-oss
```
Then, create the file ~/.asoundrc ([COLOR="Purple"][red:]~$ sudo gedit /home/USERNAME/.asoundrc[/COLOR] ), and copy these lines in it:
```
pcm.dsp0 {
 type plug
 slave.pcm "dmix"
 }

ctl.mixer0 {
 type hw
 card 0
 }

pcm.!default {
 type plug
 slave.pcm "dmix"
 }
```
Restart alsa
```
sudo /etc/init.d/alsa-utils restart
```
After that, edit /etc/firefox/firefoxrc and replace the line beginning with FIREFOX_DSP by this one :
```
FIREFOX_DSP="aoss"
```
Finally, make Amarok and all other applications use alsa. ( For Amarok, choose xine and alsa).

I hope I don't forget anything. Good luck![/QUOTE]
[QUOTE=henriet]In our case, the .asoundrc file makes alsa use dmix.
You can gather more information there :
[http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix](http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix)
[http://www.alsa-project.org/alsa-doc...p/asoundrc.php](http://www.alsa-project.org/alsa-doc...p/asoundrc.php)[/QUOTE]

I've been testing this for the last hour, and it finally seems to work!!!!
I might just unistall the flashblock extension now ;)

---

### Post by Xyc0 on 2006-08-30
My problem turned out to have nothing to do with the flash plugin, but the mozilla-vlc plugin.  It just so happened that the content was both on the same pages.

---

### Post by justinflavin on 2006-09-13
> **dr.drake said:**
> well, a quick fix for me was to install the firefox extension [flashblock]("https://addons.mozilla.org/firefox/433/"), which also solved the problem of too many annoying flash adds with blasting sound..
the problem remained, but was less noticable, because I still use sound in some flash based sites like myspace..



Yes! actually .asoundrc has something to do with it.
I did a lot of searches and it might be a problem with this file, eventhough I did not have this file (yet). 
asoundrc is the config file for the alsa sound engine, the one you should use for firefox, I found [this thread]("http://www.ubuntuforums.org/showthread.php?t=204224&highlight=asoundrc") very helpful.
So I decided to just go for it and create this asoundrc file:



I've been testing this for the last hour, and it finally seems to work!!!!
I might just unistall the flashblock extension now ;)



this also worked for me.  excellent stuff - no more Firefox crashing on YouTube!

thanks!

---

### Post by ocdude on 2006-10-10
I tried this and it did not fix my crash problem, and added another. For some reason, having the .asoundrc file at all makes skype not work, period. This is not a solution I can live with, as skype is my lifeline to my people back in the States.

---

### Post by justinflavin on 2006-10-12
> **Dommel said:**
> I have the same problem with Youtube, the strange thing is Firefox only crashes when I let a youtube video which is linked to from another site finish playing.

If i exit or pause it before the end, no problems. Also watching videos on the youtube.com site itself is no problem at all.

Exact same problem here - i've also narrowed it down to pausing a YouTube video.

when i upgraded to the newest 1.5.0.7 crashing started again whenever i encountered flash.

had to re-add 
export XLIB_SKIP_ARGB_VISUALS=1

to /usr/bin/firefox in the variables section.

still crashes though if i pause a youtube video.

---

### Post by makadam on 2006-10-18
Hello

Thanks for the hint to export the system value. I did following steps to have Firefox and flash working with 16 bit on an DELL Latitude C600:

1) Moving the Firefox link:
```
sudo mv /usr/bin/firefox /usr/bin/firefox.org
``` 
2) Creating a wrapper script, 
```
sudo nano /usr/bin/firefox
```
 with following content :
```

#!/bin/bash

export XLIB_SKIP_ARGB_VISUALS=1
/usr/bin/firefox.org $1 $2 $3 $4 $5 $6 $7 $8 $9

```
3) Making the script executable. That is all. 
```
sudo chmod a+x /usr/bin/firefox
```

This works for me for most homepages with flash as well as with [www.youtube.com](www.youtube.com). 

Best regards.

---

### Post by mohtasham1983 on 2006-11-12
thanks you,
it works for me too

---

### Post by trav5 on 2007-12-25
Me too:guitar:

---

### Post by sashko on 2008-01-20
...and me
tnx

---

### Post by guga31bb on 2008-05-12
still crashes for me on youtube =/

---

### Post by myle on 2008-06-21
The only solution that worked for me.
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/192888/comments/39](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/192888/comments/39)

---

