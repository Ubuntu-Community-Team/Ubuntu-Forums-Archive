---
title: "Another newbie with a password problem ..."
date: 2009-06-09
forum: General Help
---

### Post by bradyfehr on 2009-06-09
Ok, bought a new Dell Mini 9 (Inspiron 910) with an Intel Atom processor and Ubuntu 8.04 for my daughter. She was excited and entered a password at startup and it now appears she doesn't know what she entered. There is no CD drive so I can't boot from a CD.
 
I've searched the threads and found quite a few different ways to reset the password - once I get into the system. So far I can't get past the password request. I've tried the ESC key at boot, the 0 key at boot, and the 2 key at boot. The 2 key gets me into the setup but a password is required to see or do do anything.
 
I'm assumming I need to reset the system password. If I can just get to the command prompt I might have a chance ..... any ideas?

---

### Post by DGortze380 on 2009-06-09
> **bradyfehr said:**
> Ok, bought a new Dell Mini 9 (Inspiron 910) with an Intel Atom processor and Ubuntu 8.04 for my daughter. She was excited and entered a password at startup and it now appears she doesn't know what she entered. There is no CD drive so I can't boot from a CD.
 
I've searched the threads and found quite a few different ways to reset the password - once I get into the system. So far I can't get past the password request. I've tried the ESC key at boot, the 0 key at boot, and the 2 key at boot. The 2 key gets me into the setup but a password is required to see or do do anything.
 
I'm assumming I need to reset the system password. If I can just get to the command prompt I might have a chance ..... any ideas?

On boot, press ESC to enter the GRUB Menu (if necessary).
Select the recovery kernel.
The command to reset the password is below, replace anything in <>

```

passwd <username>

```

Enter a new password, nothing will show on the screen as you type, press enter.
Reenter the password, press enter.

Afterward, use this command to shutdown

```

shutdown -h now

```

---

### Post by bradyfehr on 2009-06-09
Thanks for the quick reply DG but I have hit ESC 100 times and I don't get the GRUB menu, it always goes to the password request.  I've tried hitting the ESC key as fast as I can and I've tried waiting until the boot screen flashes by and everything in between.  The ESC key is getting me nowhere ....

---

### Post by DGortze380 on 2009-06-09
> **bradyfehr said:**
> Thanks for the quick reply DG but I have hit ESC 100 times and I don't get the GRUB menu, it always goes to the password request.  I've tried hitting the ESC key as fast as I can and I've tried waiting until the boot screen flashes by and everything in between.  The ESC key is getting me nowhere ....

Sounds like you're doing it too early and hitting a BIOS Password. 

GRUB looks like this: [http://thegabfather.files.wordpress.com/2008/09/grub4kt.jpg](http://thegabfather.files.wordpress.com/2008/09/grub4kt.jpg)

Sometimes like this: [http://images.howtoforge.com/images/kernel_compilation_ubuntu/4.png](http://images.howtoforge.com/images/kernel_compilation_ubuntu/4.png)

---

### Post by bradyfehr on 2009-06-09
Thanks DG but no matter what I do I can't get to any screen that will allow me to type anything. I'd recognize the GRUB menu if I saw it. Looks like it's the Bios password that's restricting me. Do you happen to know how to reset that? I've just about had it and tempted to take out the cell battery but I have to disassemble the whole damn unit to get to the battery .....

---

### Post by DGortze380 on 2009-06-09
> **bradyfehr said:**
> I've just about had it and tempted to take out the cell battery but I have to disassemble the whole damn unit to get to the battery .....

That will do it.

Only 2 ways to reset a BIOS Password.
1) CMOS Jumper (Check your motherboard documentation)
2) Remove CMOS battery and power cord for a period of time

---

### Post by robert shearer on 2009-06-09
Make haste slowly. You might want to do some more research first. Seems that resetting bios on this machine may be more complex than that....see these postings ...

