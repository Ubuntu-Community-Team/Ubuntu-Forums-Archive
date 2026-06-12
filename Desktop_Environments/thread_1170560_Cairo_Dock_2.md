---
title: "Cairo Dock 2"
date: 2009-05-26
forum: Desktop Environments
---

### Post by Kysweetheart on 2009-05-26
I have just installed Cairo Dock 2. I can't get it to open the dock. When I click on Cairo Dock under System tools it pops up the configurations manager. When I put my preferences in and try to close out of the manager it will not shut down and keeps popping up and the dock still does not come up. I have to force quit the manager to make it close. Any help would be greatly appreciated. I am a newbie when it comes to Ubuntu. Thanks in advance.

Misty

---

### Post by Idefix82 on 2009-05-26
I have this same behaviour whenever I am not connected to the internet. I suspect that if there are any applets on the dock that need an internet connection (like weather forecast) the dock will not come up if it can't get the data it needs. But I am sure that fabounet will soon join this thread and lift all our doubts :)

---

### Post by j0hn00 on 2009-05-26
this has been happening to me as well. i just switched to awn instead.

---

### Post by xXeHPiCXx on 2009-05-26
Have you tried xkill? alt+f2 and type xkill and there should be an x click on the window your having trouble closing.You can also go in system monitor and look in the processes for cairo dock and close it.hope that helps.

---

### Post by Kysweetheart on 2009-05-26
I have trimmed down the problems with Cairo Dock. I reverted back and installed Cairo Dock 1.6 and I am trying to upgrade instead of doing a fresh install. I keep getting an error message when I try to upgrade. The error message is as follows:

E: /var/cache/apt/archives/cairo-dock_2.0.2_all.deb: trying to overwrite `/usr/share/cairo-dock/icon-mouse.png', which is also in package cairo-dock-data.

Thanks for the previous respond. Any help with this would be appreciated. 

Thanks.

---

### Post by Viva on 2009-05-27
Open it using the terminal to find out the error.

---

### Post by fabounet on 2009-05-27
by deactivating the applets one by one, can you find the one that makes the dock crash if there is no connection ?
it can be : 
weather trying to get the forecat
or any applet trying to download a theme that is not on your local hard drive.

Edit : also you can try v2.0.3, available on Berlios, and on the repository soon.

---

### Post by Kysweetheart on 2009-05-27
Thanks everyone for your help. Cairo Dock is now up and running. Thanks again.;)

---

### Post by fabounet on 2009-05-28
so, what did you do exactly ?
I'm interested by finding the cause of it, and I couldn't reproduce it at home.
thanks.

---

### Post by Idefix82 on 2009-05-28
Fabounet, you mean you couldn't reproduce the problem? If you put the cairo-dock into your start-up applications (I am starting it with cairo-dock -o) and if your cairo-dock contains applets that need internet access (like weather applet) and you don't have an internet connection at the time of logging in then instead of the dock the configuration manager comes up. If you close the manager then it reopens again and the dock doesn't appear, untl you have established an internet connection.

At least I think that this is because of the weather applet.

By the way, thank you very much for this fabulous software!

---

### Post by fabounet on 2009-05-29
actually I don't have it in my startup programs :D
I've tried by starting it without internet connection and with the weather applet, but no crash occured.

if someone has this bug and is using the SVN version, I'd appreciate a *ddd* screenshot ^_^

---

### Post by Keith_Beef on 2009-08-06
> **Idefix82 said:**
> ...I am starting it with cairo-dock -o...

Each time I boot, Gnome begins to start and then Cairo shows a message to ask me if I want to start with OpenGL... it informs me that I can add the -o switch to the startup command, but I can't find where Cairo is being started!

I've read other threads, and can't find any of the startup locations that they mention... I don't find the same options in my menus that are sometimes mentioned...

Please! How does Cairo get launched when Gnome starts up?

K.

---

### Post by andrea000 on 2009-08-06
> **Keith_Beef said:**
> Each time I boot, Gnome begins to start and then Cairo shows a message to ask me if I want to start with OpenGL... it informs me that I can add the -o switch to the startup command, but I can't find where Cairo is being started!

I've read other threads, and can't find any of the startup locations that they mention... I don't find the same options in my menus that are sometimes mentioned...

Please! How does Cairo get launched when Gnome starts up?

K.

to auto start cairo dock goto system->preferences->startup applications click the add 
button on the name = cairodock command to launch cairo dock-c.I'm not sure on the with
opengl i never run opengl i have had some problems with that

---

### Post by Favux on 2009-08-07
Hi Keith_Beef and andrea000,

In Startup Applications (or Sessions in Intrepid or earlier)

Name:  Cairo Dock (or Cairo Dock 2)

Command:  cairo-dock -o  (for openGL) or

          cairo-dock -c  (for Cairo)

---

### Post by theZoid on 2009-08-08
> **Keith_Beef said:**
> Each time I boot, Gnome begins to start and then Cairo shows a message to ask me if I want to start with OpenGL... it informs me that I can add the -o switch to the startup command, but I can't find where Cairo is being started!

I've read other threads, and can't find any of the startup locations that they mention... I don't find the same options in my menus that are sometimes mentioned...

Please! How does Cairo get launched when Gnome starts up?

K.

I have the same problem locating how it's starting in Xubuntu...it's not in sessions>autostart applications from the control panel......anyone?

---

### Post by abdusamed on 2009-08-17
hey-- i had the same problem. The solution is EXTREMELY SIMPLEEEEE

right click -> cairo-dock -> start cairo dock on startup!!!! [its one of the option]

---

