---
title: "Universal simple method to turnoff/disable touchpad"
date: 2010-03-03
forum: Desktop Environments
---

### Post by simonew on 2010-03-03
[SIZE=3]Disable/turn off Touchpad problem. Id be so glad if someone could help me.

I have a hp mini 210, and at first the touch pad didnt work properly, couldnt right click and so on.

But I found these commands to solve the problem and it did.

 $ sudo su

then  # echo options psmouse proto=exps > /etc/modprobe.d  /psmouse.modprobe

then   # reboot

Now the touchpad works perfectly.
But now I cant disable the touchpad in the mouse options because the check box is gone. I suppose it has something to do with the things I wrote above.

I dont want to turn off the touchpad in bios.

Ive tried the touchfreeze program but nothing happens.

Ive tried gsynaptics, but it says i have to edit xorg.conf file.
when i open it with gedit command. there is nothing in the file to add the "shmconfig on" command.

Ive installed syndaemon but it says i dont have a synaptic device. I suppose I have a non synaptic touchpad, which all of these methods and programs can be applied to. But I really dont know, I cant find touch pad specification for my hp mini anywhere. top of that i dont know much about touchpads or ubuntu. 
It seems like there is no button on the computer to turn the touchpad off, and no general command or program in ubuntu.

If someone have the time to explain to me what to do Id be greatful. Im a ubuntu newbie so please make it basic.

ok take care you all out there

simon
 
[/SIZE]

---

