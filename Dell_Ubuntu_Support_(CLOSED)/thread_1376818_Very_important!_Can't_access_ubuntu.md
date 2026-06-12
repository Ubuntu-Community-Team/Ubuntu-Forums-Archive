---
title: "Very important! Can't access ubuntu"
date: 2010-01-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mbrett on 2010-01-09
To all-

I received a used Dell Inspiron mini 9 Netbook 910 from a pawn shop off ebay. The ubuntu os was under a different administrator and I do not have an ubuntu install cd. I wanted to install my external dvd drive and it would not install. I figured that was because of administrator privileges. I used the forums to uncover the root user name through the shell.


user name: deborah


I then reset the password. Unfortunately, I then turned off the computer to reboot from shell. When I rebooted, I went to an ubuntu login screen and was told to enter my user name and password. I entered the root user name and password, and ubuntu told that the gnome manager was locked and there could be a bug.

I repeated the reset password program and this time rebooted directly from the shell. I still went to the same screen.

I have searched the forums and have not discovered any possible way to work around this. I cannot access the os, so I can't run a md5 whatever. Further, I do not have a cd drive to help out.


Right now I am in shell and I ran ls -a. It reads

(blue).   .bashrc   (blue).gconf   (blue).gnome2_private   (blue).pulse   (blue).wapi
(blue)..   (blue).dbus   (blue).gconfd   (blue).gstreamer-0.10   .pulse cookie
.bash history   .esd_auth   (blue).gnome2   .profile   (blue).synaptic

I am at loose ends. I already have the dude refunding me $75.00 because it didn't come with the external drive, webcam. or wireless card. 

Is there a work around for this?

---

### Post by mbrett on 2010-01-09
OK, used sudo to get in. Logged into administrator privileges and still can't run install cd on my external dvd drive.

I'm going to try to update the os and see if it won't work a little better.

Never used ubuntu before. A whole new world.

---

### Post by Alex!!!! on 2010-01-09
It is another world. I say, sue eBay!

---

### Post by mbrett on 2010-01-10
Gentlemen and gentle ladies=

After trying all day to figure out how to get this netbook to work I've just about had it. My best option right now is to wipe out the hard drive. I tried to install Darik's Boot and Nuke with my USB drive and Ubuntu 8.04.something, but alas that has come to naught.

So...

If any of you can give me newbie instructions on how to make a Ubuntu bootable USB for Darik's...

or...

Inform me of another way I can erase my drive without the use of a CD drive. My CD drive requires executable files. I can't download and run Wine because Ubuntu is telling me I'm all out of memory. And I can't get to the partitions because...well, 'cause I don't know what the hell I'm doing.

Any and all help would be much appreciated. I don't need a Dell paperweight.

Cheers,
Michael

---

### Post by gbrainin on 2010-01-10
I certainly understand your frustration with this computer (I'm sure we've all been in a position to want to hit one with a sledgehammer at one time or another), but I think you've got to give the forums more than 18 hours (most of which were overnight, at least in Europe and the Americas) to solve a rather unique problem.

Unfortunately, I'm not familiar with your particular hardware such that I could give you any advice which is more than a guess, but how about a guess: if the hardware is capable of booting from one, why not create a bootable USB key?  If you can get a recent version of Ubuntu running on any nearby computer (even from the live CD), you should be able to do so using System->Administration->Create a USB Startup Disk.

If you can boot the machine from USB, you should then be able to mess about with the internal hard drive as necessary.  As to what is necessary, I'll have to defer to my more experienced associates.

---

### Post by mbrett on 2010-01-10
Sorry for the dramatics.

I've tried to boot from my USB, and even if I disable my HD in bios the computer will not boot. I believe I'm not making the USB bootable. I agree with you. I think this is the solution. I just need to know how to make my USB bootable.

Thanks for the response,
Mike

---

