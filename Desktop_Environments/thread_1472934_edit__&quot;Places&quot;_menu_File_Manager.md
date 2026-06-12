---
title: "edit  &quot;Places&quot; menu File Manager"
date: 2010-05-04
forum: Desktop Environments
---

### Post by agnes on 2010-05-04
Is it possible to open the bookmarked places, in the 'Places' menu of the menu bar on the gnome-panel, with a different file manager? Like PCManFM.

---

### Post by mikewhatever on 2010-05-04
You could probably add the same bookmarks to pcmanfm and then open them, or make pcmafm your default file manager.

---

### Post by agnes on 2010-05-04
I realize I was not really clear... I mean the "Places" menu in the gnome-panel. (Not the Nautilus sidebar.) (Post edited)

---

### Post by mikewhatever on 2010-05-04
... and who was talking about the Nautilus side bar?
This is somewhat old, but you should get the idea.
[http://linuxondesktop.blogspot.com/2008/05/replacing-nautilus-with-quicker-and.html](http://linuxondesktop.blogspot.com/2008/05/replacing-nautilus-with-quicker-and.html)

---

### Post by John Teisberg on 2011-03-18
I found the secret to editing the Places Menu. 
Find this file in your Home directory:
.gtk_bookmarks
Click it to open and you will see all the 'places' that show up.
Simply delete the ones you do not like and close the file.
Done.

---

### Post by Copper Bezel on 2011-03-18
You can set a different browser as the default application to open folders, which will affect anything that opens a location, including the Places menu but not including the Desktop. In Nautilus, right click a folder, choose Open With Other Application, find your file manager on the list, and make certain the checkbox is ticked to remember this as the default application. 

I use Thunar for this myself (because it's lighter and visually more compact when I just need to open a location, even if I still need Nautilus for the heavy lifting - just turning off the default browser mode doesn't really solve the problem.)

---

### Post by HotDogEater on 2011-06-13
In 10.04 the file to edit is named ".gtk-bookmarks", a hidden file in the home directory.  (The separator is a dash not an underscore,)  Its contents on my system are as follows:

file:///home/joe/Documents
file:///home/joe/Music
file:///home/joe/Pictures
file:///home/joe/Videos 

I was able to modify the file with gedit.  In my case the entry for Documents was missing. 

HTH, Joe, K9HDE

(If this is a viable solution, please mark as "Solved". )

---

### Post by cmcanulty on 2012-02-26
I am running 11.10 classic and the gtk file no longer exists. Documents has disappeared from my places menu. How can I fix this?

---

