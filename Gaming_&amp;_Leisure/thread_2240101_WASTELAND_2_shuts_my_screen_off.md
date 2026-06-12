---
title: "WASTELAND 2 shuts my screen off"
date: 2014-08-17
forum: Gaming &amp; Leisure
---

### Post by kushwin on 2014-08-17
I had before on windows but, this has never happen to me 
until i had ubuntu installed then my screen couldnt find my hdmi 
after a couple of minutes of playing.
Is it ubuntu or could it be steam thats the problem?

---

### Post by bizhat on 2014-08-18
Which graphics card you using ?

Gaming on ubuntu is not perfect as Graphics card drivers are not optimized like in Windows.

---

### Post by oldrocker99 on 2014-08-18
Please post the output of:
```
lspci | grep VGA
```

As a Kickstarter supporter, I'm still waiting for the game to show up in my Steam library. {EDIT] I was going to say that I hadn't contributed a high enough amount to qualify for the beta, but, since yesterday, I did gain beta access and it's downloading now.\\:D/

---

### Post by kushwin on 2014-08-19
radeon hd 6450

---

### Post by kushwin on 2014-08-19
> **oldrocker99 said:**
> Please post the output of:
```
lspci | grep VGA
```

As a Kickstarter supporter, I'm still waiting for the game to show up in my Steam library. {EDIT] I was going to say that I hadn't contributed a high enough amount to qualify for the beta, but, since yesterday, I did gain beta access and it's downloading now.\\:D/


it just extended my game time from 2 to 10 minutes haha

---

### Post by bizhat on 2014-08-20
> **kushwin said:**
> it just extended my game time from 2 to 10 minutes haha

Then, try this

```

glxinfo | grep "OpenGL"

```

and post the result. This will show which driver you are using.

Try switching driver (open source/catalyst) and see if it improve the game performance.

---

### Post by kushwin on 2014-08-20
ewin@ewinscomp:~$ glxinfo | grep "OpenGL"
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD CAICOS
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.1.3
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 10.1.3
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
ewin@ewinscomp:~$

---

### Post by kushwin on 2014-08-20
> **oldrocker99 said:**
> Please post the output of:
```
lspci | grep VGA
```

As a Kickstarter supporter, I'm still waiting for the game to show up in my Steam library. {EDIT] I was going to say that I hadn't contributed a high enough amount to qualify for the beta, but, since yesterday, I did gain beta access and it's downloading now.\\:D/



ewin@ewinscomp:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
ewin@ewinscomp:~$

---

### Post by bizhat on 2014-08-21
Have you tried installing catalyst ? try it and see if it fix the problem. You can download it from

