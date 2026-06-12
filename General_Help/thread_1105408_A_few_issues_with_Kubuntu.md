---
title: "A few issues with Kubuntu"
date: 2009-03-24
forum: General Help
---

### Post by iareConfusE on 2009-03-24
Hey guys first post here, I did a search on the forum and on google, I couldn't seem to come up with a solution to either of my problems.  Ive just installed kubuntu (Intrepid) on an Acer Aspire one.

The first problem I have is that the windows are too big, and doesn't take into account the taskbar at the bottom of the screen.  For example, when I am in the desktop appearance window, the "Apply Changes" button is hidden underneath my taskbar.  I have the resolution set to 1024x600.  Any way to fix this?  It only seems to be a problem with these settings windows.  Internet browsers and other programs seem to take the taskbar taking up space into account.

My second problem is getting the wireless to work.  I'm pretty new to linux.  I've tried both Ubuntu and Kubuntu, but both with wired connections, now I'm trying it with a wireless for school use. I can't get the wireless to turn on at all.  I followed the directions at this website: [http://www.dawhoo.com/how-to-install-kubuntu-on-acer-aspire-one/](http://www.dawhoo.com/how-to-install-kubuntu-on-acer-aspire-one/)
When I get to the part where it tells me to type tar xzvf, konsole tells me that tar is an old command, and I don't know where to go from there... I'm sure others have gotten their wireless to work on their Aspire Ones, so any help would be greatly appreciated.  
Assuming I get the wireless driver to work, I'm still unsure about how to actually find these wireless networks.  I'm used to Windows, where I could just right click the icon and click search for wireless networks in range, and I don't see anything like it on Kubuntu.

Thanks in advance.

---

### Post by acmariner99 on 2009-03-24
What kind of wireless card do you have? I would suggest trying to load the b43 driver if you use a brodcom card. Also, find on kubuntu where the restricted drivers are listed and see if a wireless driver is loaded.

---

### Post by iareConfusE on 2009-03-24
> **acmariner99 said:**
> What kind of wireless card do you have? I would suggest trying to load the b43 driver if you use a brodcom card. Also, find on kubuntu where the restricted drivers are listed and see if a wireless driver is loaded.

I think I've got an Atheros card... Also, I'm not sure where to find restricte drivers, would you mind showing me?  I'll poke around while I wait.

---

### Post by acmariner99 on 2009-03-24
I am not sure about the KDE layout as I use GNOME, but I would look for something like System -> Administration -> Hardware Drivers. If a driver for your card is listed, activate it and restart the computer. If not go to the following site for where to get the driver. 

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

Unfourtunately you need an ethernet connection to see it. (I had a lot of trouble getting my wireless to work, but now, it works flawlessly). After loading the driver you will need to determine how you connect to networks. Since I do not know KDE I cant really help you there.

---

### Post by iareConfusE on 2009-03-24
> **acmariner99 said:**
> I am not sure about the KDE layout as I use GNOME, but I would look for something like System -> Administration -> Hardware Drivers. If a driver for your card is listed, activate it and restart the computer. If not go to the following site for where to get the driver. 

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

Unfourtunately you need an ethernet connection to see it. (I had a lot of trouble getting my wireless to work, but now, it works flawlessly). After loading the driver you will need to determine how you connect to networks. Since I do not know KDE I cant really help you there.

Thanks, I may actually just switch back to Ubuntu, since I'm also having some other graphical errors with the KDE desktop...Is the same process for getting the wireless card to work on Kubuntu the same for Ubuntu?

---

### Post by acmariner99 on 2009-03-24
Yes. Actually I think it is easier. I never liked KDE. If the driver is not listed as a "proprietary driver" you will need to install it manually. The web site in my previous post describes the driver you need and the process you need to follow to install it.

---

### Post by polkadotteapot on 2009-04-12
Hello,

did you have any luck with kubuntu? I'm trying it now on my Acer Aspire One while I sort out what I've broken on ubuntu ([http://ubuntuforums.org/showthread.php?t=1122506](http://ubuntuforums.org/showthread.php?t=1122506)).

To get the wireless working try loading this here first: [http://www.aspireonekernel.com/#Downloads](http://www.aspireonekernel.com/#Downloads)

---

