---
title: "Help needed: No Desktop after login to Ubuntu 8.10"
date: 2009-03-02
forum: Desktop Environments
---

### Post by fullyfandoo on 2009-03-02
Hi,

I uninstalled Evolution and in the process Braseo(CD burning software) went missing so I reinstalled it. After sometime the icons of the Desktop went missing. Though I could see the contents from My Computer. I thought of rebooting the system and once I did that I lost the Desktop. I can log in and after that the drum beat music should come followed by Desktop but none. All I see is a blank background with only option of moving the mouse cursor around.

After Googling into this a bit, so far I've performed the below with no luck:

1)
press ctrl+alt+F1.
Enter in your login name and password.
enter in: "rm /tmp -r" 
Reboot

2)
sudo dpkg-reconfigure xservr-xorg
Selected the default options there after
Reboot

3)
sudo apt-get remove compiz
sudo apt-get remove compiz-core
reboot

4)
sudo /etc/init.d/gdm stop
startx
reboot

5)

Edited /etc/x11/xorg.conf and changed Configured Monitor to Default Monitor
Save and reboot

6) From the Recovery mode tried system scan, free up space, repair broken package, Check XServer etc..but no go..

Formatting would not be an option I would consider, unless its a gone case, as too much is at stake.

May be this has something to do with Display driver or Display configuration, not sure.

Any help would b deeply appreciated.

Thanks,

FF

---

### Post by WatchingThePain on 2009-03-02
Hi, Can you get a terminal ctrl+alt+F2 then type startx and see (maybe write down) the errors that occur if any or just post them here.

---

### Post by xoorox on 2009-03-02
could you just try 
sudo apt-get install ubuntu-desktop
...and see if that restore your desktop... your files and things should be there and it will install the dependencies.  I have a vague memory of once uninstalling evolution myself and it causing problems.

---

### Post by fullyfandoo on 2009-03-02
Thank you guys for the response. Deeply appreciated.

I'm currently booted using the live CD. Let me try these and I'd let you know.

---

### Post by fullyfandoo on 2009-03-02
OK...I tried both the suggestions..and here is what I got:

I turned on the machine, log in and reached the blank screen...Press Ctrl+Alt+F2 and logged in and then entered "startx" ...got the below:

"Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again"

I've already removed the data in tmp folder. Again I rebooted the machine and below is the sequence that follows:

On TTY1 :
"Starting up...
Loading, Pelase wait...
19+0 records in
19+0 records out
kinit: name-to-dev-t(/dev/disk/by-uuid/181546d-d97a-427d-9ca7-3f194170bc1d)=dev(8,5)
kinit:trying to resume from /dev/disk/by-uuid/181546d-d97a-427d-9ca7-3f194170bc1d
kinit:No resume image, doing normal boot..."

Then comes the below :

"Ubuntu is running in low-graphics mode"..I clicked on OK and then got 
the below:

"The greeter application appears to be crashing. Attempting to use a different one"

And I click ok..all th TTY screen will flash and the messages comes back..This would happen for about 4-5 times before the process stops at TTY screen with a login prompt...

This is way beyond my imagination any every bit of suggestion, irrespective of how relevant, is welcomed.

Thanks,

FF

---

### Post by xoorox on 2009-03-02
ah you'll need to try logging into the machine directly and trying it (at your blank screen). if you boot up with the livecd you load a temporary operating system into the memory and you only update this temporary desktop if you run commands in terminal (...though you'll still be able to access files on the hard disk).
 
i think if you're able to login and get a prompt and try that ( sudo apt-get install ubuntu-desktop ) then reboot it might work. it sounds like like your ubuntu is still alive and kicking, just it's hard to see which bits are missing.
 
good luck

---

### Post by fullyfandoo on 2009-03-03
Hi,

Unfortunately now I'm not getting the login screen itself and instead getting the message about my Desktop having low resolution. 

Any ideas how would I backup my data from live CD. I can see files but cannot copy it over as it is locked. I tried Nautilus from Terminal that opens up a GUI file explorer but still unable to copy files.

If I can get this part working then I can atleast backup my data and if nothing works I can peacefully format the machine.

Thanks,

FF

---

### Post by xoorox on 2009-03-04
are you using sudo? e.g. sudo cp /home/myfolder /mybackupdrive/myfolder
 
...or sudo nautilus if you wish to use gui.
 
 
what is the desktop resolution message you get?  i wonder if it's something to do with your X settings.

---

### Post by fullyfandoo on 2009-03-05
Guys,

Thanks a lot for your suggestions.. Sudo Nautilus worked for me and I was able to backup my data..Now I'm going to reinstall Ubuntu...

---

### Post by xoorox on 2009-03-05
good good
 
If you reinstall over the same partition you may find your home folder files are preserved... I'm sure that happened to me once.  If the drive is reformatted then they won't be.  When you copy your files back into your home directory if you do have to do that then you may need to change the permissions on the files and folders - 
 
sudo chown -R user /home/user
 
be careful to get the syntax right with this... you only want to change the permissions for that specific folder ;)  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

