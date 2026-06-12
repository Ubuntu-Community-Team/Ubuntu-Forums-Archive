---
title: "Screen Hang up while installing and booting."
date: 2017-06-16
forum: Debian
---

### Post by cooldean on 2017-06-16
Hello Sir/Madam, 
I face a technical problem while migrating the Debian from a laptop to the virtual box in Windows Server ( it is one of the VMs in a physical server as well). 
it was running without any problem in my laptop (development environment), but it failed to startup in the Virtualbox in the Server; the screen hangs up at booting stage. 


```

....
....
....
[  3.241483] Write protecting the kernel read-only data: 1036k loading, please wait...
[  3.241483] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
[  3.241484] udevd[41]: starting version 175

```


the screen stopped at the stage 'starting version 175'.


I did some research and tried many solutions below, but it still did not work. 
1) I thought it might cause by the unsupportive driver of the graphic in the Windows Server, so I boot it under 'nomodeset' mode, but it still did not work. 
2) I tried to install Debian in the Virtualbox in the Windows Server via ISO directly, but it also showed black screen before getting into Install Wizard; I tried to press 'tab' and triggered Install Wizard under 'nomodeset' mode, but it still hung up with black screen before getting into Install stage.
3) I tried to install Ubuntu in the Virtualbox via the ISO file direct. It did not works as well (the result was as same as 2). 
4) I tried to find the VM via file, and booted by the VirtualBox it showed black screen even booting by 'nomodest' mode, the result was the same. 
5) I tried to install and create another Debian VM without Gnome in my laptop and migrated to the Virtualbox in the Server, the result was as same as the step 2. 
6) I was thinking to turn on EFI in BIOS setup. However, I have to wait for annual shut down in next year because too many application in running the in the server. 


I am wondering if there is anyone how can give me some advice. Any advice are highly appreciated. I have been struggling at the problem for several days. :cry:  Thanks.  :wink:

---

### Post by howefield on 2017-06-16
Thread moved to the "*Debian*" forum.

---

