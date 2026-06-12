---
title: "Video DVDs unrecognized"
date: 2006-05-31
forum: Desktop Environments
---

### Post by Angafirith on 2006-05-31
I'm running Dapper on a Dell Inspiron 1000. Recently, my DVD-ROM drive stopped recognizing video DVDs, saying the drive is empty when it isn't. I've tried data DVDs, and they work fine. I believe that the problem is over a month old at this point.

I seem to remember being able to watch DVDs on my laptop under dapper before, but I think it may have been a few months.

Before anyone asks, I do have totem-xine installed. I've also tried using xine-ui and kaffeine with no success. I don't think that this is the problem, because even trying to do "cat /dev/dvd" gives an error message (cat: /dev/dvd: No medium found).

Any insights into this problem would be appreciated.

---

### Post by Angafirith on 2006-05-31
A quick bump before bed...

---

### Post by Angafirith on 2006-05-31
This is my last attempt to bump this. :(

---

### Post by yostral on 2006-05-31
Does your "/dev/dvd" node exist? If not, create it... it's a symlink to /dev/hdc (or whatever according your CD/DVD drive)

---

### Post by SeanTater on 2006-05-31
Do you have libdvdread3 installed and run install-css.sh? You'll need that to view encrypted DVD's

---

### Post by homersbrain on 2006-05-31
I too have this problem now and then. Certain DVDs appear empty and inaccessable to Ubuntu and yet are fine under windows. It only happens with a handful of DVDs (all of them css encrypted). I have 2 dvd drives - the strange thing is that it usually only happens with one drive (although vary rarely neither will play them, in which case it means a reboot to windows to view them). I have a samsung DVD ROM and a TEAC dvdrw.

---

### Post by Angafirith on 2006-05-31
[QUOTE=yostral]Does your "/dev/dvd" node exist? If not, create it... it's a symlink to /dev/hdc (or whatever according your CD/DVD drive)[/QUOTE]
Yes, it does. It already points to the /dev/hdc, which is my DVD-ROM drive.

[QUOTE=SeanTater]Do you have libdvdread3 installed and run install-css.sh? You'll need that to view encrypted DVD's[/QUOTE]
Yes, I have already installed both of these.

[QUOTE=homersbrain]I too have this problem now and then. Certain DVDs appear empty and inaccessable to Ubuntu and yet are fine under windows. It only happens with a handful of DVDs (all of them css encrypted). I have 2 dvd drives - the strange thing is that it usually only happens with one drive (although vary rarely neither will play them, in which case it means a reboot to windows to view them). I have a samsung DVD ROM and a TEAC dvdrw.[/QUOTE]
I removed windows from this computer back in January or Febuary, so I can't do that. I suppose I should just give up and watch it on another computer.

The movie in question is Final Fantasy VI: Advent Children. I just tried putting the second disc in (the one with all of the special features and such), and it worked perfectly. It even launched Totem when I inserted it.

---

### Post by justinflavin on 2006-06-04
i had similar problems.

fresh Dapper install on a Compaq nx9030 laptop - the DVD drive is a DVD RW drive

totem-xine , libdvdread3 + install.css.sh installed (followed the instructions on the wiki) - no luck.

i couldnt figure it out.  i guess we Linux users are so used not having to reboot, that i forgot the obvious - i hadnt rebooted.

1 reboot later - and bang. i can view video DVDs in Totem.

---

### Post by Angafirith on 2006-06-04
[QUOTE=justinflavin]i couldnt figure it out.  i guess we Linux users are so used not having to reboot, that i forgot the obvious - i hadnt rebooted.

1 reboot later - and bang. i can view video DVDs in Totem.[/QUOTE]
I did try rebooting, but with no success.

Shortly after dapper came out, I decided to try reformatting and installing the final version. After the install, I thought I'd try the DVD again. For some reason that I cannot even begin to comprehend, it all magically worked perfectly for me.

---

