---
title: "[SOLVED] Todays nautilus update killed by my desktop background"
date: 2008-06-06
forum: Desktop Environments
---

### Post by pt123 on 2008-06-06
Today's update of Nautilus has killed my desktop background.

As no background image is displayed. But when I click on right click on desktop and choose "change by background", the background is listed there and shown as being selected, when I tried to select another one nothing happens to it is very slow like some errors are being generated.

 I tried deleting the ~/.gnome2/backgrounds.xml, and still no luck.

Anyone how to start the Change Desktop WP applet from a terminal then I might be able to see the errors being outputted.

---

### Post by pt123 on 2008-06-06
For some reason the draw_background value in Gconf editor was turned off. 

Turning it back on draws the WP. But there is still a bug because I am unable to choose the WP in the gnome-appearance-properties (this can be used to run from the terminal) using a mouse , but can with the keyboard. Also the CPU useage shot to 95% for gnome-appearance-properties and I had to kill it.

---

### Post by matthewn on 2008-06-06
Same issue here. Flipping the gconf value back on restores the wallpaper, but gnome-appearance-properties is unable to select a new wallpaper file. Yet another Hardy hassle. :(

---

### Post by autocrosser on 2008-06-06
Thanks pt123--

That's what I was looking for.......

I use Wallpaper Tray & it was showing change while my background stayed the same...I'll post tonight if WPTray can change things without the cpu overhead.

---

### Post by Darkchef on 2008-06-06
I had this same problem , to fix it I downloaded all the proposed updates and it was back to normal.

For noobs you need to select proposed updates under software sources under System -> Administration.

---

### Post by pt123 on 2008-06-06
> **Darkchef said:**
> I had this same problem , to fix it I downloaded all the proposed updates and it was back to normal.

But is your change background applet working fine, are you able to use your mouse to select different backgrounds in it?

---

### Post by pt123 on 2008-06-06
I have opened a bug report here
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/237990](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/237990)

If you guys can go there and confirm it and share your experience it will help the developers in solving it.

---

### Post by pt123 on 2008-06-06
> **pt123 said:**
> I have opened a bug report here
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/237990](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/237990)


The bug has been already reported and has been fixed.
[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/236778](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/236778)

 It should arrive with gnome-desktop 1:2.22.2-0ubuntu3

Maybe that what Darkchef was referring too.

---

