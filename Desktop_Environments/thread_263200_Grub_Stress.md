---
title: "Grub Stress"
date: 2006-09-22
forum: Desktop Environments
---

### Post by Old Pink on 2006-09-22
Here's the story so far:
[http://matt.moved.in/?p=5](http://matt.moved.in/?p=5)

After "only time will tell..." I rebooted, with another Error 22. 

Now, I've re-installed ubuntu, so I have 2 ubuntu partitions, 1 swap and 1 XP partition. I want 1 ubuntu, 1 swap, 1 XP. 

Problem is, I can only see the Ubuntu I don't want and XP on the grub list, so I can only get to my favourite OS by pressing e and editing everything. 

WHY THE HELL IS IT SO HARD?!?!?! Everything I do just makes the situation worse and worse and worse. I went from PERFECT, to constant rebooting, to error 22, to NO OS FOUND, back to Error 22, to too many OSes installed, back to error 22 and now to here, where I have a partition I don't want but can't remove, and a list of OSes that only includes the ones I don't want. 

Makes me want to curl up and die. Should I just go back to XP? Because I'm NOT fresh installing an OS. What. The. HELL. do. I. do. here?

_**Summary:**_

**I want:**
Ubuntu x 1
Swap x 1
XP x1 
and GRUB to show this as above. 

**I have:**
Ubuntu x2
Swap x1
XP x 1
and GRUB showing just one ubuntu (the one I don't want) and XP.

[I][B]HELP ME!!!!!!!!!!!!!!!!!!

[/B]Before requesting files, remember I'm very stressed, and alot of files of mine are attached to previous posts. [/I]

---

### Post by Old Pink on 2006-09-22
Tried Lilo, Config Failed

Reply To This Topic. I Need Information.

---

### Post by sharkcohen on 2006-09-22
Please post the contents of your /boot/grub/menu.lst and the results from ls /dev/h*

---

### Post by Old Pink on 2006-09-22
I can't. Booting brings up "ERROR 22"

Look through previous thread, the old files are in there.

I ******* hate ubuntu at the moment. It's really ******* me off that it stops windows access aswell.

---

### Post by wieman01 on 2006-09-22
Matt, Sharkcohen is right. You need to add a few line to the mentioned grub config file. Show use your /boot/grub/menu.lst and we tell you what you need to do. I basically needs those line for Windows XP:
> title Windows XP
root (hd0,0)
makeactive
chainloader +1
boot

---

### Post by Old Pink on 2006-09-22
**** this, I need sleep. I hope someone has a huge fix for all this GRUB/bootup shit.

---

### Post by wieman01 on 2006-09-22
Matt, boot from Live CD as you have done before. Do you know these steps to mount your Ubuntu partition? In case you don't:

1. Fire up a terminal.
2. sudo mount /dev/hda2 /mnt
3. gedit /mnt/boot/grub/menu.lst

That's the file. Copy it to a USB device & post the contents here.

---

### Post by wieman01 on 2006-09-22
> **Matt.H said:**
> **** this, I need sleep. I hope someone has a huge fix for all this GRUB/bootup shit.
Come on, man. Where are getting there. Don't give up. I know it's tough & you probably hate nothing more than Ubuntu, but I promise you that you'll forget about your grief as soon as your system is up & running again.

---

### Post by Old Pink on 2006-09-22
I'll post the contents soon. Let me chill/sleep for a bit. A whole day of GRUB and error 22 really gets to you.

---

### Post by sharkcohen on 2006-09-22
> **Matt.H said:**
> so I can only get to my favourite OS by pressing e and editing everything. 

Sorry, thought you could get in by doing a Grub edit on the fly.  Never fear, we can help.  Rest well, and then get back to us.

---

### Post by wieman01 on 2006-09-22
> **sharkcohen said:**
> Sorry, thought you could get in by doing a Grub edit on the fly.  Never fear, we can help.  Rest well, and then get back to us.
That's the Ubuntu spirit! :-) 

See you guys then.

---

### Post by Old Pink on 2006-09-23
Hi, 

I've calmed a little, and apologize for swearing.

I'm going to try installing DSL on another partition and let it be the boot up manager.

---

### Post by wieman01 on 2006-09-23
> **Matt.H said:**
> Hi, 

I've calmed a little, and apologize for swearing.

I'm going to try installing DSL on another partition and let it be the boot up manager.
Hello Matt, 

There we go...

_EDIT:_
Also the Deb version... Just remove the suffix (.txt) by renaming the file.

---

