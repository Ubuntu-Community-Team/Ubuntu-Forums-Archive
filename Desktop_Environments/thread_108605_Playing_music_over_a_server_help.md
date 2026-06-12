---
title: "Playing music over a server help"
date: 2005-12-26
forum: Desktop Environments
---

### Post by AceMilo on 2005-12-26
I am new to ubuntu and linux but have been playing with it for a little while, but am still having issues.  Obviously as a windows user for 15 years I am looking to make linux as familiar as possible and finding either replacements or ports of programs I use on windows and want a similar experience.

Anyway, one of my major issues right now is music.  I have my main pc running xp and a server running xp.  My server has a large hd with about 40 gigs of music on it that I mostly listen to on my main pc.  Using itunes or winamp, I can just play the files like as if they were on my local pc and they play just fine.  However, when I boot linux on my laptop, I cannot run the files.  If I just run the mp3 like I do in windows, it just won't play, but if I copy it to my desktop it will play just fine.  The windows server is just doing normal windows smb sharing and my ubuntu laptop can see the files and copy them fine, but if I try to play them over the server it just doesn't do anything.

How can I make it so that I can play my music over the server without copying it to my pc?  I have tried videos as well and the same thing happens.  Any help is appreciated.

TIA

---

### Post by sciurus on 2005-12-26
I'm confused; are you ever able to play the mp3 files from Ubuntu? If not, have you taken a look at the [restricted formats]("https://wiki.ubuntu.com/RestrictedFormats") wiki page?

---

### Post by AceMilo on 2005-12-26
Yes I am able to play mp3 files in general.  If the file is stored locally on my laptop the files will play absolutely perfect.  If I try to play them over the network off my server, they will not play.  For example, if I go on my windows pc and go to my network shares, then go to my mp3 shares, then double click an mp3, it will play fine.  If I go to windows shares, then my mp3 shares, and double click on an mp3 it will not play.  The same goes for videos.  If I drag the mp3 on my desktop and double click it it will play with no problems.

---

### Post by sciurus on 2005-12-27
Let me make sure I have this straight. You have three computers

A) Windows XP "server" sharing mp3 files using smb.
B) Windows XP destkop ("main pc").
C) Ubuntu laptop.

Computers A, B, and C are all able to play mp3 files stored locally. Computer B is also able to play mp3 files from Computer A. Computer C cannot play mp3 files from Computer A; however, Computer C can copy mp3 files from Computer A and then play them.

I tried to replicate your problem as best I could, but I can't make it occur. If I doubleclick an mp3 file on a remote windows share (smb://) in Nautilus it launches Totem and begins to play. Maybe you should try using smbfs.

---

### Post by AceMilo on 2005-12-28
Sciurus, you got it.  If you could, could you please tell me exactly what you do to make it work properly?

---

### Post by HermanAB on 2005-12-28
Have a look at this guide - scroll to the bottom:
[http://www.aerospacesoftware.com/ogg2mp3-howto.html](http://www.aerospacesoftware.com/ogg2mp3-howto.html)

It explains how to set up a simple Python based streaming music server.

Cheers,

Herman

---

### Post by AceMilo on 2005-12-28
Thx herman but thats not what I want.  I want to be able to control my music like as if it were stored locally like I do with my windows pc.  Any ideas?

---

### Post by tonderai on 2005-12-29
I can do this - as Scirius says I think you need to mount your network music drive using smbfs, instead of the default ubuntu setup (places>network servers). The way, to do this is described in [this thread]("http://www.ubuntuforums.org/showthread.php?t=26438").*

Although its a bit of a drag to setup, once done its pretty handy and more reliable. Plus, you can play music over it :D

*Instead of issuing the command to mount the drive everytime, you can put it in /etc/fstab and ask it to mount automatically onto your desktop (as described later in the thread I think). PM me if you need a hand.

---

### Post by AceMilo on 2005-12-29
tonderai, thank you for the link.  I don't know if this will solve it, but I am definitely going to try this in a minute.  I will let you know how it works.

---

### Post by AceMilo on 2005-12-29
I got smbfs installed but cannot mount any of my shares properly.  Can someone please give me some info on how to use the smbfs file system properly?

---

### Post by sciurus on 2005-12-29
[QUOTE=AceMilo]Can someone please give me some info on how to use the smbfs file system properly?[/QUOTE]

Did you read the manpage for smbmount?

---

### Post by AceMilo on 2005-12-30
[QUOTE=sciurus]Did you read the manpage for smbmount?[/QUOTE]

Your gonna have to tell me what that means.

---

### Post by Zwack on 2005-12-30
man pages are "manual pages" they are help pages if you prefer.

The command to read them is

man

so in this case, open a terminal and type

man smbmount

If it helps I can't find that page on my system...

Z.

---

### Post by tonderai on 2005-12-30
[QUOTE=AceMilo]I got smbfs installed but cannot mount any of my shares properly.  Can someone please give me some info on how to use the smbfs file system properly?[/QUOTE]

I have this set up between two ubuntus, so your situation is a little different, but this is what you can try on the ubuntu laptop. You may have to do some configuration on the XP server to create the proper 'smbuser' for your laptop to login with, but probably you can use your normal login.

1.) ```
sudo gedit /etc/samba/smb.conf
``` to edit your samba configuration making sure that the workgroup is the same as your XP network.

2.) ```
sudo /etc/init.d/samba restart
``` to restart samba with the new settings

3.) ```
sudo mkdir /media/music
``` to make a local directory for your share to be mounted in

4.) ```
sudo mount -t smbfs -o username=netusername,password=netpassword //XP-COMPUTER_NAME/xp-share-name /media/music/
``` to mount the xp samba share locally. Substitute netusername and netpassword with the details you use to login to your XP server, and XP-COMPUTER_NAME with the name of the server on the network (usually caps), and xp-share-name with the name of the shared folder.

If it succeeds there should be no output from the command line and you should get the folder mounted on your desktop (go to /media/music to make sure if it doesn't). Otherwise you would get an error message such as "Access Denied" or "Invalid share name" which would narrow your problem down further.

5.) To make things easier, or automate the mount - edit your /etc/fstab ```
sudo cp /etc/fstab /etc/fstab_backup 
sudo gedit /etc/fstab
```
Then add the line:
```
//XP-COMPUTER-NAME/xp-computer-share /media/music smbfs username=netusername,password=netpassword,nousers,auto 0 0

```
This should mount your share at startup automatically. A more secure method is to remove the password option, change 'auto' to 'noauto' and mount the share manually the following: (you should be prompted for the password)
```
sudo mount /media/music
```

Get back with any error messages ;)

---

### Post by AceMilo on 2005-12-30
tonderai, thx for the info, I will try it soon.  I just have 1 quick question.  What if my xp box has no password on the smb serve?  I have no username or pw for my windows box shares.  What do I put?  Just omit the variables in the command?

---

### Post by tonderai on 2005-12-31
To be honest, I'm not sure. I managed to network fine with win2k some time back, and then I used the default username='administrator', password=''. Surely XP has multiuser logins - but probably it is turned off by default. If you could enable that, then you could probably create a suitable login. 

Best thing is to try the mount command and see what it says.

---

### Post by pelle.k on 2006-01-06
It works flawlessly for me. But note that multiuser login for shares is default behaviour. You have to disable this in XP. I usully go for the "I understand the risks of sharing these files, and do not want to use the guide. Just enable file-sharing", and i think this is called "simple file sharing" in Windows 2000. Without it file sharing in Windows 2000 can be a real PITA nightmare.

---

