---
title: "GRUB reinstalled, Ubuntu works, but Vista error on load"
date: 2009-09-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Zantedeschia on 2009-09-20
I have Vista and Ubuntu on dual boot.
After I deleted the media direct partition GRUB didn’t work any longer. So I did the following instructions that I found here in the forum:

“ajmorris
April 26th, 2008, 06:11 AM
hi there,
to fix this, we are going to re-install your grub into the Master Boot Record, so, do the following:

Boot into the live cd, then in a terminal:
1) sudo grub
2) find /boot/grub/stage1 (this will give an output of (hd#,#))
3) root (hd#,#) (where #,# are the numbers found in step 2)
4) setup (hd0)
5) quit
6) reboot

Then, after your computer has rebooted, grub should load again :)”

GRUB works again and I can boot into Ubuntu but when I try to boot Vista it gives me the following error:
“starting up…  a disk error occurred”

The menu.lst reads as follow:

#on /dev/sda2
title Windows Vista/Longhorn (loader)
root (hd0,1)
sacedefault
makeactive
chainloader +1


Do I need to change something in there to make it work?

I also use Bitlocker. Could this be a problem?

I am grateful for any help. Since I am just a "plain user" of Ubuntu and don't go too often into the Terminal and only when I have simple instructions as above, please keep your answers on beginner level so that I can make sense of it. Thank you in advance.

---

### Post by Bucky Ball on 2009-09-20
In Ubuntu, can you open a terminal and post the result of:

```
sudo blkid
```

Even simpler, if you know where the Vista install is you can change (hd0,1) to that. This is saying it is on first physical disk, second partition which indeed equals sda2, but that is not necessarily correct. Generally this should be (hd0,0) if you installed Vista first.

---

### Post by Zantedeschia on 2009-09-21
> **Bucky Ball said:**
> In Ubuntu, can you open a terminal and post the result of:

```
sudo blkid
```Even simpler, if you know where the Vista install is you can change (hd0,1) to that. This is saying it is on first physical disk, second partition which indeed equals sda2, but that is not necessarily correct. Generally this should be (hd0,0) if you installed Vista first.


sudo blkid:
/dev/sda1: UUID="72DA1BB2DA1B7219" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="62aa0e86-a624-4100-9176-c8a1ac62168d" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="54bf4e4e-d2a8-4509-8e1c-58c967cc8873" 

Yes I installed Vista first. So you suggest that I shall change root (hd0,1) to (hd0,0)?
I thought when it says /dev/sda2 then it should say (hd0,1) in root, but this is just an uneducated guess of mine.

---

### Post by lindsay7 on 2009-09-21
It looks like vista is on sda1 or hd(0,0).

You can type sudo gedit /boot/grub/menu.lst and make the change. Do to change anything else.  You may also want to save your current menu.lst file for safty-backup reasons before you make the change.

---

### Post by Zantedeschia on 2009-09-21
> **lindsay7 said:**
> It looks like vista is on sda1 or hd(0,0).

You can type sudo gedit /boot/grub/menu.lst and make the change. Do to change anything else.  You may also want to save your current menu.lst file for safty-backup reasons before you make the change.


It worked!!! Thank you so much Bucky Ball and lindsay7, you guys rock! :)

(I don't know why the entry in menu.lst said "on /dev/sda2" although it was in fact on sda1. This was confusing to me and made me unsure to change anything.)
[]("http://ubuntuforums.org/member.php?u=762393")

---

### Post by lindsay7 on 2009-09-21
Sometimes this menu gets changed. If there is # in front of a line it will be ignored and is considered info only.  You do not need to change this at this time just remember that the line that reads #on /dev/sda2, is incorrect.  It should read #on /dev/sda1.  I would leave it alone.

---

### Post by Zantedeschia on 2009-09-21
> **lindsay7 said:**
> Sometimes this menu gets changed. If there is # in front of a line it will be ignored and is considered info only.  You do not need to change this at this time just remember that the line that reads #on /dev/sda2, is incorrect.  It should read #on /dev/sda1.  I would leave it alone.


Thank you, yes, I was aware that it was a comment field like // in Java. Nevertheless the info confused me. I am thinking about changing it so that it displays the correct sda for future reference before I'm getting too old and forgetful. lol

---

### Post by Bucky Ball on 2009-09-21
Anything that has '#' in front of it is a comment only and/or not read by the system. Thus:

```
# /dev/sda2
```... is just a comment and can be totally incorrect as you found out. You could put:

```
# gammy pigeon!
```... and it would not make any difference as long as you had a '#' there and the correct line under (in your case hd0,0 which is sda1).

---

### Post by Zantedeschia on 2009-09-21
> **Bucky Ball said:**
> Anything that has '#' in front of it is a comment only and/or not read by the system. Thus:

```
# /dev/sda2
```... is just a comment and can be totally incorrect as you found out. You could put:

```
# gammy pigeon!
```... and it would not make any difference as long as you had a '#' there and the correct line under (in your case hd0,0 which is sda1).

Thank you, yes, I am aware that # marks a comment field. I had programming classes before and I know of the concept of comment areas marked by #,', //, /**/, etc. The info sda2 confused me nevertheless since I'm not familiar with the guts of Linux/Ubuntu and where it came from.

---

### Post by drs305 on 2009-09-21
Grub (legacy) doesn't treat all # symbols in /boot/grub/menu.lst as comments however. 

The "Automagic" section contains #'s which are NOT comments in the traditional sense. The # symbol, for whatever reason, is used as a marker for the Automagic section. A line beginning with a single comment symbol is acted upon, while a line starting with ## would be treated as a comment *in this section*.

The AUTOMAGIC section is between 
### BEGIN AUTOMAGIC KERNELS LIST
and
## ## End Default Options ##

Thus, in the following lines, the first is a comment but the second will be acted upon.
> 
## howmany=7   [COLOR="DarkRed"] << Comment[/COLOR]
# howmany=all   [COLOR="DarkRed"]<< Not a comment[/COLOR]


---