[http://support.amd.com/en-us/download](http://support.amd.com/en-us/download)

Try "Latest Linux beta driver"

---

### Post by oldrocker99 on 2014-08-21
Some ATI users, and some games, work better with the open-source radeon driver, and some work better with the ATI fglrx driver. You have to see which one works better for you and your card.

---

### Post by kushwin on 2014-08-22
> **bizhat said:**
> Have you tried installing catalyst ? try it and see if it fix the problem. You can download it from

[http://support.amd.com/en-us/download](http://support.amd.com/en-us/download)

Try "Latest Linux beta driver"

i tried latest beta driver but it said the script had errors in it
and it could corrupt the file 
im going to try the other one

---

### Post by bizhat on 2014-08-22
Where you get the script have errors in it ? I installed beta 2 times, never had any such problem. May be corrupt download or the way you installing it.

---

### Post by oldrocker99 on 2014-08-22
It is a **very good idea** to install video drivers when the display manager (which is, among other things, the screen you log in to) is **not** running:

```
sudo apt-get install dkms
```

The **D**ynamic **K**ernel **M**odule **S**upport program makes kernel support of the driver you're installing nice and tidy, and, as a bonus, will link the driver to a new kernel you might install yourself, or in an upgrade, so you don't have to reinstall the driver if you get an upgrade.

Now, note the output of:
```
more /etc/X11/default-display-manager
```

That's your display manager, which I'm calling *dm. Use the actual name in the code below.

Then hit **CTRL-ALT-F1**.

This will open a console on a separate screen. You'll be asked for your username and password and it'll take a few seconds to give you a command prompt. Then:
```
sudo service *dm stop
```
This will return a message that a service [name] stopped. Now, remember the path to your video driver, which I'll call "path/driver" in the code below:
```
sudo sh path/driver
```

This ought to get the driver installed. If you continue to get an error, try redownloading the driver.

If the driver installed okay, or even if it didn't, you need to exit by:
```
sudo service *dm start
```

This will return you to a login screen. Or, you can play it smart and reboot right from the command prompt:
```
sudo shutdown -r now
```


**If** everything went well, the driver should be installed. I will add the caveat that I haven't used anything from ATI in years; I was using nVidia before I abandoned Windows, and I'm glad in retrospect I did. I tried to keep things generic.

---

### Post by bizhat on 2014-08-23
AMD Catalyst need GUI to install ? It even ask you for installing some language pack before you can proceed, if not you get a GUI with out no text for GUI elements.

---

### Post by oldrocker99 on 2014-08-23
OK, the nVidia drivers put up a DOS-looking screen when the display manager is stopped, and that's what I was talking about. Again, I have little familiarity with ATI's drivers, and I didn't know that they had a graphical interface. I still think that installing with the display manager off is the best way to go.

---

### Post by kushwin on 2014-08-24
> **oldrocker99 said:**
> It is a **very good idea** to install video drivers when the display manager (which is, among other things, the screen you log in to) is **not** running:

```
sudo apt-get install dkms
```

The **D**ynamic **K**ernel **M**odule **S**upport program makes kernel support of the driver you're installing nice and tidy, and, as a bonus, will link the driver to a new kernel you might install yourself, or in an upgrade, so you don't have to reinstall the driver if you get an upgrade.

Now, note the output of:
```
more /etc/X11/default-display-manager
```

That's your display manager, which I'm calling *dm. Use the actual name in the code below.

Then hit **CTRL-ALT-F1**.

This will open a console on a separate screen. You'll be asked for your username and password and it'll take a few seconds to give you a command prompt. Then:
```
sudo service *dm stop
```
This will return a message that a service [name] stopped. Now, remember the path to your video driver, which I'll call "path/driver" in the code below:
```
sudo sh path/driver
```

This ought to get the driver installed. If you continue to get an error, try redownloading the driver.

If the driver installed okay, or even if it didn't, you need to exit by:
```
sudo service *dm start
```

This will return you to a login screen. Or, you can play it smart and reboot right from the command prompt:
```
sudo shutdown -r now
```


**If** everything went well, the driver should be installed. I will add the caveat that I haven't used anything from ATI in years; I was using nVidia before I abandoned Windows, and I'm glad in retrospect I did. I tried to keep things generic.

im sorry im pretty new to ubuntu or trying to dig deep in computers in general 
but what do you mean by the path to my video driver  
is this it 
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
(thanks for bearing with me guys)

---

### Post by oldrocker99 on 2014-08-25
By "path to your video driver," I simply meant wherever you saved it when you downloaded it. A lot of people download to their Desktop folder, and, since when you do the steps I outlines, your current directory is your /home folder, just, for example:
```
cd Desktop
```
and then you can run the installation command on the driver you downloaded.

---

### Post by oldrocker99 on 2014-08-25
By "path to your video driver," I simply meant wherever you saved it when you downloaded it. A lot of people download to their Desktop folder, and, since when you do the steps I outlined, your current directory is your /home folder, just, for example:
```
cd Desktop
```
and then you can run the installation command on the driver you downloaded.

---

### Post by Sara_simpleNewz on 2014-09-09
kushwin, did any of this work for you? i have a similar problem and wanted to check with you first before trying to follow the instructions (i've tried many things from some great [sites]("http://simplenewz.com/2014-08-05/Mainstream/feed/1898") and tbh i'm getting a migraine just thinking about trying something else lol)

---

