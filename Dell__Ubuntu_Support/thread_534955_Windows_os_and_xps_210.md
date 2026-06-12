---
title: "Windows os and xps 210"
date: 2007-08-25
forum: Dell  Ubuntu Support
---

### Post by Kevin J on 2007-08-25
I recently downloaded Ubuntu 7.04 onto my Dell XPS210.
I cannot find a way to access the windows OS. Can anyone tell me how to access the windows Operating sysem? 

If you need further technical details, I can try to provide them.

Kevin J

---

### Post by Zack McCool on 2007-08-25
> **Kevin J said:**
> I recently downloaded Ubuntu 7.04 onto my Dell XPS210.
I cannot find a way to access the windows OS. Can anyone tell me how to access the windows Operating sysem? 

If you need further technical details, I can try to provide them.



Do you mean access your files on the Windows partition?  Do you want to read them, or are you looking for read/write access?

NTFS partitions can be mounted already for read access.  If you open "Computer", they will often already be listed there, and clicking on them will mount them.

If you need to mount them manually, open a command line and do a 'man mount' for the specific format for NTFS.

If you need read/write access, install the NTFS-3G package.  Note, though, that writing to an NTFS partition is risky.

If you show what your specific partitions are, I can construct the commands that you'd need for mounting the device manually, if the man page is a bit daunting for you...

Joe

---

### Post by Kevin J on 2007-08-26
Joe,
Thanks for the response. If you decide to carry on helping be aware that I am in uncharted territory, at least for me, and some of the responses will be really dumb!
I do mean access my files in the windows partition. Ideally I should like to be able to boot to either Ubuntu or windows and use either as an OS
I have two files in the windows partition, they are not big so just to get to see them would be good enough. I can re-write the information by just looking at the screen.

You said:
NTFS partitions can be mounted already for read access. If you open "Computer", they will often already be listed there, and clicking on them will mount them.

When you say open "computer" I am not sure what you mean. Which icon should I use to open the 'computer' I did not see it on the boot menu. (The machine is currently set to open ubuntu on startup)

I can look at the Manual mount of the this later, how do I know what the specific format for the NTFS is? (Is it on the boot menu?)

Thanks

Kevin J

---

### Post by Jubalgunn on 2007-09-09
Which version of ubuntu did you use to install on your DELL XPS 210 ?
and how ?
I have a Dell XPS 210 and to date have not been able to install Ubuntu on it !!
Please let me know.

---

### Post by Kevin Jones on 2007-09-10
I downloaded Ubuntu 7.04.
I bought the disk from the web for nine dollars.
Idid have some problems. I have ubuntu and windows operating side by side. I have not been able to connect to the internet on ubuntu yet

Kevin

---

### Post by Zack McCool on 2007-09-11
> **Kevin J said:**
> Joe,
Thanks for the response. If you decide to carry on helping be aware that I am in uncharted territory, at least for me, and some of the responses will be really dumb!
I do mean access my files in the windows partition. Ideally I should like to be able to boot to either Ubuntu or windows and use either as an OS
I have two files in the windows partition, they are not big so just to get to see them would be good enough. I can re-write the information by just looking at the screen.

You said:
NTFS partitions can be mounted already for read access. If you open "Computer", they will often already be listed there, and clicking on them will mount them.

When you say open "computer" I am not sure what you mean. Which icon should I use to open the 'computer' I did not see it on the boot menu. (The machine is currently set to open ubuntu on startup)

I can look at the Manual mount of the this later, how do I know what the specific format for the NTFS is? (Is it on the boot menu?)

Thanks

Kevin J

By "Computer", I mean click on "Places", then "Computer" in the Gnome desktop environment (The GUI that Ubuntu uses)...

---

