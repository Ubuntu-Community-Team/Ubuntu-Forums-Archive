---
title: "Boot up problem"
date: 2008-01-16
forum: Desktop Environments
---

### Post by Jorgel on 2008-01-16
Hello everybody.  I have a problem here. I installed KDE last night and everything was great!!  Go to work today turn on my computer and Grub takes me to the Kubuntu boot up screen. Here's where it gets irritating. The bar starts loading and then... it goes into a command line mode instead of the regular login. It asks for my user name.. done, asks for password...done and then..... it remains on the command mode and thats where I'm at.

What do I do to have it work properly again? I'm just an Ubuntu newb so many aspects of commads and such are still over my Linux knowledge.

BTW I'm currently on Live CD if that helps anything. Thank You

---

### Post by sumguy231 on 2008-01-17
In the broken system, try running 'sudo /etc/init.d/kdm start' and take down any error info. You can try reconfiguring the graphics by running this command:
```
sudo dpkg-reconfigure xserver-xorg
``` 
Just go through the wizard-type setup and answer the information about your hardware, then try
```
sudo /etc/init.d/kdm start
```
again.

---

