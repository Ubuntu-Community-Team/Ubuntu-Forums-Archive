---
title: "VisualBoyAdvance tip"
date: 2005-12-23
forum: Gaming &amp; Leisure
---

### Post by barfos on 2005-12-23
I downloaded VisualBoyAdvance with synaptic package manager, and the emulator worked fine (I love it when that happens 8)).  But there was a problem on exit 'error writing .sav file.'  I tried a few things and theres was no problem with permissions of the roms folder.

Here's how I fixed it.  In the file /etc/VisualBoyAdvance.cfg where it says batteryDir= and has nothing, that is supposed to imply save the .sav files in the same directory as the rom.  Since this didn't work, AND since the installation put an empty and un-used folder in my home directory /home/evan/.vba, i decided to put that in the /etc/VisualBoyAdvance.cfg config file. Note that you'll need to use sudo to write to that file.

sudo gedit /etc/VisualBoyAdvance.cfg

```

batteryDir=/home/yourname/.vba
```
where yourname is your user name.

you might want to set the other directory variables to that directory too, like for save state and capture.

Why isn't the ~/.vba folder in the config file by default?
Why won't the save to rom folder default behavior work?
Bah!! This is the kind of simple thing that windows lovers love to hate about linux! Or maybe I just installed a weird package and no one else but me had this problem.

Hope this helps!!!
barfos

---

### Post by atf487 on 2005-12-23
Good call, I was wondering how to get this to work...

Thanks.

---

### Post by Shadomaster_Kitty on 2005-12-27
I've been having issues with this thing - I can't open files. When I try to, I get a memory dump and it dies completely. Can anyone advise me as to what it's doing wrong, and what needs to be added or changed?

---

