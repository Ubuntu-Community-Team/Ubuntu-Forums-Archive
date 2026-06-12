---
title: "Why I got windows desktop before login screen?"
date: 2009-05-22
forum: General Help
---

### Post by cd-r80 on 2009-05-22
Just before ubuntu login screen opens I got windows XP desktop screen for a half second. Why? I had this before In Hardy, but It showed my old ubuntu desktop. Strange memories?

---

### Post by frenchn00b on 2009-05-22
> **cd-r80 said:**
> Just before ubuntu login screen opens I got windows XP desktop screen for a half second. Why? I had this before In Hardy, but It showed my old ubuntu desktop. Strange memories?

Could you be please mroe specific, or even. add screenshots?
 
(ximport)

impttroot.sh
```
chvt 7 ; sleep 5 ; XAUTHORITY=/var/lib/gdm/:0.Xauth DISPLAY=:0.0 import -window root prtscrshot.png
```

---

### Post by Astenorh on 2009-05-22
Can you send some specs as well!

---

### Post by lisati on 2009-05-22
> **cd-r80 said:**
> Just before ubuntu login screen opens I got windows XP desktop screen for a half second. Why? I had this before In Hardy, but It showed my old ubuntu desktop. Strange memories?

I've had similar on occasion, and suspect that it could be random "rubbish" that's left in video RAM after you restart your computer.

---

### Post by Legace on 2009-05-22
> **cd-r80 said:**
> Just before ubuntu login screen opens I got windows XP desktop screen for a half second. Why? I had this before In Hardy, but It showed my old ubuntu desktop. Strange memories?

It doesn't show the windows login screen, but a "memory" from Windows. I know this is a bug, just don't know how to fix it..

---

### Post by Astenorh on 2009-05-22
Got a similar thing on my cell phone! It is surely the graphic's cards memory!

Or maybe your computer has nightmares of Windows!

---

### Post by Name change on 2009-05-22
I agree it must be the graphics card memory...
It not in this form but similar happened to me. But not any more.

BTW: I use nVidia 180.51 driver... And KDE.
But it stopped somewhere about 180.30 release.

---

### Post by bacardiandwatermelon on 2009-05-22
> **lisati said:**
> I've had similar on occasion, and suspect that it could be random "rubbish" that's left in video RAM after you restart your computer.

Yeah the same thing happens to me, it only shows for a split second, not a major at all... I have a ATI Mobility FireGL 9000

---

### Post by ActiveFrost on 2009-05-22
ATI Radeon™ 9200 PRO and yeah, I've seen this joke as well. Right before loading live session user ( before installing Ubuntu ) it loads my Windows screen ( 1-2 seconds ) :D

---

### Post by cd-r80 on 2009-05-22
I don't know when execute that command to get that screen. But like already answered it is likely a video memory problem. I thought that it does not appear Any more in Intrepid. It was annoying little security flaw in Hardy to see old screens before login. Bank accounts etc. Dont, know how to clean that memory?

I use Ati 9250.

---