### Post by gbrainin on 2010-01-10
Looking at the manuals (avaliable at [http://support.dell.com/support/edocs/systems/ins910/en/index.htm]("http://support.dell.com/support/edocs/systems/ins910/en/index.htm")), it appears if you press either F12 or 0 while the Dell logo appears during the boot sequence, you should get a bootable device menu.  So you'll need to have your USB device plugged in before you start booting, then you should be able to select it from the menu that comes up.

---

### Post by mbrett on 2010-01-11
Did that. Disabled hard drive as well. When the computer rebooted, it would run and say 'Operating System not found'. I think my problem is that the USB is not bootable. But I can't find anything about how to make a USB bootable.

Thanks for checking the manual!
Mike

---

### Post by gbrainin on 2010-01-11
How did you create the USB device?  Did you use System->Administration->Create a USB Startup Disk?  If not, I suggest trying that.

---

### Post by snowpine on 2010-01-11
Hi Mike, whenever I buy a used computer, I always wipe the hard drive and do a fresh install of the operating system (I don't want someone else's junk).

Here are the official instructions for installing ubuntu from a USB stick: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

You might also find some useful tutorials on this site: [http://www.ubuntumini.com/](http://www.ubuntumini.com/)

Linux is a big transition, so be patient with yourself and enjoy the process!

---

### Post by mbrett on 2010-01-11
snowpine- 

Thanks for the help! I've tried that how-to and it just does not work. I do not have the app uscreator on the machine and I can't download it because I have no more room on my HD.

I have searched the ubuntu mini site and not come across any usable information.

gbrainin-

I do not have that application on my machine. When I updated files after I bought the computer, a few files could not be added. My guess is that this is because my HD is almost completely full.

---

### Post by snowpine on 2010-01-11
> **mbrett said:**
> snowpine- 

Thanks for the help! I've tried that how-to and it just does not work. I do not have the app uscreator on the machine and I can't download it because I have no more room on my HD.

I have searched the ubuntu mini site and not come across any usable information.

gbrainin-

I do not have that application on my machine. When I updated files after I bought the computer, a few files could not be added. My guess is that this is because my HD is almost completely full.

If your hard drive is full, you may need to borrow a friend's computer to create the USB startup device. Alternately, you could get an external CD drive and install Ubuntu from a Live CD. I do not know of any way to install Ubuntu on a computer with a full hard drive without using a CD or USB drive. Good luck!

---

### Post by gbrainin on 2010-01-11
I agree; I think the easiest way to deal with this would be to borrow someone's computer to create the USB device.  I'm pretty sure that you can do this from a Live CD, so you don't need to borrow a machine that runs Ubuntu or make any changes to the borrowed machine's drive.  (Though it will be noticeably slower running from the live CD.)

---

### Post by nerdy_kid on 2010-01-11
some flash drives (like mine) come preformatted with extra 'features' and crap, i made a new partition table on mine (using ubuntu's partition manager) and then all i have to do is extract an iso file directly to the flash drive and its bootable.  idk, hope this helps :|

---

### Post by mbrett on 2010-01-14
Hey thanks you guys for the help. I don't know why I didn't think about creating the USB boot from my desktop. Hit another roadblock. I downloaded the 9.10 netbook remix to my desktop and it jammed up both installer. I downloaded another 9.1 netbook remix from our mirror and, according to winMd5Sum, both it and the first don't match the right hash. They both have the same:

f39f85663f93f89baf111541e804a83a
f39f85663f93f89baf111541e804a83a

The correct hash is this, according to our documentation:

ed6e77587b87fe0d92a2f21855869f00

So, let's try the regular 9.1 desktop. Guess what? Same thing.

Mine downloaded from our mirror:
4a748b1d6ae10585b5c31c31ff6a2fc3
4a748b1d6ae10585b5c31c31ff6a2fc3

And on record we have:

8790491bfa9d00f283ed9dd2d77b3906
or 
3faa345d298deec3854e0e02410973dc

So is this my desktop? Or, is there a better place to dl these isos? Or am I doing this completely wrong?

---

### Post by gbrainin on 2010-01-14
I'm not quite sure what you mean by "our mirror," but it certainly sounds like you're getting a corrupted version of the ISO for some reason.  Hopefully, it's the place you're downloading from, since that's easy to fix: just try a different one.  Or better yet, bittorrent:[http://http://www.ubuntu.com/getubuntu/downloadmirrors]("http://http://www.ubuntu.com/getubuntu/downloadmirrors")

---

### Post by mbrett on 2010-01-14
I download netbook remix through bit torrent, sent the md5 to winMd5sum and received the same md5 has as the first two:

f39f85663f93f89baf111541e804a83a

Which is not the right hash. I tried to make a boot copy anyway, and it failed at the 8th file, some squash file. I don't know, but that is where it jams up each and every time.

---

### Post by Kai69 on 2010-01-14
Most dells come with a factory reset partition have you tried this. When you switch the computer on and the bios screen displays hit F11 you have to be quick though what it does is reset the computer to factory condition ie wipes all data saved on HDD . i have used this on my laptop and worked for me.

---

### Post by gbrainin on 2010-01-14
I just double-checked the md5sum on the version of the 9.10 desktop that I had lying around on my hard drive.  8790491bfa9d00f283ed9dd2d77b3906, just like it's supposed to be (and different from yours).  And you've tried downloading from more than one source.  So, this leads me to think that the problem is on your end somehow: either something's honked up with your connection, or with the windows machine you're downloading on, or perhaps with the windows md5 program.

Not being an expert on any of these, I'd default to changing them one at a time until you find a combination that works.  Tedious, I know, but that's what I'd be doing in your place--unless you have a friend somewhere with a known-good Ubuntu CD.

---

### Post by d3v1150m471c on 2010-01-14
applications > system > administration > startup disk creator. If you're trying to make it so you can run ubuntu from the usb then have the usb drive plugged in and boot from the installation cd, and then simply install it to the usb drive. The usb is going to need to be at least 2gb in size. I recommend 4.

---

### Post by mbrett on 2010-01-14
Dell Netbook 900's don't have an F11 key.

My netbook does not have an the start up usb creator on it. Earlier points on the thread explain why I can't use the netbook.

If someone would be willing to send me a good Ubuntu install CD via mail, please let me know. I would pay for next day delivery and pay a service fee through paypal. 

Please let me know.

Thanks,
Mike

---

### Post by mbrett on 2010-01-14
My major confusion- how can the ubuntu files all install funny via firefox download and bittorent when I literally have dled hundreds of files to this desktop and never had a problem like this. This makes me believe it is not the connection or the desktop. Maybe the USB drive? I'm going to have my wife bring home some from work tomorrow.

Can I use my Sansa Fuze as a USB device if I delete everything from it? 

Straws being grasped.

---

### Post by nerdy_kid on 2010-01-15
> **mbrett said:**
> My major confusion- how can the ubuntu files all install funny via firefox download and bittorent when I literally have dled hundreds of files to this desktop and never had a problem like this. This makes me believe it is not the connection or the desktop. Maybe the USB drive? I'm going to have my wife bring home some from work tomorrow.

Can I use my Sansa Fuze as a USB device if I delete everything from it? 

Straws being grasped.

you can copy files to the fuze, but not sure if you can boot of it, probably not.

---

### Post by mbrett on 2010-01-16
OK, I'm an idiot. Turns out it just took a bit to load ubuntu netbook remix through unetbootin. DLed to new 1GB Kingston stick. Tried to boot Dell Mini 9. 

'Operating system not found' at each of the three USB ports. 

The stick is password protected. Does that have something to do with it? Or can you not USB boot to a Dell Mini 9?

Feel I'm almost home here. Thanks much to you guys!

---

### Post by nerdy_kid on 2010-01-16
> **mbrett said:**
> OK, I'm an idiot. Turns out it just took a bit to load ubuntu netbook remix through unetbootin. DLed to new 1GB Kingston stick. Tried to boot Dell Mini 9. 

'Operating system not found' at each of the three USB ports. 

The stick is password protected. Does that have something to do with it? Or can you not USB boot to a Dell Mini 9?

Feel I'm almost home here. Thanks much to you guys!

the password protected stick would fry it.  I would wipe the stick with gparted by creating a new partition table.  This would permently destroy some the password protecting ability though.

---

