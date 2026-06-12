---
title: "Ubuntu thinks I am not the system administrator"
date: 2010-02-15
forum: Desktop Environments
---

### Post by fleppmar on 2010-02-15
Hi!

I converted from Windows to Linux yesterday. So, I am completely new at this! :-)

Have been searching through the forums for about an hour now, but cant see anyone else having the same problem. Anyhow!

I have been tweaking Ubuntu 9.10 through the Compiz-program, have made myself a nice looking Cube ect, but. Now, my desktop icons have disapeared. They are still in the /home/desktop folder, but I can not see them on any of my 4 home screens.

I found a possible solution using sudo to reinstall nautilus, but get this message:

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

So, basicly, I have two problems. My desktop icons and right click options are gone, and apparently I am not the administrator, eventhough im the only user of my computer.

Any suggestions would be lovely! :)

regards.
fleppmar

---

### Post by Satoru-san on 2010-02-15
Welcome to the forums :)

What command were you using to reinstall nautilus?

you should have used this one:

```
sudo apt-get purge nautilus
sudo apt-get install nautilus
```

**DONT BLINDLY RUN COMMANDS THAT PEOPLE ON THE FORUMS TELL YOU**
*some times people will post malicious command that will destroy your install*
If you have any questions about what the commands do, ask someone!

---

### Post by fleppmar on 2010-02-15
Hi. Thanks for the reply. :-) 

I did as you said, and after I login now. It only goes into terminal. 
I cant find any commands to enter my desktop. Lol!

Please help! :-)

i used the install naurtilus directly the first time.

---

### Post by Satoru-san on 2010-02-15
> **fleppmar said:**
> Hi. Thanks for the reply. :-) 

I did as you said, and after I login now. It only goes into terminal. 
I cant find any commands to enter my desktop. Lol!

Please help! :-)

i used the install naurtilus directly the first time.
Try 
```
startx
```

if that doesn't work, then post your /var/log/Xorg.0.log

are you sure that you didnt really install 'naurtilus' because that is != 'nautilus'

Reinstalling Nautilus would not cause this problem, something else went wrong.

---

### Post by fleppmar on 2010-02-15
Permissipn denied. :-/

just a typo from the phone.

---

### Post by Satoru-san on 2010-02-15
> **fleppmar said:**
> Permissipn denied. :-/

just a typo from the phone.
If permission is denied then there is something even more wrong, if you dont have any important files on ubuntu, you may as well reinstall and just do some reading before you start changing settings that might ruin your system.

If you do have important files then I can tell you how to back them up to a removable drive. 

Your system is fixable but if you cant post any logs because it is your only computer or what ever it is just SO much simpler to reinstall. Sorry that that happened to you. I cant really figure out how nautilus is keeping X from starting though. It is not vital to it starting I dont think and You did reinstall it.

---

### Post by fleppmar on 2010-02-15
Hi.

Ok. Thanks. I am reinstalling now. Never got so far as to transfer the important files from my external drive. ;-)

Now, my last question. Hehe. How to boot from the Ubuntu CD in terminal, since it wont load automatically during startup.

---

### Post by Satoru-san on 2010-02-15
> **fleppmar said:**
> Hi.

Ok. Thanks. I am reinstalling now. Never got so far as to transfer the important files from my external drive. ;-)

Now, my last question. Hehe. How to boot from the Ubuntu CD in terminal, since it wont load automatically during startup.
Your computer's bios is what boots the CD, you can either hit f2 and change the boot order to CD first over Hard drive, and this will ignore regular cds unless they are bootable.
Or you can hit either f10 or f12 depending on your bios and it will bring up a boot menu that will allow you to choose your cd, do this when the computer is P.O.S.T.ing.

---

### Post by fleppmar on 2010-02-15
Okey. Tried both F2 and F12. None of the reacts. Goes straight to GRUB loading.. :-/

---

### Post by Satoru-san on 2010-02-15
> **fleppmar said:**
> Okey. Tried both F2 and F12. None of the reacts. Goes straight to GRUB loading.. :-/

try <delete> <escape> <f10>

one of those will work.

maybe even <f1>

---

### Post by fleppmar on 2010-02-15
Tried to repair broken packages. Didnt work. heh

After that I tried to continue with normal boot.

This is the error I got.

login: [ 86.16....]usb 4-1: device is not accepting adress 8, error -62
[86.708051] usb 4.1: device not accepting adress 9, error -62
86.808125] hub 4-0: 1.0: unable to enumerate USB device on port 1.

Problem is, it is a laptop. And I disconnected my usb mouse.

---

### Post by fleppmar on 2010-02-15
")$("%

I have tried F1, F2, F3, F4.......to F12. ESC, Delete, tab, nothing works.

I even tried to put in my Vista CD. Nothing will boot. Goes straight to login window for Ubuntu. :-(

And now, the boot window is different. Earlier it was the fujitsu siemens logo, and a progress bar.
Now it looks more like ms-dos and reading my ram in 1second before continuing to the log in screen.

On that screen it also is written that one can press F2 or F12. Nothing works!

Im about to cry and throw my computer out the window! ;-)

