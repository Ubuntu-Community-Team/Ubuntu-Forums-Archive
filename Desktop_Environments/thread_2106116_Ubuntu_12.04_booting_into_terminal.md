---
title: "Ubuntu 12.04 booting into terminal"
date: 2013-01-18
forum: Desktop Environments
---

### Post by nagubhai on 2013-01-18
Hello Guys,

After updating my pc with latest updates, when i restart my pc it is booting into terminal as below

[IMG]http://img8.uploadhouse.com/fileuploads/17181/171812914e81ef0696974fa2cd88e5218bf72c79.jpg[/IMG]

When enter "startx" command in the terminnal I am receiving below output:

[IMG]http://img1.uploadhouse.com/fileuploads/17181/1718129926ded855654f848c243b762d5ac31dbb.jpg[/IMG]

I am able to boot into Ubutnu using "Previous Linux versions". :popcorn:

Please help what is the issue here?

---

### Post by dms-audio on 2013-01-18
Have you installed the nvidia drivers at some earlier date or are you using the open source ones ?

You could try booting into the previous kernel if you have not removed it. Should be in your grub boot menu.

If you have installed the binary nvidia drivers then you may want to remove them from command line and revert back to the open source ones as a test.
I am on an ati card with the binary drivers and occasionally kernel updates can break things.

---

### Post by Rsxhawk on 2013-01-18
I have had a similar issue on my 12.04 64-bit install.  It doesn't happen all the time but sometimes when the machine is rebooted, it will boot into that first screen you posted where it displays the login at a terminal input.  Instead of providing my credentials, I just hit enter and then it boots into the GUI like its supposed to.  I'm not sure why it gets confused and does this as it doesn't appear to be negatively impacting anything its just kind of a nuisance.  

I am not experiencing the second screen you have posted though, sorry.  Since I started using linux, it seems to be plagued with little issues like this that really detract from its overall appeal.  Why can't these small issues get resolved so our machines just boot like its supposed to?  Its not enough for me to quit using linux, its just annoying when simple things like, um, rebooting (a simple task) become another hurdle of just using the machine.

---

### Post by grahammechanical on 2013-01-18
Ubuntu sits on top of the Linux kernel which uses a command line interface. So, first the kernel is loaded and then Ubuntu logs into the kernel in our name and then loads to a GUI log in screen. Most of the time this login to the kernel is hidden from view by a splash screen. I some times see the Linux message when I am running the Ubuntu development release. But I have never had the loading stop until I pressed enter.

I also think that a lot of issues are caused by heavy modification of the OS. Lots of configuration scripts are run during the loading process. There can be conflicts that require more than one attempt to activate modules.

Regards.

---

### Post by jimmytbane on 2013-01-18
Whats happening here looks similar to what happens when you use the command ctrl + shift + F1. (could be ctrl + alt + F1). I don't know a quick way to fix your problem but if you burn a 12.10 cd and load it up it has an option to repair ubuntu or write over it. Just think about if your willing to do that.

---

### Post by Kantstandya on 2013-01-18
After yesterdays system update (which also updated some x-server components from what i remember) I had the same problem. System would boot into terminal. 

startx command gave me almost the same error:
[img]http://imageshack.us/a/img189/7986/sta702252.jpg[/img]

So i figured it must be because of then latest nvidia drivers I installed directly from nvidias website some time ago.

Removing and then installing nvidia-current package solved this:
```
sudo apt-get remove nvidia-current
sudo apt-get install nvidia-current
```On the side note I had to boot into my Windows 7 partition to google this solution, a system that has never failed me. On the other hand I've had about a dozen problems with ubuntu 12.04 x64 since i got it 2 months ago. Often something would stop working for no apparent reason or after a system update and I have to google a fix. The only reason I havent send this system back to where it came from yet is because I like learning it. Go figure O_o

---

### Post by nagubhai on 2013-01-19
Thanks for all responses.

I resolved it myself. I don&#8217;t know what i did exactly to resolve this. Below are the actions which did:
1. Removed NVIDIA drivers
2.Tried to install drivers from UI. It failed.
3.When I restart my PC, it asked for partial upgrade. I accepted it. Boom my UI is back

---

