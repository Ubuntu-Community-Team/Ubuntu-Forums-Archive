---
title: "Moving .VirtualBox to another partition and keeping integerity"
date: 2009-02-19
forum: General Help
---

### Post by linuxology on 2009-02-19
I am running an XP virtual box within the host O/S Ubuntu.  I want to move the .VirtualBox folder to a new partition without messing up what I have.  I have searched the forum and google and have not come across anything that makes me fully confident about the move.  Is there an article/tutorial or instructions for this?  I have tried to copy it to another partition then set VBox to go to the new partition, but Vbox stated there was another install with the same <something>  Can someone help with this I would not think this is very difficult

---

### Post by linuxology on 2009-02-22
Bump TO Top

---

### Post by msrinath80 on 2009-02-22
All you need to do is move the .VirtualBox directory from ~/ to where ever you want it. Next create a symbolic link as follows:

ln -s /where_ever_you_put_it/.VirtualBox ~/.VirtualBox

HTH

---

