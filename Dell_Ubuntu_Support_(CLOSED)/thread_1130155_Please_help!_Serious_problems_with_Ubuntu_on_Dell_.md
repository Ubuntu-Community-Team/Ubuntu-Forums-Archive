---
title: "Please help! Serious problems with Ubuntu on Dell laptop"
date: 2009-04-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ashleyjordan2323 on 2009-04-19
I don't even know where to start there are so many things wrong with my system right now. 

The main problems are that my update and package manager won't run properly and that when I am running torrents it causes my whole system to go crazy, I'm forced to shut down every time. Then on restart it runs fsck and sees there are errors, fixes the errors while it's scanning but then it always says "exit status 3 - FAIL" and then it boots. I try to run torrents again, sometimes they work for a while but they always error out eventually and then the process starts all over again. 
My Firefox is also completed effed up. It won't let me go back on any page and it doesn't save any history at all, it displays the first website that I typed into the address bar the entire time I have that window open, never shows the new URL when I move on. 

I have tried to take as many pictures as I can of the start up issues, I don't have a splash so I can see all the errors running by lol I don't really know anything about Ubuntu or Linux at all, a friend installed it for me and I'm trying to get it fixed up without having to bother him all the time! Please help! email me (thecharredremain@hotmail.com) for images of the start up and errors or more info. I have some errors that I will try to dictate below but I've just been jotting down what I can aside from the pictures I've been taking >.<


These are some of the errors I get when torrenting - I get about 5 different errors though
Torrent paused: disk write error no storage for slot (the number changes - Ive noticed 627-779-948 a lot)

-Write failed: INput Output error 

-Torrent Paused: disk write error write failed: read only file system 

THEN on restart I get this -

Checking root system FSCK dev/sda1 contains a file system with errors check forced

then a bunch of stuff runs by quickly but it all ends with 
STATUS: DRDY ERR
error: UNC
end request: I/O error dev sda sector 54005984


then 

LP: driver loaded but no devices found 

this also appears a lot

Buffer I/O error on device sda  sector 54005984

BufferI/O error on sda1 logical block 6750740-6750745


there are a ton more things that look completely wrong on start up, not to mention the Firefox package manager and torrent issues. I dunno what the hell I did but I can't even update now and it's starting to drive me a little nuts.

help a girl in need of downloads! [-o<

---

### Post by prshah on 2009-04-19
> **ashleyjordan2323 said:**
> 
then a bunch of stuff runs by quickly but it all ends with 
STATUS: DRDY ERR
error: UNC
end request: I/O error dev sda sector 54005984


DRDY errors can occur with either physical or logical damage to the hard disk drive.

In this particular case, I'd guess the damage is physical.

I'd suggest you run a detailed check on your hdd as outlined below. Be warned that using the below commands may likely make your data irrecoverable, so use with caution, and at your own risk.

Perhaps a backup will be a good idea.

Here's a summary of what you have to do; boot into the recovery console, ensure that your hdd is not mounted, then run fsck with the -c -y switches to force corrections.

The details on how to do this are complicated; i'd suggest professional help. But post back if you want to do this anyway.

---

### Post by matrixblue on 2009-04-19
I agree with the above post. It does appear to be a physical problem with the hard disk.

---

### Post by lawson012 on 2009-05-11
I have the same problem as ashley but mine is:
Buffer I/o error on deivce sda1 logical block 8064627
I think this is what is stopping me launch ubuntu. If there are any solutions please reply
I get some busybox crap aswell but im looking into that now

---

