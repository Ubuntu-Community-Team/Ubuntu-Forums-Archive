---
title: "Several problems with themes and images."
date: 2009-01-25
forum: Desktop Environments
---

### Post by AlucardArg on 2009-01-25
Hey guys.
Some days ago, I switched to Ubuntu (from WinXP, of course) and I love it so far.
But now I'm starting to freak out...
Last night I wanted to install some themes, but they required GTK+ 2.0, so, I installed it, and as you know, it requires many other packages, and that packages, require others. The thing is that some of them gave errors, like if they weren't installed, but I did have the package, just in another location, or another version (or something like that, I'm quite a n00b here), so what I did was to ignore the package check during configure (*).
Finally got it installed, and all of the other packages (pango, glib, and stuff).

Now to the problem itself:
If I try to open a JPEG image with Image Viewer, it always tells me that it cannot recognise the format. Still, I can open it with Firefox, or GIMP.
Also, on the theme list, only appears the themes that I've downloaded (mostly GTK+ 2.0 dependant). If I set a customised mouse pointer, it'll still appear "stock" over Firefox, or other programs.
And finally, the theme will disable by itself, randomly, to something that looks like Windows 98 (all grey, squarish, and, basically, awful)


I'd HATE to reinstall ubuntu, but I guess I'll have to do so. But before that, can someone please help me out here?


I'm running Ubuntu Ibex, btw.

---

### Post by oldos2er on 2009-01-25
How did you install gtk2 and its dependencies? It's not clear from your post exactly what's going on. The most appropriate way to do it would be using aptitude on CLI, or Synaptic Package Manager.

 This isn't Windows, reinstalling the OS won't fix your problems.

---

### Post by AlucardArg on 2009-01-25
Yea, I should have installed GTK using Synaptic, but instead I downloaded all the dependencies and stuff from internet (I think most of them were from Linux From Scratch).
I had some other problems (not being able to open "Computer", because nautilus couldn't find locations, or something like that. External units not mounting, etc... I basically messed up everything), so I ended up backing up some stuff, and installing Ubuntu again. As soon as I get home, I'll reconfigure everything again.

But if I may ask, how should I search GTK in Synaptic? I'm pretty sure it's a silly question, but I think it doesn't appear as "GTK+-2.0" Or does it?
(I needed it so I could install some themes)

---

### Post by oldos2er on 2009-01-25
The actual package name is gtk2-engines. I used the regular (not quick) search and typed in gtk, then looked under packages starting with the letter g.

---

### Post by Ben Page on 2009-01-25
That GTK is actually a GTK theme, Im thinking that you downloaded only window decoration, and when you set the window decoration it asks for corresponding GTK theme (its basically a buttons theme) so you need to look closer witch GTK its looking for, for example GTK-aurora, GTK-human (theme) and find and download exactly that file not the GTK engine, but GTK theme. For cursors, its normal, you have to re-log, or even restart the OS to get completely themed cursor.
You don't necessarily need to download GTK from synaptic (especially if its a external theme found on gnome-look.org, you can try searching "theme" in syn, like ubuntustudio-theme). If you download themes manually, they can often be incomplete, and because of that you will get GTK engine that & that missing, or icons theme missing, you can still use incomplete themes by selecting customize in themes tab (and select individual components individually, icons, cursors, GTK theme, Window frame etc...)

---

### Post by AlucardArg on 2009-01-25
A big thanks for both of you guys.
Now I'm installing all updates, and stuff from the Update Manager, and as soon as that finishes, I'll try instaling a GTK2 theme from Syn. Supposedly, it should see that I don't have GTK+ 2.0 installed, and it'll install it, and it's dependecies... It's just a guess, of course.

And sorry to bother you with my n00b questions :P

---

