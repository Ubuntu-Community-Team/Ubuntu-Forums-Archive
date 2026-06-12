---
title: "GNOME Desktop Freezing"
date: 2005-07-21
forum: Desktop Environments
---

### Post by awtomlinson on 2005-07-21
My GNOME desktop frequently freezes.  Even if I use Ctrl+Alt+Backspace, the issue is not resolved.  I have to reboot the computer.  When I log back in after the system has booted back up, everything loads properly, but I receive a "Missing Command To Run" error message.  There are no specific symptoms, as this occurs no matter what applications are running.  The only added startup service from the default installation is Firestarter.

---

### Post by musicman2059 on 2005-07-21
What are your system specs?  You may want to try a less resourceful window manager such as XFCS.

```
sudo apt-get install xfcs
```

---

### Post by awtomlinson on 2005-07-21
system specs are fine.  amd xp 3200+ cpu, 1 gb ram.

---

### Post by peter07 on 2005-07-22
I have some similar peoblems. Sometimes Gnome freezes and only last used window is working ( for example one firefox tab, or something ). I check cpu and memory usage (using top comand in console) - but everthing seems to be good. My problems have begun after actualization. I've update my system using sudo apt-get dist-upgrade. What may couses problems??

---

### Post by FunTo on 2005-07-25
I have same problem with my nautilus. ](*,) 

Someone find a solution ??

ps: sorry my english :-#

---

### Post by awtomlinson on 2005-07-28
i did forget to mention that i am able to move my mouse cursor, but i am unable to click on my menu or anything on the desktop or the gnome panel.  i have a feeling that wine is causing this.  i've been using dvd shrink alot with wine.  will test this to verify.

---

### Post by abrouwers on 2005-07-28
Did you check the xorg log to see why it is crashing?  Definitely start there...

---

### Post by awtomlinson on 2005-07-28
how to check the xorg log file?

---

### Post by vladuz976 on 2005-08-03
i am having similar problems
desktop freezes only mouse is usable.
only thing i can do is reboot.
can someone look at this log files please?
i am not really experienced at this.

[http://paste.ubuntulinux.nl/916]("http://paste.ubuntulinux.nl/916")

[http://paste.ubuntulinux.nl/914]("http://paste.ubuntulinux.nl/914")

[http://rafb.net/paste/results/vrj47t41.html]("http://rafb.net/paste/results/vrj47t41.html")

[http://paste.ubuntulinux.nl/919](http://paste.ubuntulinux.nl/919)

---

### Post by ruff on 2005-08-03
Had a similar problem myself. Gnome would just lock up, the mouse would still move, but I could not run any new applications or unfreeze what was already running.

I found that it did not happen however until I did the 'gnome sound fix' listed in the Unoficial Ubuntu Guide. I figured that this fix may have been the cause of my problems and sought to find an answer. 

Upon further investigation in the forums I found a replacement asound.conf script that fixed my problem. It seems it was due to the fix I originally applied not allowing full duplex. The second fix enabled full duplex and this stopped my freezes.

No problems since.

**My Hardware - Modified Toshiba A70 notebook**
512mb Ram
80gb Harddisk - Internal
40gb Harddisk - External USB Device
Internal DVD-Ram/+- writer
ATI Radeon 9100 Mobility Graphic card
1280 x 800 LCD Display
Atiixp sound (ac97)
ALPS Touchpad
Logitech USB optical mouse
3 internal USB2.0 ports
external USB2.0 hub with 7 ports
external D-Link router with internal USB print server
Epson Stylus C65 printer on print server
Lan connection with 3 other Windoze machines through external router also sharing printer.
Internal Firewire (Ieee1394) port - connected to Panasonic digital movie camera.
Internal PCMCIA device
Internal PCI 5 in 1 card reader
Canon A85 Digital still camera connected via USB
Wireless Internet connection via router

All hardware working perfectly under Ubuntu except PCI card reader - will have to purchase an external USB version to obtain linux support. Had to blacklist soundcard in hotplug and add to modules to get sound working correctly - even windoze has a problem with this soundcard on this notebook.

Cheers,

Michael.

---

### Post by vladuz976 on 2005-08-03
the odd thing then would be that i had no sound running. nothing.
the only thing that changed for me since i had these freezing problems is that i tried to configure mutt.
i noticed that everytime i run fetchmail i get the freezing. i don't know if that has anything to do with it.

---

### Post by awtomlinson on 2005-08-03
ruff, can you provide me with the second script to fix the issue?  hopefully this is what it is.  i did indeed use the original sound fix.

---

### Post by ruff on 2005-08-03
>  	ruff, can you provide me with the second script to fix the issue? hopefully this is what it is. i did indeed use the original sound fix.

Not a problem. I cant remember the person who originally posted this, but this is the code.

```
pcm.card0 {
  type hw
  card 0
# mmap_emulation true
}

#pcm.dmix0 {
#  type dmix 
#  ipc_key 34521 
#  slave {
#    pcm "card0" 
#  }
#}


pcm.dmix0 {
	type dmix
	ipc_key 1024 ## needs to be a power of 2
	slave {
		pcm "hw:0"
		period_time 0
		period_size 1024
		buffer_size 8192
               # format S16_LE
		rate 44100 ## not necessary
	}
#slowptr true
}





pcm.dsnoop0 {
  type dsnoop 
  ipc_key 2048
  slave {
    pcm "card0" 
  #  rate 48000
  }
}

pcm.asym0 {
  type asym 
  playback.pcm "dmix0" 
  capture.pcm "dsnoop0"
}

pcm.pasym0 {
  type plug 
  slave.pcm "asym0"
}

# 'dsp0' is espected by OSS emulation etc.
pcm.dsp0 {
  type                  plug
  slave.pcm             "asym0"
}

ctl.dsp0 {
    type                hw
    card                0
}

pcm.!default {
  type                  plug
  slave.pcm             "asym0"
}

ctl.!default {
    type                hw
    card                0
}
```

---

### Post by awtomlinson on 2005-08-04
thanks ruff, i have changed the script, & we'll soon see if this resolves the issue.  i resolved the "missing command to run" error by uninstalling nessus.

---

### Post by RedLine on 2005-08-04
I have a similar problem. My gnome is freezing after I login. This happend when i have changed my CD-RW. I have tryed to switch them back, to install new kernel, xorg, gnome but nothing worked for me. What can i do to fix my system?

---

### Post by neighborlee on 2005-08-04
[QUOTE=awtomlinson]i did forget to mention that i am able to move my mouse cursor, but i am unable to click on my menu or anything on the desktop or the gnome panel.  i have a feeling that wine is causing this.  i've been using dvd shrink alot with wine.  will test this to verify.[/QUOTE]

its not wine..i've had similar ( near exact ) symptoms myself..

I think someone said its a CDROM race condition ( some bug in gnome/kernel ?) and if you keep a CD in the drive it stops it for now..

whether its related to you or not I can't say but it can't hurt ( if it works then you will know )

I have not heard about this asound. conf and the gentleman that brought up the  CDROM fix did n ot mention it i'm fairly certain..

anyway I look fwd to hearing back about this asound.conf possible fix...anyone else tried the  CDROM fix ??:

cheers
neighborlee

---

### Post by vladuz976 on 2005-08-05
ok, so here is what helped me.
all i did is make the rendering of my nvidia card in xorg.conf "false"
that did it. there seems to be a bug in the nividia driver.
never had the problem again.

---

