---
title: "How do I handle upgrading a current program?"
date: 2009-06-19
forum: General Help
---

### Post by harecanada on 2009-06-19
Hi.
I'm using a music player called Songbird. It resides at Applications>Sound and Video. Now I got an e-mail telling me there is an upgrade to a new version. I click on the link and go to the site. Download the Linux version. It downloads to my desktop as Songbird_1.2.0-1146_linux-x86_64.tar.gz (I'm not very good with .tar.gz files) 
So I right click it and extract it to my Desktop. Now I have a folder that says Songbird. I open it and of course it has a lot of stuff in it. There is an icon that says Songbird so I click on it and it opens the program. I checked the version and it is the upgraded version, and it works. Now my questions are: 
1] Why do I have two versions of Songbird one in Applications and one in the folder on my Desktop? 
2] How do I get rid of the older version in Applications and replace it with the newer version? 
3] How do I get a shortcut on my Desktop to the new version of Songbird. 
Can someone help me out on this?
Thanks,
harecanada

---

### Post by jonobr on 2009-06-19
Hello

Im not familiar with songbird and cant answer all your questions but it sounds like its an app that does not check to see if its already installed.

In the uncompressed archive, there should be some file that says README or something of that nature.
If you read it, maybe it mentions you need to uncompress and run in a certain location?

A shortcut on your desktop can be done by creating a sympbolic link

This is done using the ln -s ~/Destkop/link ~/music/mysmusic command.

if you type man ln on the terminal it will give you exammples.

You should see a new icon on your desktop which when you enter it, now takes you to the ~/music/mysmusic  directory.

To remove the symbolic link (if your testing it) just remove it using delete.
It will only delete the sim link, not the target directory

---

