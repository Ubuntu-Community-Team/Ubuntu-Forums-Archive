---
title: "GDM could not write to authorization file"
date: 2009-05-27
forum: General Help
---

### Post by fro1156 on 2009-05-27
Go to bottom of thread for problem!


Thanks













So I have been using my Xubuntu machine for 2-3 years now as my torrent machine.  While deluge has been great and i have not had to many problems with connecting to some torrent trackers, i have ran into a problem.  As the title says, when i try to log in i get the GDM error message.

I got into the shell and check my df -h and of course like all the other posts i have read though, it is 100% full.  So i begin to attempt to go though the rm -r/trash or similar commands and can't really get anything to delete.  :-x

So my problem is this, i can't remember/ type in the right command to delete something or anything to get it so i can look at the GUI to get this thing running again.  

What i am asking of this user community is a few suggestions to what command i can type in to maybe see what is in my home folder, or other folders so i can log in again!

thanks so much in advance, and i am sorry to bother you all with such an easy fix for most of you all!!

---

### Post by mikewhatever on 2009-05-27
Try the following two:
sudo apt-get clean
sudo apt-get autoremove

---

### Post by fro1156 on 2009-05-27
i knew this would happen, problem solved... IT removed 53 mb, just enough to get it started and i deleted 2.3 gigs but my Deluge client will not open now.  I might make a seperate post here, unless someone comes though here and knows the issue.

The problem is that i click on Deluge and it kinda loads (processor lights up) but no window appears..  Any ideas?

---

### Post by mikewhatever on 2009-05-28
Try running deluge from Terminal, the output might give a clue on the problem.

---

