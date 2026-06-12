---
title: "make bootable USB Dell Ubuntu 8.0.4 from windows?"
date: 2009-01-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Mr. Mulder on 2009-01-07
Hi there,

Just been reading a lot of back posts about this here and can't quite find the exact answer im looking for...

...At the moment I have a Dell Inspiron Mini 9 installed with Win XP, I want to take it off and put on the Dell Ubuntu version that ships with it, not this netbook remix version but the Dell one that's specifically optimized for this netbook. 

I don't have an external CD drive but i do have a 4GB USB stick so my question is this, how do i obtain the original Dell version of Ubuntu that you can get with the Inspiron Mini 9 and once i have the image, how can i make it USB bootable within windows?

---

### Post by notwen on 2009-01-07
[Official Mini 9 Ubuntu Image]("http://mydellmini.com/forum/dell-mini-9-ubuntu-restore-iso-image-t287.html")  --- NOTE, I think Dell had this available, then removed the link from their site.  So not too sure if they want it readily available or not,you may wish to check.

[Unetbootin]("http://unetbootin.sourceforge.net/") ---  This very handy application will allow you to format a USB flash drive into a LiveCD for multiple distros.

Hope this helps, I would have dug around to try and more reliable link to the Dell Image, but I'm currently at work.  =]

---

### Post by Ancalagon82 on 2009-01-07
> **notwen said:**
> 
[Unetbootin]("http://unetbootin.sourceforge.net/") ---  This very handy application will allow you to format a USB flash drive into a LiveCD for multiple distros.


Will other information on the USB still be readible in non-Ubuntu machines?

---

### Post by notwen on 2009-01-07
> **Ancalagon82 said:**
> Will other information on the USB still be readible in non-Ubuntu machines?

Other information on the USB drive used will be lost as it is formatted in the process of making the USB act as a LiveCD, so be sure to back up your USB drive's data before hand.  Read their website for more information.  =]

---

### Post by Mr. Mulder on 2009-01-07
> **notwen said:**
> [Official Mini 9 Ubuntu Image]("http://mydellmini.com/forum/dell-mini-9-ubuntu-restore-iso-image-t287.html")  --- NOTE, I think Dell had this available, then removed the link from their site.  So not too sure if they want it readily available or not,you may wish to check.

[Unetbootin]("http://unetbootin.sourceforge.net/") ---  This very handy application will allow you to format a USB flash drive into a LiveCD for multiple distros.

Hope this helps, I would have dug around to try and more reliable link to the Dell Image, but I'm currently at work.  =]

Awesome! Thanks for the UNetbootin link, just what im after! ...had a look at the Dell site and can't see a download link for the distro, looks like they've taken it down :( ...there's a few torrents about on piratebay and mininova but i fear they're for this notebook remix and not the proper Dell release?

Edit: Ah, I believe this might be it [http://www.root-core.org/Inspiron_910_Ubuntu_A00.img](http://www.root-core.org/Inspiron_910_Ubuntu_A00.img) ...I'll let you all know once i've tried to install it

---

### Post by Mr. Mulder on 2009-01-08
That .img seems to be legit.

I have a problem in making the bootable USB stick with Unetbootin. I select the .img from the windows desktop, made sure its the correct USB drive and click on "Ok". It says its created it and asks me to reboot, I reboot to the USB stick. 

It then comes up with the Unetbootin splash screen. The only option is either Default or Tab and a countdown for about 19 seconds which just goes back to 19 seconds once its run down.

Am I missing something? It doesn't actually write the .img to the stick does it? Just some files saying where to find it? Because the Unetbootin stage only takes around seconds, not long enough to write a gig and a half file to the stick?

---

### Post by armandh on 2009-01-08
I suggest using the iso file to burn a bootable DVD then use that DVD as your scource.
the original supplied with the mini9 is a DVD due to the larger than CD size.

I recommend using regular 8.10 if you have the 8G drive or better

while it is a bigger "footprint" in the drive it has all of Ubuntu, 
my mini9 sports compiz and plays all the medibuntu.org codex.

while the dell mini9 8.04 has all it needs it did not have all I wanted.

---

### Post by Mr. Mulder on 2009-01-08
Hi there, DVD's not an option for me as I don't have an external drive and (not sure if this is true) I heard the Dell release was optimized power wise specifically for the mini 9 to make it run faster and more efficient than regular ubuntu? 

...though not my first choice, if i were to go with 8.10 my problem would still remain with unetbootin of the bootable USB not working/creating?

---

### Post by notwen on 2009-01-08
Try using a regular Ubuntu .iso rather than the .img provided to see if perhaps Unetbotin does not like the .img file.  Although I can say I was able to create a bootable version from the .img file provided by Dell.  Not sure, what the issue may be, but I have seen some complain of .img files not working as well as .iso files, although like I've said I've never had such an issue w/ either image type.  Wish I could be of more assistance. =\

---

