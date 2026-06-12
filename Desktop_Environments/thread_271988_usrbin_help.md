---
title: "/usr/bin help"
date: 2006-10-05
forum: Desktop Environments
---

### Post by ClarkePeters on 2006-10-05
Sometimes I can't find an installed program because it doesn't automatically show up in my applications menu (and I use synaptic for my installs, so not sure why)
So, I think I've found some of them but not sure
so someone please steer me, or edumacate me

/usr/bin  <--- these are the executable files?
/usr/share <-- these are the complete program/installed files minus the executable?

and what is  /usr/sbin?

finally, are there any other important folders in /usr I should know or folders other than /usr that is important to helping a normal guy install programs and keep up with documents.

thanks in advance  :???: 

p.s. do the tar files and such get saved after an install and are they necessary should I find them and clean up my system?

sometimes I can't find things with the locate or find command nor by the search box in nautilus. That's why I'd like to know where things go, but any advice on improving my search results would help too. [do I need to reboot after install to have a file show up in search--one time after I installed streamripper I did a locate streamr and nothing came up then I went back the next day after shutdown and boot-up and found it with the same locate streamr --and I always double check for typos so that wasn't the problem]

---

### Post by Kateikyoushi on 2006-10-05
In synaptic you can check what files a given package installs so you can easily find what you are looking for.

---

### Post by CatKiller on 2006-10-05
Sometimes you need to get a new menu for new menu items to show. Not always, but sometimes - don't know why. Either log out and log back in or **killall gnome-panel** to refresh the menus. Similarly, you sometimes need to refresh the filesystem before new files will be returned by locate. **sudo updatedb** will do this, although it does take a little while.

The most straightforward method if you really can't find out how to run an installed program is, as Kateikyoushi says, to look at the package properties in Synaptic to see which files are installed.

[This Wikipedia page]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") may give you the information you seek on why things are put in certain places, and according to that page /sbin contains "System administrative binaries (e.g., init, route, ifup) (**s**ystem **bin**aries)".

---

### Post by ClarkePeters on 2006-10-06
Thanks those tips really helped, as long as I know that sometimes the system needs some kind of refresh then I know its not me making the mistake. 

Especial thanks for the heads-up on using the synaptic properties. I didn't realize it was there (or I should say, I assumed it would have only a tidbit of info--lots of good info there)---way too cool!  Thanks!8)

---

