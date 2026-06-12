---
title: "Nautilus Problem"
date: 2009-11-14
forum: Desktop Environments
---

### Post by shanksy75 on 2009-11-14
Hi, i've recently performed a clean install of Karmic 64 bit as I wanted to make use of the ext4 filesystem.

I have a small problem when navigating in Nautilus.  Certain folders I can view the contents fine one minute and then when I go back a few minutes later the window only loads up part of the folder contents and is left constantly trying to load.

The only way I can get round this at present is to perform a reboot.

If I navigate to an affected folder using the terminal I get the follwing message :

(nautilus:3402): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

Is this a recognised bug or a problem with just my filesystem?

Thanks in advance.

---

### Post by bernardfrancois on 2009-11-14
You could report a bug by running 'sudo ubuntu-bug nautilus' and following the instructions on the web page that will be opened. You may have to install some packages to be able to run this command.

Reporting a bug this way will also show you some similar bug reports, so you may find an answer there.

---

### Post by pataphysicianu on 2009-11-14
This bug seems to bee related to your error. Though no one has reported the issue of not finishing displaying folders. So it's possible this error message is not directly related to your problem, but one that is spit out anytime nautilus is run from command line under 9.10

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/454234](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/454234)

---

### Post by shanksy75 on 2009-11-15
I'm not sure this bug is related to the error message from the terminal.

I get the same error message from the terminal whether the folder I open is affected or not.

I have submitted as a new bug anyway, someone with more knowledge than me can decide if its related.

Thanks

---

### Post by bernardfrancois on 2009-11-15
Ok. Can you post a link to the bug report?

---

### Post by shanksy75 on 2009-11-15
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/482905](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/482905)

As stated on the bug report the same error does not appear to occur when running nautilus under a KDE session.

---

### Post by 2541 on 2009-11-15
Hi, shanksy75!

> I have a small problem when navigating in Nautilus. Certain folders I can view the contents fine one minute and then when I go back a few minutes later the window only loads up part of the folder contents and is left constantly trying to load.

The same thing happens with nautilus on my 64 bit Karmic-installation. 
But it only occurs, when I drop a new file into this folder.
Otherwise nautilus behaves normally.
Very strange...

---

### Post by shanksy75 on 2009-11-16
2541 This sounds identical.  The folders that affect me are ones where I am constantly moving video files to.
I can't remember if it has ever happened without having just added a file to the folder.

Are you also using ext4 filesystem?

---

### Post by 2541 on 2009-11-16
> Are you also using ext4 filesystem?

Yes, I also use ext4. 
And I move PDF-files into the affected folders.
During the time the folder tries to load, it sometimes looks as if all files were gone.

I've just discovered, that after a reboot the folder behaves normally and even the new files are inside it.
But then it starts again...

---

### Post by jeperezd on 2009-11-17
Same issue here with my Karmic 64 bits over an ext4 filesystem.

The files are completely visible in a terminal.

Even I have the filesystem exported with samba and my laptop with Karmic 64 bits also can see the folder perfectly, but in the desktop, anytime I move a new file to the folder I sopt watching all orsome of the files.

---

### Post by 2541 on 2009-11-17
Now, without changing anything on my system  and without another reboot (!) the problem disappeared.
At the moment I can move files around and the folders behave as they should.
Hmmm...

---

### Post by Donalb on 2009-11-19
Similar for me to Shanksy75.

But I'm on 32-bit and it's happening me on 2 external FAT32 drives. I've only noticed it where there are large video files in the folder, which I keep on an external HDD.
First I though it was one HDD about to fail so I reformatted the other HDD (which had been used as a system clone for the Karmic install) and moved everything to it. But the same issue there.

Terminal lists all the files in the folder(s) fine.
Affected folder is constantly waiting to update, but never completes.
A system reset will put it back to normal for a while. 
Closing media tab or Nautilus doesn't work.

I was going to report it as a bug but couldn't figure out in Launchpad if the bug already existed.

---

### Post by Donalb on 2009-11-19
Trying something from someone else's problem,
I found that by turning off Preview in Nautilus>Edit>Preferences>Preview, all files now display. 
I can then switch it (Preview) back on and contents are still displayed.
I tried dropping the Local Files preview size from 10mb also but it had no effect.
Getting a better idea of how to report the bug now though.

Edit: And this looks like a reported version of the bug;
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/397192](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/397192)

---

### Post by 2541 on 2009-11-19
> **Donalb said:**
> Trying something from someone else's problem,
I found that by turning off Preview in Nautilus>Edit>Preferences>Preview, all files now display. 
I can then switch it (Preview) back on and contents are still displayed.

Donalb, thank you for the hint. This works for me as well.
But I hope that there will be a fix to nautilus sooner or later.

---

