---
title: "Can not boot 19.10 xfce on two PCs after power cut"
date: 2020-01-31
forum: Desktop Environments
---

### Post by Jonners59 on 2020-01-31
I lost power last night and since getting it back up two PCs refuse to start.

One is always on as it hosts another Debian OS via Virtual Box to run 3CX IP-PBX and the other was off, but plugged in and is my normal PC (with a dual boot option for Windows 10)

Attached is the text I get...  (Ignore the fat person taking the photo :-) )  It starts the boot fine.  Gets to Grub and passes that too.  Then get the 19:10 logo and dots, and then this....

ANy help please?
PS all bar the EXIT cmd do not work.

---

### Post by yancek on 2020-01-31
Not sure from your post if the journalctl and systemctl commands function, do they?  What happens if they do or what happens if not, any warning/error messages.

---

### Post by ajgreeny on 2020-01-31
First step for me would be to boot to a live system using the USB or DVD you used to install the OS.

From that run terminal command ```
sudo fdisk -l
``` to make sure you get the partition names correct and finally run [/code]sudo e2fsck /dev/sdx#[/code] changing the sdx# to whatever is the root partition of the OS in question.

That action may find errors in the filesystem and offer to repair them which you should accept.

If you get output which you don't understand come back and ask.

---

### Post by Jonners59 on 2020-01-31
Hiya, sorry had been out.  They didn't but I I seemed to make it work on the last attempt before I went out.  I managed to run journalctl -xb

I wasn't quite sure how to use it.  It threw up a few lines then stopped, so I hit enter and it threw up some more and I just kept going.  Twice there were text in red which I noted.  The one I think is the issue (???) is dev-sdd1

---

### Post by Jonners59 on 2020-01-31
> **ajgreeny said:**
> First step for me would be to boot to a live system using the USB or DVD you used to install the OS.

From that run terminal command ```
sudo fdisk -l
``` to make sure you get the partition names correct and finally run [/code]sudo e2fsck /dev/sdx#[/code] changing the sdx# to whatever is the root partition of the OS in question.

That action may find errors in the filesystem and offer to repair them which you should accept.

If you get output which you don't understand come back and ask.

Thank you for that.  I managed to get the journalctl to work and got dev-sdd1 in red, so assuming THAT is the faulty bit.  PS:  This is at this point only on one of the two machines, the PC that is on all the time.  So will try and fix this first.

---

### Post by Jonners59 on 2020-01-31
OK, managed to get one machine going.  WHat I did:
At the Emergency Mode Screen I pressed ENTER
Then I ran ```
journalctl -xb
```  (JOURNALCTL -XB)
That listed rows of text and stopped and required a "enter" to continue in steps of text for some 2,000 plus lines.  In there there are items marked in RED.  Make a note of these especially those that are Directories.

Rebooted and after entering EMERGENCY MODE tried, but in my case failed:
```
sudo -i
f disk -l  (L)
unmount "directory listed in red above"
fsck -y "directory listed in red from above"
```
Power off

I then remembered reading that this error was normally caused by either faulty directory HW, or corrupt directory or corrupted "fstab" entry, so by removing the offending entry from fstab should cure it, so I ran...

```
sudo nano /etc/fstab
```
and  put a # at the start of the line for the "directory listed in red from above"
Saved and rebooted and all was good.

In my case the faulty directory was an external hard drive dev/sdd1

Now for PC 2 that was off when the power failure occurred.  Hope it is as easy to fix.

---

### Post by Jonners59 on 2020-02-02
OK, so managed to get the second PC working too, pretty much using the same method.  I did get a lot more RED error messages in the  ```
[COLOR=#000000][FONT=&quot]journalctl -xb[/FONT][/COLOR]
``` log.  Would be nice if it summarised these at the end and also told you how to get out.  Took ages playing with every key combo I could find.  :-)

The issue was exactly the same.  On both machines I have attached an external Hard Drive in a box, and it seems this box, when power is lost does not turn on again automatically, the on/off switch needs to be pushed.  Now I know, should save me all the heart ache next time.  The point is, though, there are still some useful lessons.

Most of these errors from what I have seen and experienced come for a directory or hard drive or remote device automatically connected to and listed in fstab that for some reason is no longer available.  Be it corrupted, damaged, offline, or the fstab itself being corrupted.  The key is to know what and how to fix it.  The ```
[COLOR=#000000][FONT=&quot]journalctl -xb[/FONT][/COLOR]
``` log will tell you the what, to then fix it you need to open fatsb and cmd out (add a ```
#
``` to the start of the line(s)) or re-write the offending line.  To get to fstab, as you can't use any of the TXT editors like gedit, my preferred is to use ```
nano
```, and the file is in /etc/, so the command is ```
[FONT=Ubuntu Mono, monospace][COLOR=#000000]sudo nano /etc/fstab
```.  You obviously need root access to amend such an important file, hence the ```
sudo[/COLOR][/FONT]
```

Besides the line connecting to the external hard drive I also found a line repeated and the original # blocked.  Which was odd.  It was an auto connection to a directory on a remote PC.  They were identical and I wonder if the PC wrote it itself when struggling to open the device...  Either way I cleaned it up and put a # against both and the External hard drive entry and saved.  Rebooted and was able to get in as normal.  When I had discovered the issue I was able to remove the # against the external HD so that it reboots automatically ```
sudo gedit /etc/fstab
```.  Job done.

Hope this helps others and will certainly be an aide memoir for myself.

---

