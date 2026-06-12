---
title: "xfce right scrollbars driving me nuts"
date: 2011-10-13
forum: Desktop Environments
---

### Post by marinara on 2011-10-13
On xubuntu(natty narwal) i maximize the window, then i click in the scrollbar area, at the right edge of screen.

some apps like mousepad, gnome commander work fine.

other apps like firefox, gedit, ignore the click. (on those rightmost pixels)


TL;DR:
I'm clicking on the rightmost screen pixel, clicking on what looks like a scrollbar, but some maximized apps seem to ignore the click.

anyone?  at this point i'll accept sympathy.
I have a similar problem with the applications menu button (xfce button) on the panel1 panel.

---

### Post by alexcabal on 2011-10-17
This has been driving me crazy too since I switched to XFCE from Unity/Gnome Shell madness.  Does anyone have a solution?

---

### Post by iamnotthemessiah on 2011-10-17
thank you very much, i didnt even notice until i read this :P

---

### Post by sffvba[e0rt on 2011-11-08
Big BUMP for this thread as I am having the same issue (recent switch to XFCE, like 6 hours ago)...

Anybody have any ideas?


404

---

### Post by Toz on 2011-11-08
Just having a look at this. If I'm understand this correctly.... on my system, the right-most x number of pixels are actually part of the frame of the window and not the scrollbar (x being determined by the theme in use). You have to come in a few pixels to actually get the scrollbar. Unfortunately, I don't have mousepad or gnome commander installed to compare - and all other apps seem to behave in the same manner.

In the event that its a screen positional thing, also have a look at the Workspaces module in the Settings Manager. There you can play around with screen margins.

---

### Post by sffvba[e0rt on 2011-11-10
> **Toz said:**
> Just having a look at this. If I'm understand this correctly.... on my system, the right-most x number of pixels are actually part of the frame of the window and not the scrollbar (x being determined by the theme in use). You have to come in a few pixels to actually get the scrollbar. Unfortunately, I don't have mousepad or gnome commander installed to compare - and all other apps seem to behave in the same manner.

**In the event that its a screen positional thing, also have a look at the Workspaces module in the Settings Manager. There you can play around with screen margins.**

Will do, thanks...

Never had this issue in Ubuntu... So annoying :)


404

---

### Post by bmomjian on 2011-11-12
The Workspace module doesn't seem to help --- it just adds more space between the window and the edge of the screen.  I suppose if you could make the value negative it might help, but you can't.

---

### Post by Toz on 2011-11-12
How about Settings Manager -> Window Manager Tweaks -> Accessibility Tab -> Hide frame of windows when maximized? I just realized that I have this selected and when I unselect it the behaviour is different.

---

### Post by bmomjian on 2011-11-12
I already had that option checked.  When I uncheck it, I do see the window edge, which kind of makes it worse.

---

### Post by m_duck on 2011-11-12
You can do it if you modify your theme. It definitely works for GTK 2.0 programs, but I've not checked for GTK 3.0 ones.

Basically the theme variable you want to change is the following line in your GTK-2.0 theme (it is line 64 in the copy of greybird I am using):
```
GtkScrollbar            ::trough-border                         = 3
```where I guess the 3 will be theme dependent. So, to remove the padding on the outside of the scrollbar, simply change this '3' to a '0'.

**In more detail:**
Make a copy of the theme you want to use, in this example 'greybird':```
sudo cp -r /usr/share/themes/greybird /usr/share/themes/greybird2
```*Note: you could also copy it to ~/.themes/ in your home directory (you may have to create it first) to save using sudo.*

Change into the gtk-2.0 directory of the copy of the theme in question:```
cd /usr/share/themes/greybird2/gtk-2.0
```Open the gtkrc in your favourite editor (as root):```
sudo vim gtkrc
```or```
gksu leafpad gtkrc
```Edit the line mentioned at the beginning of this post to change the value to 0.

Finally, save and exit your editor, and apply the modified theme (or just reapply the theme if you didn't make a copy). There should now be no 'padding' around the scrollbar (note that some programs e.g. Firefox will need restarting since they aren't strictly GTK).

Hopefully this helps!

---

### Post by marinara on 2011-11-12
Does that fix also fix the same problem with the xfce button on panel1?
I can't test this, I've switched to lubuntu because of thsi bug already.

---

### Post by m_duck on 2011-11-12
I'm not sure of that problem? There is no border around the menu button for me if that's what you mean?

---

### Post by marinara on 2011-11-13
about the bug I'm talking about on the panel1 panel xfce button.

moving the mouse to the left edge of the screen, the button doesn't accept clicks, moving it to the top of the screen, same problem.

---

### Post by m_duck on 2011-11-13
That is odd. The button extends to the screen edges here. I'm using stock Xubuntu 11.10 if that is of any help? I do recall the behaviour you describe from another box I was running XFCE on (non-*buntu), but that no longer has it.

I've attached some panel settings for the stock Xubuntu 11.10 for reference, in the hope it can be of some use.

---

### Post by marinara on 2011-11-14
might as well close the thread.

Thanks m_duck

BTW lubuntu has same problem, but all you have to do is change the widget theme to LXDesign

Thanks again

---

