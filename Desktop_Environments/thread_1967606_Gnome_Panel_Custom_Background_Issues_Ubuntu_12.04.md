---
title: "Gnome Panel Custom Background Issues Ubuntu 12.04"
date: 2012-04-28
forum: Desktop Environments
---

### Post by mpmistr on 2012-04-28
[IMG]http://img62.imageshack.us/img62/5835/gnomepanel.jpg[/IMG]

I'm still having issues selecting a customer background in Ubuntu 12.04 using Gnome Classic. I thought this was fixed in 12.04. I'm using Zukitwo theme (for Gnome 3.4) and trying to use a custom image for top panel.

Any idea how to fix this??

On a side note...

[IMG]http://img856.imageshack.us/img856/1164/dragselect.jpg[/IMG] 

Drag and select seems a bit messed up too, this seems theme related though. I'm not sure how to edit/fix this either however.

Any help would be appreciated!

---

### Post by LarsKongo on 2012-04-28
Custom background in Gnome 3 fallback panel is not 100% possible. Only certain parts of it uses the custom bg. I've tried to change the theme to add transparent parts instead of using the css gradient colors, but it creates artifacts and sometimes crashes the panel.

As for the 2nd thing. I'm working on an update for Zukitwo, so that bug will be fixed. ;)

---

### Post by mpmistr on 2012-04-28
There is no way to edit a theme to use a custom background?

---

### Post by mpmistr on 2012-04-30
Maybe the better question is, are these things going to be fixed? I really enjoy the gnome panel fallback. It seems like the best option for people who are still used to the gnome2x interface.. if they just fixed some minor quirks it would be pretty awesome..

Also I am a huge fan of your work on Zukitwo, great theme. :)

---

### Post by algoritm13 on 2012-05-08
It nervous me. I really want gnome panel with transparent background. Will it be fixed or developers indifferently for this problem? Switch to "progressive" 12.04 has brought new challenges.

---

### Post by mpmistr on 2012-05-09
I would like to know as well. I do like the gnome panel fallback mode especially on a LTS.. however the fact little things like this do not work makes it hard to use.

I hope it is fixed eventually I really do not like Gnome Shell or Unity and "Classic" really is nice but it's still kind of incomplete.. also wish we could get some anti-aliased window borders in 12.04 too.. it gets old having to hack Emerald every release.

I'm not sure if this will ever be fixed. Most bug reports on gnome panel seem to be responded with Unity 2d being the preferred fallback mode.. yet I hear Unity 2d is being dropped. It would be nice to have a functional gnome panel environment and I would think a lot of other end users feel the same way.

Gnome 3 is a regression in a lot of ways for an end user, sadly.

---

