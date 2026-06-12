---
title: "network manager applet..."
date: 2009-04-12
forum: Desktop Environments
---

### Post by zander1013 on 2009-04-12
hi,

i have somehow deleted the network manager applet from the application bar at the top of the screen.

it is not in the "add to panel" list for the panel.

how do i put the applet back in the panel please?


-zander

---

### Post by _Purple_ on 2009-04-13
Is Notification Area added to your panel? Try to add Notification Area from Add to Panel.

---

### Post by RedSingularity on 2009-04-13
Yeah it is usually under "notification area" on the panel.

---

### Post by tpost001 on 2009-04-13
I am having the same problem and posted it.  I cannot find a Notification Area Applet.  When I right-click the top panel, there is no option for Notification Area Applet.

---

### Post by tpost001 on 2009-04-13
Nevermind.  Thanks.  I found it.  Right-click on the top panel, Add to Panel, and then pick Notification Area.  Thanks a million.  

But...

Now I have 3 nm-applets.  How do I get rid of the 2 extra ones I don't need?  I cannot "remove from panel" on those.

---

### Post by zander1013 on 2009-04-13
thanks all it was the notification area.:popcorn:


@topost001: if you right click on the applet you want to remove it should give you a "remove from panel" option in the drop-down menu.


peace, love and free software!!!):P

-zander

---

### Post by jaschulz on 2009-04-13
I have a cousin of this problem.  I, too, accidentally deleted the Network Manager applet.  I restored it by going to System>Preferences>Sessions and checking the Network Manager item in that list.  Now, however, even though I have enabled auto log-in, when I boot up, the Network Manager puts up a dialog asking for my password.  How can I avoid this dialog?

thanks,

JAS

P.S.  Even though in System>Preferences>Bluetooth I have checked "Never display an icon", the system turns on my bluetooth as it boots and puts the icon in my panel.  How can I tell the system to leave bluetooth dormant?  thanks again

---

### Post by Jakey_TheSnake on 2009-04-13
> **jaschulz said:**
> I have a cousin of this problem.  I, too, accidentally deleted the Network Manager applet.  I restored it by going to System>Preferences>Sessions and checking the Network Manager item in that list.  Now, however, even though I have enabled auto log-in, when I boot up, the Network Manager puts up a dialog asking for my password.  How can I avoid this dialog?

thanks,

JAS

P.S.  Even though in System>Preferences>Bluetooth I have checked "Never display an icon", the system turns on my bluetooth as it boots and puts the icon in my panel.  How can I tell the system to leave bluetooth dormant?  thanks again

The network dialog is for wireless I presume? At one time I saw a "remember" option below it, but only once. Maybe they thought it was a good idea, then changed their minds? I don't think you can, anyway, at least without some tinkering in configuration files. 

System > Preferences > Sessions, just uncheck Bluetooth.


edit: you guys can back up exactly how your panel looks with:

```
gconftool-2 --dump /apps/panel > ~/paneldata.entries
```

Then after you accidentally delete stuff again, you can restore it to its previous state with:

```
gconftool-2 --load ~/paneldata.entries
``` 

Please note that "~/" is a shortcut to "/home/username/". You can change the filepath if you wish.

---

### Post by jaschulz on 2009-04-13
The thing is, before I stupidly deleted it (and then resored it) the system would boot, and the wireless would connect, without asking for any password.  Doesn't that mean I should be able to restore that behavior?

JAS

---

### Post by tpost001 on 2009-04-13
I would like to get back to my issue.  

zander1013 suggested I right click the extra nm-applet and click "remove from panel".  I have 4 computers running Ubuntu 8.04.2.  I can't do as you suggested on any of them.  Can you really do that?  I can remove just about anything you mention on the panel with your method, but nothing inside the "Notification Area" that you helped me restore has that option.  Is the best idea to remove it again and then reinstall it?  I think I will give that a try.

---

### Post by Jakey_TheSnake on 2009-04-13
> **jaschulz said:**
> The thing is, before I stupidly deleted it (and then resored it) the system would boot, and the wireless would connect, without asking for any password.  Doesn't that mean I should be able to restore that behavior?

JAS

Ah, well then you should. But, alas, I do not know how. It bugged me for a while too, but then I saw the plus side when friends started playing with my laptop.

---

### Post by benerivo on 2009-04-13
I would try using wicd rather than the default networkmanager applet, as it won't ask you for a password every time.

@ JakeTheSnake -- What did DDT originally mean? I heard it meant Deadly Damian Torture.

---

### Post by tpost001 on 2009-04-13
Solved:  My problems are over!  Thanks for everyone's help.  SO if anyone wants to know (this is for 8.04)...

If your network applet goes away on the upper panel, it is because the "Notification Area" applet got removed by accident.  The "Notification Area" can be removed by right clicking on the 2 columns of dots that look like a panel separator.  That's what I thought it was and I right-clicked and removed it from the panel.  That action also removes your network applet (nm-applet) and the update notification applet.  You won't see the familiar red arrow for security and/or other updates anymore, either.  

To get them back, right click on any blank area of the panel and select "Add to Panel...".  The "Add to Panel" window pops up.  Scroll down to "Notification Area - Area where notification icons appear" and select it and click +ADD.  If your network applet does not appear immediately, press Alt-F2 for the "Run Application" window and type in nm-applet.  It will now appear.  

The "Add to Panel" window also has a Network Monitor applet.  It is different than the nm-applet.  It does not have a selector for available wireless networks, but it does show your interface device and the packets sent and received.

---

### Post by fennypotter on 2011-10-22
> **tpost001 said:**
> Solved:  My problems are over!  Thanks for everyone's help.  SO if anyone wants to know (this is for 8.04)...

If your network applet goes away on the upper panel, it is because the "Notification Area" applet got removed by accident.  The "Notification Area" can be removed by right clicking on the 2 columns of dots that look like a panel separator.  That's what I thought it was and I right-clicked and removed it from the panel.  That action also removes your network applet (nm-applet) and the update notification applet.  You won't see the familiar red arrow for security and/or other updates anymore, either.  

To get them back, right click on any blank area of the panel and select "Add to Panel...".  The "Add to Panel" window pops up.  Scroll down to "Notification Area - Area where notification icons appear" and select it and click +ADD.  If your network applet does not appear immediately, press Alt-F2 for the "Run Application" window and type in nm-applet.  It will now appear.  

The "Add to Panel" window also has a Network Monitor applet.  It is different than the nm-applet.  It does not have a selector for available wireless networks, but it does show your interface device and the packets sent and received.

Thanks for the explanation, i've got the problem but solved by this.. :popcorn::):P:KS

---

