---
title: "Brand New Install, Black Screen Post-Login"
date: 2009-06-05
forum: General Help
---

### Post by Literati on 2009-06-05
Hi there,

I just reinstalled Ubuntu 9.04 64-bit using the alternate installer (So as to have my drives configured in RAID).

The installation finished, and I login from GDM, and then I get a black screen with my mouse cursor in the center.

This is my series of events since last night:

1. Re-Install Ubuntu 9.04 to setup RAID 1 & RAID 0 drives (Worked flawlessly)
2. On that instal, I accidentally botched my ATI FGLRX Driver install
3. Try a multitude of fixes. Give up. Reinstall again
4. That install provides black screen / cursor
5. Boot into live CD, completely wipe the two drives I was using for RAID, and start fresh.
6. Re-Install with my RAID 0 & RAID 1 again. 
7. Where we are now.

What bothers me is that between my very first RAID instal (Which worked) and the subsequent two, I didn't do anything differently, nd the Xorg Files / ATI Drivers I messed up should have been restored on a CLEAN install.

Furthermore, I've tried the following

1. Remove Compiz & Compiz-core
2. dpkg-reconfigure -phigh xserver-xorg (Also, just a standard reconfigure)
3. Using "Failsafe GNOME"
4. sing xfix from the Recovery Mode.

My card is a (usually) well-supported HD4850 and I run it on a Q6600 with 4GB of RAM

No amount of googling has solved my problem. So, can anyone help me?

EDIT: The only thing that I can think of is that Ubuntu, in my working RAID Install, asked me if I wanted to encrypt my /home drive (A seperate, non-RAID 1TB drive) so I agreed and went on with my business. But now I'm thinking it might be the problem, as when from a tty I run "ls /home/username" I see only two files "Access-Your-Private-Data.desktop" and "README.txt" :S

---

### Post by Literati on 2009-06-05
Anyone? You'd think a clean install would fix it... I can't use my PC without it, obviously...

---

### Post by Literati on 2009-06-06
( I'm really willing to try anything here... :S

---

### Post by Literati on 2009-06-06
Yet another bump. :(

---

### Post by merlinus on 2009-06-06
If indeed you are willing to try anythng, then use dban (or similar utility) to completely wipe your hdds and start over.  With what you have already learned, it *should* go better.

---

### Post by Literati on 2009-06-06
> **merlinus said:**
> If indeed you are willing to try anythng, then use dban (or similar utility) to completely wipe your hdds and start over.  With what you have already learned, it *should* go better.

Well, I'd like to hold out a day or two before resorting to that. Reason being:

I thought it might've been my newly encrypted /home that was causing the problem, so I went into fstab and commented out my /home drive and restarted. And yet the same problem still re-occurs. 

Like, to me it seems as though there is no logical explanation for what is happening. I've tried a multitude of solutions but alas nothing. So if a complete wipe is what I need, then so be it, but I'm still going to hole out one or two more days. :)

---

### Post by merlinus on 2009-06-06
Expecting logic from a computer is like expecting Klingons to become peace emissaries.;)

However, I do not believe ubuntu will load without a /home directory or partition, so commenting it out in /etc/fstab might not do the job.

---

### Post by Legace on 2009-06-06
It seems the FGLRX driver broke Ubuntu. Try to uninstall it:

Reboot PC, select "Recovery mode" in boot-manager (GRUB) and then go for "root shell" option (you might need to press the DOWN arrow a couple of times). 
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```

then type
```
exit
```

and select "resume normal boot"

This should get you back to your Ubuntu desktop, but running on default drivers.

---

### Post by Literati on 2009-06-06
Legace,

I followed your intructions, and as it turns out, I didn't have xorg-drivers-fglrx installed to begin with, so I instaled them and still have no luck. So then I reconfigured the xserver and still nada. :S

I've noticed however, that for most people their xserver-xorg reconfigure takes them to select their graphics card. Mine only does the keyboard portion of the setup, then quits me and just says "xorg.conf updated. backup blah blah." Which I found odd.

I' going to try another reinstall, but I'm going to have it ignore my encrypted 1TB drive, and see if it gets along or not. Cause at least if it does, I can maybe decrypt it or somesuch. Wish me luck :P

---

### Post by Literati on 2009-06-06
:D!

It worked! I set my Encrypted Drive to mount on /media/TB, and it worked, now to try and unencrypt it... Is that even possible? Who knows, more exploration to be had. :) I'm just glad I got it period :P

---

