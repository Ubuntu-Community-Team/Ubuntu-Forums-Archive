---
title: "Configure samba without the command line?"
date: 2006-09-04
forum: Desktop Environments
---

### Post by ethridgt on 2006-09-04
Hello all,

I can easily configure samba using the command line.  I recently tried the "Shared Folders" option under "Administration".  I did this on a clean copy of Dapper.  It correctly prompted me to install either samba or nfs.  I chose Samba.  After it installed Samba, it displayed the dialog that I could use to define which folders to share.  I configured a folder and clicked the ok button.

However, after walking through these steps it wouldn't let me connect to the share using my existing username/password.  To get it to work I had to drop to a command line and add a user to samba's configuration using smbpasswd.  

I'm confused by this.  Did I do something wrong?  Do we really expect new users to just "know" to add a samba user?  This seems like a real usability problem.  Can somebody let me know if I made a mistake or the "Shared Folders" is just flawed?

-- tale

---

### Post by FIONEX on 2006-09-04
No, it's not necessary to have a username and password.  If you wish, there's a command to remove a username and password requirement!  I think it was -x or something!

---

### Post by almrking on 2006-09-04
I used SWAT to configure Samba. I don't think it comes as a default application installed with Ubuntu 6.06. It gives you a GUI for configuration.

---

### Post by ethridgt on 2006-09-05
Maybe I didn't make myself clear.  I couldn't access the share from another computer after configuring using only the graphical tools that shipped with Dapper.  I had to set a password before I could access the share.  I feel like the intent is that I should be able to configure everything without a command line.  

Is it possible to configure a fresh Dapper install to share a directory using samba with only the "Shared Folders" dialogs?

---

### Post by SeanHodges on 2006-09-05
I can confirm this issue, having just tried to configure windows sharing using just the Shared Folders utility shipped as standard with Ubuntu.

Permissions should be available in this utility, as it is nobody can access the shares you create.

Have you raised a bug request on launchpad, ethridgt?

---

### Post by SeanHodges on 2006-09-05
I would like to add two additional issues that I had (please correct me if I have missed something):

1. By default, the Shared Folders utility sets all of the shares to "browseable=no", forcing the user to type the entire path to the share (only printers are invisible at root of server in Network Places) Assuming that they are setting this up in a safe "home" environment (otherwise they probably wouldnt be using this tool!) this security precaution is probably not necessary and should be ON by default in my opinion.

2. When the user closes the utility, it should restart the samba service, to apply the changes (perhaps a Yes/No dialog to confirm the action). Otherwise the user will need to restart the service manually to achieve this (and they may not be aware of this).

Other than that, I was pretty impressed with the tool.

---

