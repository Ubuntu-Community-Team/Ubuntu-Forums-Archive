---
title: "Panel and running programs"
date: 2011-08-12
forum: Desktop Environments
---

### Post by chejose on 2011-08-12
This morning while working the top panel stopped showing the programs I was running. I have been looking at forums and it seems that what I need is to install an applet that shows the active windows.

Good, but I don't know what the name of the applet might be to install it!

I am running Gnome 2.

Thanks,

José

---

### Post by ~!geek!~ on 2011-08-12
Right click on the panel you mentioned and select 'add to panel' -> choose windows list applet. 
If you are not able to search windows list there, try googling for it.

(Following is not recommended)
Worst case, you may reset all the panels using these commands:
gconftool-2 --shutdown-> rm -rf ~/.gconf/apps/panel->pkill gnome-panel. Now you should get all the panels set to defaults i.e. in original state when you installed ubuntu.

---

### Post by chejose on 2011-08-12
Thanks ¡Geek!

But what I got was little plain buttons... white. I will try what you suggest to see if I can find the applet using Google.

Well, I finally came to the conclusion that I lack the applet... it is either broken or lost.

So what would be the program name to install to be able to install the Windows list applet?

José

---

### Post by mkham on 2011-08-18
ubuntu AMD64 4-10 on Acer AMD Turion Ml32, 1gig ram, 1.6gig Mh

On mine the panel just doesn't load (top or bottom) every few days. I restart, run the repair version (though it after first 2 screens only shows a strip of text on the left), hit enter a few times. Seems to try to run Clam, but I can't see it, and HD ain't flashing. 

 Running /scripts/init-bottom, it finds ACPI warning Null Object Descriptor1 for \_SB_.BAT1._BST  expected integer

After panel is OK for 5-7 days. Got any idea how to fix this? Thought it just would be OK with kernal upgrade, but it's been doing this for 3 months

---

