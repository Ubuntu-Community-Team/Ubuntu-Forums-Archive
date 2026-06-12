---
title: "Problems editing moprobe.d"
date: 2009-03-05
forum: General Help
---

### Post by Pepse3 on 2009-03-05
To begin with about a week ago I put some commands in modprobe.d and I forgot what I did to get them there.  Now I gotta get them out and re insert some different commands.  When I remove those commands (they are blacklist commands) I am asked what to save them as.  Would I mess things up If I said Modeprobe.d.old?

Pepse.

---

### Post by sgosnell on 2009-03-05
/etc/modprobe.d is a directory.  You need to edit the file(s) in that directory, because you can't edit a directory.

---

### Post by Pepse3 on 2009-03-06
Okay, here is how I got there:  in a konsole I did cd /etc .  Then typed mc (midnight commander), then scrolled down to /modprobe.d then hit F3 (view) then scrolled down to blacklist, hit F4 (edit).  Removed the items but I can't remove them as when I hit F2 (save) it wants me to Confirm Save File: blacklist .  I hit save and I get save as "enter filename" blacklist .  And I click OK and I get "cannot save file"  "dismiss", and I do.

Pepse.

---

### Post by adult swim on 2009-03-06
if you want to add things to your blacklist you can do like this
```
sudo nano /etc/modprobe.d/blacklist
``` then add ```
blacklist ndiswrapper
``` if you wanted to blacklist the ndiswrapper module.  to save you can hit ctrl+x and then hit y.

---

### Post by Pepse3 on 2009-03-06
Okay, that is something I need to know Later.  Right now I need to remove 5 items from /modprobe.d blacklist.

Pepse.

---

### Post by sgosnell on 2009-03-06
So do what Adult Swim told you.  In a terminal, type 
```
sudo nano /etc/modprobe.d/blacklist
```
That opens nano, a minimal text editor which will let you modify the blacklist file.  Put a # at the start of the lines you want to remove from being blacklisted (# indicates a comment, not read by the system).

---

### Post by Pepse3 on 2009-03-06
Well, nano is about like vim and to me that ain't good.  OKAY SO I went to nano with the command given and put a # in front of those that need to be idealt with  on boot.  Since I don't know the nuances of nano I had to go to session and click close, and Then I went back to see what happened and there are NO # in front of what I had to do.

@adult swim  What you showed for ndiswrapper  is an example, right?

Later, much later.  I am oughta here until Friday early PM.

Pepse.

---

### Post by Pepse3 on 2009-03-12
That opens nano, a minimal text editor which will let you modify the blacklist file. Put a # at the start of the lines you want to remove from being blacklisted (# indicates a comment, not read by the system).

  Okay, that's good as far as putting a # in front of what I need for modprobe.d , but I can't figure out HOW to save and exit.  BUT,  I assume I can do the same thing in midnight commander?  If so, the problem I have is editing.  First I go to Konsole and type "cd /etc/modprobe.d" then I do "mc".  Then once I'm in "mc" I go down to "blacklist" then hit F4 (edit) then scroll down to the 4 items I have to remove and it doesn't matter if I erase them or put a # in front, the big problem I have is trying to "F2" Save.  When doing that I get "confirm Save file: blacklist? "  I click "Save" and it goes to a screen of: Save as:  "enter file name: blacklist" and I click Okay and the error is Cannot Save file:  [Dismiss].  And I push enter (return) and it is still there so I just click the X in the upper right and say frigit.

  So, if anybody understands what I am trying to do and hopefully has a clue as how to amend this let me know 

  REMEMBER, I am a KUBUNTU user.

Pepse.

---

### Post by sgosnell on 2009-03-12
In nano, you use Ctrl-x to exit, then type 'y' for yes when prompted to save the file.  Gedit is a lot easier, but it doesn't exist in Kubuntu.  There should be a GUI editor, but I don't know what it is, probably Kedit.  You'll have to open it, or Midnight Commander, a lame app if I ever saw one, as root to be able to save anything.

---

### Post by Pepse3 on 2009-03-13
That's it.  It worked.  At least that part.  After doing what you gave I re checked it in midnight commander and the # are in front of what I had to put them in front of.  So, now supposedly on boot they will be ignored like I never put them there to begin with.  Of course now I gotta make changes somewhere in modprobe.d in order to hopefully get my DVB-S card to work in Linux.

Thank you sgosnell.

Pepse.

---