[http://en.community.dell.com/forums/p/19245362/19384692.aspx](http://en.community.dell.com/forums/p/19245362/19384692.aspx)


Oh and just to point out the obvious... Have you got a spare keyboard you could plug in an try the escape key on that??

What do the Dell help desk say?? it can't be the first time that anyone has had this problem??


> The 2 key gets me into the setup but a password is required to see or do do anything.

What are the options on the set up screen if any?

Can you boot from usb? External cd drive?

---

### Post by bradyfehr on 2009-06-09
Dell was worthless, they said they don't support Ubuntu so they sent me here. There are no options on the setup screen because I can't get to the setup screen without the password. I turn on the computer, maybe 6-7 seconds of blank screen then I see the Phoenix bios load very quickly, then a plain screen comes up prompting for the password.
 
I'll try the keyboard trick, I have nothing to lose .....

---

### Post by DGortze380 on 2009-06-09
> **bradyfehr said:**
> Dell was worthless, they said they don't support Ubuntu so they sent me here. There are no options on the setup screen because I can't get to the setup screen without the password. I turn on the computer, maybe 6-7 seconds of blank screen then I see the Phoenix bios load very quickly, then a plain screen comes up prompting for the password.
 
I'll try the keyboard trick, I have nothing to lose .....

If 2 brings you to the BIOS Setup for a password, what happens if you press nothing, is it a different password screen??

Maybe it is an SSD password after all.

Either way, you're not through boot yet, so we've got to erase that password to get to ubuntu.

Can you boot a USB Stick? Or CD from an external drive?

---

### Post by bradyfehr on 2009-06-09
If I do nothing I get a blank screen with a simple password request. If I hit the 2 key I get the Phoenix Bios Setup Utility screen in the background (but empty of content) with the same simple password request in the foreground.
 
I'm going to have to get a stick with more capacity to get the CD onto it before I can try that method. I have no external CD drive and at this point I'm ready to just send the damn thing back ....

---

### Post by robert shearer on 2009-06-09
> Dell was worthless, they said they don't support Ubuntu so they sent me here.

They are wrong. The problem is not with the O/S, grub, or the lost Ubuntu password but with the Bios protection password that, presumably,  Dell installed.

If it is a new Dell then it is a problem they should help with and if you ask them they should be able to provide a bios password override. 
They will want proof of ownership, serial numbers etc, but if it is all correct I don't see the problem.

Ask them nicely but be prepared to mention whatever consumer protection organisation your country has ;).

---

### Post by QIII on 2009-06-09
It really doesn't sound like the OS at all.  It sounds to me like she was prompted by the BIOS for a password to secure the SSD before she even got to Ubuntu.

Call Dell back and tell them you can't even get to Grub, so you think that the BIOS or SSD password was reset.

Dell may be able to give you a backdoor based on the serial number.

If they can't, you may be up the proverbial creek.  A new SSD might be a bit spendy.


Addendum:  OK, robert shearer!  Steal my thunder while I was talking to my daughter!  Sheesh!  Ya.  Dell is giving the guy short shrift.

---

### Post by michy99 on 2009-06-09
Found on another thread:

[http://ubuntuforums.org/showthread.php?t=1182992](http://ubuntuforums.org/showthread.php?t=1182992)

If you have an original Dell Mini 9 with Ubuntu pre-installed, you may have a hard time entering the GRUB menu as the default delay is zero. This is particularly problematic if you're trying to reset your password using the passwd command.

You can enter the recovery mode following these steps:

1. Boot the mini 9 while pressing ESC every second
2. When you see the "MBR 2FA:" prompt or similar, the boot process is stopped.
3. Press ENTER and ESC very fast one after the other.
4. You should then see the GRUB menu. Using the up and down arrows, highlight the second option and press ENTER to boot into recovery mode.

---

### Post by QIII on 2009-06-09
Good catch!

If that works, someone will have to talk through editing the menu.lst to give 5 or 10 seconds of delay.

Good job!

---

### Post by robert shearer on 2009-06-09
QIII , beat me this time! (like the "short shrift" by the way. is that Portlandese ??)

---

### Post by QIII on 2009-06-09
"Short shrift" is a somewhat archaic expression.

It means something along the lines of "To make short work of - to give little consideration to."

---

### Post by robert shearer on 2009-06-09
Full links...

[https://answers.edge.launchpad.net/dell-mini/+faq/311](https://answers.edge.launchpad.net/dell-mini/+faq/311)

[https://help.ubuntu.com/community/DellMini9](https://help.ubuntu.com/community/DellMini9)

---

### Post by QIII on 2009-06-09
Then --

Go to the terminal and type

sudo gedit /boot/grub/menu.lst

Change the line 

"timeout		0"

to 

"timeout		15"


Whose brilliant idea was it to default the timeout to 0?

---

### Post by michy99 on 2009-06-09
> **QIII said:**
> Whose brilliant idea was it to default the timeout to 0?

"Gee, we don't want to inconvenience these people by making them wait 15 seconds to boot in. Why would they ever need to access the grub menu, anyway?"

---

### Post by robert shearer on 2009-06-09
> Whose brilliant idea was it to default the timeout to 0? 

a wet cat ?    ( as in Ding Dong ...)

---

### Post by QIII on 2009-06-09
> **michy99 said:**
> "Gee, we don't want to inconvenience these people by making them wait 15 seconds to boot in. Why would they ever need to access the grub menu, anyway?"


Recovery mode?  Why would anyone ever want to get to that?

---

