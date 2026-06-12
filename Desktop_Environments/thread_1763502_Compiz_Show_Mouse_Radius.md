---
title: "Compiz Show Mouse Radius"
date: 2011-05-20
forum: Desktop Environments
---

### Post by vitz3 on 2011-05-20
Hi all,

I just wanted to share something with you all. If this belongs somewhere else let me know.

I got the idea from this **[thread]("http://ubuntuforums.org/showthread.php?t=557491")**

I wanted the show mouse effect to not rotate around my mouse (just a preference)and have the emitters directly under my cursor. So by editing two files it gave me the desired effect to an extent. 

1. Just in case back up your compiz settings.
2. Open a terminal and type - sudo nautilus . It'll ask for your admin password.
3. The file manager should now be open, go to /usr/share/compiz/showmouse.xml copy the file and rename the copy to showmouse.xml.bak.
4. Open showmouse.xml with the text editor.
5. Scroll down to the bottom and look for the "radius" section. Go to the <min>10</min> entry and change it to 2. Save.
6. Go to /usr/lib/compiz/libshowmouse.so copy the file and rename the copy to libshowmouse.so.bak.
7. Open the file with Ghex and search for the string radius on the right side of the search box.
8. It'll look like a jumble of words, but look after the word radius and find <min>10</min> change to 2. Save.
9.Compiz should now disable itself.
10. Reboot and re-enable Compiz and try out the show mouse plugin, it should now allow you to use a smaller radius.

Notes: 
For some reason it wouldn't allow me to use a radius of 0 or 1. If anyone has any tips it would be appreciated.

Thanks

---

### Post by Bonster on 2011-05-22
Does seem to work at value 2 either, my compiz wouldnt load with that

---