---

### Post by fleppmar on 2010-02-15
Hi. Suddenly sudo startx worked.
Got this error message:
Fatal server error:
Server is already active for display 0
if this server is no longer running, remove /tmp/.X0-lock and start again

Tried: sudo remove /tmp/.X0-lock - got this response: remove, command not found.
Tried: sudo /tmp/.X0-lock - got this response, /tmp/.X0-lock ommand not found.

---

### Post by Satoru-san on 2010-02-15
> **fleppmar said:**
> Hi. Suddenly sudo startx worked.
Got this error message:
Fatal server error:
Server is already active for display 0
if this server is no longer running, remove /tmp/.X0-lock and start again

Tried: sudo remove /tmp/.X0-lock - got this response: remove, command not found.
Tried: sudo /tmp/.X0-lock - got this response, /tmp/.X0-lock ommand not found.

Sorry I was out on buisness. The command it rm in linux. You were on the right track. startx does not need sudo to run, however.

---

### Post by Satoru-san on 2010-02-15
> **fleppmar said:**
> Im about to cry and throw my computer out the window! ;-)
**DONT DO THAT D:**

on a lighter note.. here is something funny for you:

> Frustrated Windows users have two choices:

-Throwing computers out of windows
-Throwing windows out of computers 



;) 

Hope you get it working.

---

### Post by FlyDude on 2010-02-15
> **fleppmar said:**
> Hi. Suddenly sudo startx worked.
Got this error message:
Fatal server error:
Server is already active for display 0
if this server is no longer running, remove /tmp/.X0-lock and start again

Tried: sudo remove /tmp/.X0-lock - got this response: remove, command not found.
Tried: sudo /tmp/.X0-lock - got this response, /tmp/.X0-lock ommand not found.

First rule of thumb: don't run startx as root. 

If your Server is already active, your X is started. Type top or htop to see if it started.

You can kill X by typing 

```
killall X
```Type this command to see if your screen comes on.

```
startx
```I reckon you may have some problem with gdm (the login manager) or something else if this doesn't work. Give the entire output of dmesg after your system's loaded. Also as Satoru-san said, give the output of /var/log/Xorg.0.log. 

```
cat /var/log/Xorg.0.log | wgetpaste
```Or you can paste them to pastebin.

Also to add, depending on your laptop, your boot order is different. Watch your initial screen when you turn on your screen if it says "Press F(n) for settings." (n is for any number) For Toshiba, it should be F12. Some laptop may use F8 also. 

Remove command in Bash is rm. But don't use this without knowing what you're doing. It could damage your system. Type man rm for more details.

---

### Post by Satoru-san on 2010-02-15
hehe, flydude uses gentoo, where there is a handy command called wgetpaste, this however is not on ubuntu.

You will have to mount your flashdrive and copy it to it.

```
sudo mkdir /mnt/usb
sudo mount /dev/sdb1 /mnt/usb
sudo cp /var/log/Xorg.0.log /mnt/usb
sudo dmesg > /mnt/usb/dmesg
sudo umount /mnt/usb
```sdb1 is most likely going to be it, but if it isnt you can find out with fdisk -l

---

### Post by fleppmar on 2010-02-16
Hi, guys! 

Thanks for trying. Didnt work though. 
And, I have tried every possible boot-button there is! Sat for an hour yesterday rebooting the hell put my computer. 

Seems like i need to buy a new one. :-/

---

### Post by oldos2er on 2010-02-16
Can you post the make/model of your laptop? We should be able to help you get into your BIOS.

---

### Post by Satoru-san on 2010-02-16
How did you install it the first time?

And PLEASE do this. You just need to boot your old ubuntu, not off the cd.

> **Satoru-san said:**
> 

```
sudo mkdir /mnt/usb
sudo mount /dev/sdb1 /mnt/usb
sudo cp /var/log/Xorg.0.log /mnt/usb
sudo dmesg > /mnt/usb/dmesg
sudo umount /mnt/usb
```sdb1 is most likely going to be it, but if it isnt you can find out with fdisk -l

---

### Post by fleppmar on 2010-02-17
Hey, guys!

Thanks for more tips. But, yesterday I got my roomate to format my entire HDD. After that, that GRUB ("?=("¤%")/%"%) that shadows the original BIOS was in the way. So after about 6hours online on the different forums. We finally managed to reinstall ubuntu. Hehe.

Who knew linux would be this hard? :P

---

### Post by FlyDude on 2010-02-17
Linux *is* hard. :)

Ubuntu, Mandrake, Fedora has been touted as one of the easier distribution to install and manage on your system, however. 

Nevertheless, I'm glad you were able to have your system in the working condition. If you have any other questions, make sure to add details of what you did, how you did them and what are the errors that's given to you. Make sure to be detailed when you seek help. 

Good luck with your Linux adventure! :)

---

