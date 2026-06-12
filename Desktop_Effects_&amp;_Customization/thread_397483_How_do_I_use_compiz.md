---
title: "How do I use compiz?"
date: 2007-03-30
forum: Desktop Effects &amp; Customization
---

### Post by sneffers on 2007-03-30
I upgraded to ubuntu edgy and saw that it said it was installing comipz. How do I use it? I typed in compiz-manager in terminal, but all it did was make my panels and window borders disapear. I also have no sound and my panels, when they have a background image, are all fuzzy and black and pink and green and blue behind the appletts and stuff.

---

### Post by floke on 2007-03-30
Its been a while since I used Compiz - but I seem to remember that you have to edit you xorg.conf file. Have you checked out their website for installation details?

If you can run Compiz you should be able to run Beryl, which many people (myself included) believe to be the superior version for bling value.

You can check it out here:

[http://www.beryl-project.org/](http://www.beryl-project.org/)

---

### Post by sneffers on 2007-03-31
I haven't checked their website. I would like to use beryl, but I'm afraid it's gonna make my computer crash. I thought compiz was more stable. I don't care as much about compiz and beryl as much as I do about my panels getting all messed up.

---

### Post by FuturePilot on 2007-03-31
Are you sure you upgraded to Edgy? Only Feisty comes with Compiz. You can do it the graphical way by going System>Preferences>Desktop Effects or you can do it through the terminal which might be a good idea to see if you have any errors. Just do```
compiz --replace
``` If you would like a configuration manager for Compiz check my sig.
Compiz is a little more light weight than Beryl but now Beryl has reached stability so it's pretty safe to use now.

---

### Post by sneffers on 2007-03-31
What's your sig? I don't know what sig is? And I don't have system>preferences>Desktop Effects. and I can hardly use my laptop (which is the one that I am talking about) because everytime the screensaver goes on I can't get back to my desktop.

---

### Post by airtonix on 2007-03-31
a sig is "newSpeak" for signature.

winston...where are you? i want my speakWrite back NOW!

---

### Post by sneffers on 2007-03-31
Oh, I get it now... BUT I STILL NEED HELP!!!! MY PANELS are messed up and I can't use compiz and nothing worked than anybody told me to do! also my screensaver won't turn off a blank screen! PLEASE!!!! HELP!!!!!!

---

### Post by FuturePilot on 2007-03-31
Ok try doing this

```
sudo nvidia-xconfig --add-argb-glx-visuals
```
If that doesn't work then do this
```
gksudo gedit /etc/X11/xorg.conf
```
Then go to the section titled "screen" and add this line in that section
```
Option "AddARGBGLXVisuals" "true"
```
Save the file then log out and press <Ctrl><Alt><Backspace> to restart X server. Log back in then try the Compiz again.

---

### Post by sneffers on 2007-04-02
Ok, I'll try that. Thanks for all your help so far.

---

### Post by sneffers on 2007-04-02
Everytime I restart xserver my comp crashes. And what are those codes for. I mean I'm not even running compiz now.

---

### Post by sneffers on 2007-04-02
I never logged out and restarted the xserver but I deid both of those things and on the firs one it said that that command was not found, and I did all the stuff on the nest one and it still didn't work. So I just turned the screensaver off.

---

### Post by sneffers on 2007-04-02
Oh yeah, I still NEED HELP WITH MY PANELS! I don't know how to get a screenshot on there though.

---

### Post by FuturePilot on 2007-04-02
Ok, what graphics card do you have? And what driver are you using? The open source or the proprietary one? In a terminal do this ```
glxinfo | grep OpenGL
``` then post the output. That will answer those questions.
To take a screenshot just use your Print Scr button on the keyboard, then you can attach it to one of your posts.

---

### Post by sneffers on 2007-04-02
This is the output of the command:

  OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
OpenGL extensions:


But I am working on installing the newest Nvidia drivers for using beryl, so it might change.

---

### Post by FuturePilot on 2007-04-02
Ah, that seems to be the problem. You need the proprietary Nvidia driver to get Compiz working correctly. Once you get those installed, it should work then.

---

### Post by sneffers on 2007-04-03
I don't know how to get the newest Nvidia drivers though. I tried but it didn't work.[ATTACH]28894[/ATTACH]
  This is the panel. Look at the top. That's what it looks like.

---

### Post by FuturePilot on 2007-04-03
So what driver are you using then? Is it the nvidia-glx from the repos? That one should  still be able to do what you want it to. Also make sure that the default depth in the xorg.conf file under the screen section is 24 and not 16. If it is 16 change it to 24 save the file log out and restart X.

---

### Post by sneffers on 2007-04-03
Um, I didn't understand that. I don't know how to change the xorg.conf file and Don't know what Nvidia driver it is 'cause I used envy but it messed up my x server and now it won't start up. It says to restart the x server when it is configured correctly.

---

### Post by FuturePilot on 2007-04-03
Ok, you might want to try this. Write this down or print it or something since you will only be at a command line. After X server fails to load run Envy again and select the uninstall option then try running this command
```
sudo dpkg-reconfigure xserver-xorg
``` reboot and if X fails to start again make sure you are using the nv driver for now by doing this```
sudo nano -w /etc/X11/xorg.conf
```
Go to the device section and make sure the line that says driver says "nv" and not "nvidia" <Crtl>X to exit. Then Y to save, then hit Enter. Reboot and see if Xserver starts. It should this time. Then if it does start, after you log in open a terminal and do this
```
sudo apt-get install nvidia-glx
```
After it installs you need to change back to the nvidia driver by doing```
gksudo gedit /etc/X11/xorg.conf
```
Change "nv" to "nvidia" in the device section and a little farther down under the screen section change the default depth to 24 if it isn't already. Also add this under the screen section ```
Option "AddARGBGLXVisuals" "true"
``` Save then log out and restart X. Hopefully that works.

---

### Post by sneffers on 2007-04-04
I ran envy, but I had to add a -t parameter and that worked. But I chose the option "clean up all Nvidia driver installations". Is that the one you wanted me to do?

---

### Post by FuturePilot on 2007-04-04
I was saying to remove the latest nvidia driver and use the one from the repos but if you still want the latest nvidia drivers then reinstall them with Envy and let Envy configure xorg for you. But make sure that you still add ```
Option "AddARGBGLXVisuals" "true"
``` by doing this```
sudo nvidia-xconfig --add-argb-glx-visuals
```

---

### Post by sneffers on 2007-04-04
I ran the other commands on your other post but it didn't do anything. And when I opened the xorg.conf file, nothing was there, all it was was a blank screen and said new document on the bottom. I reconfigured the xserver using the dpkg-reconfigure xserver--xorg, but I still didn't have anything. I'll try those other commands, though.

---

