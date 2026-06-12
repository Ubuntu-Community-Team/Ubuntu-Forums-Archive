---
title: "WINE issues and WoW"
date: 2006-06-07
forum: Gaming &amp; Leisure
---

### Post by GmAz on 2006-06-07
Ok, I have installed the latest WINE with the World of Warcraft patches.  It seemed to install fine with no errors, however it will not create the drive_c structure.  Everywhere I look says that I should see a .wine folder in my Home folder, but nothing is there.  I Installed WoW just to see if it would and it did the full install, but I can't for the life of me find where it went.  Any help would be great. 

This is what I get when I run winecfg:

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/gmaz', starting in the Windows directory.
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.

Do i need to install Wine as root?

I used wine-0.9.14_wow_i386.deb for the Wine package.  Any help would be great!  Thanks!

---

### Post by GmAz on 2006-06-07
Bump...would have liked at least one response.

---

### Post by tflovik on 2006-06-08
have you tried to run winecfg, you must do that before you can use wine.

:)

---

### Post by omegasyphon on 2006-06-08
did you turn on the option to view hidden files? .wine is a hidden folder

---

### Post by eqisow on 2006-06-08
You need to run winecfg and configure your virtual drives. There are instuctions for doing this on the Wine wiki.

---

### Post by GmAz on 2006-06-08
Ya, I found the "View Hidden Files" option.  Felt like more than a n00b.  As for the winecfg, I was doing that, but didn't know the path for the C: drive in the config.  I found it was /.wine/drive_c/  Took me forever, but i got it.  thanks!

---

### Post by clarke.rainey on 2006-06-09
New version of wine today... 915... and I did not notice it in the system updates... any way for me to revert back to the special WoW package I got from the forums?..

---

### Post by eqisow on 2006-06-09
clarke.rainey, I've already updated the WoW version of Wine on the wiki to 0.9.15. Just follow the instructions and install that.

[https://wiki.ubuntu.com/Wine]("https://wiki.ubuntu.com/Wine")

---

### Post by glaze on 2006-06-09
I'm just curious -- what audio options you people use in winecfg? ALSA or OSS? Direct Sound HW acceleration? Driver Emulation unchecked/checked?

---

### Post by eqisow on 2006-06-10
WoW works better with OSS. I also have Hardware acceleration set to full, which youy should do as well unless it doesn't work for some reason. Driver emulation is unchecked.

---

### Post by 0okie on 2006-06-22
I've tried configuring my wine over and over and I still get it.. I'm doing something wrong, but I don't know what. I set drive C to the path that wine created drive_c at and it still freaks out. When I click browse to change it it says it's failed to create a directory:

"err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ookie\\Desktop"'."

Is there something I need to add to the Windows files Wine created or is it something I need to mess with on the unbuntu desktop? I can't really find anything in Wine FAQs to help me with it, or I keep doing something wrong D:

---

