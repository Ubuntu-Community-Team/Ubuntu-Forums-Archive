---
title: "nVidia driver issue, i'm new please help"
date: 2009-05-28
forum: General Help
---

### Post by trexler on 2009-05-28
I have been trying to figure out why I can not use the restricted drivers. I have 2 nVidia 9800 gtx+ graphics cards. I do not know if sli is enabled in ubuntu. I'm running the latest version. Whenever I install the driver and restart it takes me to a terminal screen. I do not ever get to the desktop. I've researched for hours but I can't get any straight answers and I don't know how to get back to the desktop without reinstalling ubuntu because I'm not very good with the terminal. I do not care if I use sli in ubuntu but I do not want to take out the card because I use it when I'm in windows.

I'm wondering if I can just disable one video card and then install the driver. Maybe that will work but I'm no expert. I can follow directions really well so any help will be greatly appreciated.

---

### Post by gettinoriginal on 2009-05-28
Hi, welcome to ubuntu.  First, check System > Administration > Software Sources (enter password), then make sure that the first 4 boxes are checked.  Then open a terminal and copy paste the following:
```
sudo apt-get install linux-restricted-modules
```
Now you should be able to go System > Administration > Hardware Drivers and enable the driver that is recommended.

---

### Post by michy99 on 2009-05-28
If you read his post you would see that he is not able to get to the desktop.

---

### Post by gettinoriginal on 2009-05-28
I understood the OP to say they could not access the desktop when trying to install the driver.  I appologize if that is not the case.  If there is no desktop, the OP can try this, then use the previous post.
System Restore
Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

---

### Post by dagrump on 2009-05-28
OK, you are not going to like it but if you want sli, it requires a bit of elbow grease. first you install the drivers & reboot. Now you get a terminal you log in. first you need to know the bus ID of your video cards & determine which is your primary card. so you would type lspci, this will give a list of your hardware. look for your video cards & note the numbers at the front of the listing. Should look something like 01:00.0 or the like.
Now I use my upper card, which is the bus id I use as the primary card, that why I say note them both, if you pick the wrong one you just edit the file you are getting ready to create. 
Now comes the fun part, type sudo nvidia-xconfig, it will ask for your password, & hit enter. Now you have an xorg.conf file, that we need to edit.
To do that you you type sudo nano /etc/X11/xorg.conf & hit enter. To edit arrow down to the line above where you wish to insert a line & hit enter, arrow down & enter your info. It should have the lines added in the devices section like this file.
Now that you have added the the line BusID  "01:00:00" or whatever yours is  & the Option "SLI"   "SFR" in the device section. You would use ctrl+o to overwrite or save the file & ctrl+x to leave nano.
You should be back to your prompt now. So we need to restart & see if she flies. So, sudo shutdown -r now, enter. Hope that gets ya there.  
I can't get that text file to open right, You might look in the 64 bit support & search for sli. I know I attached it before.

---

### Post by trexler on 2009-05-29
Thanks for your replies. I am currently at work so I will try this when I get home. You are correct gettinoriginal, I can currently get to the desktop because I do not have the driver installed at the moment.
I will try your way first and then if it still takes me to the terminal screen I log into upon reboot then I will try dagrump's reply.

---

### Post by MedellinManDem on 2009-05-29
> **gettinoriginal said:**
> Hi, welcome to ubuntu.  First, check System > Administration > Software Sources (enter password), then make sure that the first 4 boxes are checked.  Then open a terminal and copy paste the following:
```
sudo apt-get install linux-restricted-modules
```
Now you should be able to go System > Administration > Hardware Drivers and enable the driver that is recommended.

This doesn't work for me.

The light doesn't turn green at all.

---

### Post by gettinoriginal on 2009-05-30
Is there a button for "activate" ??  When it does the driver search,  Does it give you a recommended driver ?? Is there a button for "activate" ??  You can also try:
```
sudo apt-get install linux-restricted-modules-generic meta-package
```

---