### Post by LarsKongo on 2012-05-10
> **mpmistr said:**
> also wish we could get some anti-aliased window borders in 12.04 too.. it gets old having to hack Emerald every release.
Try to see if you can enable Mutter as the WM in fallback mode for anti-aliased rounded window corners. (Same system requirements as gnome-shell. Don't do this in Unity btw, because it depends too much on compiz.)

---

### Post by mpmistr on 2012-05-10
> **LarsKongo said:**
> Try to see if you can enable Mutter as the WM in fallback mode for anti-aliased rounded window corners. (Same system requirements as gnome-shell. Don't do this in Unity btw, because it depends too much on compiz.)

Good idea. I may give that a try. It's too bad Mutter isn't quite as robust as Compiz as far as eye candy though.

---

### Post by Giant Speck on 2012-05-20
I'm wondering if this is a problem with gnome-panel itself.  I've been thinking of submitting a bug report about this for a very long time now, but I don't know the source of the problem.  I think it's very strange that you can change the background of the panel itself but not of the actual applets.

---

### Post by LarsKongo on 2012-05-20
> **Giant Speck said:**
> I'm wondering if this is a problem with gnome-panel itself.  I've been thinking of submitting a bug report about this for a very long time now, but I don't know the source of the problem.  I think it's very strange that you can change the background of the panel itself but not of the actual applets.
I suppose the bug should be reported to those who create the applets. (Especially the indicator-applet.)
A bug report with something like this:
*"Applets should use the same background specified by the user in gnome-panel settings."*

There's a possibility of changing the backgrounds in gnome-panel.css.
I've tried setting all backgrounds to the color @transparent (specified in gtk.css as rgba(0,0,0,0).) But there are some artifacts/instability, and the indicator-applet (+ some others) just doesn't follow any rules at all.

---

### Post by Giant Speck on 2012-05-20
> **LarsKongo said:**
> There's a possibility of changing the backgrounds in gnome-panel.css.
I've tried setting all backgrounds to the color @transparent (specified in gtk.css as rgba(0,0,0,0).) But there are some artifacts/instability, and the indicator-applet (+ some others) just doesn't follow any rules at all.
Yeah, I've even set the background-image to "none" and it doesn't do anything.

---

### Post by kabukiM0n0 on 2012-06-20
Is there any feedback if there going to look into this bug?
I'm having the same issue and it's just pure frustration everytime i log in. :(

k.m

---

### Post by hawthornso23 on 2012-07-21
The strange thing is that the indicators ported by jconti in his ppa respected transparency perfectly. When the official ones in the repository came out they regressed.

---

### Post by Giant Speck on 2012-07-22
I believe I saw a Blueprint in Launchpad stating that they intend to port all of the indicators to GTK 3 (I had no idea they weren't already).  I'm wondering if this will help the situation.

---

### Post by Destructo47 on 2012-07-22
If using Gnome Shell, then gnome-shell.css in /usr/share/gnome-shell/theme can be modified. Modifying the section labeled /*Panel*/ may hold promise. You can eliminate the black background stuck under the panel by changing 'background-color' from 'black' to 'transparent'. This doesn't completely fix it, but it's a step forward. Oh yeah, make sure you backup gnome-shell.css before you modify it.

---

### Post by Giant Speck on 2012-07-26
I've just discovered that if you select the "solid color" option under the Background tab in the Panel Properties dialog, it'll let you change the background color of the panel.  As long as the opacity slider is moved all the way to the right, the indicators obey the panel color.  Slide the slider even the tiniest bit to the left, and the indicators start doing their own thing.

I just wish I knew which package is causing this behavior, so that I can properly report it.

---

### Post by Frogs Hair on 2012-07-27
The software center indicates the gnome-session-fallback is community maintained , but when viewing properties in synaptic this url is provided.
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss)

---

### Post by mpmistr on 2012-07-28
I guess this bug is still lingering? I moved back to Gnome2 until they can provide a decent gnome classic experience for Gnome3..

I really wish they would focus on making gnome panel work in gtk3 and a sane configuration tool for themes/colors instead of forking with MATE/Cinnamon, ect..

---

### Post by hawthornso23 on 2012-09-05
Is there an official bug report associated with this annoyance?

---

### Post by hawthornso23 on 2012-09-05
Answering my own question, the inability of indicator applet to respect transparency in gnome panel is due to a regression in GTK. The launchpad bug report is here

[https://bugs.launchpad.net/gtk/+bug/966697](https://bugs.launchpad.net/gtk/+bug/966697)

If you are annoyed by it then go there and click on "affects me".  No sign of action. It is a GTK problem and the GTK people should fix their broken API.   That seems to be the theory anyway. I'm not holding my breath.

---

### Post by black veils on 2012-09-05
how about installing```
xfce4 xfce4-goodies
```a desktop which has been a good alternative for people who used gnome 2. you can have panel transparency and backgrounds, you will probably want to remove the sessions plugin though, another option can be used. you can choose amount of panels, and placement etc

---

### Post by cmcanulty on 2012-09-05
My panels constantly change back to gray though set as lt blue. Happens in classic and xfce very annoying

---

### Post by Dolsilwa on 2012-10-06
Bug still exists in 12.10 beta 2.  I hope someone will repair this :-/ For 12.04 users i recommend mate-panel for now - it's almost as good as gnome2 panel.

---

### Post by u2nTu on 2012-10-31
...and still happening with the latest 12.10.


Setting Radiance theme produces yet a third state:[INDENT]On login, panel backgrounds show what's set (blue). After a short time, they change to Radiance color. Then usually three or four times over the next several minutes,  they change to the dark brown of the default Ambiance theme, flipping immediately back to the Radiance color. Finally, the dark brown stays and the changes stop. **Really ugly.**
[/INDENT]
All the flipping of background colors is quite convulsive -- screams "BUG!"

Echoing the hopes of others that this will soon be fixed.

---

