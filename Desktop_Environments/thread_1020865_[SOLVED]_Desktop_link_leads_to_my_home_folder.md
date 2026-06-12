---
title: "[SOLVED] Desktop link leads to my home folder"
date: 2008-12-24
forum: Desktop Environments
---

### Post by jinjiru on 2008-12-24
When I open Nautilus and try to navigate to my Desktop folder clicking the Desktop link in the Nautilus sidebar, it shows not the Desktop folder but my home folder.
Please take a look at the picture:
[URL=http://farm4.static.flickr.com/3289/3133319121_fc4e1d7689_o.png]
[IMG]http://farm4.static.flickr.com/3289/3133319121_231ff5f74b_m.jpg[/IMG][/URL]

As you can see I clicked to the Desktop link and got my /home folder :(
The Desktop folder itself does exist and I can place files there. But there's a second problem: they do not appear on the ~real~ Desktop (i.e. where my wallpaper is set):

[[IMG]http://farm4.static.flickr.com/3203/3134148172_47a58a32bf_m.jpg[/IMG]](http://farm4.static.flickr.com/3203/3134148172_64b37ceb0d_o.jpg)
As you can see, there're files in my Desktop folder but they're not displayed on my desktop screen.

More than that, the right click does not work on my desktop screen and I cannot set background by right-clicking and choosing the Properties menu.

Here're my gconf-edit screenshots:
[[IMG]http://farm4.static.flickr.com/3196/3134159444_503f18e401_m.jpg[/IMG]](http://farm4.static.flickr.com/3196/3134159444_37baa6c577_o.jpg)  [[IMG]http://farm4.static.flickr.com/3127/3133337759_369531f945_m.jpg[/IMG]](http://farm4.static.flickr.com/3127/3133337759_b8d91efbf4_o.jpg) [[IMG]http://farm4.static.flickr.com/3085/3134188706_a4f57f1694_m.jpg[/IMG]](http://farm4.static.flickr.com/3085/3134188706_5b613e3a7f_o.png)

You can see that the "desktop_is_the_home_dir" setting is turned off and "show_desktop" (which should render the icons on the desktop) is set ON.

Also I can add that there's a Home link and a Desktop link in the Places menu, but they both lead to the /home/jinjiru (my Home folder). And also you can see that there's no Home link in the Nautilus sidebar (thought it was there some time before!):
[[IMG]http://farm4.static.flickr.com/3101/3133355335_fcaac95576_m.jpg[/IMG]](http://farm4.static.flickr.com/3101/3133355335_aa4a93479e_o.png)

I'm sorry I cannot write a better explanation of my problem because of my poor English, and I just hope anyone could find what my problem is and help me!
I just want my Desktop back!

---

### Post by gettinoriginal on 2008-12-24
Try "View"  reset to defaults.  :P

---

### Post by jinjiru on 2008-12-25
> **gettinoriginal said:**
> Try "View"  reset to defaults.  :P

Does not help :((

---

### Post by getkart on 2008-12-25
Same problem here,

I pressed a key combination some time back and all my desktop contents were gone. Then i saw that Desktop folder was in trash with nothing in it. I igored it for sometime since I had only a few files in desktop earlier. Then after some 3 to 4 restarts, my home folder contents were spewed across my desktop and lo my home folder is in my desktop now!

Did you press any key combination? I am digging for the symlink that does this job. I don;t how though... 

`locate Desktop` the following is I think some relevant result,
Someone know what these files do... Never tried python before so.. I don;t know.
--
/var/lib/python-support/python2.5/xdg/DesktopEntry.py
/var/lib/python-support/python2.5/xdg/DesktopEntry.pyc
/var/lib/python-support/python2.4/xdg/DesktopEntry.py
/var/lib/python-support/python2.4/xdg/DesktopEntry.pyc
/usr/share/python-support/python-xdg/xdg/DesktopEntry.py
---

---

### Post by getkart on 2008-12-25
~/.config/user-dirs.dirs
Set XDG_DESKTOP_DIR to the following... 

XDG_DESKTOP_DIR="$HOME/Desktop"

(earlier it was pointing my home directory.)

As an aside:
The comments in that file say that we can change the values... and it 
seems /etc/X11/Xsession.d/60xdg-user-dirs-update invokes xdg-user-dirs-update to update the directory entries by reading user-dirs.dirs file.

Enjoy!

---

### Post by getkart on 2008-12-25
Hey Jinjiru,

The cleanest way is to run 

xdg-user-dirs-update --set DESKTOP ~/Desktop

in your shell.

ENJOY!


My last post here!!

---

### Post by jinjiru on 2008-12-25
> **getkart said:**
> Hey Jinjiru,

The cleanest way is to run 

xdg-user-dirs-update --set DESKTOP ~/Desktop

in your shell.

ENJOY!


My last post here!!


Thank you so much!! Everything is ok now!
Thanks a lot again!

---

