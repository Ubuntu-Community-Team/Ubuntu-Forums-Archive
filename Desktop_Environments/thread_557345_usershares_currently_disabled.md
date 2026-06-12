---
title: "usershares currently disabled"
date: 2007-09-22
forum: Desktop Environments
---

### Post by MacDuff on 2007-09-22
Using Ubuntu 7.04 with the Nautilus desktop, when I right click on a folder with the intention of sharing it, the option menu gives me two choices:
First is called "Sharing Options" and the second is called: Share Folder.
The seond option (Share Folder)  was not there when I first installed Ubuntu but I had problems with file sharing and eventually downloaded everything I could find in the repositories  that seemed to be a tool for Ubuntu to handle directory/file sharing.  So now I have the second (first in menu hierarchy) choice.

When I click this option (Sharing Options), I get an input window in which I can check "Share this folder" and I can enter a share name.  There is another checkbox "Allow other people to write in this folder"  When I check the boxes and attempt to use the button [Create Share] I get a message "'net usershare'  returned an error 255:netusershare:usershares are currently disabled"

What do I have to do to enable usershares? Or is this application not necessary and if it is not necessary, what do I look for in the Synaptic Package manager to remove the extraneous option?

Thanks

---

### Post by dmontalvao on 2007-10-30
I have the same problem. I am only bumping your thread. Did u find a solution?

Thanks!

---

### Post by pndragon on 2007-11-16
This is what worked for me.

In a terminal:
```
sudo mkdir /usr/local/samba/lib/usershares
sudo chgrp *yourusername* /usr/local/samba/lib/usershares
sudo chmod 1770 /usr/local/samba/lib/usershares
```
Then add these parameters> usershare path = /usr/local/samba/lib/usershares
usershare max shares = 10 # (or the desired number of shares) to the global section of your smb.conf.

All of these instructions are on the smb.conf manpage

Works like a charm!

---

### Post by RenegadeGopher on 2008-03-27
I had this same problem, however when i tried the instructions on the manpage, (identical to the ones above), rebooted, i got nothing.

 Anytime I try to share a folder, "net usershare:  usershares are currently disabled"

I also have a problem finding the network printer(HP photosmart 7550) in samba... ive tried getting it through cups/smb, however no matter what i do, it can't connect. However, i know it's connected as 3 other comps (one with OSX, and two with windows), see it.


i've tried removing/reinstalling samba before, thinking maybe i just F'd with teh settings a little too much, still no avail. :(

---

### Post by mtopro on 2008-04-26
> **MacDuff said:**
> Using Ubuntu 7.04 with the Nautilus desktop, when I right click on a folder with the intention of sharing it, the option menu gives me two choices:
First is called "Sharing Options" and the second is called: Share Folder.
The seond option (Share Folder)  was not there when I first installed Ubuntu 

> 
net usershare'  returned an error 255:netusershare:usershares are currently disabled"


pndragon's post didn't work for me, and you may have already found the fix..  But I wanted to post just in case someone else out there has the same problem.  I spent hours trying to find which file was causing the added second option in Ubuntu 7.10. It was preventing network folder share no matter which user was logged in.:confused:

The fix?  Try uninstalled package for 'nautilus-share' then reboot.:)

---

