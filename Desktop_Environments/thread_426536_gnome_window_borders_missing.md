---
title: "gnome window borders missing"
date: 2007-04-28
forum: Desktop Environments
---

### Post by ka0wbx on 2007-04-28
just recently when I startup a gnome session the applications have no window borders and control points.
kde loads & runs ok  just the gnome sessions. did something get deleted or changed. 
I have tried to reinstall the gnome packages but that did not help.

any ideas.

thanks

---

### Post by llamakc on 2007-04-28
Were you experimenting with "Desktop Effects"?

type "ALT-F2" and in the run dialog box enter "metacity --replace"

---

### Post by Sunflower1970 on 2007-04-28
I just spent the day trying to figure this out. I had the desktop effects on and then turned them off. All borders went away. Finally typed metacity in a terminal and everything came back, but when I rebooted, they went away again. I finally added Metacity to the startup menu and everything has been find (crosses fingers)

This also happened in Xubuntu after I had turned off Beryl. I never did try to get them back...(I reinstalled Ubuntu-desktop thinking it was something I had screwed up with the Xubuntu installation...)

---

### Post by Tom B on 2007-04-29
I have a similar problem. When I upgraded to Feisty, the first time I booted there were no window borders. When I opened the "Desktop Effects" window and clicked on "Enable Desktop Effects" the borders appeared, then it loaded for a little bit and a message popped up that says that the effects couldn't be enabled. The windows were normal for the rest of the session. Then I rebooted, and they were gone again. This time I typed metacity in a terminal like you did, and they came back, but went away as soon as I closed the terminal. I tried running metacity on start up too but it didn't work- none of the start up programs run until I click the "Enable Desktop Effects" button. After I do that, it works, but it's annoying to have to click on that every time I start the computer. Any ideas?

---

### Post by kaede on 2007-04-29
sighhh, this desktop effect really making a problem with my ubuntu. anyone know what is the default session program for gnome? recently i just remove all of the session. since all my window seems messed up. quite similar with the one happen here. :D

---

### Post by proyexeneta on 2007-06-10
Hi people... There should be a bug in GNOME... Don't tell Bill about it. 
The Solution is "metacity --replace"
And it happened after I set the automatic session ON. So I turned it off and everything is all right now (Well... not everything)

---

### Post by mister_p_1998 on 2007-06-11
> **Sunflower1970 said:**
> I just spent the day trying to figure this out. I had the desktop effects on and then turned them off. All borders went away. Finally typed metacity in a terminal and everything came back, but when I rebooted, they went away again. I finally added Metacity to the startup menu and everything has been find (crosses fingers)

This also happened in Xubuntu after I had turned off Beryl. I never did try to get them back...(I reinstalled Ubuntu-desktop thinking it was something I had screwed up with the Xubuntu installation...)

look here:

[http://ubuntuforums.org/showthread.php?t=446763](http://ubuntuforums.org/showthread.php?t=446763)

---

### Post by itsbradman on 2007-08-24
much easier if you just add metacity --replace to the startup menu under preferences>sessions!

---

### Post by Stonesphere on 2007-09-25
Holy crap.  I installed Compiz like normal, typed the Compiz --replace cmd, lost windows borders.  I wasn't really wanting to turn on compiz, I have used the Eyecandy, taken my screen shots for bragging rights, and now I am over it.  So, after uninstalling everything, when I logged into Gnome I was still missing windows borders.  I was ready to re-install, even ready to switch to KDE, then I found this post and felt really stupid.  I had tried to re-install Gnome, was even willing to just keep logging into Gnome-Save.  BUT, all I needed was to run  Metacity --replace. 

VIVA UBUNTU, VIVA UBUNTU FORUMS  :guitar:

---

### Post by fawkes on 2007-11-11
My window borders disappeared while simply changing themes one day. I did the "metacity --replace" noted above and they returned. However, if I try switching to normal or enhanced effects, they disappear. If I switch to normal or enhanced and *then* do "metacity --replace" it switches back to no effects and the borders return. No effects it is!

---

### Post by f0ku5 on 2007-12-26
This helped me:

[http://ubuntu-utah.ubuntuforums.org/showthread.php?p=3962575#post3962575](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=3962575#post3962575)

---

### Post by bharadwaj on 2007-12-26
i don think there is any relation between the Desktop effects and the window border. May be it is emrald behinde the mess

---

