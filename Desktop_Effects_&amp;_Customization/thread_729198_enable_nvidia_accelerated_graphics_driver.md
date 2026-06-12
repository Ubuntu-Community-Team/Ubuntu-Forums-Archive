---
title: "enable nvidia accelerated graphics driver ?"
date: 2008-03-19
forum: Desktop Effects &amp; Customization
---

### Post by smooth3006 on 2008-03-19
i already installed the latest graphics drivers for my nvidia card. but when i go to enable custom desktop appearance, i get this pop up from ubuntu. should i enable this ? i mean wont there be a conflict between my nvida drivers and this ? :confused:

---

### Post by smooth3006 on 2008-03-19
shouldn't my nvidia drivers i installed enable 3d graphics by default ? i just don't understand why ubuntu wants me to enable another driver ?

---

### Post by smooth3006 on 2008-03-19
BUMP.... any ideas guys ?

---

### Post by Jester_Paul on 2008-03-19
Enable it, it should be fine.  I'm using a restricted Nvidia driver as well.

Ubuntu likes to warn users that their drivers aren't free (open source), but it's perfectly fine and shouldn't cause any conflicts.

---

### Post by smooth3006 on 2008-03-19
> **Jester_Paul said:**
> Enable it, it should be fine.  I'm using a restricted Nvidia driver as well.

Ubuntu likes to warn users that their drivers aren't free (open source), but it's perfectly fine and shouldn't cause any conflicts.

yeah but i already installed the drivers from the nvidia website for my card. i don't see why i would have to install this too ? my graphics are fine as far as i know. i just don't know why it asked me to install that too ? i didn't think you could run two drivers for the same card ?

---

### Post by Jester_Paul on 2008-03-20
On my machine, I can't even run any desktop effects unless I enable the driver.  When I enable the driver in Ubuntu, it automatically downloads and installs the driver for me.  Where did you get your driver?  Directly from the Nvidia website?

I'm not by far an expert or anything, but I'd just enable the driver just to stop the dialog from popping up and annoying me. :)

---

### Post by patrickfromspain on 2008-03-20
have you set driver "nvidia" in your /etc/X11/xorg.conf?

---

### Post by smooth3006 on 2008-03-20
> **patrickfromspain said:**
> have you set driver "nvidia" in your /etc/X11/xorg.conf?

im sure my driver is working as i have custom desktop effects with compiz. yes i installed the driver from the nvdia site and with a guide i found online. it even installed a nvidia control panel.  i assume the x11 is set when the driver was installed, if not i have no clue how to do it ?

---

### Post by Therion on 2008-03-20
Go to System/Administration/Restricted Drivers Manager.  

Does THAT show the nVidia Restricted Driver being installed **and** "Enabled"?

There is a check-box specifically for enabling the installed Restricted Driver.

---

### Post by smooth3006 on 2008-03-20
> **Therion said:**
> Go to System/Administration/Restricted Drivers Manager.  

Does THAT show the nVidia Restricted Driver being installed **and** "Enabled"?

There is a check-box specifically for enabling the installed Restricted Driver.


heres a screenshot.

i don't see what difference it makes if i use restricted drivers provided by ubuntu or the official driver i installed from nvidia.  the question is which is better to use?  because i do know i can't have both enabled at the same time.

---

### Post by Therion on 2008-03-20
> **smooth3006 said:**
> heres a screenshot.

i don't see what difference it makes if i use restricted drivers provided by ubuntu or the official driver i installed from nvidia.  the question is which is better to use?  because i do know i can't have both enabled at the same time.
Personally, I use the Restricted Driver.  It will enable you to use your video card to it's fullest potential.  There are philosophical reasons for NOT using it, however, and if someone wants to explain them fine.  

More to the point though, you'll notice the checkbox I made reference to is NOT checked, so you are not currently using the Restricted Driver.  Clicking on that box will enable the restricted driver (after a reboot).  

Which driver you prefer to use it up to you, but that's HOW you enable the Restricted Driver should you decide you want to.

---

### Post by smooth3006 on 2008-03-20
> **Therion said:**
> Personally, I use the Restricted Driver.  It will enable you to use your video card to it's fullest potential.  There are philosophical reasons for NOT using it, however, and if someone wants to explain them fine.  

More to the point though, you'll notice the checkbox I made reference to is NOT checked, so you are not currently using the Restricted Driver.  Clicking on that box will enable the restricted driver (after a reboot).  

Which driver you prefer to use it up to you, but that's HOW you enable the Restricted Driver should you decide you want to.

thanks, i don't think it matters what driver i use. if i use the restricted ones, ubuntu automatically updates the driver if need be. if i use the ones straight from nvidia, i have to manually install new updates. for now until i encounter a problem i will use what i currently have installed.  :)

---

### Post by Therion on 2008-03-20
Okay just to clarify a couple things...  The driver you download from the nVidia website (or install using Envy) is the nVidia *Restricted* Driver.  It is written by the folks at nVidia.  It's called "Restricted" because the code for this driver is NOT open-source.

The driver you get from the Canonical/Ubuntu Repository is an *open-source* driver.  It's not as powerful as the Restricted Driver because nVidia doesn't want to release everything required to write an equally effective open-source driver.  ONLY fully open-source software is allowed in the Repos for distribution with Ubuntu. 

Hence you have the choice:  You can install a true, open-source driver found in the Repo (at the expense of a certain amount of hardware functionality) ... **OR** ... you can install the Restricted, non-open-source driver from nVidia (that will fully utilize your hardware's potential).

I'm not trying to sway your decision one way or the other -- I really don't care what driver you use -- but it was clear from your post you weren't understanding the finer points between the two driver choices.

---

### Post by smooth3006 on 2008-03-20
> **Therion said:**
> Okay just to clarify a couple things...  The driver you download from the nVidia website (or install using Envy) is the nVidia *Restricted* Driver.  It is written by the folks at nVidia.  It's called "Restricted" because the code for this driver is NOT open-source.

The driver you get from the Canonical/Ubuntu Repository is an *open-source* driver.  It's not as powerful as the Restricted Driver because nVidia doesn't want to release everything required to write an equally effective open-source driver.  ONLY fully open-source software is allowed in the Repos for distribution with Ubuntu. 

Hence you have the choice:  You can install a true, open-source driver found in the Repo (at the expense of a certain amount of hardware functionality) ... **OR** ... you can install the Restricted, non-open-source driver from nVidia (that will fully utilize your hardware's potential).

I'm not trying to sway your decision one way or the other -- I really don't care what driver you use -- but it was clear from your post you weren't understanding the finer points between the two driver choices.

oh i see, so even though i downloaded and thought i installed the driver form the nvidia website im still currently using the less powerful one then provided by ubuntu. so i guess i should enable the restricted driver after all. or am i totally off base here ?

---

### Post by Therion on 2008-03-20
> **smooth3006 said:**
> oh i see, so even though i downloaded and thought i installed the driver form the nvidia website im still currently using the less powerful one then provided by ubuntu. so i guess i should enable the restricted driver after all. or am i totally off base here ?
From what I can tell, you are using the open-source driver.  If you want to use the Restricted Driver, all you need to do is put a check mark in that little box that says "Enable".  You'll be prompted to reboot at that time and when you do, you'll be running under the Restricted Driver.  You will then be able to use ALL of the plugins that Compiz has to offer; some of which *require* the restricted driver.  

But again, if you're happy using the open source driver, there's no point in switching.

---

