---
title: "All my panels have gone away"
date: 2010-02-11
forum: Desktop Environments
---

### Post by perevera on 2010-02-11
I manipulated the two pannels, making them to automatically hide, then changing one of them to the upper side...

Suddenly it stopped working, I could not complete the change, and on the next restart no panel show up!

I guess I need to reset the configuration of gnome-panel or something, but I have no idea how to do so.

Please help!

---

### Post by saif_held on 2010-02-11
Try **Alt+F2** then type **gnome-panel**...hope this restores the panel(s)

---

### Post by howefield on 2010-02-11
If that doesn't work reset them to default by typing the following 3 commands into a terminal.

```
gconftool-2 &#8211;-shutdown
```
```
rm -rf ~/.gconf/apps/panel
```
```
pkill gnome-panel
```

---

### Post by perevera on 2010-02-11
Wonderful, howefield, this fixed the issue!

Thank you both.

---

### Post by redcrystalmoon on 2010-02-22
I have the same issue but I don't know how to open a terminal without a panel? there's no option for a terminal when I right click on the desktop.
Thanks
RCM
*Also, alt f2 does nothing for me...

---

### Post by gadolinio on 2010-02-22
> **redcrystalmoon said:**
> I have the same issue but I don't know how to open a terminal without a panel? there's no option for a terminal when I right click on the desktop.
Thanks
RCM
*Also, alt f2 does nothing for me...

ALT F2 should give you a little window where you can type an application's name to make it run. 
If that doesn't work and you have no panels, try this: double click your user's icon on the desktop. When the file browser opens, go to filesystem (list on the left), then from the folders you see on your right enter "usr", then "bin". You'll see a lot of files there. There's one called "gnome-panel"; double click it.

---

### Post by redcrystalmoon on 2010-02-22
Thank you! 
Alt F2 still did nothing for me, but going into the bin folder did the trick... let's hope it stay's there now!
Thanks again!

---

### Post by koleoptero on 2010-02-22
The alt+f2 run dialog in gnome is handled by the gnome-panel so when it's not running the run dialog doesn't appear.

---

### Post by gadolinio on 2010-02-22
> **koleoptero said:**
> The alt+f2 run dialog in gnome is handled by the gnome-panel so when it's not running the run dialog doesn't appear.

Didn't know that... :o
So it is the same as with Alt+F1, which opens the applications menu (though this one is more obviously panel-related).

---

### Post by gadolinio on 2010-02-22
> **redcrystalmoon said:**
> Thank you! 
Alt F2 still did nothing for me, but going into the bin folder did the trick... let's hope it stay's there now!
Thanks again!

You're welcome. Just in case this happens again, you can create a link to that file and keep it in your user's folder. So next time you just double click your folder in the desktop, and then the link to gnome-panel.

---

### Post by afrodeity on 2010-03-11
This was very useful, always bothered me on occassion, then recently totally went awol, now it fixed, thanks.

---

### Post by bgflounder on 2010-04-04
going through filesystem didn't work for me... searched and have no gnome-panel. is this something i need to add from the application add/remove? i'm confused why i can't find it... any ideas?

---

### Post by YnotStrebor on 2010-05-01
Many thanks Howefield,

After I upgraded from 9.10 to 10.04 the desktop panel menus disappeared. gnome-panel was running, but the desktop menu bar was not showing.

On one forum post running the update manager was suggested e.g.
sudo apt-get update
sudo apt-get upgrade
sudo shudown *exampletime10:20*

After running the 3 lines of code Howefield suggested, everything returned to normal, no need to reboot. Many thanks.

---

### Post by YnotStrebor on 2010-05-01
I was too hasty - the problem of the missing panels reoccurs after reboot. Something is broken in the upgrade from 9.10 to 10.04. As a temporary workaround Howefield's method works.

---

### Post by jacksonpollack on 2010-05-02
I upgraded from Karmic to Lucid and while the panel was just fine for awhile (save the problems with getting my volume applet back), today it did not appear when I booted up. Alt+F2 doesn't work (linked to the panel I assume?), and if I manage to open a terminal and type "gnome-panel" I get: 

```
gnome-panel: error while loading shared libraries: libgnome-desktop-2.so.11: cannot open shared object file: No such file or directory
```

