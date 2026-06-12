---
title: "Sudo issues!"
date: 2011-08-11
forum: Desktop Environments
---

### Post by Tyson87 on 2011-08-11
Hey All,

I logged into my linux box today and try to install something using sudo apt-get but it doesnt prompt me for my pw and it just gives me this reply.

server:~$ sudo apt-get install putty 
Sorry, try again.
Sorry, try again.
Sorry, try again.
sudo: 3 incorrect password attempts


I cant remember changing any files and am not sure what is going on. 

I tried Sudo root and i get authentication failure. 

below I have listed outputs that may help someone help me! thanks in advance. 


su root
Password: 
su: Authentication failure

id cgunn 
uid=1002(cgunn) gid=1002(cgunn) groups=1002(cgunn),4(adm),6(disk),20(dialout),21(fax),22(voice),24(cdrom),25(floppy),26(tape),27(sudo),29(audio),30(dip),34(backup),44(video),46(plugdev),60(games),103(fuse),104(lpadmin),112(netdev),115(admin),1000(aned),120(sambashare),129(ftp)

ls -la /etc/sudoers
-r--r----- 1 root root 587 2010-09-09 19:02 /etc/sudoers

---

### Post by wazupwiop on 2011-08-11
You have some major problems there.  I have never experienced this myself, but I think you might want to consider a reinstallation of the OS.  Here are a few questions I have that might be useful to others:

If you use a sudo command to do anything other than a download, what happens?

What kind of Ubuntu are you running (studio, xubuntu, etc.)?  What version (8.04 lts, 8.10, etc.)?

Have you noticed any other things affected by this other than the terminal?

What are you using your linux box for?  (Home server, media center, etc.)

Because the sudo command doesn't work, it may be hard to install programs or fix the problem.  A reinstallation might save you a lot of time if you don't have too many files on your linux box.  You can always take off your most important files and back them up on a drive somewhere, reinstall the OS, and then reinstall ubuntu or whatever linux OS you are using.

---

### Post by wojox on 2011-08-11
[ResetPassword]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by Tyson87 on 2011-08-18
Thanks guys, actually just rebooted it twice and it seemed to have corrected itself.

---

### Post by eentonig on 2011-08-18
> **Tyson87 said:**
> Thanks guys, actually just rebooted it twice and it seemed to have corrected itself.

Check your system closely for suspicious internet traffic. Seems like a possible rootkit.

---

### Post by Tyson87 on 2011-08-18
Actually now that you mention it, recently when i log out I lose internet connectivity and i do a ifconfig and eth0 is not listed.. i reboot and it comes back on or ill remove the cat 5 cable from the nic card and it comes back online.. Also, Im fairly new to linux to i wouldnt even know where to start looking for root kits. 

Thanks for the info.

---

