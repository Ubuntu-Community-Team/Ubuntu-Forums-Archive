---
title: "memory usage, 2d lag .. GNOME more than KDE?"
date: 2006-12-14
forum: Desktop Environments
---

### Post by gribelu on 2006-12-14
So i moved from windows.. i only booted to windows when i needed to chkdsk my ntfs drives and get them to mount in ntfs-3g :).. and when i needed to use Photoshop but that's another story (adobe sucks!)

I used the standard Ubuntu Edgy 6.10, with Gnome. Memory usage climbed as i opened more and more applications.. i admit, i have a problem.. even though i only have 512mb of ram i multitask alot. A standard desktop for me look like this:
-Firefox(Swiftfox) with ~20tabs, Amarok, Gaim, Jedit with 5-10 files open(java based editor/ide), Azureus
-a few consoles
-about 6 partitions mounted through ntfs-3g.. wich does use some memory if you look at the processes it starts.

Problem is.. except the fact that i can't get Gnome to prompt me when i delete a file (or disable the trash).. i like it better than kde.

BUT.. It uses about 100mb more memory than KDE. This happends after a few hours.. it just climbs and climbs. Right now i've been under KDE for about 3 hours and the swap usage is at 20mb. Memory usage ~350mb wich i consider normal.
If i use Gnome for that long, intensively, it uses like 100 or more swap memory.. and about the same physical memory or more.

What i need you to tell me.. Is this normal? If it is.. i'll just use KDE..

Thanks!

P.S. I disabled most of the eye candy under both KDE and Gnome. Only basic themes with no special effects or whatever.

---

### Post by padre999 on 2006-12-14
Strange that your computer uses swap...

I use K/Ubuntu now for a year, and the only time I experienced swapping was when I accidentally created a 3x4 meter 300dpi image in Gimp. I also have a 512MB on my computer.

Anyway.

Are you sure you are interpreting the memory values in the right way. Often people get confused about cached memory, which is actually free memory. See [http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Overview_of_memory_management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Overview_of_memory_management)

On KDE vs Gnome memory usage see [http://ktown.kde.org/~seli/memory/](http://ktown.kde.org/~seli/memory/)

---

### Post by gribelu on 2006-12-15
I know about the cache/buffers thing... it's not that :)
Gnome just starts eating up memory and doesn't give it back until i restart x

Oh and my swappiness value is 30... so it's not that either :)

Anyway.. does your gnome do the same thing? :)

---

### Post by padre999 on 2006-12-15
If you look at the bar above this post it says "Kubuntu 6.10 Edgy User"... :roll: 

Sorry.

Somebody else please!?

---

### Post by zgornel on 2006-12-15
It's normal, especially if you use it intensivelly. What does matter is not how much memory it uses, it's how responsive it is when a lot of apps are opened.

---

### Post by mcduck on 2006-12-15
well, Azureus and Firefox are known memory hogs, and I bet the java-based text editor adds some too.. Then there's Amarok, which needs to load some KDE libraries and that adds even more.. No wonder that you're a bit low on memory ;)

edit: to delete files straight in gnome (without using trash) open file manager, go to Edit/Preferences and on the Behavior-tab enable 'Include a Delete command that bypasses Trash'. Now you can right-click a file and select to delete it without sendig it to Trash. (if I remember right shift-del is the keyboard shortcut)

---

### Post by gribelu on 2006-12-16
I know they are memory hogs.. that's exactly why i used them for testing. And afaik Firefox and Azureus depend on some GTK libs, as well as Gaim. So i don't think AmaroK is the hog here.
If i close all my apps, after using them for some time Gnome doesn't free up as much memory as KDE.

And about the delete thing.. i knew about Shift-Del since windows 95:)) ... the fact that there's no prompt when i hit Del worries me because one day i might hit that key by mistake and not even realize it until it's too late. I'm working with many php files and whatnot, constantly moving, creating, deleting so that possibility isn't one that i wanna live with.

---

