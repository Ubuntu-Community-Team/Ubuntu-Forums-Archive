---
title: "Mounting SSH folders through nautilus"
date: 2008-05-05
forum: Desktop Environments
---

### Post by zhark1 on 2008-05-05
Hello.

Since I've upgraded from Gutsy to Hardy I can no longer mount remote SSH folders through the built-in support in nautilus. Even sftp://server:port immediately gives the same connection denied error.

Anyone know how to fix this?

---

### Post by _Narcisse_ on 2008-05-05
Hi zhark,

Did you try with Menu -> Places -> Connect to server, then choose SSH in server type, and check add bookmark to have it ready in "Places" next time...

---

### Post by clint1010 on 2008-05-10
Hi, I am trying the same thing as zhark1 with no success

I can ssh to my server via a terminal no problem, but when I try Places=>connect to server, it creates a desktop link and puts the entry in the places menu, but I can't connect/browse this location with nautilus. Also, when I go through the "connect to server" method, it does not ask for a password? but it does when I use a terminal?

I must be missing something, please help

---

### Post by arddwyn on 2008-05-20
Has anyone found an answer to this question?
I used to have no problem connecting to the ssh server we keep in the house for our backups under Gutsy with Nautilus. I tried the "connect to server" option with the bookmark, but when it connects me i can see the folders in the server with  my files, but if I try to open a folder or a file gnome-panel freezes. If I try to access my ssh server through the created bookmark it says it can not connect to location "sftp://... etc".
Is there any way to revert the ssh functionality to the previous version on Gutsy or to fix this? 
Any help will be greatly appreciated.

---

### Post by jtrindle on 2008-05-20
Clint1010: Can you unmount the link on the desktop (right click, unmount) and try to reconnect? 

Did you say you wanted the password remembered forever?  If so, it might be in the keyring 

Applications->Accessories->Passwords and Encryption Keys->Passwords

and delete the key corresponding to the user:server.

Then try and reconnect your normal way.

arddwyn: Possibly try deleting the bookmark and recreating it?

---

### Post by arddwyn on 2008-05-20
I recreated the bookmark and deleted the password on the keyring to start fresh. I was able to connect from the newly created bookmark but still when I access the ssh folders even though I can see my folders I can't do anything. Just now looking at it with only firefox and the nautilus window open, my CPU was at 94% and it took 30 seconds between clicking on the main menu and when my options showed up. I tried opening another window with the files I wanted to copy to the server and Nautilus shut down. I am running Gutsy server edition on the other computer and never had a problem before the Hardy upgrade :(

---

### Post by jtrindle on 2008-05-21
what's the output of:

  top -n 1

? I'm curious about the first four lines.  Doesn't matter if you're trying to open a Samba share at the time or not.

---

### Post by sideshownick on 2008-05-22
After fresh install of Hardy (8.04) "connect to server" no longer works for ftp.  Same if I simply type [ftp://ftp.servername.com](ftp://ftp.servername.com) in nautilus' address bar.  I get the error:

Couldn't display "ftp://ftp.servername.com/"
Error: Invalid reply
Please select another viewer and try again.

Have never had this problem before, and the server(s) still accessible by other means.  This is a piece of basic functionality I expect to just work... anyone know what's going on?

---

### Post by Coombabah on 2008-05-24
I've been having the same problem but only with some servers (Solaris).
I installed kubuntu-desktop via Synaptic and selected KDE instead of gdm for my session.
My tests found that nautilus (under Gnome) has problems with some servers (Solaris) but dolphin (under KDE) doesn't.
I love the way you can have Gnome and KDE and just pick which one you want for the session at the login screen.
There may be simpler workarounds but switching to KDE is one way of getting sftp to work from the file manager again.

Edit: I just found out you can run KDE and Gnome simultaneously switching between Gnome and KDE using ctrl+alt+( F7 or F8 ) if you have plenty of RAM.
Also noticed you can just run Dolphin under Gnome :)

---

### Post by zhark1 on 2008-05-24
I just found out something, I've specified Port = 2002 in /etc/ssh/ssh_config, to make it easier to connect (w/console) to my own computers, which I'm running on that port. When connecting to my own computers, with ssh running on that port, it doesn't matter if I fill inn port in the connect dialog in gnome, but when I try to connect to others servers running on the standard port (22) it immediatly shows up with an error message. It seems the gnome client simply ignores the specified port, and connects to the default port in /etc/ssh/ssh_config.

BTW: I checked the gnome keyring beforehand, and it had no entries what so ever.

---

### Post by tlesaul2 on 2008-05-26
I'm running Hardy and I've tried mounting an ssh folder through Places > Connect to server and it seems to work just fine the first time it opens.  It opens the subdirectory I specified and puts a shortcut on my desktop just like it should.  When I close the file browser and click on the icon to reconnect to the remote directory it no longer opens the correct subdirectory.  It opens the root directory instead.  Is there any way to get the shortcut to continue to open the subdirectory instead of the root directory?  I know this was possible in Feisty, but I can't seem to figure it out anymore.  Any help would be appreciated.

---

### Post by ftmichael on 2008-06-26
See [http://ubuntuforums.org/showthread.php?t=554555](http://ubuntuforums.org/showthread.php?t=554555) for some advice about this.  It fixed the problem for me, but interestingly it didn't help on my boyfriend's computer at all, even though we have the same setup. Still trying to figure out what the issue is on his system.

Michael

---

### Post by vinichc on 2011-03-21
I had the same problem... this is a bug with sftp when ssh has some responses...
this FAQ solved my problem

[http://openssh.org/faq.html#2.9](http://openssh.org/faq.html#2.9)

---

