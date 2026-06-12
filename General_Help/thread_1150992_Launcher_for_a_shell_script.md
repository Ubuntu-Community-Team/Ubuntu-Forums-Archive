---
title: "Launcher for a shell script"
date: 2009-05-06
forum: General Help
---

### Post by firemedic624 on 2009-05-06
I'm not sure if this the proper place for this question.  If not please move it to the appropriate place.  I have a program that I use to tether my Blackberry to my computer for internet access.  The program is berry4all aka bbtether.  It is extracted to my home folder but needs to be run as root so it will recognise the phone.  To run program I start the terminal and enter the following command: _**[COLOR="Blue"]user@user:~/bbtether$ sudo /bbtether/berry4all.sh[/COLOR]**_.  I then have to enter the password for sudo and then the program starts.  What I want to do is create a launcher or something so I can run the program with a single click without having to enter the password for sudo.  Is there a way to do this?  I have looked all over google and can't really find anything that works.  Any help is appreciated.

Thanks Tim :confused:

---

### Post by aquavitae on 2009-05-06
I assume its a bash script?  Do you know exactly why it needs root permissions?  If its just a single program it needs to run, you might be able to do it by changing the permissions on that program, although that's a bit risky. If it needs to use "mount", you might be able to modify it to use pmount.  Maybe you could post the script?

---

### Post by firemedic624 on 2009-05-06
All I know is that it won't recognize the phone if it's run with the user privaliges.  Here is the conntents of berry4all.sh.

#!/bin/sh
python bbgui.py

---

### Post by aquavitae on 2009-05-06
try running ```
sudo chmod u+s berry4all.sh
```
It should change the permissions to suid for the script, meaning that it will always run with root permissions without a password.  Then you can run it without sudo.

---

### Post by firemedic624 on 2009-05-06
Ok I tried that and it didn't work.  It starts the program but it is uable to find the phone.  Also I looked over my original post and realised that I wrote the command down incorrectly.  This is the command I have to enter: _**[COLOR="Blue"]user@user:~/bbtether$ sudo ./berry4all.sh[/COLOR]**_.  Sorry about that.

---

### Post by firemedic624 on 2009-05-06
bump

---

### Post by aquavitae on 2009-05-07
Sorry, I got myself confused.  The command I gave you won't fix it - my concepts were muddled.  But you should be able to tweak the sudo config file to allow you to run it without entering a password.  I just need to check how then I'll post back.

---

### Post by geirha on 2009-05-07
Have you tried these instructions?
[http://www.berry4all.com/faqs#why_needs_to_run_as_root_](http://www.berry4all.com/faqs#why_needs_to_run_as_root_)

---

### Post by aquavitae on 2009-05-07
There are two ways of doing this.  The first is to give yourself permission to use sudo on that file without entering a password, and then creating a new script which runs "sudo berry4all.sh", which you will be able to run by clicking on it.  The second it to add a udev rule so that beery4all.sh is automatically run with root permissions when you plug the device in.  I've got both methods below:

**1. Using sudo**

Type the following to edit the sudoers config file:
```
EDITOR="/usr/bin/gedit" visudo
```
It should open it up in gedit (text editor), then add this line to it, replacing <...> with the appropriate commands:
```

*<username>*    localhost = NOPASSWD: *<full path to berry4all.sh>*
```
For example, if your username is "joe", you might have this:
```
joe   localhost = NOPASSWD: /home/joe/bbtether/berry4all.sh
```
You then need to create a script file (e.g. called runberry.sh) containing the following:
```
#!/bin/sh
sudo *<full path to berry4all.sh>*
```
And make it executable:
```
chmod a+x runberry.sh
```
You should be able to run it just by clicking runberry.sh.

**2. Using udev**

This is a bit more complicated (but probably far more useful), so if you get stuck, just post the output you've got so far from the various commands below and I'll see if I can help further.

The first thing you need to do is to find out some information about the device. Plug in the blackberry and run this command: ```
tail /var/log/messages
```
You should see a log of events which occurred when you plugged it in, at somewhere in it you will see the device name its been given (e.g. /dev/ttyUSB0) I'm going to assume that that's the name for the rest of the commands, so wherever I've used it, just replace it with what you've got. The next step is to get the udev info about it:
```
udevinfo -a -p $(udevinfo -q path -n /dev/ttyUSB0)
```
You should get a list of values something like this (taken from [http://reactivated.net/writing_udev_rules.html]("http://reactivated.net/writing_udev_rules.html")):```

looking at parent device '/devices/pci0000:00/0000:00:07.0/host0/target0:0:0/0:0:0:0':
    KERNELS=="0:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{ioerr_cnt}=="0x0"
    ATTRS{iodone_cnt}=="0x31737"
    ATTRS{iorequest_cnt}=="0x31737"
    ATTRS{iocounterbits}=="32"
    ATTRS{timeout}=="30"
    ATTRS{state}=="running"
    ATTRS{rev}=="3.42"
    ATTRS{model}=="ST3120827AS     "
    ATTRS{vendor}=="ATA     "
    ATTRS{scsi_level}=="6"
    ATTRS{type}=="0"
    ATTRS{queue_type}=="none"
    ATTRS{queue_depth}=="1"
    ATTRS{device_blocked}=="0"

```
The last step is to write a rule for udev. This is quite complicated to explain, but if you want to give it a try, read [http://reactivated.net/writing_udev_rules.html]("http://reactivated.net/writing_udev_rules.html").  Otherwise post the output from the commands above and I'll write one for you.

---

### Post by aquavitae on 2009-05-07
> **geirha said:**
> Have you tried these instructions?
[http://www.berry4all.com/faqs#why_needs_to_run_as_root_](http://www.berry4all.com/faqs#why_needs_to_run_as_root_)

I wish I'd read that before typing my long howto above!  Its a far better solution, although you could still modify 99-bbtether.rules to run berry4all.sh when inserted.

---

