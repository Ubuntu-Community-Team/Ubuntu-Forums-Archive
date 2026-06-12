---
title: "A problem with permissions?"
date: 2006-04-13
forum: Desktop Environments
---

### Post by Rhapsody on 2006-04-13
After much preparation, I've finally got Kubuntu installed now. Aside from a few niggles, it seems to be working fine.

My only serious problem is my Speedtouch ADSL MODEM. After consulting a [helpful page](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html) I've managed to get the firmware working, but I'm still not online. The problem seems to be with certain files that the proceedure there tells me to create like pap-secrets, chap-secrets, speedtch, and dial. I've created the files in my home folder and copied them over to where they're needed (using the commands on that page) but the copied versions of the files are totally blank!

From what I've gathered, this is a problem with permissions. The commands appear to work fine, but the files continue to be blank and any attempt to edit them results in an 'Access Denied' error. Any attempt to edit the folder permissions results in exactly the same error.

What's going on here? I've followed the instructions as closely as I can, but nothing about this sort of problem was noted. Why can't I edit these files?

---

### Post by UbuntuJohan on 2006-04-13
Try to use sudo before the copy command then they will be copied by root.
That is usually needed for system files like these.
e.g.
sudo cp /home/user/file /etc/system/
This will copy the file file to /etc/system/ and give it root permissions.

Try this if it doesn't help I need some more details to be able to help you.

Cheers
//Johan

---

### Post by Rhapsody on 2006-04-13
[QUOTE=UbuntuJohan]Try to use sudo before the copy command then they will be copied by root.
That is usually needed for system files like these.
e.g.
sudo cp /home/user/file /etc/system/
This will copy the file file to /etc/system/ and give it root permissions.[/QUOTE]
From looking at the commands, they all appear to use sudo. Like "sudo install -m 600 speedtch /etc/ppp/peers". I try the command, it asks for my password, I give it, but the resulting file is blank! The one in home has the required data, but the one I see in /etc/ppp/peers has nothing in it!

[QUOTE=UbuntuJohan]Try this if it doesn't help I need some more details to be able to help you.[/QUOTE]
What kind of a details? I only installed Kubuntu earlier today, so I don't really know what kind of details would help with this.

---

### Post by xenmax on 2006-04-13
if sudo does not allow you to edit files, then perhaps your account does not have admin privileges?
What is output of groups command? Check if it contains group "admin".
Also, but did you perform an expert install by any chance?

---

### Post by Rhapsody on 2006-04-13
[QUOTE=xenmax]if sudo does not allow you to edit files, then perhaps your account does not have admin privileges?[/QUOTE]
I wasn't using sudo to edit the files, I just took a look at them with Kate. As far as I can tell, there's nothing in them. Files in the same folders have data in them, but the files I've copied over are blank.

[QUOTE=xenmax]What is output of groups command? Check if it contains group "admin".[/QUOTE]
I'll have to reboot to try that, since I'm typing this from within Windows.

Edit: Yep, found "admin" right on the end of a rather large string of words.

[QUOTE=xenmax]Also, but did you perform an expert install by any chance?[/QUOTE]
I'm pretty sure I didn't. I was told it was unneccessary.

---

### Post by UbuntuJohan on 2006-04-13
Sorry I should have read the link before making my last post!

If we take the command 
```
sudo install -m 600 speedtch /etc/ppp/peers
```
Which is one that you get problems with, right?

I have never used the install command myself. but from what I understand you can acheive the same thing with 

```
sudo cp speedtch /etc/ppp/peers/
sudo chmod 600 /etc/ppp/peers/speedtch
```

That is what I usually do. You could try that and see if it makes any difference.

But I think that you see the file as a empty file because only root has read access to /etc/ppp/peers/
Also the permisson setting 600 in the install command will cause that only the owner (in this case root) will be able to do anything with the file.

So if you instead do (just make sure that you are in your home directory)
```
ls -l speedtch 
```
and compare the output with what you get with
```
sudo ls -l /etc/ppp/peers/speedtch 
```

The printouts should have the same size.

Here is an example for annother file in the same directory.
```
mythtv@myth:~$ sudo ls -l /etc/ppp/peers/provider 
-rw-r-----  1 root dip 1093 2006-03-24 20:21 /etc/ppp/peers/provider

```
The size of this file is 1093.
If the sizes match then you have the same content in the files.

Annother way to check that you have content in the file is 
```
sudo more /etc/ppp/peers/speedtch 
```

The details I was after was ls -l or sudo ls -l of the files.

I hope this is of more help to you than my last post ;) 

Cheers
//Johan

---

### Post by Rhapsody on 2006-04-13
OK, I'll have to reboot again to try all that. But this seems like a promising lead.

Edit: Now typing this into Konqueror from within Kubuntu. The problem? A slight typo in my speedtch file. I left two apostrophies at the end of my username rather than one. Fixing the made it all work.

---

