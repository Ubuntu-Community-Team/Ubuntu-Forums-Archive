---
title: "Gnome-Pilot File Upload via shell or java?"
date: 2009-05-27
forum: General Help
---

### Post by celem on 2009-05-27
I can upload a file to my Palm by dropping it onto the panel sync applet but I would like to have a way to do this in a shell script or, better yet, in java. I keep my passwords in the Palm in the Keyring for Palm program (v5 database) and use the KeyringEditor java program on my Ubuntu desktop. I want to be able to edit passwords in either place and cause them to sync even though there is no conduit.

When I change a password on the Palm, it backups the file Keys-Gtkr.pdb to the desktop and KeyringEditor sees the updated Keys-Gtkr.pdb file. If I change a password on the desktop with KeyringEditor the Keys-Gtkr.pdb file is updated but not uploaded to the Palm unless I drop it onto the panel sync applet before a sync. My ultimate goal is to modify the java program KeyringEditor to cause the updated Keys-Gtkr.pdb file to be queued for upload with the next sync.

Any ideas would be appreciated!

P.S.: I use Jaunty AMD64.

---

### Post by jamesstansell on 2009-05-28
Since it sounds like you know how to program you might want to bring this question up in the programming forum.

Also, [http://www.jsyncmanager.org/](http://www.jsyncmanager.org/) may be of interest to you.  I'm not why, but I'm not seeing any recent activity on that project.  I think there are also similar projects out there.

---

### Post by celem on 2009-05-28
jamesstansell, thank you for pointing out the jSyncManager project. I will examine it for clues on how to accomplish my mission. 

Regarding jSyncManager's inactivity, it is probably related to the diminished interest in Palm platforms. It seems that, currently, most people want their cellular telephone to include their Palm-type functionality as well as portable internet. I am more of a one tool per job kind of guy so I still use a Palm daily. There are still plenty of standalone Palm users around - just less than there used to be.

---

### Post by celem on 2009-05-28
The following command causes an upload of the keypass database upon the next sync. I will eventually code it into the keypasseditor.

gpilot-install-file --later /home/*username*/.palm/Keys-Gtkr.pdb

---

