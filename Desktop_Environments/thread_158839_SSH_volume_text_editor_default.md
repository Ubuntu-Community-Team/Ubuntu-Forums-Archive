---
title: "SSH volume text editor default"
date: 2006-04-11
forum: Desktop Environments
---

### Post by wilstoff on 2006-04-11
I've tried everything imaginable to change how i open text files in a mounted ssh on my desktop.   I basically want to click on a text file when browsing my ssh and open it with nedit.  But for some reason it keeps comming up gedit.  I've tried updating alternatives changing file names and almost anything i could think of.  Even right clicking and changing the file type default opening still opens in gedit even though nedit is clicked.

Anyone have any suggestions?

---

### Post by kapello on 2007-10-26
Me too! Except, I'd like to use gvim. No answers since 2006... so it's not possible?

EDIT just thought to try opening gvim first, then File > Open and enter address as ssh://user@address.com

message comes up "can't open file because it isn't local"

Also tried ssh through Terminal, then "gvim filename.php". Again no success. I realise I can just use normal vim on the commandline, which is fine, but the file-browser method has the advantage of also allowing easy drag-drop for image files etc. So I really really want to be able to use the gui not commandline, but also keep using vim/gvim as text editor.

---

### Post by Maxtorm on 2008-04-17
I'm not sure anyone is following this thread any more, but just in case:

I got it working with gvim (I'm assuming the same method will work with nedit). The trick was to mount the ssh volume using sshfs rather than accessing it directly through Nautilus. ```
sudo apt-get install sshfs
```Then, to mount the ssh directory:```
sudo sshfs user@host.domain:/path/to/your/directory /local/mount/point
```Keep in mind that the mountpoint will only be accessible to su, so to use nautilus, you have to invoke it with gksu. If you're using a specific ssh server regularly, you can just create an icon that launches```
gksu nautilus /local/mount/point
```Hope that helps!
*EDIT:* One other thing.. probably obvious from the previous posts, but you have to right-click and choose Open with Other Application the first time you edit a file of each type.

---

