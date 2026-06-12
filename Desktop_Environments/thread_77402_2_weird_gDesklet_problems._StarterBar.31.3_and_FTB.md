---
title: "2 weird gDesklet problems. StarterBar.31.3 and FTB.3.1"
date: 2005-10-16
forum: Desktop Environments
---

### Post by MetalMusicAddict on 2005-10-16
Im using Breezy with gDesklets .35.2. The 2 desklets are: [StarterBar.31.3]("http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210") and [FTB.3.1]("http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=224").

If you look at the screenshot you can see the monitors in the upper right. Thats [FTB.3.1]("http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=224").  All the meters/graphs are pegged. In the middle Im tryin to change the icon/PNG for a launcher. I cant. They're all greyed-out for some reason. 

Desklets not updated for .35.2? 

Is there a way to get Hoary gDesklets in Breezy? 

[[IMG]http://img331.imageshack.us/img331/8986/screenshot7tx.th.png[/IMG]](http://img331.imageshack.us/img331/8986/screenshot7tx.png)

---

### Post by darknuala on 2005-10-16
I have the same problem with the icons being greyed out when setting up the starter bar.  It works if I want to use something in usr/share/pixmaps, but everything in usr/share/icons is greyed out.  I've even copied some of the icons to my home folder, thinking maybe it was a permissions thing, but that didn't work either.  Can anyone suggest anything?

---

### Post by MetalMusicAddict on 2005-10-23
Little bump. ;)

---

### Post by skirkpatrick on 2005-10-23
It's not just FTB that has problems with gauge items, it seems that any desklet with a gauge item pegs to the full width of the desklet.  I tried a Sidebar disk usage desklet who's gauge is only supposed to go part way across the desklet and it draws the entire width.  I tried editing the source for the desklet but nothing I did worked so I think the problem is with gdesklets itself.

---

### Post by MetalMusicAddict on 2005-10-23
I tried Hoarys gDesklets this afternoon and got the same results. So I think its something outside it. The "Plotting" desklets work fine but the gauge ones are borked.

Weird.

---

### Post by skirkpatrick on 2005-10-24
And considering that 0.35.2 was released back in July, I'm surprised nobody's complained about this before.  I know it was working on my Hoary install before I upgraded to Breezy but I don't remember what version I was running.  I think I installed it on my daughter's computer, maybe I can find out from it.

---

### Post by davebgimp on 2005-10-24
I had huge problems with gdesklets upon first installing. The starter bar would not display anything and many of the other apps would cause an immediate crash with the program. Uninstalling gdesklets-data (which, I think Synaptic includes by default with the install) completely fixed the issue. The only thing you have to do is manually download and install the apps (very easy) as none are now preinstalled.

As far as the icons being greyed out. I see mention of moving them to the pixmaps or home folder with no luck, but did you actually check and compare the permissions on your desired icons and compare them to the permissions on anything in the pixmaps folder to see if anything's different?

---

### Post by MetalMusicAddict on 2005-10-24
I just figured out that I can manually input the path. If I try to use the "Browse" button to the right of the field when the window comes up the list on the right is very squished and I have to resize it to see anything.

Oh well though as long as I can edit it.

---

### Post by griefman on 2005-12-01
hey guys... i have the same problem with the gauges... the bars for the the disk and the memory for anyone applet are allways overfilled... any ideas... something new these days?

---

### Post by MetalMusicAddict on 2005-12-01
Nope. Still borked. I just switched to the "Plot" FTB ones. They work fine. StarterBar is also still weird but it also seems to be a Gnome issue.

---

