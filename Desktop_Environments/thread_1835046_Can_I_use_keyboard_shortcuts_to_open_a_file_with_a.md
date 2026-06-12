---
title: "Can I use keyboard shortcuts to open a file with an application?"
date: 2011-08-28
forum: Desktop Environments
---

### Post by focaccio on 2011-08-28
I was playing around with kupfer, gnome-do, gnome-launch-box and was really disappointed that I couldn't just get a program to create launch triggers like Quicksilver for Mac.  Kupfer seemed the closest, but was not stable on my system (could have been user error, anyway...) I finally gave up and am now satisfied with the (gnome desktop) built-in keyboard shortcuts in system preferences for launching applications.

What I need to do now is open files with a keyboard shortcut.  Is there some way to append the command to open an application so that it opens a particular file in the application?

Any help, much appreciated!

---

### Post by focaccio on 2011-08-28
Oh it would also be awesome if there was a way to open a folder view with a keyboard shortcut.  Is that possible?

Thanks

---

### Post by Krytarik on 2011-08-28
Generally, you can use the command "gnome-open" for this kind of stuff. Applied to either a file or a directory, it would open them with the applications associated to them.

For example,
```
gnome-open /home/USER/Pictures
```(full path to be sure) would open the directory "Pictures" in Nautilus.

And
```
gnome-open /home/USER/Pictures/Photo.jpg
```would open the image "Photo.jpg" in the currently set default application, in my case Eye of Gnome (Image Viewer).

And so on.

However, you can, of course, also run the respective application directly and pass the file/directory to it, like this:
```
nautilus /home/USER/Pictures
eog /home/USER/Pictures/Photo.jpg
```Whatever is easier or fits better in a specific case.

Greetings.

---

### Post by focaccio on 2011-08-28
Krytarik,
Thanks for the key: "gnome-open".  Everything I need to do is working now!  I can create triggers/hot-keys to open folders and files with the standard system preferences keyboard shortcuts tool.
Thanks

---

