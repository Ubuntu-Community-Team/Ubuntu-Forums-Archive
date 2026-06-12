---
title: "Maximize window after snap to side"
date: 2018-05-29
forum: Desktop Environments
---

### Post by nraygun on 2018-05-29
I can drag a window to the edge of the screen to make it take up either half of the screen or a quarter of the screen. Pretty handy.

However, when I snap a window to the side, and then hit the maximize window button, it doesn't maximize. I have to drag the window to the top to maximize.

Is this normal? Is there a way to make window maximize by hitting the window button instead of dragging?

Xubuntu 18.04, 4.15.0-22-generic

---

### Post by nraygun on 2018-05-31
Update: I only see the symptom when I drag to the edge to make the window take up half the screen. Dragging to take up quarter of the screen seems to maximize when the button is clicked.

---

### Post by tea for one on 2018-05-31
> **nraygun said:**
> I can drag a window to the edge of the screen to make it take up either half of the screen or a quarter of the screen. Pretty handy.

However, when I snap a window to the side, and then hit the maximize window button, it doesn't maximize. I have to drag the window to the top to maximize.

Is this normal? Is there a way to make window maximize by hitting the window button instead of dragging?

Xubuntu 18.04, 4.15.0-22-generic

I have Xubuntu 18.04 with the same kernel as you on a little netbook and I can snap a window to 50% and maximise (without dragging to the top).

When I click maximise again (i.e. when the window is 100%), the window returns to its original position (i.e. before it was snapped to 50%)

I haven't touched any of the window settings so I would suggest that your performance may not be usual.

I assume that you know about the Window Manager and Window Manager Tweaks under Settings.

I've had a look at the wealth of options but I can't see the exact one that explains your dilemma. 

There is a snapping option under Window Manager Advanced Tab and the box "To screen borders" is ticked.

I wish I could be more precise but, to be honest, I do not exactly understand what all the Window settings do.


Best wishes

---

### Post by nraygun on 2018-06-05
Thanks Tea.
I dont see anything in the Window Manager area that would affect this behavior.
I did see a double click to maximize option. Didn't know I could do this. But, with a window snapped to 50%, double clicking the title does nothing. But if I snap a window to 25%, it works just like the max button.
I don't think I've messed with any WM settings - I tend to leave those alone.

Any other ideas?

---

### Post by tea for one on 2018-06-05
Hello  nraygun

I regret to advise that I have no _concrete_ suggestions but I have a few comments:-

Did you install Xubuntu from the 18.04 ISO or upgrade from a previous version?

Is your install in a VM?

Do you have another kernel in your grub list? Try booting an alternative kernel to see if that helps.

Have you changed your theme?

There is an entry under Settings Editor for xfwm4 with switches like "snap_to_border" and "snap_to windows" but I have never altered these settings.

Just for info - My installation is a fresh download of Xubuntu 18.04 Core and I add packages as I require them.

Best wishes

---

### Post by nraygun on 2018-06-05
It's a new install of 18.04 from the ISO via thumb drive. Wiped the drive and installed it fresh.
I have no other kernels in the grub list other than what the new install put there.
I'm using the Arc theme. I think this is a pretty popular one.
I've not done anything in Settings Editor, but I see that snap_to_border is checked while snap_to_windows is not.

---

### Post by tea for one on 2018-06-06
> **nraygun said:**
> It's a new install of 18.04 from the ISO via thumb drive. Wiped the drive and installed it fresh.
I have no other kernels in the grub list other than what the new install put there.
I'm using the Arc theme. I think this is a pretty popular one.
I've not done anything in Settings Editor, but I see that snap_to_border is checked while snap_to_windows is not.

Yes, I agree that Arc is a popular theme and doesn't cause window management difficulties.

My settings of snap_to_border and snap_to_windows are the same as yours.

One last suggestion - do you still have the ISO on your thumb drive? Boot to a live environment and test the window snapping?

Kind regards

---

### Post by again? on 2018-06-06
I see this problem in Xubuntu with [**GNOME Core Applications**]("https://en.wikipedia.org/wiki/GNOME_Core_Applications") that don't use the xfwm4 window manager for the title bar.
eg
Gedit has the problem but Thunar does not.

---

### Post by tea for one on 2018-06-06
> **guber2 said:**
> I see this problem in Xubuntu with [**GNOME Core Applications**]("https://en.wikipedia.org/wiki/GNOME_Core_Applications") that don't use the xfwm4 window manager for the title bar.
eg
Gedit has the problem but Thunar does not.

Good grief - you must have mucked about with various applications to discover this - splendid catch, I doff my hat.

I confirm that Gedit and Gnome Calculator also misbehave along with Firefox.

Just to clarify, these applications misbehave when the window is snapped to 50% but they seem to work if snapped to 25%.

Best wishes

---

### Post by again? on 2018-06-06
> **tea for one said:**
> Good grief - you must have mucked about with various applications to discover this - splendid catch, I doff my hat.

I confirm that Gedit and Gnome Calculator also misbehave along with Firefox.

Just to clarify, these applications misbehave when the window is snapped to 50% but they seem to work if snapped to 25%.

Best wishes

It's got to do with interpretation of window states.
You can see this when using certain themes.
With windows that use xfwm decorations, the maximize icon matches when maximized vert left and maximized full.
[ATTACH=CONFIG]280008[/ATTACH]

With gnome decorations, the icon still indicates unmaximized when maximized vert left.
[ATTACH=CONFIG]280009[/ATTACH]

Something I hadn't noticed as I only show the close button in the title bar.
I use easystroke gestures to run wmctrl commands to toggle window properties and position which works irrespective of decorations.

[COLOR="#FF0000"]**Edit**[/COLOR]:
Depending on how much this bothers you, there is a solution.
In 17.10 and up you can install gtk3-nocsd which disables Gtk3 client side decorations.
```
sudo apt install gtk3-nocsd
```
May need to log out.

In effect gtk3-nocsd removes the gnome client side window buttons and utilizes the default title bar in gnome core applications.
[ATTACH=CONFIG]280010[/ATTACH]

---

### Post by tea for one on 2018-06-07
> **guber2 said:**
> 
Depending on how much this bothers you, there is a solution.


Hello again

Thanks for your detailed reply - very welcome.

This window behaviour with various applications doesn't bother me at all but I hope that the OP will try your suggestion and see if satisfies their needs.

Kind regards

---

### Post by nraygun on 2018-06-07
Guber2 for the win!!!
I'll try the nocsd thing later.
Thank you so much for two things, 1. That I'm not crazy(well, not due to this anyway), and 2. The Solution!

---

### Post by nraygun on 2018-06-07
Darn! No go.
I added gtk3-nocsd to my Xubuntu 18.03 and tried running chromium with
gtk3-nocsd chromium

I still get the problem. I also tried adding the environment variables as shown at the hosting github page.

---

### Post by again? on 2018-06-07
In chromium settings, enable "use system title bar and borders". 
```
chrome://settings/appearance
```

After installation of gtk3-nocsd you do not need to do anything else
except maybe logout. Run applications as normal.
From the github page:
> The Debian package already comes with integration code to automatically disable CSDs when installed, 
so after package installation only a re-login is required to have CSDs disabled on non-GNOME desktops.

---

### Post by nraygun on 2018-06-08
On Chrome, I don't use the system title bar since it shortens the screen real estate that Chrome takes up.

Maybe I'll live with the system title bar for a bit to see if it grows on me since this is the way to get the maximize button to work again.

---

