---
title: "Kubuntu Install Dependency Prob"
date: 2005-07-07
forum: Desktop Environments
---

### Post by champion on 2005-07-07
Now that I've **finally **got Ubuntu running on this old box, I want to install Kubuntu. So I run Synaptic, browse to [color=DarkGreen][color=Black]**kubuntu-desktop**[/color][color=Black], and try to mark it for installation. Synaptic replies,

[/color][/color] ```
 kubuntu-desktop:
 Depends: konversation but it is not going to be installed
``` [color=DarkGreen][color=Black]
I browse to [color=DarkGreen]**[color=Black]konversation[/color]**[color=Black], mark it for install, and Synaptic replies,

[/color][/color][/color][/color] ```
konversation:
  Depends: kdelibs4 (>=4:3.4.1) but 4:3.4.0-0ubuntu3.2 is to be installed
``` [color=DarkGreen][color=Black][color=DarkGreen][color=Black] The **kdelibs4:3.4.1** doesn't seem to be listed in Synaptic, only **kdelibs4:3.4.0-0ubuntu3.2**.

I am now stuck. ](*,)  Any help would be much appreciated.


[/color][/color][/color][/color]

---

### Post by SGC on 2005-07-07
Read this post: [http://www.ubuntuforums.org/showpost.php?p=225750&postcount=2](http://www.ubuntuforums.org/showpost.php?p=225750&postcount=2)

---

### Post by champion on 2005-07-08
[font=Trebuchet MS][size=3]I made the requisite addition to the repositories source list, and now Synaptic will proceed with the kubuntu-desktop install once the required packages are downloaded. **Yay! **\\:D/ Thanks![/size][/font]

---

### Post by Rory on 2005-07-08
Yes, but once Kubuntu-desktop is installed, will Synaptic open back up?  Mine no longer will, unless I go in to terminal and type: sude synaptic.  When I try to open from the menu/desktop, I get an hourglass and then it doesn't open.  Something happened when I went from Ubuntu w/ kde to Kubuntu.  

Any suggetions?

Rory

---

### Post by SGC on 2005-07-08
[QUOTE=Rory]Yes, but once Kubuntu-desktop is installed, will Synaptic open back up?  Mine no longer will, unless I go in to terminal and type: sude synaptic.  When I try to open from the menu/desktop, I get an hourglass and then it doesn't open.  Something happened when I went from Ubuntu w/ kde to Kubuntu.  

Any suggetions?

Rory[/QUOTE]
 My synaptic works perfectly, try this:
Right click on kmenu and choose "Menu editor", then go to "system" and choose "Package manager(synaptic package manager)"

In the right panel change the command from **synaptic** to **kdesu synaptic**

---

### Post by Rory on 2005-07-08
[QUOTE=SGC]My synaptic works perfectly, try this:
Right click on kmenu and choose "Menu editor", then go to "system" and choose "Package manager(synaptic package manager)"

In the right panel change the command from **synaptic** to **kdesu synaptic**[/QUOTE]

Well, that did the trick.  Thank you!

But, it was an interesting trip...

Before I read your response, I had shut down Ubuntu and opened it back up.  Synaptic now worked.  I saw your post and checked the command.  It was still: synaptic.

I then noticed I need to upgrade four packages: one was konversation and the other three were acrobat related.  Did the update and synaptic no longer worked.  What is the deal with Konversation???  

It was then that I tried your command and synaptic is back up.

Weird.

Thanks very much!

Rory

---

