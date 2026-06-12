---
title: "Almost impossible to open the Message Tray with the mouse."
date: 2014-02-15
forum: Desktop Environments
---

### Post by cdysthe on 2014-02-15
Hi,

I have Ubuntu GNOME 13.10 x64 on three very different laptops, but they all have one thing in common, it's almost impossible to open the Message Tray by holding the mouse pointer over the bottom screen edge (which the Gnome wiki says is one of the ways to do it). I have to drag the mouse cursor back and forth often for 10 seconds or more to get it to pop up, and sometimes it won't at all. I know I can do the key combo, but I prefer using the mouse so I was wondering if there's anything I can do to get it to work as reliably as the top left corner does which always opens Activities without any problems or delays.

---

### Post by jimbean on 2014-02-15
try a different mouse is your mouse older usb, serial its happing to me

i know u said laptop but how old is laptops try a seperate mouse

---

### Post by cdysthe on 2014-02-15
> **jimbean said:**
> try a different mouse is your mouse older usb, serial its happing to me

i know u said laptop but how old is laptops try a seperate mouse

I'm having the same problem on three different laptops. One is a six year old Asus, the two others one older and one brand new Thinkpad. I have worked on this some more and found out that your do not only have to hover over the the bottom of the screen, you need to apply pressure downwards which is not easy with a touchpad. I always use touchpads, never separate mice. I do not even like using them, so that is probably why I find the problem to be present regardless of which laptop I am on. And I do all my computing is on laptops with touchpads so this is a bit of a problem for me with Gnome-Shell. I wish that the tray was triggered the same way Activities are, by a corner, the lower right corner would be ideal for me. I will see if I can live with this, if not, one of the great things about Linux comes into play: Choose the desktop environment that works for you! :)

---

### Post by sammiev on 2014-02-15
Seems to work as it should here. Make sure you bring the mouse down towards the center of the screen and not the sides.

---

### Post by cdysthe on 2014-02-15
> **sammiev said:**
> Seems to work as it should here. Make sure you bring the mouse down towards the center of the screen and not the sides.

Yes, it does work but I really have to slide down the touchpad to get it to work. Maybe I can get used to it. Same thing on all three laptops. Works much better with a separate mouse or even the red dot mouse thingy on the Thinkpads.

---

### Post by buzzingrobot on 2014-02-15
This annoyance affects a lot of people with ThinkPads or other laptops.  It is fixable by editing one line of Gnome Shell code;

Make your way to /usr/share/gnome-shell/js/ui/layout.js.

You need to make one small adjustment to layout.js.

Cursor down from the top of that file until you see this little stanza:
```

// The message tray takes this much pressure
// in the pressure barrier at once to release it.
const MESSAGE_TRAY_PRESSURE_THRESHOLD = 250; // pixels
const MESSAGE_TRAY_PRESSURE_TIMEOUT = 1000; // ms

```

It's at line 27 here.

You need to change the line that reads "const MESSAGE_TRAY_PRESSURE_THRESHOLD = 250; // pixels".  

Changing the "250" to a lower number will make it easier to trigger the display of the Message Tray.  I set it to 50.

After making the change and saving the file, logout and in, or restart Gnome Shell (alt-f2+r) to activate it.

You will need to have root authority to save this file, so use sudo to launch your editor.

Also, this file could be overwritten during an update.  That hasn't happened to me, but it is certainly possible.

(When I mess about with a file that isn't intended for user editing, I make a copy of the original.  E.g., "layout.js_orig".  I also add a comment in many cases to indicate the change I made.  In this case, I made the edited line read:
```

const MESSAGE_TRAY_PRESSURE_THRESHOLD = 50; // pixels **Was 250**

```

The '//' marks the beginning of a comment that will be ignored by the Javascript interpreter.)

---

### Post by cdysthe on 2014-02-15
> **buzzingrobot said:**
> This annoyance affects a lot of people with ThinkPads or other laptops.  It is fixable by editing one line of Gnome Shell code;

Make your way to /usr/share/gnome-shell/js/ui/layout.js.

You need to make one small adjustment to layout.js.

Cursor down from the top of that file until you see this little stanza:
```

// The message tray takes this much pressure
// in the pressure barrier at once to release it.
const MESSAGE_TRAY_PRESSURE_THRESHOLD = 250; // pixels
const MESSAGE_TRAY_PRESSURE_TIMEOUT = 1000; // ms

```

It's at line 27 here.

You need to change the line that reads "const MESSAGE_TRAY_PRESSURE_THRESHOLD = 250; // pixels".  

Changing the "250" to a lower number will make it easier to trigger the display of the Message Tray.  I set it to 50.

After making the change and saving the file, logout and in, or restart Gnome Shell (alt-f2+r) to activate it.

You will need to have root authority to save this file, so use sudo to launch your editor.

Also, this file could be overwritten during an update.  That hasn't happened to me, but it is certainly possible.

(When I mess about with a file that isn't intended for user editing, I make a copy of the original.  E.g., "layout.js_orig".  I also add a comment in many cases to indicate the change I made.  In this case, I made the edited line read:
```

const MESSAGE_TRAY_PRESSURE_THRESHOLD = 50; // pixels **Was 250**

```

The '//' marks the beginning of a comment that will be ignored by the Javascript interpreter.)

And that is why this is such a great place to be! Problem solved and I'm an even happier Gnome-Shell/Ubuntu user! Thank you so much!

---

