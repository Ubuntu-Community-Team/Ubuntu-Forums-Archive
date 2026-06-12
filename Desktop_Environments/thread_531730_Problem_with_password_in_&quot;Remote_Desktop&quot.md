---
title: "Problem with password in &quot;Remote Desktop&quot;"
date: 2007-08-21
forum: Desktop Environments
---

### Post by respider on 2007-08-21
Hey, I'm setting the password in vino-preferences or System -> Preferences -> Remote Desktop

When I try to connect to the machine, all I get is wrong password, no matter what I put in the password field in vino-preferences...

I did check and recheck the password, tried small passwords, long passwords, etc.

I tried to remove the remote desktop conf file from .gconf and begin from the very start and I get the same error, take a look:

> pedro@capuntu:~$ vncviewer 127.0.0.1
VNC viewer version 3.3.7 - built Mar  8 2007 21:56:52
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.7 (viewer 3.3)
Password: 
VNC authentication failed
pedro@capuntu:~$ 

I get this error locally and remotelly.
Always using default ubuntu vncviewer (in my girlfriends house or university).
Always @ ubuntu 7.04

I'd appreciate any help, thanks in advance.
Sorry for bad english writting.

---

### Post by scrooge_74 on 2007-08-21
I can't help much there, but this [howto]("http://ubuntuforums.org/showthread.php?t=499431") was very usefull to get me a remote desktop working

---

### Post by respider on 2007-08-23
> **scrooge_74 said:**
> I can't help much there, but this [howto]("http://ubuntuforums.org/showthread.php?t=499431") was very usefull to get me a remote desktop working

thats not excactly what I need, but thank you anyway...

my problem is with "Remote Desktop" which I guess is vino-server...
problem with the password field.. If I remove the password I can connect without problem, but who would do that? :(

---

### Post by scrooge_74 on 2007-08-23
Maybe you can configure some sort of public/private key and wont need the password

---

### Post by Chudilo on 2007-08-23
I've got it working!

1) On the VNCViewer window (the first screen that comes up when you  start it) click on "Options..."
2) Select the Misc Tab.
3) Check the "Only use protocol version 3.3" check-box.
4) Hit OK

That's it.
In addition, I noticed that once I connected with a password successfully, I could use the newer protocol as well.

---

### Post by respider on 2007-08-23
> **Chudilo said:**
> I've got it working!

1) On the VNCViewer window (the first screen that comes up when you  start it) click on "Options..."
2) Select the Misc Tab.
3) Check the "Only use protocol version 3.3" check-box.
4) Hit OK

That's it.
In addition, I noticed that once I connected with a password successfully, I could use the newer protocol as well.

well I use vncviewer in another linux box, there is no "Option" button, but probably there is some parameter to use only 3.3 protocol, thanks for your help!
I'll try this later :):)

---

### Post by mavicus on 2007-08-27
Good information.
I'm curious to know if there is a way to make this configuration change from the command line, or by editing a file.

It would be handy to know for those who are unable to get to a remote desktop session and use gnome to make the changes, but are able to connect in through telnet or SSH etc...

UPDATE:
Doh! sorry I misunderstood the solution. Please disregard (or remove) this reply.

---

### Post by Cptn-Spaulding on 2007-11-13
Well I'm on Gutsy AMD64 on both machines and I'm having the same issue as the OP, either starting with the vncviewer command or with the Terminal Server Client app. I don't see any option either on the graphical front end or via command line parameters to change protocol version, any other idea out there?

---

### Post by iampad on 2008-01-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+s...no/+bug/141032](https://bugs.launchpad.net/ubuntu/+s...no/+bug/141032) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This solution from [https://bugs.launchpad.net/ubuntu/+s...no/+bug/141032]("https://bugs.launchpad.net/ubuntu/+s...no/+bug/141032") solved my problem, I hope it might help.

> 
Binary package hint: gconf

Under fully updated 7.0.4 (as of 9/19/07), changing your remote desktop password is problematic.

What does NOT work is to open the Remote Desktop preferences, change the password, and close. Even logging off and then back on doesn't correctly change it (it seems to change it to something, but not to what I set it to.

To successfully change the password, I had to:
Open remote desktop preferences
Clear the password (delete all characters), close
logout and then back in
Open remote desktop preferences again
Set the password to what I wanted it to be
close, logout, then log back in


---

### Post by patspam on 2008-06-25
I had the same problem. Similar solution to iampad, except that didn't need to logout/in. Just set password to blank, save & close. Then re-open, and set to your desired pass. Very annoying!

Patrick

---

