---
title: "Application menu font color"
date: 2010-12-23
forum: Desktop Environments
---

### Post by JMBurton2001 on 2010-12-23
Hello,

I've just about got my desktop configured the way I want. My problem at this point is that the menu font colors in all my OpenOffice applications will not cooperate. See attached screenshot. All other menus are the same as the Firefox menu -> dark background, white text. All my OpenOffice menus are -> dark background, black text.

How do I change the menu font color to white in **_only_** OpenOffice without affecting all my other applications?

Thank you for your replies!



[COLOR=White].[/COLOR]

---

### Post by Frogs Hair on 2010-12-23
From OO menu , tools > options > colors > add. Sorry , misunderstood , I don't see any options to do this . The gnome color chooser may be worth a look.

---

### Post by JMBurton2001 on 2010-12-23
Thanks for the reply Frogs Hair! Much appreciated! I had looked in all the OO settings and couldn't find anything concerning the menu font colors. I installed Gnome color chooser and it doesn't have any settings (or at least that I can find) that specifically address menu font colors.

Is there a configuration file behind the scenes somewhere in OO (or elsewhere) that controls the menu font color?

---

### Post by Frogs Hair on 2010-12-23
OO uses your gtk theme , so you would have to edit the theme file its self. It is possible but I have not done it.

---

### Post by mcduck on 2010-12-24
> **Frogs Hair said:**
> OO uses your gtk theme , so you would have to edit the theme file its self. It is possible but I have not done it.

Might take a lot of tweaking to get to work, as OpenOffice actually doens't use the GTK theme, at least not correctly. It's not a GTK application, it just picks some stuff from the theme you use and then tries to draw something similar. Much like Firefox does, only with less success... :D

---

### Post by JMBurton2001 on 2010-12-24
Oh well... You win some, you lose some! At least the menu's are clear when selected... Thanks guys!

---

### Post by Francewhoa on 2012-02-19
**Solution**

[LIST=1]
[*]Edit the following file located in your home directory at
```
home/<your-username-here>/.profile
```
[*]At the bottom of that file, add the following new line
```
export SAL_USE_VCLPLUGIN=gen
```
[*]Logout or reboot Ubuntu. Enjoy :)
[/LIST]

**Notes**
[LIST]
[*]Works with Ubuntu 10.04 and OpenOffice 3.x
[*]This option will be maintained during an OpenOffice update or upgrade. Easy.
[*]If you do not see the “.profile” file it's because you must activate the show hidden files feature in your Ubuntu window browser. Under the “View” menu.
[*]The OpenOffice menu will be much easier to read. But their appearance will be without any fancy pants design. That is black text on light gray background menu.
[*]Source: [http://crunchbanglinux.org/forums/post/55327/#p55327](http://crunchbanglinux.org/forums/post/55327/#p55327)
[/LIST]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212989&stc=1&d=1329697670[/IMG]

---

### Post by overdrank on 2012-02-19
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

