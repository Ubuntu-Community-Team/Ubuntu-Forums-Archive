---
title: "SweetHome3D - simple, easy CAD type application"
date: 2009-06-19
forum: General Help
---

### Post by charonred on 2009-06-19
SweetHome3D is a great little 3D Home Design CAD application for anyone that want's to do some home room/addition design and furniture layouts etc.

It's Java based and platform independent; so it will run on Linux, Mac or Windows. 

I've only just found it and thought I'd post a step-by-step guide how to get it working on Ubuntu &#8211; I have Hardy 8.04.2 but it should be the same procedure on Intrepid and Jaunty.

First download current version 2.0 from here to your desktop;
[http://sourceforge.net/project/downloading.php?group_id=152568&filename=SweetHome3D-2.0-linux-x86.tgz]("http://sourceforge.net/project/downloading.php?group_id=152568&filename=SweetHome3D-2.0-linux-x86.tgz")



As the downloaded file is a '.tgz' file, you'll need to extract it using Terminal, so open a Terminal window
 >Applications > Accessories > Terminal

first make a directory to extract the .tgz file to
```
mkdir /home/username/tarsrc/
```
(where '[COLOR="Blue"]username[/COLOR]' is your login username, and '[COLOR="Blue"]tarsrc[/COLOR]' was what I named my folder for extracting tarballs to)



Leaving terminal for a moment; I then opened my Home folder, then the tarsrc folder 
> Places > Home > tarsrc

I then dragged the 'SweetHome3D-2.0-linux-x86.tgz' tarball from my desktop into the tarsrc folder.



Then back in Terminal I changed to that directory.
```
cd /home/username/tarsrc/
```


After changing directory in terminal, I checked that the tarball was there.
```
ls
```
(listed the tarball as [COLOR="Blue"]SweetHome3D-2.0-linux-x86.tgz[/COLOR])



Then I ran this command to extract it.
```
tar -zxvf SweetHome3D-2.0-linux-x86.tgz
```

(This created a new directory with the relevant files inside it - [COLOR="Blue"]SweetHome3D-2.0[/COLOR])



I then closed Terminal and opened the SweetHome3D-2.0 folder 
> Places > Home > tarsrc >  SweetHome3D-2.0

next, locate the 'SweetHome3D' file and right click on it, select 'Make Link', then drag the link to your desktop for convenience.

To run this successfully, if you have Desktop Effects enabled, you need to disable it - right click the desktop, select 'Change Desktop Background', then go to 'Visual Effect' tab and change settings to 'None'.

Go back to your desktop and click the 'Link to SweetHome3D' &#8230; have fun.

ps - don't forget to re-enable Desktop Effects when finished using SweetHome3D

---

### Post by Yaka on 2009-08-01
thanks for this, my dad sells and installs kitchens and says this is way better than  the £2000 program he uses to design and layout kitchens for his customers

---

### Post by charonred on 2009-08-01
glad post helped; I haven't used the program much myself, but my brother (who is a bit of a technophobe), reckons it's great -  he's using it to design his new garage and music room; and I'm impressed with the detail he's gone too (even made a drum kit).

---