The only thing I can do is open nautilus and go to /usr/bin and run gnome-panel. Howefield's technique did nothing except reset what my panel would look like. It didn't automatically come back up, nor will it appear each time I reboot/login. I've even set it to run in "Startup Applications", but to no avail.

Any help would be appreciated, thanks!

---

### Post by mathias j sagartz on 2010-05-02
Not sure if this is exactly the same but here is my tale of woe

Working with an old desktop that had been running 8.04

Update failed so I installed from a LiveCD. Dual boot with XP. System 
runs great off of the CD. After installation of 10.04 and a restart, 
the system worked well. Tried lots of stuff off the Gnome menus.

Restarted and booted XP. That worked too.

On my next restart I selected Ubuntu from the grub menu and the system 
gave me the sign in requester. I signed in but the desktop never 
appeared. All I got was the background and a mouse pointer.

Right clicking the mouse brings up a 7 item menu that includes items for
creating a folder, creating a document, ....., choose a new background.
The menu works. If I click create a document an icon for a new file
appears on the screen. Clicking on the icon brings up a window running
gedit. Choosing the new background item brings up a window with candidate
new backgrounds. I have no idea how to get the gnome desktop back. The
sign in screen has a bar at the bottom that shows Gnome is the default
session setting.

Booting into XP continues to work.

I've tried changing the GRUB_CMDLINE_LINUX_DEFAULT= line in the 
/etc/default/grub to add nomodeset. That didn't help.

Ctrl-alt-F1 will get me a terminal and I can use ps to look for process
information.  Unfortunately I'm not experienced and don't know what
should be running if gnome is working properly.
  ```
ps -x | grep gnome
```
shows a number of items including /user/bin/gnome-session with an SSl
status, whatever that means.

---

### Post by mathias j sagartz on 2010-05-03
Apparently my problem is different. 

Both Alt-F1 and Alt-F2 work for me. I used Alt-F2 to run "gnome-panel" but
it had no effect.  

I can run the menu choices brought up by Alt-F1 and they work as expected.
If I try to shrink the window an app. is runing in, it travels down to 
where the panel should be and disappears.

---

### Post by jacksonpollack on 2010-05-03
My problem might have had to do with me manually compiling the panel back in Karmic to get rid of the pesky black arrow on the main menu icon. I recompiled it and it seems to be working fine now. Doubt that this reflects a problem most people have...

---

### Post by YnotStrebor on 2010-05-04
Hi Jacksonpollack,

How did you recompile the panel. Please could you post the commands?

Maybe this is what I need to do - ever since the Lucid upgrade from Karmic my panel bars have gone missing.

Cheers & thanks.

---

### Post by mathias j sagartz on 2010-05-04
Howefield's three lines of code have worked for me. I just put those commands (see Howefield's post above) into a file, which I called panels, 
and saved it to my home directory.  Be sure it has an executable permission.

When the blank background comes up I simply press alt-F2, type in
/home/myusername/panels and press the run button.  That brings up
my panels.

The panels vanished after the first reboot and I didn't recompile anything.

---

### Post by ioliver on 2010-05-05
I also have a panel issue.

I upgraded from 9.10 to 10.04 and on restart I have 3/4 length blank panels top and buttom. I fiddled for a while and found the right clicking, choosing properties and then unchecking "Expand" got me a working panel in the middle of the screen. Rechecking expand got me a working full width panel.

However, on logging out/in, I'm back to 3/4 width panels on the LHS of the top and bottom both with no menus or icons.

Ideas?

Ian

---

### Post by MLXXXp on 2010-05-08
I have exactly the same "partial length blank panels after boot" problem that **ioliver **just reported. For me both panels are only about 1/4 width on the left side. My screen size is 1920 x 1080.

This is a fresh install of 10.04. I get the same problem with a live CD boot. I was previously running 8.10 without any panel problems.

---

### Post by MLXXXp on 2010-05-12
At least in my case, I've found a way to fix the "blank panel" problem.

I went into **System ->  Preferences -> Appearance** and in the **Visual Effects** tab tried to switch from **None** to **Normal**. This selection didn't "take" (my graphics card doesn't support it?) and the widow stayed greyed out for quite a while, but since doing this my panels have come up normally after a log out or re-boot.

I also tried this with a live boot of the 10.04 CD. Before the fix the panels would be corrupted after logging out and back in. Afterwards, the panels were fine.

---

