---
title: "Barry software for using Blackberry as a modem"
date: 2009-04-08
forum: General Help
---

### Post by go_beep_yourself on 2009-04-08
Hello, I've been using my Blackberry curve model 8320 as a modem in Linux with the barry software. Some times it works. Other times it causes my Blackberry phone to do strange things such as turn the display black and blink a red light at the top and show an hourglass rotating for a while. Other times, it refuses to connect and gives tons of errors such as these.

): Error in usb_bulk_read
Exception in IpModem::DataReadThread: (-19, error submitting URB: No such device): Error in usb_bulk_read
Exception in IpModem::DataReadThread: (-19, error submitting URB: No such device): Error in usb_bulk_read
Exception in IpModem::DataReadThread: (-19, error submitting URB: No such device): Error in usb_bulk_read
Exception in IpModem::DataRea^CException in IpModem::DataReadThread: (-19, error submitting URB: No such device): Error in usb_bulk_read
select(): Interrupted system call
exception caught in main(): (-19, error submitting URB: No such device): Error in usb_bulk_read


Whats the correct way of turning off the script? I tried running sudo poff in another console. I was going to reset the connection because I couldnt load webpages, but then it wouldnt redial giving me this message.

chris@ubuntu:~/Desktop$ sudo pppd call barry-tmobileus
[sudo] password for chris: 
Initializing
No device selected
Connect script failed
Script /usr/sbin/pppob finished (pid 9892), status = 0x1
chris@ubuntu:~/Desktop$ lsusb
Bus 006 Device 005: ID 0781:5151 SanDisk Corp. Cruzer Micro 256/512MB Flash Drive
Bus 006 Device 003: ID 0c45:6282 Microdia Audio (Microphone)
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 0fca:0004 Research In Motion, Ltd. 
Bus 001 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 03f0:7a04 Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
chris@ubuntu:~/Desktop$ mount | grep -i blackberry
/dev/sde1 on /media/BLACKBERRY_ type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
chris@ubuntu:~/Desktop$ 

It causes screen to go black and red light to turn on at top
have to take phone battery out and reboot phone and reboot linux for it to work again

chris@ubuntu:~/Desktop$ sudo pppd call barry-tmobileus
Initializing
exception caught in main(): (-19, No error): Error in usb_bulk_read
Connect script failed
Script /usr/sbin/pppob finished (pid 19167), status = 0x1
chris@ubuntu:~/Desktop$

---

### Post by billdotson on 2009-08-17
bump. This guy has posted on at least two different forums with no help yet. I am having this issue as well, does anybody have an idea of why this is going on?

Thanks.

---

### Post by billdotson on 2009-08-17
I think part of the problem with this might have to do with the device numvers given by lsusb. My blackberry shows up as device 003 and his is 006. I have heard it needs to be 004 or 001. However, I cannot find what all the codes for the lsusb output mean and do not know how to tell the system to recognize it as that type of device.

---

### Post by go_beep_yourself on 2009-08-19
> **billdotson said:**
> I think part of the problem with this might have to do with the device numvers given by lsusb. My blackberry shows up as device 003 and his is 006. I have heard it needs to be 004 or 001. However, I cannot find what all the codes for the lsusb output mean and do not know how to tell the system to recognize it as that type of device.

I've solved the problem already. Here's what you do. First, get the latest svn of all the barry software. Ok, those lsusb codes just mean which usb port you have the phone plugged into. Try plugging it into a different usb port, and see if that number changes, so really, that number is irrelavent. Now it always works fine the first time I make a connection, but if I lose connection for whatever reason. I do this.

```
chris@ubuntu:~$ psgrep pppob

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
chris     4211  0.0  0.0   7524   904 pts/1    S+   03:33   0:00 grep --color=auto pppob
root     13933  0.0  0.0   4024   248 pts/3    S+   Aug18   0:00 sh -c /usr/sbin/pppob -P hidden
root     13935  0.8  0.0  26720   840 pts/3    Sl+  Aug18   2:46 /usr/sbin/pppo  -P hidden
chris@ubuntu:~$ 
```

psgrep is just a bash function I created in my .bashrc using the ps command. Right now I am connected with no problems, but if you encounter a problem. See if pppob is still running in the background. If it is, you will need to kill it like this.

```
sudo pkill -9 pppob
```

Sometimes these are necessary and some times not to make the BB work again as a modem.

```
btool -X
breset

```

If you do those commands, be patient. Look at your blackberry screen. If it shows an hour glass, check again in a few minutes and then after loading security software is completed, you can attempt to redial again.

---

