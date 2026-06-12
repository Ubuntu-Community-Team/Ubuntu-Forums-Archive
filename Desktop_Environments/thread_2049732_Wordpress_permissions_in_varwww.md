---
title: "Wordpress permissions in var/www"
date: 2012-08-29
forum: Desktop Environments
---

### Post by Reflux on 2012-08-29
Hi, this is my first post ):P
I recently moved my development environment from Windows 7 to Ubuntu 11.10 so I'm a complete noob.
Installed LAMP and bluefish. Everything is working nicely.
Currently I'm working on a Worpress theme so I drag-and-drop a lot of image-files in nautilus to my theme-folder.
When I try to access these files through the Wordpress website it fails because I didn't yet set the right permissions on the file.

How I handle it now is open a terminal, type 'gksudo nautilus' go to the directory, set the properties of all underlying files to 'read and write' and then it works, 
but since I have to do it every time, whenever I want to replace/add an image it's kind of a hassle for my workflow... 

I just want to be able to drag-and-drop images from a random directory to a directory in var/www for Wordpress to access, without any trouble or workarounds each time...

---

### Post by mhgsys on 2012-08-29
[http://askubuntu.com/questions/19898/whats-the-simplest-way-to-edit-and-add-files-to-var-www](http://askubuntu.com/questions/19898/whats-the-simplest-way-to-edit-and-add-files-to-var-www)

---

