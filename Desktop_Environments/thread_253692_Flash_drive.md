---
title: "Flash drive"
date: 2006-09-08
forum: Desktop Environments
---

### Post by Big_J on 2006-09-08
I'm having problems mounting (or detecting) my flash drive.. It's a Lexar JumpDrive Secure and I know it works on linux because:
1. It says so on the box :)
2. It has linux drivers on it.
3. I already used it on linux... Slackware, Knoppix, SimplyMepis

But I have not been able to use it in ubuntu at all, and I also can't use my sandisk card reader, the light goes on but nothing happens when I put a card in. 

But the important thing is the flash drive for now, I have a very bad schedual at college, and I'm there all day long for two classes, so between classes I went to the computer lab and typed started working on my paper, for about three hours, and now that I'm home I want to finish it. But I can't get ubuntu to detect the flash drive!

I added this in my /etc/fstab:
**/dev/sda1       /mnt/usb        vfat    defaults,utf8 0  0**

Nothing.. When I sudo mount /mnt/usb (and I did also make a usb directory in mnt, doesn't work either) I get this:
**mount: special device /dev/sda1 does not exist** -- (it's plugged in)


I don't get it, what do I need to do?
My laptop as not with me, I need the paper this weekend and the only computer I have access to in 4 days is this one, which has ubuntu.. 
Please help

---

### Post by whizbaby on 2006-09-08
Please read this
[http://www.ubuntuforums.org/showthread.php?t=168221](http://www.ubuntuforums.org/showthread.php?t=168221)

---

### Post by Big_J on 2006-09-08
That didn't help at all, it doesn't list the drive.
It's not even being detected...

```
root@Condor3:/home/bigj# lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 001 Device 001: ID 0000:0000  

```
Why does it show three usb ports? I currently have 6, and all of them have power...

---

### Post by whizbaby on 2006-09-08
I cannot find the string *lsusb* on the page I mentioned. Did you plug it in, wait for like ten secs, and then type **sudo fdisk -l**? The drive is still not listed then (is that what you're trying to say)?

---

### Post by Big_J on 2006-09-09
lsusb is not from that page, that page didn't work at all. I can wait for hours (I actually left it plugged in all night) and nothing, I pluged it in all the ports, nothing. I did lsusb to show that it's not being detected...

---

### Post by whizbaby on 2006-09-09
This is weird. Have you tried **lshal|grep usb** to see if the system finds it (or lshal|grep exar)? Ubuntu (if it detects the thingy) will try to mount it on itself, so it's important to see if the prerequisites for auto-mounting meet.

---

### Post by Big_J on 2006-09-12
Update:
I gave up, and used windows to format it in FAT, and now it works!

---

### Post by Big_J on 2006-09-29
And then it stoped working shorty after, so I bought a new drive and it worked for a while, then stopped... And I can't use my card reader. But I can use both the usb drive and the card reader on my laptop (running ubuntu) without any problems.. Maybe it doesn't work on my desktop because I compiled a kernal, maybe I left a necessary option out? If so, what do I need to enable and how do I do it?

---

### Post by dcstar on 2006-09-29
> **Big_J said:**
> And then it stoped working shorty after, so I bought a new drive and it worked for a while, then stopped... And I can't use my card reader. But I can use both the usb drive and the card reader on my laptop (running ubuntu) without any problems.. Maybe it doesn't work on my desktop because I compiled a kernal, maybe I left a necessary option out? If so, what do I need to enable and how do I do it?

Install a standard kernel and see if it works, otherwise be prepared to waste a lot of time (possibly never) finding out why your complied kernel doesn't work.

There are very good reasons for all of those warnings about using non-standard kernels.

---

### Post by Big_J on 2006-09-30
What do you mean non standard?
I got it from kernel.org!

I read somewhere that usb drives are detected as scsi devices in linux, which I understand is not enabled by default when you download the kernel right?
So how do I enable scsi?

Or correct me if I'm wrong.. I'm still in the first semester of my computer science major :) 
I know alot about the outside working, but I'm not in the source yet...

---

### Post by whizbaby on 2006-09-30
> **Big_J said:**
> What do you mean non standard?
I got it from kernel.org!

Standard would mean a kernel from the ubuntu repositories.

---

### Post by Big_J on 2006-10-01
Well, I just got a new monitor and I can't use anything more than 1024x768, and my / has about 300mb left so I'm going to reinstall... 
This will fix many things!

---

