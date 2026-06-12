---
title: "NVIDIA Geforce 7900 GS: Can't Enable Visual Effects"
date: 2008-12-17
forum: General Help
---

### Post by Macadeus on 2008-12-17
I have reinstalled Ubuntu 8.04 just to start with a clean slate of drivers. In the past i have enabled the accelerated driver through system->admin.->hardware drivers and then not been able to enable Visual Effects. is there a specific driver for my graphics card?

---

### Post by Macadeus on 2008-12-17
I also have not updated anything on my computer. I just installed Ubuntu 8.04 and left it alone.

---

### Post by Therion on 2008-12-17
Okay, so you are probably being "alerted" that there are restricted drivers available but you have not yet installed them, is that correct?  

If you're NOT being told that there are restricted drivers available, that would indicate that your video card is not being properly recognized.

Assuming it IS being properly recognized, I suggest you do your normal updates FIRST.  Do them all, rebooting and such as required, and not worrying about your video driver just yet.  Do all your updating and THEN go to the Driver Manager and install the restricted driver.

---

### Post by Macadeus on 2008-12-17
i didn't get a message however saying i have restricted drivers, but it is listed when i go to the hardware drivers:
NVIDIA accelerated graphics driver (latest cards)

---

### Post by graysky on 2008-12-17
You might wanna head over to the [official nvidia site](http://www.nvidia.com/Download/index.aspx?lang=en-us) and grab their driver for your architecture.  Installing the nvidia driver under Ubuntu/Debian is cake:

Make sure you have the linux-headers for your kernel as well as make and gcc (you can get them via apt-get or aptitude).

drop to another tty (ctrl+alt+F1)
$ su
# /etc/init.d/gdm stop
# cd /path/to/your/driver/download
# sh NVID<TAB>

(run the installer, answer the questions, compile and you're done)

# /etc/init.d/gdm start
_________________

---

### Post by Therion on 2008-12-17
Alright so you do NOT have the restricted driver installed yet, but the Hardware manager has properly identified your video card.  This is good.  Do NOT install the video driver yet.

Do your regular updates now.  You'll need to reboot and then check, manually, for more updates.  

When there are no more updates to be installed, THEN install the restricted driver and reboot your PC.

After that reboot, attempt to enable Desktop Effects.

---

### Post by Macadeus on 2008-12-17
This is a dumb question and i feel like a complete idiot, what do you mean by manually check? I ran the update via this code:
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install linux-image-generic linux-headers-generic
I'll check it through the system->update thing once i reboot

---

### Post by Therion on 2008-12-17
Oh...  So you're doing a dist-upgrade then?  What version of Ubuntu were you starting from; was it 7.10 or what?  I was assuming this was a fresh install.

When I say do your updates "manually", I just mean going to System/Administration/Update Manager and installing the updates it finds.  No need to feel stupid for asking.

---

### Post by Kevbert on 2008-12-17
You may need to set up your Software Sources. Go to System-Administration-Software Sources and check that the top four boxes are ticked under Ubuntu Software and Important, Recommended and Unsupported boxes are ticked under the Updates Tab. If you now update with the command you first used you should get the option to install a Restricted Driver for your display adapter.
If you want Compiz go to Applications-Add/Remove and search for ccsm (and install it).

---

### Post by philinux on 2008-12-17
System>admin>hardware/restricted drivers. Select the recommended one and install it.

If it says it's in use it's already installed.

---

### Post by Macadeus on 2008-12-17
ok, it works, but now my resolution is like 640x480 and i can change it only to 320x240, each at 50 hz

---

### Post by Macadeus on 2008-12-17
i fixed the last problem by editing my xcorg.conf file. I just want to say thanks everyone for the help

---

