---
title: "Music player error..."
date: 2005-08-16
forum: Desktop Environments
---

### Post by xequence on 2005-08-16
I have all my music on my windows partition. I set it to automatically mount the  windows partition when the computer loaded. WHen I try to play it from Music player it puts up two boxes. "Could not open resource for writing" and "Could Not Pause Playback". I thought it was just doing that in XFCE but then I went back to gnome and it did the same thing. Does anyone know what is wrong? Thanks in advance =P

ALso on the subject of XFCE, how to I make a button in the botton taskbar thingy launch an application? XFCE Is really cool and fast but there are some little annoying things :P

---

### Post by varunus on 2005-08-16
Can you post your /etc/fstab file so we can see exactly how you mounted the drive?

Cannot open the disk for writing?  That's strange...the Music Player should be able to play off of read only drives too, I'm doing it right now...

Can you try copying a music file from the windows partition to the linux one?  And then try playing it?

And could you clarify what you mean by bottom taskbar thingy?  Do you mean the main panel of XFCE?  Can't you add a "launcher" to the XFCE panel?  I think its called a launcher, might be a starter or a launch button or something...been a while since I've used XFCE...

---

### Post by xequence on 2005-08-16
I did it the way ubuntuguide said. Here is the fstab...

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
 

Back in gnome again, they work in Totem. (THe one in windows and copied to linux). ANd they work in Music player... ANd everything else does now too O_O COuld it just be XFCE messing up?

ANd I mean the main panel, yes. I dont know all the names of the docks and panels and stuff :P

I put in the name of the application and it doesent work when I click it.

EDIT: I put the name of the application in and it worked for gnometris but not limewire, which is what I intend to put there.

---

### Post by varunus on 2005-08-16
If they're working in GNOME they should work in XFCE too...try it again.  Are you sure the error came from the Windows partition?  If you had the music player playing something off a CD, or a network, or a USB drive, or something that isn't there now, this could cause this error too...Since the music player makes a library.

If you want to try an alternative music player, I can suggest two: XFMedia is built for XFCE, and beep-media-player is a winamp clone for linux.  You might also like Muine...Google for screenshots of each.  Linux is all about choice :smile:

Can you post a screenshot of what you entered in XFCE?  Like, a screenshot of the dialog...If you can't find how to take a screenshot, the GIMP can do it from "File-Acquire", and you can also type "gnome-screenshot" into a panel (I recommend making a keyboard shortcut to PrintScreen to call gnome-screenshot, not sure how to do that in XFCE though).

EDIT:
Ok, so it worked for Gnometris but not limewire?  Haha, that makes more sense.  For limewire, you need to do the following:
[http://www.ubuntuguide.org/#limewire](http://www.ubuntuguide.org/#limewire)

Except instead of just making a .desktop file for limewire, add a button to the XFCE panel with "runLime.sh" in it.

---

### Post by xequence on 2005-08-16
[[IMG]http://img53.imageshack.us/img53/3900/screen6jk.th.jpg[/IMG]](http://img53.imageshack.us/my.php?image=screen6jk.jpg)


EDIT: Oh, I didnt see the answer you edited. THanks =D Ill try it now.

---

### Post by varunus on 2005-08-16
Ohhh.  I think I know what it is.

The problem isn't your windows drive, its that Rhythmbox uses the sound server ESD to output sound.  In XFCE, esd isn't started automatically.  Open the "Run program" dialog box and type "esd".  Then try rhythmbox again, it should work...You can set it up to open automatically in the XFCE control panel under sessions, i think.

By the way, what sound card do you have?  You, like many people, may start to notice that some programs don't make sound and some do...If I know your sound card I can tell you what to do, and you'll never have to worry about sound again.

---

### Post by xequence on 2005-08-16
My SOund card? Oooooh, thats a hard one... I have no idea, my parents bought it a couple years ago then when they got a newer one I got it. It is 700mhz celeron coppermine with 191 mb ram and a 18.9 GB hdd.

OH, and the limewire thing worked :) THanks alot =D

But I have to go now, ill be back later :P

---

### Post by varunus on 2005-08-16
When you get back, can you post the output of "lspci" in a terminal (applications->system tools->terminal)?  This will list all of the devices in your computer, so it will show what sound card you have.

---

### Post by sandmanfvr on 2005-08-16
I have noticed some sounds play and then they don't to.  I will tell ya, my sound card is a Turtle Beach Santa Cruz.  Does that help?

---

### Post by varunus on 2005-08-17
Most sound cards that have this problem, the following procedure should be followed to fix them (hehe, I'm the author of the original "configure sound properly" howto for ubuntu warty, it was later ported over to the UbuntuGuide...):

1.  Install the package "libesd-alsa0" from synaptic.  Also install the packages "alsa-oss" and "gstreamer0.8-alsa" if you do not have them.

2.  Create a .asoundrc file in your home directory.  Mine looks like this, should work I think (works for me); there are variations in the "Hoary Tips and Tricks" section of the forum.
```
pcm.card0 {

  type hw

  card 0

  mmap_emulation true

}

pcm.!output {
type dmix
ipc_key 1234
ipc_key_add_uid 1
slave {
pcm "card0"
period_time 0
period_size 1024
buffer_size 8192
rate 44100
}
bindings {
0 0
1 1
}
}

#
# DSNOOP input device
#
pcm.!input {
type dsnoop
ipc_key 4321
ipc_key_add_uid 1
slave {
pcm "card0"
period_time 0
period_size 1024

rate 44100
}
}

#
# ASYM duplex device
#
pcm.!duplex {
type asym
playback.pcm "output"
capture.pcm "input"
}

#
# Make the duplex device default
#
pcm.!default {
type plug
slave.pcm "duplex"
}

#
# OSS Compability

pcm.!dsp0 {
type plug
slave.pcm "duplex"
}

ctl.!mixer0 {
type hw
card 0
}
```

3.  Configure ESD to use ALSA:  Open up your /etc/esd/esound.conf using "sudo gedit".  Change it to the following:
```
[esd]
auto_spawn=0
spawn_options=-terminate -nobeeps -as 2
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options= -d output
```

4.  Reboot your computer.

5.  Configure gstreamer to use ALSA:  Open up System->Preferences->Multimedia Systems Selector.  Change input and output to ALSA; you should be able to successfully test both, with a tone for output, and nothing for input (unless you have a microphone).

6.  Enjoy!

You can now set all your programs to use ALSA or ESD for sound output, and everything will make sound.

---

### Post by xequence on 2005-08-17
THis is just conveinent. Everything stopped working, I came back here to read, and you have an answer for everything =D Im doing it now :) THanks!

---

