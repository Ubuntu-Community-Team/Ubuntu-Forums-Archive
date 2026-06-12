---
title: "Desktop leftovers..."
date: 2009-01-02
forum: General Help
---

### Post by Shiv4m on 2009-01-02
I have realized this for awhile but was to lazy to post here on how to get rid of it. If you look at the screen shot below you will see files with an ending ~, I want to know how to remove those files because they are not on my desktop. Screen shot of the ~ files:

[[IMG]http://img48.imageshack.us/img48/3123/screenshotfileuploaduu4.png[/IMG]](http://imageshack.us)
[[IMG]http://img48.imageshack.us/img48/screenshotfileuploaduu4.png/1/w802.png[/IMG]](http://g.imageshack.us/img48/screenshotfileuploaduu4.png/1/)

_**ANOTHER QUESTION PLEASE!**_
I want to share files with my computers in my network. How can I do this I have an XP Pro and Ubuntu.

---

### Post by iPodVision on 2009-01-02
CLick on it then click remove..?

---

### Post by jerome1232 on 2009-01-02
Those are backups. Whenever gedit or vim save a file (possibly other text editors), they make a copy of the old version and tack a ~ to the end of it, you can't see them unless you are viewing hidden folders in your file manager.

If you want to delete them just delete them like you would any other file but unless you turn off the backup feature in gedit or vim (or whatever text editor is is you use) they will keep coming back.

---

### Post by Shiv4m on 2009-01-02
Thanks for explaining to me what they are jerome1232 +rep :D

Have any idea on folder sharing with my other computers?

---

### Post by oldos2er on 2009-01-02
"I want to know how to remove those files because they are not on my desktop."

 You can prevent gedit from automatically creating backup copies of files you edit by clicking (within gedit) Edit, Preferences, Editor, and unchecking the box in front of 'Create a backup copy of files.'

 I think it's a handy feature tho'.

---

### Post by jerome1232 on 2009-01-02
Didn't even see that question :)

Well since your sharing with a windows computer I would probably use samba.

If your using gnome the easy way to turn this on is Navigate to a folder you would like to share, then right click it, click "sharing options", check "share this folder", hit "modify share". You should be prompted to isntall some software then restart your session. Log back in and repeat the process (the service get's installed but the folder didn't actually get shared)

Now the folder should be browsable from your xp box under network places.

---

### Post by Shiv4m on 2009-01-02
> **jerome1232 said:**
> Didn't even see that question :)

Well since your sharing with a windows computer I would probably use samba.

If your using gnome the easy way to turn this on is Navigate to a folder you would like to share, then right click it, click "sharing options", check "share this folder", hit "modify share". You should be prompted to isntall some software then restart your session. Log back in and repeat the process (the service get's installed but the folder didn't actually get shared)

Now the folder should be browsable from your xp box under network places.

How would I view the XP's files? In Network I only see my sister's PC which is connected through WiFi, how can I check a computer that has an ethernet cable?

---

### Post by jerome1232 on 2009-01-02
> **Shiv4m said:**
> How would I view the XP's files? In Network I only see my sister's PC which is connected through WiFi, how can I check a computer that has an ethernet cable?

You have to turn on file sharing on the Widnows box you wish to connect to. (it's done through a similiar process if I remember correctly actually) If you use a host based firewall (like norton, mcafee) you will also have to configure the firewall to allow traffic on that port, or trust computers on the lan.

---

### Post by Shiv4m on 2009-01-02
I got it all done thanks a lot!

---

