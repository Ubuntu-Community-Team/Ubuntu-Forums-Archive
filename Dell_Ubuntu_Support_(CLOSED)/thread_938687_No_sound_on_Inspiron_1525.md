---
title: "No sound on Inspiron 1525"
date: 2008-10-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Helios89 on 2008-10-05
Hi all,
a friend of mine just bought a Dell Inspiron 1525 (not the one with ubuntu pre-installed, but the one with windows XP ) and he decided to install Ubuntu and remove completely Windows.

I've installed Hardy from scratch (so no upgrading of Gutsy) and I realized that the sound card does not work. 

It seems that is not even recognized by the system (i remember of having read, as an output of many things tried, "No sound card" or sth similar [the message was in italian])

I just don't know what to do. :(

I've searched in this forum (in particular see [http://ubuntuforums.org/showthread.php?t=776516](http://ubuntuforums.org/showthread.php?t=776516)) but the solution posted in results seems not to be effective.

(The kernel should be 2.6.24.19)

I hope you guys can help me, as I am very puzzled :confused:

---

### Post by Helios89 on 2008-10-05
Well, I found another guide that seems to work fine:

[http://en.nothingisreal.com/wiki/GNU/Linux_on_a_Dell_Inspiron_1525#Sound](http://en.nothingisreal.com/wiki/GNU/Linux_on_a_Dell_Inspiron_1525#Sound)

---

### Post by wilco602003 on 2008-10-05
I've the same problem...no sound and followed Helios89's guide [http://en.nothingisreal.com/wiki/GNU...ron_1525#Sound](http://en.nothingisreal.com/wiki/GNU...ron_1525#Sound) 
but at the point before reboot:-

1.  I can not find the file /etc/modprobe.conf.local: in order to add the line options snd-hda-intel model=3stack

2.  System...Preferences...Sound...gives the following:

    " audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback."

     ...when I test the ALSA sound playback...

Further:-

3.   lspci | grep -i audio responds with

     "00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)"

     ...whereas...

4.    asoundconf list   indicates nothing...(!)

     ...any help gratefully received...

---

### Post by grayamf on 2008-10-16
> **wilco602003 said:**
> I've the same problem...no sound and followed Helios89's guide [http://en.nothingisreal.com/wiki/GNU...ron_1525#Sound](http://en.nothingisreal.com/wiki/GNU...ron_1525#Sound) 
but at the point before reboot:-

1.  I can not find the file /etc/modprobe.conf.local: in order to add the line options snd-hda-intel model=3stack

2.  System...Preferences...Sound...gives the following:

    " audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback."

     ...when I test the ALSA sound playback...

Further:-

3.   lspci | grep -i audio responds with

     "00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)"

     ...whereas...

4.    asoundconf list   indicates nothing...(!)

     ...any help gratefully received...

You shouldn't have followed Helio's guide. His sound card uses the STAC9228 chip set. But the lspci results shows that yours is a Intel 82801H. 
My Inspiron 1525 uses the same chip set as yours, and it worked out of the box(Hardy). So you shouldn't need to make any extra changes.

---

### Post by gbazuin on 2008-10-23
> **wilco602003 said:**
> I've the same problem...no sound and followed Helios89's guide [http://en.nothingisreal.com/wiki/GNU...ron_1525#Sound](http://en.nothingisreal.com/wiki/GNU...ron_1525#Sound) 
but at the point before reboot:-

1.  I can not find the file /etc/modprobe.conf.local: in order to add the line options snd-hda-intel model=3stack

2.  System...Preferences...Sound...gives the following:

    " audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback."

     ...when I test the ALSA sound playback...

Further:-

3.   lspci | grep -i audio responds with

     "00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)"

     ...whereas...

4.    asoundconf list   indicates nothing...(!)

     ...any help gratefully received...


Same problem here. Inspiron 1525 bought with Vista and 8.04 installed with cd from download.
I do have sound, in a terminal window pressing backspace gives beeps (system error sound).
But
for audio test I get
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

Fail to connect instead of Could not open.. But close to the same error message.

lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
exact same message and
 asoundconf list
Names of available sound cards:
nothing.

I googled the error message and see that it's a know bug, but don't see a work around. Can anyone help? Thanks in advance.

---

### Post by iaskedalice09 on 2008-10-25
Similar issue. I bought a pre-installed one 1525n and worked fine up until yesterday... There's no sound device recognised. Any thoughts?

---

### Post by amendt on 2008-10-25
I have a Dell Inpiron 1525 that has a Intel 82801H sound chip that works in skype, and Sound Recorder  I just have to select HDA Intel (hw:Intel,0) as well as I had to download flash 10 to make video.google.com to work.

---

### Post by iaskedalice09 on 2008-10-25
TO ALL: 

Try this, it worked for me (the Second fix, near the bottom):
[Ubuntu 8.04/Issues/No Sound After Distribution Or Kernel Upgrade - DellLinuxWiki](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade)
If already running Ubuntu 8.04 and upgrading to kernel 2.6.24-17-generic

Restore name of sound driver that old modem driver renamed:

$ cd /lib/modules/2.6.24-17-generic/ubuntu/sound/alsa-driver/pci/hda
$ sudo mv snd-hda-intel.ko.REPLACEDBYhsfmodem snd-hda-intel.ko

Remove old sound drivers from kernel module directory:

$ cd /lib/modules/2.6.24-17-generic/updates
$ sudo rm snd-hda-intel.ko
$ sudo rm snd-hda-codec.ko

Rebuild initrd and reboot:

$ sudo depmod -a
$ sudo update-initramfs -u
$ sudo reboot

The modem should now be recognized and fully functional.

---

### Post by Zakhafr on 2008-11-01
I have a similar issue.

Inspiron 1525N - pre-installed Ubuntu
$lspci | grep -i audio 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)


It worked fine until kernel 2.6.24-19
Now with the new 2.6.24-21, there is no sound at all playing because no sound driver is recognized (the tray icons shows it), although Dell released a new version of the 2.6.24-21 from the launchpad (shame it was "unsigned")

At the moment, as a workaround, I modified the GRUB menu.lst so that the system still starts with 2.6.24.19

Any insights to why 2.6.24-21 breaks the sound would be useful.
Apparently I'm not the only one have seen that, on the very active French forums there has been a couple of people loosing sound playback with revision 21 of the kernel.

**[Edit]** Thanks to **IAskedAlice09**, it should be noted that although the tutorial you linked is said to work when migrating to revision 17, it does also work when changing from revision 19 to 21 !
So now I got rid of my own workaround, and I can boot on 2.6.24-21 with no problem.

---

### Post by riesengreen on 2008-11-07
> **iaskedalice09 said:**
> Similar issue. I bought a pre-installed one 1525n and worked fine up until yesterday... There's no sound device recognised. Any thoughts?

Yeah, this is my story exactly...

Any easy-to-understand info appreciated (hope it's okay to post on this thread as a beginner...)

---

### Post by tikki3hill on 2008-11-09
Hi, im having this problem as well...
it seems to be when i download upgrades... it works fine till then, how can i undo/uninstall the correct upgrade(the one that has messed my sound-card up)? im really new to ubuntu...in using and inspiron 1525 with the linux that comes ready loaded (ubuntu 8.04)..
thanks (yeah, i hope its ok to post on here)

---

### Post by iaskedalice09 on 2008-11-11
See this...

[Ubuntu 8.04/Issues/No Sound After Distribution Or Kernel Upgrade - DellLinuxWiki](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade)

---

