---
title: "Fixing a Windows Boot Problem from Ubuntu"
date: 2005-06-14
forum: Desktop Environments
---

### Post by NakedGreekStatue on 2005-06-14
(I wasn't exactly sure which forum to put this thread.)

I used to have Redhat 8.0 installed with my WIndows XP HE. I have Partition Magic 8.0 on it and I hadn't used Linux for a long time as when I installed XP it overwrote the GRUB installer so I could not select linux at boottime. I wasnt using Linux much at that time, so no biggie. But about a week ago I saw an option in Partition Magic where you set to boot a specific partition. So out of curiosity I set it to boot my old RH Linux partition and restarted to the computer. Well to make a long story shart the RH didnt work so I installed Ubuntu over it and it works great. But now I still want to use XP for some things but I when I select WIndows XP at start up it loads fine but before it gets to the login screen it displays an error message that I will copy down soon. And then the computer restarts itself. I assume that something Partition Magic wrote is trying to make it boot up the linux partition or something like that. So I need to find some way to disable the PM intervention and tell XP to boot itself up normally. Could somebody help me out here? ](*,)

---

### Post by Takis on 2005-06-14
Hi there,

Hit F8 while Windows is just beginning to boot (before the black background with the logo appears) and select safe mode. Hopefully it won't start up Partition Magic.
Out of curiousity, why are you using it anyway? My friend insists on using it too, but there's nothing it can do that a Linux & Windows box can't.

(Moderators: is this in the right subforum?)

---

### Post by NakedGreekStatue on 2005-06-14
[QUOTE=Takis]Hi there,

Hit F8 while Windows is just beginning to boot (before the black background with the logo appears) and select safe mode. Hopefully it won't start up Partition Magic.
Out of curiousity, why are you using it anyway? My friend insists on using it too, but there's nothing it can do that a Linux & Windows box can't.

(Moderators: is this in the right subforum?)[/QUOTE]
 I am using mainly for Photoshop which I could not get to work with WIne. I also play games on windoz(of course). I just cannot work with Gimp. I'll try what you said

---

### Post by Takis on 2005-06-14
No I wasn't questioning Windows, I'm not quite that elitist yet.

I meant Partition Magic.

---

### Post by NakedGreekStatue on 2005-06-14
I used PM(illegally i confess) to resize my NTFS partition to make room for linux. I could not find another program that could easily resize NTFS partitions.

But anyways I kept pressing F8 the whole time after I selected WIndows XP on the GRUB list. Nothing happened and I got the same error as before. "autocheck not found - skipping AUTOCHK" and the computer rebooted.

---

### Post by Takis on 2005-06-14
[QUOTE=NakedGreekStatue]I kept pressing F8 the whole time after I selected WIndows XP on the GRUB list.[/QUOTE]
Not continuously, I hope...
(did you hold it down, or keep whacking it?)

---

### Post by NakedGreekStatue on 2005-06-14
lol I kept whacking it. Should I try holding this time?

---

### Post by Balut on 2005-06-14
Your Windows system partition is marked as "hidden NTFS".

You can download a program called ptedit from PowerQuest for free.

Boot to a DOS disk, run PTEdit, and change the "partition type" from hex 0x17 to hex 0x07 if your Windows partition is NTFS or 0x1C to 0x0B for FAT32.

---

### Post by Takis on 2005-06-14
No, whacking it is the right way to go. That's very strange that it won't let you get into it.

For clarification, is the exact error message this:
autochk program not found. skipping autocheck
?

---

### Post by NakedGreekStatue on 2005-06-14
[QUOTE=Takis]No, whacking it is the right way to go. That's very strange that it won't let you get into it.

For clarification, is the exact error message this:
autochk program not found. skipping autocheck
?[/QUOTE]
 other way around. "autocheck not found. skipping AUTOCHK"

---

### Post by NakedGreekStatue on 2005-06-14
Balut - I dont have a DOS disk, but I did find a trial version of this program [http://www.dfsee.com/dfsee.htm](http://www.dfsee.com/dfsee.htm) that should be able to do the same thing. Do I just follow the same instructions as you gave me with this program? I am not sure what to do because I don't really know what is wrong...

---

### Post by Balut on 2005-06-15
If you have a CD Burner, you may want to try
The Ultimate Boot Disk:  [http://ubcd.sourceforge.net/](http://ubcd.sourceforge.net/)

This disk has several disk partition editors & one of them may be able to switch the hidden status of your Windows partition.

To clarify your problem, when you used Partition Magic to set your boot partition, it takes over your MBR as the boot loader & hides your other system partition, which in your case was your Windows partition.  

You then installed Ubuntu, which most likely overwrote the MBR with GRUB, which is a linux boot loader.  The problem is, GRUB doesn't know how to unhide your Windows partition.

Did you create a boot disk with Partition Magic when you installed it?

---

### Post by Balut on 2005-06-15
If you do have GRUB as your boot loader, then all you have to do to unhide your Windows partition is to add an “[COLOR=Red]unhide[/COLOR]” command before the “root” line in your menu.lst file.

Edit the your menu.lst file by entering the following command into a terminal.

```
sudo gedit /boot/grub/menu.lst
```

Example below:

title Windows XP Professional
[COLOR=Red]unhide[/COLOR] (hd0,0)
root (hd0,0)
makeactive
chainloader +1

This example is assuming that your Windows partition is on the first partition of your first hard drive.

---

### Post by NakedGreekStatue on 2005-06-15
Editing the menu.lst file worked like a charm. Hey thanks a lot! \\:D/

---

### Post by Takis on 2005-06-15
Woah, that was totally over my head. Point of the story though I guess is that you may want to avoid Partition Magic.

---

### Post by Balut on 2005-06-15
Your welcome.  I felt your pain, since I did exactly the same thing to my system with Partition Magic.  

Just remember that if you reinstall Windows it will overwrite your MBR again.  You will need a Linux boot disk or a live cd to restore GRUB.  Or you could edit your Windows boot.ini file to account for your Linux partition.

There are several good HOWTO's out there on dual-booting.

---

