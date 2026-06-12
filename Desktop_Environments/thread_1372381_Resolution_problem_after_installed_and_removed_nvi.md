---
title: "Resolution problem after installed and removed nvidia-glx-new"
date: 2010-01-04
forum: Desktop Environments
---

### Post by IceTox on 2010-01-04
Hello!

I found myself wanting to "pimp" up my desktop, and starting reading about the various theme engines at 

[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

Following the advice about enabling compiz, I was forced to install nvidia-glx-new in order to get compiz fully working. After doing so, I rebooted, and my screen went black as soon as I reached the login window. (monitor didn't find any output)

So, I removed the nvidia drivers by "sudo apt-get remove nvidia-glx-new", and now it's back to normal. However, my screen resolution is reduced to 800x600.

-----
iceman@iceworld:~$ lspci | grep -i vga 
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)

-----

Where did I go wrong?

---

### Post by ratcheer on 2010-01-04
> **IceTox said:**
> Hello!

I found myself wanting to "pimp" up my desktop, and starting reading about the various theme engines at 

[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

Following the advice about enabling compiz, I was forced to install nvidia-glx-new in order to get compiz fully working. After doing so, I rebooted, and my screen went black as soon as I reached the login window. (monitor didn't find any output)

So, I removed the nvidia drivers by "sudo apt-get remove nvidia-glx-new", and now it's back to normal. However, my screen resolution is reduced to 800x600.

-----
iceman@iceworld:~$ lspci | grep -i vga 
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)

-----

Where did I go wrong?

Removing the nVidia driver means you fell back to the default VGA adapter that is part of the OS. To run hi-res graphics, you need to install one or the other nVidia drivers. I have been using the 195.22 Beta for several weeks with no problems. There is also a newer 195.53 alpha version, but I haven't tried it.

I have run an nVidia driver with Compiz, and I never found anything that didn't work.

Tim

---

### Post by IceTox on 2010-01-04
so I tried installing nvidia-gxl-new again, and went to "Hardware Drivers" and disabled the nvidia drivers before restarting. Than resolution is fixed, but I cannot use compiz without having the nvidia drivers enabled. 

Once I enable them, and restart I get still the blank screen.

Any clue?

---

### Post by ratcheer on 2010-01-04
I am having trouble understanding, because we do things in completely different ways.

I install the nVidia driver by downloading a .run file from the nVidia web site. I install it manually by these instructions:

Ctrl-Alt-F1
cd (to directory where you saved the nVidia .run file)
sudo service gdm stop
sudo sh ./xxxxxxxxx.run
(When the script asks if you want to autoconfigure xorg, select Yes)
sudo reboot

These instructions have always been successful for me. You should then be rebooted into a hi-res GUI environment. You should then be able to configure Compiz, as desired. You should not have to disable the nVidia driver.

I hope this helps.

---

### Post by IceTox on 2010-01-05
ratcheer, you have been most helpful :-) 

I did it the way you told me you did it, and now everything works super mate!

It looks like installing nvidia drivers using apt doesn't work too good with my system.

Again, you have been most helpful, ratcheer!

Thanks,

Cato

---

### Post by ratcheer on 2010-01-05
You are welcome. I am glad I could help.

Tim

---

