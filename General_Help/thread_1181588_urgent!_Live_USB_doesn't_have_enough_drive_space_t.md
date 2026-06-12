---
title: "urgent! Live USB doesn't have enough drive space to boot..."
date: 2009-06-08
forum: General Help
---

### Post by jorx on 2009-06-08
Hi everybody!

I have a semi-urgent problem. 
What I've got is Linux Mint 7 running persistent off of a USB flash drive- I've got a 4GB casper-rw persistence file which should have been plenty. Now I was getting a little low on space...

I was installing some software (presumably with plenty of space to spare) when the synaptic manager gave me errors- saying "out of space".  So I thought "no big deal, I'll delete everything in the /tmp dir and reboot Gnome". 

But Gnome would give me an error. So I rebooted the computer.   Now Gnome won't even load! Upon bootup I get a few errors--
yet fortunately I still have the command line terminals . ( F1 keys )

So I'm a relative noob in linux- can you tell me how to empty the trash bin or fix this problem?

Thanks, I appreciate the help! This little USB bootable Linux has become a mainstay of my computer usage- transferring my professional software from desktop to desktop easily.  And it's something the windows can't do!

---

### Post by GrimRe on 2009-06-08
You could try also removing /var/cache/apt/archives to get rid of the downloading archives. You can also try removing /var/log

```

rm -R /var/cache/apt/archives/
rm /var/log

```

Also, not sure if there is a GRUB option in the livecd to boot to recovery mode? If there is try booting to that and choose the option to create some free space and reboot.

Hope this helps.

---

### Post by jorx on 2009-06-08
Turns out I can't actually type any commands in! It just gives me errors relating to no disk space. I can't even rm anything!

So I have 2 options I can think of-

edit the boot flags somehow- (not sure how to do this- is it possible to just boot to init 3?)
OR

boot liveCD- then plug in my USB drive and try to penetrate the casper-rw file. I"m not sure how to do that- since a windows machine can't read it.  Is there some way to mount or look inside of the casper-rw persistent loop file?

---

### Post by jorx on 2009-06-08
Ok, I think I've solved it for now.  After researching- I ended up doing the following-

-Booting up on my original live CD.

-Plugging in my bootable USB drive with the casper-rw persistent loop file

-Mounting the casper file with the command:
sudo mount -o loop /media/casper   (after mkdir)

Then I was able to go into it and delete stuff. I really don't understand how I filled the 4 GB loop file so fast... 

And deleting it is not enough- I have to try to find the invisible .trash folder and empty that as well...

but hopefully it should boot now!

---

