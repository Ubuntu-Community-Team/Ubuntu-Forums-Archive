---
title: "Ubuntu usability - wpa and partition mapping"
date: 2006-01-09
forum: General Help
---

### Post by jomurmiranda on 2006-01-09
Gentlemen,
I am a believer of open source computing. Since the late 1990's, I have seen my friends use Linux, starting with Red Hat way back then. Ubuntu is the first distribution I've felt compelled to try because it responds to the needs of the user: it should be simple, i.e. Linux for human beings. Somehow, somewhere, I think that most forum help guides fail to recognize a simple truth: the terminal should never have to be opened in order to perform necessary tasks. I offer you two issues that have not been solved according to this belief, in the hope that this community can solve them:

1. Visibility and mapping of partitions: I have several partitions on my hard disk. Using System->Administration->Disks I can mount them. However, this is not permanent. I have to redo it every time I login. I know this can be done permanently using fstab, but this violates the no terminal rule.

2. WPA wireless support: I know this has been discussed ad nauseaum in the forums, and that presents it biggest flaw. The first solutions I read back in the WW days involved--wait for it--recompiling the source code. Now newer solutions involve configuring wpa_supplicant. I even know there is a wpa_gui interface, but strangely, it is not accesible with the Synaptic manager. I understand this is not a trivial problem, but I refuse to believe that at this point an elegant solution cannot be found.

Thanks for all your help, and I sincerely admire your effort and devotion to a noble cause.
Respectfully,
Oscar

---

### Post by zoiks on 2006-01-09
Some googling yields kfstab, but it doesn't appear to be in the main ubuntu repos.  I don't know, you might have some luck finding a .deb for it.

Or, try this: Right click the panel, choose "Add", select "Run Application".  Then, click the button that looks like gears, type "gksudo gedit /etc/fstab", make the necessary changes, save your work, and reboot.  No command line necessary!  Ain't life grand?

Care to volunteer your time to code these things you have such a firm belief in?  Principles are great, since they lead people to devote their time to stuff they believe in.  In any case, the reality is that right now, in Linux, the vast majority of people are going to have to hit the command line now and then.  Jeez, even in Windows I have to resort to a command line to do ping, nslookup, ipconfig, nbtstat -R, edit routes, do a FIXMBR (from a recovery console) and various other things.  And sometimes I even have to edit a text file like LMHOSTS or a batch file.

---

### Post by Thunk on 2006-01-09
I am not sure if this would qualify as "no terminal", but you can create a launcher on your desktop with the mounting command, then load it on startup using System-->Preferences-->Sessions, in the Startup Programs tab.

---

