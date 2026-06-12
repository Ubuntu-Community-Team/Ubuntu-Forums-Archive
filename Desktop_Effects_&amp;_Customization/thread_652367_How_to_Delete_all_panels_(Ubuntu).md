---
title: "How to: Delete all panels (Ubuntu)"
date: 2007-12-28
forum: Desktop Effects &amp; Customization
---

### Post by LinuxIsInnovation on 2007-12-28
Hello all.

I am starting this thread because I thought this might help those who want a clean and empty desktop w/o panels.

My aim is to delete all the Gnome panels. 

First of all, you need to have a composite desktop. This is needed for the Avant Window Navigator which we can use as a replacement to the panels.

For Gnome desktops, we can right-click on a panel and click on "Delete Panel" to delete it. But this is not applicable for the last panel on the screen.

To remove the last panel, here are the steps:

1. Goto System -> Preferences -> Sessions
2. Click on Current Session tab. Find gnome-panel there and set it's style to 
"Trash" and click Apply button. DO NOT close the Sessions Window
3. Now open a terminal and type:
```
$killall gnome-panel
```
4. Now close the terminal window and go back to the sessions window. 
5. Click on the Session Options tab and **check **(tick) the "Automatically remember running applications when logging out" check-box. 
6. Click on the "Remember currently running applications" button.
7. Close the sessions window.

Done!! :)

You can reboot to test whether the panel comes up again or not.

Here is how my desktop looks now w/o panels:
[ATTACH]54505[/ATTACH]

If you have any other innovative suggestions, please share. :D

---

### Post by LinuxIsInnovation on 2007-12-28
In Avant Window Navigator (AWN), you will have all the required applets that you have for a panel.
Get AWN from here:
[http://awn.wetpaint.com/page/Download?t=anon](http://awn.wetpaint.com/page/Download?t=anon)

---

### Post by bill_greene on 2008-01-14
thanks for the excellent how to. ;)

---

### Post by MNICY on 2008-01-15
Very nice :D

---

### Post by LinuxIsInnovation on 2008-01-15
You are all welcome :)

---

### Post by tehsVen on 2008-03-06
Awesome instructions!  However, the only problem with this is that the Run Dialogue (Alt + F2) runs through gnome-panel.  Once you remove gnome-panel, you don't have access to the Run Dialogue anymore.  Anyone know of any way to fix this?  I'd like to have the Run Dialogue pop up with either Alt + F2, or whatever else I can configure it to.

Thanks!

---

### Post by Faud on 2008-03-06
Just use your terminal to start anything that alt+f2 would have started such as ```
firefox
``` or if you only want to remove the panels for that session just ```
 gnome-session-remove gnome-panel
```
also there really is not a need for AWN, just a way to get to your terminal. and to get your panel back just ```
gnome-panel
```

---

### Post by tehsVen on 2008-03-06
Thanks for the suggestion, but that really didn't solve my problem.  I don't want to have to run stuff through terminal all the time - I like the quickness of Alt + F2 (and there are no residual windows as well).  Plus, the Run Dialogue resolves names for you that sometimes don't show up in the terminal (like Calculator).  Therefore, the only options I am looking at again, is either running things through terminal, which I feel is messy and not as efficient at the Run Dialogue, or having an annoying gnome-panel being displayed somewhere.  So I guess my question is then, is it possible to access the Run Dialogue (specifically, not a terminal) without having gnome-panel running?

---

### Post by Faud on 2008-03-06
So, Im assuming you are not using something like AWN correct ? Which would be just drag and drop on the awn panel
```
gcalctool
``` is the command for the calc, not that, that is what you wanted. Im like almost trying to figure out how you would create a panel w/o creating a panel because that is what it seems to me that you want.

---

### Post by tehsVen on 2008-03-06
Actually, I am using AWN.  However, as far as I know, there aren't any applets or launchers that you can configure to run the Alt + F2 dialogue (or something comparable to it).  I'm hoping that I'm wrong here.  :)  I also am not sure what you mean when you say that you can simply drag and drop to the AWN bar?  I know that works for files and stuff, but not sure how it applies to this situation.

Edit:

Ok, I understand what you mean by creating a panel and dragging and dropping in AWN.  However, this isn't what I'm going for at all.  I just want to be able to run the Run Dialogue (Alt F2) without having gnome-panel running (since it creates a very annoying window that is not easily hide-able).

---

### Post by King_Critter on 2008-03-06
Regarding the Alt-F2 Run dialog -- in the repositories is a program called gRun, which is basically a stand-alone version of the Run dialog.

---

### Post by tehsVen on 2008-03-06
Awesome!  That is exactly what I was looking for!  Thanks for the help!

---

### Post by Saraphim on 2008-03-06
To replace the alt+F2 run bar you could also take a look at [GNOME Do]("http://do.davebsd.com/"), which, as we all know, is crazy delicious. If you make sure it starts with your session, you can change it's bindings from gconf-editor in apps->gnome-do, or alternatively, you could simply add the keybinds for anything in apps->metacity->keybinds and global_keybinds, if I'm not entirely mistaken. 

-- Sarah

---

### Post by sweetfishremix on 2008-03-06
All I'm missing is my Wifi thing. Is there a wiget or avant plug in for this?

---

### Post by SomeGuyDude on 2008-03-06
> **sweetfishremix said:**
> All I'm missing is my Wifi thing. Is there a wiget or avant plug in for this?

Put the "notification area" in AWN, and if it's still not showing up, run "nm-applet".

---

### Post by sweetfishremix on 2008-03-07
The Notification area in AWN dosent do anything, and the run np-applet just opens another wifi thing inside the panel, so thats useless

---

### Post by RiazM on 2008-04-09
Are you trying to use the notification area when you still have another notification area open in a panel? If so the AWN one will not work. Remove the panel notification area and restart awn and see if it works.

---

