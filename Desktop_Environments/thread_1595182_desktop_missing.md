---
title: "desktop missing"
date: 2010-10-13
forum: Desktop Environments
---

### Post by mlempenau on 2010-10-13
About three days ago I installed a USB/Firewire CCA.  I was using 10.04 and my desktop basically disappeared.  The picture I used for my background was there but everything else was missing.  I searched the web for help but did not find anything that worked.  When version 10.10 came out I decided to install.  During this install there were three times it asked if I wanted to use a new conf file or my old one.  Each time I said to use my old one.  (maybe the problem?)  After a successful install I still had the same problem.  

I have three accounts on my computer.  Administrator, mine and guest.  Two are super user accounts with the guest being just a user.  Both the admin and my account have had the desktop reconfigured by changing the placement of icons and lists.  The guest account was not changed.  Login in the admin is the same as my account with missing desktop controls.  I logged on to the guest account and it came up normally.  So I generated a new account and gave it super user status.  Now I have a super user account that I can login to but my old account with settings and programs are still not with me.  What to do?  Being new to Ubuntu I am stuck.  I suspect that there is something I can do to fix this but don't know what.  I would appreciate some help.  thanks,  Mike

---

### Post by P4man on 2010-10-13
What's a "cca" ? You mean a card?
THis may sound silly, but have you tried waiting a ridiculous long time (several minutes) ? Ive seen similar issues with hardware that wasnt working properly, in my case a modem driver that I had to blacklist. I would only get a mousepointer and wallpaper, but after several minutes the panels finally appeared.

If the panels do show after a very long time, open a terminal and type

```
dmesg
```

Copy paste the output here. If the panels do not show up, open a TTY by pressing control+alt+F1, log in, and type in the same code. If you want to post it here, redirect the output to a file with:

```
dmesg > dmesg.txt
```

The file will be put in the homefolder of the user account you logged in with.

---

### Post by mlempenau on 2010-10-13
Actually I have waited a long time.  I have run into that before.  I will try your instructions and get back to you.  CCA = Circuit CArd assembly.  :)

---

### Post by mlempenau on 2010-10-13
I got the file but it will not let me upload it because it is 55.5k ... and I too much of a newbie to have figured out how to compress files yet.

---

### Post by P4man on 2010-10-13
```
zip dmesg.zip dmesg.txt
```

Or just right click the file, then compress.

Alternatively, upload it to pastebin.com

---

### Post by mlempenau on 2010-10-13
Ok, sorry I had to leave the computer in a hurry.  I have compressed and attached.  Thanks for helping.  Mike

---

### Post by P4man on 2010-10-13
Cant see anything in there that really jumps out at me. Ive never seen the last line 

```
[51.760545] ptrace of non-child pid 1862 was attempted by: gdb (pid 1921)
```

and im not sure what it means (did you try to obtain a backtrace?), but I doubt its related to your problem.

Perhaps we should look at 

/var/log/user.log

and 

/var/log/messages

see if that sheds any light. FWIW, the USB and firewire controller seem to work.

---

### Post by mlempenau on 2010-10-13
Well, I looked at them but really am not sure what I'm looking at.  Here they are ...

---

### Post by P4man on 2010-10-13
Did you encrypt your home folder during setup? I see a shedload of errors about encryptfs and it seems like it could be this bug:

[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/372014](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/372014)

I just glanced over that thread, and it appears possibly related to skype and/or zero length files.

---

### Post by mlempenau on 2010-10-14
I have read all the info and am not sure what to do next.  I am thinking about removing security from the home folders at least until I am more adept at this s/w.  I could also look for 0 length files.  I'm still not sure from reading the info if this was fixed as a bug.  There seems to be some discussion to that effect.  Any comments are appreciated.  Mike

---

### Post by P4man on 2010-10-14
Strange that the bug gets a low priority when its been around since 2009 and prevents one from actually using drive encryption :confused:. I guess it works for most people, but its just with some hardware?

Anyway, yes your best bet is probably not using encryption for now.

---

### Post by acompay on 2010-10-15
[SIZE=3][FONT=Calibri]Hello Sir/Madam,[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I have been struggling changing the monitor resolution to 1280x1024. I ran CVT and xrandr to add new resolutions. I was able to save it on the NVIDIA software (I have a ViewSonic VG10b monitor.), but it lasted no more than a week. After doing a few more attempts I decided to change the drivers for NVIDIA driver for Ubuntu 9 (the ones in use were for Ubuntu 5 or 6). After rebooting I can't log on to the system anymore. I ran the recovery option, rebooted the regular mode, and got the message &#8220;Ubuntu 9.10 myname-desktop tty1&#8221;.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]myname desktop login: myname; password: xxxxx Now I get to the root: myname...~$                        I ran again CVT and xrandr and when I tried to add a new mode I got the message: Can't access the desktop[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]What can I do? I will appreciate very much your help![/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Kind regards,[/FONT][/SIZE]
[FONT=Calibri][SIZE=3]Acompay[/SIZE][/FONT]

---

### Post by P4man on 2010-10-15
acompay, please start a new thread; doesnt look like your problem has anything to do with encrypted home folders.

---

