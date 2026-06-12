---
title: "Man Down.. Ubuntu hosed"
date: 2007-12-17
forum: Desktop Effects &amp; Customization
---

### Post by LT72884 on 2007-12-17
Ok, here is what has happened. I HAD ubuntu(7.04) all nice and perty with beryl working like a charm. i think i used ENVY to grab the newest nvidia driver at the time ( 4 months ago). I never update my system because i was using it for my Linux class labs. So last week or so i decided i wanted to update. It installed 114 packages. I rebooted and KABOOM. blue screen saying that xserver is hosed due to the nvidia kernel. so i fiddle for three or so hours trying to do 
#apt-get install nvidia-glx-new

it installs but a no go. so i use envy in text mode and grab the newest driver again and now i get a signal over range and now beryl crashes my system and i cant do any visuals. for some reason the desktop properties wont allow me to choose a refresh rate any higher than 45hz. and a res over 800x600. i used to be able to get 1024x768 at 75hz. This all happened on a pc. the funny thing is i just installed 7.04 on my everex laptop that has the nvidia 7600 card and i followed an online tutorial on installing beryl and it craps out. it crashed and actauly did a UNSAFE restart according to the boot screen. so i had to do a fsck on the HDD. Now beryl semi works. it loads but when i double click on the terminal or any other file it opens it in all white. i try to rotate cube and it locks it up. it used to work so something happened between 3 months ago and now with beryl.

---

### Post by MNICY on 2007-12-17
You updated with drivers you got from ENVY installed. Thtas the problem.
You have to uninstall before the update :(

There probaly is a way to fix it, but i would back up any data and reinstall the system.

---

### Post by LT72884 on 2007-12-18
> **MNICY said:**
> You updated with drivers you got from ENVY installed. Thtas the problem.
You have to uninstall before the update :(

There probaly is a way to fix it, but i would back up any data and reinstall the system.

what do you mean. Envy is used to update nvidia. why would i have to uninstall my nvidia drivers before updating.I have never had to uninstall any drivers before updating.  i was just updating packages not the nvidia kernel itself. im so lost. lol. envy doesnt tell me that i have to uninstall anything, neither does the packet manager or software updater.

---

### Post by LT72884 on 2007-12-18
im so lost. lol. you guys sure know how to make me confused. ok so what is the best way then to install beryl. it doesnt work for me and it used to. Not even on my new laptop does it work.

---

### Post by Tristam Green on 2007-12-18
I think I had this same issue with Envy and my ATI drivers.  The simple fix for me was to uninstall Envy and then continue using my ATI restricted drivers.  Sorry to hear this happened to you though; I'm unsure if your fix is as simple :\

---

### Post by PmDematagoda on 2007-12-18
First clean out all your Nvidia drivers.

Use:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

after reconfiguration do:-

```
sudo startx
```

To make the driver vesa which should bring you to a GUI.

Then do:-

```
sudo apt-get remove nvidia-glx-new
```

After that remove the Nvidia driver that was installed using Envy using Envy itself(There are two drivers since you installed one using Envy and the other using the repos and they are not the same.

Once you finish that, you can use the Restricted Drivers Manager to install the drivers for the VGA card using the repository, or you can use Envy, either way is fine but do not do both.

That should fix your problem.

---

### Post by LT72884 on 2007-12-18
i will do that but i never installed the driver using a repo. it has allways been envy on my PC. is there a way to tell if i have two diff drivers? i have allways used envy on my PC. i used a repo for my laptop.

ok under xserver config it list like 7 diff drivers to pick from, im guessing i want the 7th one that says vesa.

---

### Post by LT72884 on 2007-12-18
ok that didnt work. that pretty much turned off my card. i did the 

sudo dpkg-reconfigure -phigh xserver-xorg

then choose vesa as driver and then choose my resolutions and then hit enter and it saved it. I then did a 

sudo startx

and now my monitor goes to off mode. "NO RGB SIGNAL" then turns off.

thanx for the help so far though. i have no idea what is going on LOL. the story of my life

---

### Post by LT72884 on 2007-12-18
i think i have to reinstall OR i might try apt-get dist-upgrade. Even in recovery mode it doesnt want to work.

---

### Post by lswest on 2007-12-18
what could be the problem is that the software updated itself and installed some drivers that are for the new kernel, so a distribution upgrade might help.

---

### Post by LT72884 on 2007-12-18
> **lswest said:**
> what could be the problem is that the software updated itself and installed some drivers that are for the new kernel, so a distribution upgrade might help.

yup i think thats what happened becasue i went into recovery mode and did a 

root#sudo dpkg-reconfigure -phigh xserver-xorg

picked nv for the driver and then my resolutions. did a 

root#sudo startx

and it actually got me into gnome. so then i went to konsole because i couldnt find terminal. i ran a

sudo apt-get remove nvidia-glx-new
sudo apt-get remove nvidia-glx
sudo reboot

then i get blue screen of death that says cant start xserver want to read error out put. so i hit yes and then it says FAILED to load NVIDIA kernel modual.

---

### Post by lswest on 2007-12-18
well, that means the configuration of your xserver is wrong, try changing it back to VESA and trying to boot from there.

---

### Post by LT72884 on 2007-12-18
> **lswest said:**
> well, that means the configuration of your xserver is wrong, try changing it back to VESA and trying to boot from there.
did that and my screen goes black and say "RGB NO SIGNAL" lol. its driving me nuts.

---

### Post by BigSilly on 2008-03-22
> **PmDematagoda said:**
> First clean out all your Nvidia drivers.

Use:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

after reconfiguration do:-

```
sudo startx
```

To make the driver vesa which should bring you to a GUI.

Then do:-

```
sudo apt-get remove nvidia-glx-new
```

After that remove the Nvidia driver that was installed using Envy using Envy itself(There are two drivers since you installed one using Envy and the other using the repos and they are not the same.

Once you finish that, you can use the Restricted Drivers Manager to install the drivers for the VGA card using the repository, or you can use Envy, either way is fine but do not do both.

That should fix your problem.

Just wanted to post up and say thanks for your info here. I've just successfully rescued my Ubuntu install with this bit of text! I'd installed a new graphics card today, and thought I needed to install nvidia-settings from Synaptic. This I did and it unfortunately it removed my Nvidia driver too and left me with no screen, just a terminal and no clue what to do. Luckily I dual boot with Mandriva, so I came here looking for assistance and your post helped me out of a big mess!

Thankyou very, very much indeed! Phew eh? :D

---

