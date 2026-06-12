---
title: "Ubuntu 14.10 - NVIDIA 346.35 - Unity not starting"
date: 2015-02-10
forum: Desktop Environments
---

### Post by Lucas_Ricardo on 2015-02-10
I'm trying to use unity after update nvidia driver from 340.65 to 346.35, but no success. Loads only wallpaper, there are no icons, there is no toolbar. I tried a lot of solution...but still the same, the commands that I tried:

dconf reset -f /org/compiz/  **(OK)**

setsid unity  [COLOR=#ff0000]**(ERROR)**[/COLOR] "compiz (core) - Error: Plugin 'opengl' not loaded."

unity --reset-icons [COLOR=#ff0000]**(ERROR)**[/COLOR] "compiz (core) - Error: Plugin 'opengl' not loaded."

Tried to downgrade the nvidia driver to the same 340.65 no success, the problem continues.

Anybody have some idea?

---

### Post by v3.xx on 2015-02-10
Can you go to recovery mode and bring up CCSM (compiz control panel) then activate the opengl plugin?

---

### Post by richlion2 on 2015-02-12
Hello, 

I am very new to Ubuntu, so I my experience is a bit not as good as with other distros. What I do know is that since new Nvidia screwed up my other distros which was Gentoo and Sabayon I decided to try both Ubuntu and Kubuntu on an HP laptop with an Nvidia cards. After the installation I installed the 340 driver, I also installed nvidia-settings, however nothing worked until I rebooted my machine. I will not tell if the Nvidia driver above 340 would cause any issues, I haven't tried. 
After the reboot everything works like a charm, no errors whatsoever.

Regards, 
Richlion

---

### Post by grahammechanical on 2015-02-12
How did you install both of those Nvidia drivers? Ubuntu and Kubuntu for that matter have an Additional Drivers utility that offers Nvidia 331.133 or 3.04.125. There is a reason why the Ubuntu developers are not quick to make the latest Nvidia drivers available through Additional Drivers.

How did you remove one Nvidia driver and install another? What commands did you use? There are a couple of things we can try in this situation.

1) At the desktop wallpaper, right click the wallpaper and if a menu appears select change desktop background. That will open System Settings and from there  we can get to Software and Updates>Additional Drivers tab and change video drivers.

2) Use Recovery mode Resume. That may load to a working desktop using an open source video driver called llvmpipe. From there we go to System Settings>Software and Updates>Additional drivers tab.

Is this referring to the first time you installed Ubuntu and Kubuntu and before you installed Nvidia 340.65?

> [COLOR=#000000]After the installation I installed the 340 driver, I also installed nvidia-settings, however nothing worked until I rebooted my machine. I will not tell if the Nvidia driver above 340 would cause any issues, I haven't tried. [/COLOR]

That statement is confusing me. You know Nvidia 340.65 works. You know that a reboot is often needed. I suggest that you activate the open source video driver (Nouveau) and see if that fixes things. Reboot and shutdown and reboot to confirm all is working. And then continue with your experiments.

Regards.

---

### Post by richlion2 on 2015-02-13
I used these instructions:
[http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/](http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/)
I think this really is explained very nicely. I don't know if those instructions are relevant if someone loses the X-Window due to a crash or problems with the driver. 

When I installed Ubuntu and then Kubuntu it was using the generic Nouvau driver, because I could not get my external HDMI screen working. The instructions on that site did the trick, except for the system restart which is not mentioned.

Hope this helpls.
Bare in mind in terms of Ubunty I am a baby penguin here, so apart from instructions from the web I can't offer any complete solutions.

---

### Post by Lucas_Ricardo on 2015-02-13
[IMG]http://i.imgur.com/FfVWo8L.jpg[/IMG]

Hi [COLOR=#000000]v3.xx, when [/COLOR]I chose "failsafex" option at recovery mode but the screen became like this picture above, CTRL + ALT + F1 not working to enter text mode.

---

### Post by richlion2 on 2015-02-15
Can you try the hints from here?
[http://askubuntu.com/questions/172319/how-can-i-start-in-safe-mode](http://askubuntu.com/questions/172319/how-can-i-start-in-safe-mode)

Somehow you need to get to a mode where you can get a pure UNIX Terminal login, once you manage to do that, let us know.
The next step would be to login with your account (I can ssume you are the admin) , get the commands to start the network and then use commands to remove the new Nvidia driver and install the previous version.
This dodgy new driver must have gone into many distros, some untested.
Here's what Linus has to say about them:
[https://www.youtube.com/watch?v=IVpOyKCNZYw](https://www.youtube.com/watch?v=IVpOyKCNZYw)

---

### Post by Lucas_Ricardo on 2015-02-15
[SIZE=3]**grahammechanical **[/SIZE]

I installed the driver 346.35 via script **NVIDIA-Linux-x86_64-346.35.run** using **sudo ./script name** . After that, the problem occours and I removed using **sudo apt-get remove --purge nvidia*** , but in the first time that I installed a nvidia driver, I used **sudo apt-get install nvidia-340** and works fine the only problem was the tearing, because of this problem that I started to use newest drivers...

**About yours suggestions:**

1) At the desktop wallpaper, right click the wallpaper and if a menu  appears select change desktop background. That will open System Settings  and from there  we can get to Software and Updates>Additional  Drivers tab and change video drivers.

[B]I did that, but was possible to do right click after installing 340.76 driver, before that there wasn't no menu at right click. I changed the driver from Nvidia to Noveau, reboot notebook and nothing changed.

[IMG]http://i.imgur.com/0AAqatl.jpg[/IMG]

[IMG]http://i.imgur.com/G9fqIaA.jpg[/IMG]
[/B]
2) Use Recovery mode Resume. That may load to a working desktop using an  open source video driver called llvmpipe. From there we go to System  Settings>Software and Updates>Additional drivers tab.

**In Recovery Mode the screen was like this:**

[IMG]http://i.imgur.com/FfVWo8L.jpg[/IMG]

---

### Post by Lucas_Ricardo on 2015-02-15
After removing all nvidia driver again **sudo apt-get purge nvidia*** I enter to** GNOME Flashback (Metacity)** and tried to load Unity:

[IMG]http://i.imgur.com/XRrbal5.png[/IMG]

Same problem with opengl plugin, but if i try to check the box opengl at compiz-manager when I close it and open again the selection gone....

---

