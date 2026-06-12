---
title: "[SOLVED] VLC handles places"
date: 2008-11-03
forum: Desktop Environments
---

### Post by gibbsnich on 2008-11-03
Hey everybody!

I hope someone can help me with this one as this behaviour is really annoying ;-) 
Yesterday I dist-upgraded from 8.04.1 to 8.10.
Now whenever I select any entry in the "Places"-menu (I use the german Ubuntu version and I hope this is this right translation.. I mean the menu item next to the gnome terminal; it has sub-items for "Home Folder", "Desktop", my mounted external HD, ..) *VLC* starts up and starts playing the first media file it finds in the place I selected. 
What I actually want (and what always happened until I upgraded) is a nautilus window that shows the contents of the selected folder.

I'm sure I didn't change any configuration related to file handling or something. I searched for related config options in the obvious places in nautilus and gnome, I tried to search google but couldn't come up with the right terms, it seems.
Any ideas? 

Thanks in advance!
Michael

---

### Post by gibbsnich on 2008-11-03
Found the "right terms" (as you always do *after* posting..) and [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/267402](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/267402)
was quite helpful.

---

### Post by tuxxy on 2008-11-03
This is a well documented bug in Ibex, see the report

[https://bugs.launchpad.net/ubuntu/intrepid/+source/gnome-panel/+bug/260492](https://bugs.launchpad.net/ubuntu/intrepid/+source/gnome-panel/+bug/260492)

To make life easy for you simply you need to edit and remove a line from your .local/share/applications/mimeapps.list

```
sudo gedit .local/share/applications/mimeapps.list
```

The line amy look similar to  

```
MimeType=x-directory/gnome-default-handler;x-directory/normal;inode/directory;application/x-gnome-saved-search;
```

If you are unsure post the output here and Ill see if I can see it :)

---

