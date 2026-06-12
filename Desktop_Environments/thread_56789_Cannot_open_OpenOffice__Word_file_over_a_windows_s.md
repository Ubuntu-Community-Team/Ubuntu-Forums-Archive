---
title: "Cannot open OpenOffice / Word file over a windows share"
date: 2005-08-14
forum: Desktop Environments
---

### Post by freeman on 2005-08-14
Hi,

I have few machines running Windows XP with OpenOffice. 

I have just installed ubuntu linux on a old machine lying around which was previously running NT4 Workstation.

We are using windows style file sharing across the network.

I cannnot open OpenOffice files over a network windows share (Microsoft file and print sharing) in ubuntu. I have to copy the file to local harddisk before opening it.

When I double click on the file over a network, open office starts but it shows nothing and the heading is untitled2.

Although a text files opens perfectly in gedit across a network, none of the word, excel files open over the network in ubuntu.

Any ideas ?

We are just testing out Linux and to make use of very old boxes lying around in our office. So far the experience has been challenging but its a nice way to learn !! I have already shifted my home desktop to ubuntu and enjoying it. Gosh ! I havent used a antivirus, firewall, anti spam what not in some time  \\:D/

---

### Post by bdamon on 2005-08-14
[QUOTE=freeman]Hi,
I cannnot open OpenOffice files over a network windows share (Microsoft file and print sharing) in ubuntu. I have to copy the file to local harddisk before opening it.

Although a text files opens perfectly in gedit across a network, none of the word, excel files open over the network in ubuntu.
[/QUOTE]


Are you mounting the share? You will have to actually mount the share before you can  edit the files in OO. I think you will also find that even though Gedit opens files they are read only. This has something to do between Gnome VFS and the applications.

---

### Post by ps- on 2006-09-18
This is not the solution most people are looking for. There is a much better one .. I do not understand why they did not change it already for dapper. For me, its a bug in the openoffice packages.

It is no solution to mount smb shares in the filesystem - its painful if you are using a notebook in several network locations.

I just had the same problem because of a new installation. After some searching I could not get the right answer .. but I remembered the solution - so posting here for others (and me if I will have the problem again ^^):

Look at your MIME settings in konqueror. There you will find that openoffice documents are set like:

"ooffice -writer %U"

if you change that to

"ooffice -writer **%f**"

the file will be copied to a temp directory before its opened. If it changes, konqueror is smart enough to ask if it should upload the new version.

---

### Post by Mujaheiden on 2007-03-29
Where do I alter these mime settings in gnome? Is there different settings for network files and local files?

I have this small Preferred Applications tool in my System > Preferences, but there soo little there, that it really doesnt make any sense.

---

