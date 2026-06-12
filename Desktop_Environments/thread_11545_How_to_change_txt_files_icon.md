---
title: "How to change txt files icon?"
date: 2005-01-17
forum: Desktop Environments
---

### Post by pgoya on 2005-01-17
Hi all

I want to change just txt files icon... How can I do that??

Thanks! :-P

---

### Post by Perfect Storm on 2005-01-18
Okay, if you have an icon theme installed:

First rename the file 'gnome-mime-text-plain.png' and copy it and rename the copy to 'gnome-mime-text.png' and another 'gnome-mime-text-x-readme.png'

then
cd /where/your/file/is
cp gnome-mime-text-plain.png gnome-mime-text.png  gnome-mime-text-x-readme.png /home/<username>/.icons/<name of the icon theme>/128x128/mimetypes

reboot or exit X and login again.

or if you're using 'human' icon theme

Does the renaming as above
cd /where/your/file/is
sudo cp gnome-mime-text-plain.png gnome-mime-text.png  gnome-mime-text-x-readme.png /usr/share/icons/Human/scalable/mimetypes

reboot or exit X and login again.

---

### Post by pgoya on 2005-01-18
Thanks! 
It was not exactely what did you say but it helps... :mrgreen:  I didn't have the file "gnome-mime-text-plain.png" but "gnome-mime-text.png"
I did: "sudo cp gnome-mime-text.png gnome-mime-text-plain.png gnome-mime-x-text" and it works perfectly. :D

---

### Post by Perfect Storm on 2005-01-19
Oh, sorry. A typo Error. It should say: 'Rename your icon to' blah blah  :oops:

---

