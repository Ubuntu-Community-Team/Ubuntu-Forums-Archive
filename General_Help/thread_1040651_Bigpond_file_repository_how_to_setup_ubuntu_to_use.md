---
title: "Bigpond file repository how to setup ubuntu to use?"
date: 2009-01-15
forum: General Help
---

### Post by joewski on 2009-01-15
My ISP (Internet service provider) have set up a number of repositories at [http://mirror.files.bigpond.com/](http://mirror.files.bigpond.com/) for various linux distros including Ubuntu. The ISP's been pretty quite about linux and only saw this link in a tiny post in the new files forum.

The actual ubuntu repositories are setup here

[http://mirror.files.bigpond.com/ubuntu/](http://mirror.files.bigpond.com/ubuntu/)

Ubuntu isn't setup out of the box to take advantage of this repository so I was wondering if somebody with experience could me by explaining how to configure Ubuntu to take advantage of this repository. 

I don't want to kill my Ubuntu update by playing with the setting in the Software sources without some clue as to what I need to do.

Thanks.

---

### Post by blazemore on 2009-01-15
Could you please run
```
sudo cat /etc/apt/sources.list
```

And paste the output here in [code ] tags? Thanks.

---

### Post by drs305 on 2009-01-15
Here are the links to the ubuntu documentation on repostitories. The first is for gui and the second for command line. Both have sections for adding repositories.

[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

[https://help.ubuntu.com/community/Repositories/CommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine")

I recently updated one of them. If you have questions just come back and ask.

---

### Post by mdurham on 2009-01-15
> **joewski said:**
> My ISP (Internet service provider) have set up a number of repositories at [http://mirror.files.bigpond.com/](http://mirror.files.bigpond.com/) for various linux distros including Ubuntu. The ISP's been pretty quite about linux and only saw this link in a tiny post in the new files forum.

The actual ubuntu repositories are setup here

[http://mirror.files.bigpond.com/ubuntu/](http://mirror.files.bigpond.com/ubuntu/)

Ubuntu isn't setup out of the box to take advantage of this repository so I was wondering if somebody with experience could me by explaining how to configure Ubuntu to take advantage of this repository. 

I don't want to kill my Ubuntu update by playing with the setting in the Software sources without some clue as to what I need to do.

Thanks.
The files are just for downloading. After downloading what you do with it is up to you. If you download an iso,  obviously you must burn it to a CD/DVD. What you do depends on the type of file that you downloaded.
Which file(s) do you want?
Cheers, Mike (Bigpond user!)

Edit: Sorry joewski, I didn't realise that you were talking about a mirror. Ignore what I just wrote.

---

### Post by joewski on 2009-01-15
> **blazemore said:**
> Could you please run
```
sudo cat /etc/apt/sources.list
```

And paste the output here in [code ] tags? Thanks.

Here is the listing.
Thanks for your help I can sort of see how it works just from this file.
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030)]/ intrepid main restricted
deb http://au.archive.ubuntu.com/ubuntu/ intrepid main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ intrepid-security universe main multiverse restricted
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-updates universe main multiverse restricted
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-proposed universe main multiverse restricted

deb cdrom:[Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main multiverse restricted universe
deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030)]/ intrepid main restricted

```

I presume I just insert something like 
deb [http://mirror.files.bigpond.com/ubuntu/](http://mirror.files.bigpond.com/ubuntu/)

But what with the spaces in the text. Is this text pointing to files or something?

---

### Post by blazemore on 2009-01-15
You're exactly right :)
Rather than using an exact HTTP reference, it uses a different way of telling the server what folder to use (dists/intrepid-proposed, etc)
You'd have to go through and change all the "canonical" references to the one in question.
However, if you go to Administration -> Software Sources -> Download from -> Other, is the server on that list?

---

### Post by joewski on 2009-01-15
Ok I think I got it to work, adding this line to third party addons in the software sources

```
deb http://mirror.files.bigpond.com/ubuntu intrepid main multiverse restricted universe
```

I assume that I would need to add the other bits too ie
intrepid-backports
intrepid-proposed
intrepid-security
intrepid-updates

In a similar style.

Now do I need to disable all the other sources ie Cononical, community etc. or is ubuntu smart enough to get the files from the bigpond mirror repositories first?

---

### Post by joewski on 2009-01-15
```
deb http://mirror.files.bigpond.com/ubuntu intrepid main multiverse restricted universe

deb http://mirror.files.bigpond.com/ubuntu intrepid-backports main multiverse restricted universe


deb http://mirror.files.bigpond.com/ubuntu intrepid-proposed main multiverse restricted universe

deb http://mirror.files.bigpond.com/ubuntu intrepid-security main multiverse restricted universe

deb http://mirror.files.bigpond.com/ubuntu intrepid-updates main multiverse restricted universe


```

Ok I've tested the above lines and it works sweet. You also need to disable all the other other software sources.

It now means I can fully load and test all sorts of apps in Ubuntu.

Note if you don't want to be testing proposed software leave out the line with intrepid-proposed.

Here is a directory listing of repositories

```

dapper/	2008-Dec-17 03:19:19	-  	Directory
dapper-backports/	2008-Nov-12 18:00:28	-  	Directory
dapper-proposed/	2008-Nov-12 18:00:28	-  	Directory
dapper-security/	2008-Nov-12 18:00:28	-  	Directory
dapper-updates/	2008-Nov-12 18:00:28	-  	Directory
feisty-backports/	2008-Nov-12 18:00:28	-  	Directory
feisty-proposed/	2008-Nov-12 18:00:28	-  	Directory
feisty-security/	2008-Nov-12 18:00:28	-  	Directory
feisty-updates/	2008-Nov-12 18:00:28	-  	Directory
gutsy/	2008-Nov-12 18:00:28	-  	Directory
gutsy-backports/	2008-Nov-12 16:13:35	-  	Directory
gutsy-proposed/	2009-Jan-10 17:38:42	-  	Directory
gutsy-security/	2008-Nov-12 18:00:28	-  	Directory
gutsy-updates/	2008-Nov-12 18:00:28	-  	Directory
hardy/	2008-Nov-12 18:00:28	-  	Directory
hardy-backports/	2008-Nov-12 18:00:28	-  	Directory
hardy-proposed/	2008-Nov-12 18:00:28	-  	Directory
hardy-security/	2008-Nov-12 18:00:28	-  	Directory
hardy-updates/	2008-Nov-12 18:00:28	-  	Directory
intrepid/	2008-Nov-12 18:00:28	-  	Directory
intrepid-backports/	2009-Jan-15 17:42:51	-  	Directory
intrepid-proposed/	2008-Nov-22 16:17:11	-  	Directory
intrepid-security/	2008-Nov-26 16:15:40	-  	Directory
intrepid-updates/	2008-Nov-13 16:32:24	-  	Directory
jaunty/	2008-Nov-12 16:13:01	-  	Directory
jaunty-backports/	2008-Nov-12 18:00:28	-  	Directory
jaunty-proposed/	2008-Nov-12 18:00:28	-  	Directory
jaunty-security/	2008-Nov-12 18:00:28	-  	Directory
jaunty-updates/	2008-Nov-12 18:00:28	-  	Direct

```

I hope this is of some assistance to other Bigpond users.

---

### Post by blazemore on 2009-01-16
I use Virgin Media, their repo is in the Software Sources tool.

---

### Post by swampy5 on 2009-02-22
[QUOTE=joewski;6556323]```
deb http://mirror.files.bigpond.com/ubuntu intrepid main multiverse restricted universe

deb http://mirror.files.bigpond.com/ubuntu intrepid-backports main multiverse restricted universe


deb http://mirror.files.bigpond.com/ubuntu intrepid-proposed main multiverse restricted universe

deb http://mirror.files.bigpond.com/ubuntu intrepid-security main multiverse restricted universe

deb http://mirror.files.bigpond.com/ubuntu intrepid-updates main multiverse restricted universe


```

Thanks for the hints on how to enable the bigpond Intrepid repository
Here is a listing of sources.list on my intrepid machine configured for bigpond repositories

deb [http://mirror.files.bigpond.com/ubuntu/](http://mirror.files.bigpond.com/ubuntu/) intrepid main multiverse restricted universe 

deb [http://mirror.files.bigpond.com/ubuntu](http://mirror.files.bigpond.com/ubuntu) intrepid-backports main multiverse restricted universe 

deb [http://mirror.files.bigpond.com/ubuntu](http://mirror.files.bigpond.com/ubuntu) intrepid-proposed main multiverse restricted universe 

deb [http://mirror.files.bigpond.com/ubuntu](http://mirror.files.bigpond.com/ubuntu) intrepid-security main multiverse restricted universe 

deb [http://mirror.files.bigpond.com/ubuntu](http://mirror.files.bigpond.com/ubuntu) intrepid-updates main multiverse restricted universe

But running apt-get update returns this error message
 Failed to fetch [http://mirror.files.bigpond.com/ubuntu/dists/intrepid/Release](http://mirror.files.bigpond.com/ubuntu/dists/intrepid/Release)  Unable to find expected entry  deb/binary-i386/Packages in Meta-index file (malformed Release file?)

Any ideas how to resolve this?

After changing the sources.list on a couple of other ubuntu Intrepid installations I found the problem which was caused by an extra forward slash after ubuntu in the first line - removed that and the error message disappeared

---

### Post by joewski on 2009-03-06
> **swampy5 said:**
> 
But running apt-get update returns this error message
 Failed to fetch [http://mirror.files.bigpond.com/ubuntu/dists/intrepid/Release](http://mirror.files.bigpond.com/ubuntu/dists/intrepid/Release)  Unable to find expected entry  deb/binary-i386/Packages in Meta-index file (malformed Release file?)

Any ideas how to resolve this?


I found the Bigpond.com repositories had missing files sometimes, I just check the original repositories on in the software sources and Ubuntu seems to find the missing files and using the update manager. Then I un-check them again. It's simple and works. Overall this keeps the download usage to a minimum.

---

### Post by Herman on 2009-03-07
:D Hey Joe! (and others), I'm happy to be able to discuss this with someone else who's interested.

Can you take a look in the following link and let me know if it looks okay to you, [COLOR=#000066]**[Bigpond sources.list]("http://users.bigpond.net.au/hermanzone/p5.htm#Bigpond_sources.list")**[/COLOR]?

Of course, if you have Intrepid Ibex, yours would be a bit different, that one in the link's for Hardy, because it's the LTS (Long Term Support) release.

I noticed that sometimes there are a few hiccups with it too, from time to time, so I also try to get all the updates and install what software I can from bigpond first, then if there are errors, I revert to the original /etc/apt/sources.list file which I keep a backup copy of.

I made a backup of my original file and named it /etc/apt/sources.list.original, ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.original
```and then I modified my sources.list with the Bigpond repositories, and made a backup copy of that one called /etc/apt/sources.list.bigpond, ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bigpond
```
I was just restoring either one with a cp command whenever the need arose,
```
sudo cp /etc/apt/sources.list.original /etc/apt/sources.list
```or the opposite,
```
sudo cp /etc/apt/sources.list.bigpond /etc/apt/sources.list
```That's how I was doing mine for quite some time. :D

---

### Post by Herman on 2009-03-07
A friend of mine who's not so good with the command line visited me the other day and complained about the hiccups with the bigpond mirror site and asked if there was an easier way to do this, (switch sources.list files), so I fixed it for him and it worked so well I am now setting my own computers up the same way.  :)

Here's what I did,

1. I made two icons using the Gnu Image Manipulation Program, (see attachments to this post). 

2. I copied my icons to /usr/share/icons/
```
sudo cp switchsourcesback128.png switchsources128.png /usr/share/icons/ 
```3. I made two scripts that will restore either sources.list file and then run apt-get update and apt-get upgrade.
Here are my two scripts, (they're very simple)
```
#!/bin/bash
# switch sources to original ubuntu sources list
sudo cp /etc/apt/sources.list.original /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade
``````
#!/bin/bash
# switch sources to bigpond
sudo cp /etc/apt/sources.list.bigpond /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade

```4. I right-clicked 'Applications' and clicked 'Edit Menus'.
A window titled 'Main Menu' opened.
There are two panes in the 'Main Menu' window, in the right hand side are '_M_enus', and to the right are '_I_tems'.

5. In the '_M_enus' pane, I selected  'Programming', (or whatever you like), and to the left of the 'Items' pane. I clicked the button called '+ Ne_w_ Item'. 

6. A 'Create Launcher' box appeared in front of the 'Main Menu' window.
(i) I set the 'Type' spinbox to 'Application in Terminal'
(ii) In the 'Name' field, I typed in the title I want to see after my icon for new launcher in my menu.
(iii) In the 'Command' field, type the path and name of the script I want to run
(iv) Find the 'Choose Icon' button over to the right of the 'Create Launcher' box and click on it.
In the top field of the next window, I typed: /usr/share/icons/
My icons showed up in the viewing pane, and I just clicked on the one I wanted and clicked 'Okay'..

7. I repeated steps 4 to 6 with the opposite script and icon

8. I looked in my 'Applications' menu under 'Programs' and found my new launchers with my new icons and tried them out and they work great.  Now it's very quick and convenient whenever someone wants to revert back to the original sources.list for a while and then back to their Bigpond one, even if your user doesn't like using the command line. :)

If anyone's interested, here are the two icons I made, (out of parts I copied from existing icons), you can probably copy them from here, (right-click and 'save image as').

---

### Post by Herman on 2009-03-07
Here are the two scripts, (see attachments), just in case someone wants to use them but doesn't know yet how to make a script. :D

Note: On testing this in another computer, I found that I had file permission problems when trying to run the scripts. 
That can easily be fixed by running a chmod command on them,
```
sudo chmod 755 switchsourcesbigpond.sh
sudo chmod 755 switchsourcesubuntu.sh
```
Where: the scripts are in the username directory.
I suggest you actually keep them somewhere else where they won't be likely to be accidentally moved or deleted, and you should insert the correct file path to these two commands if you have copied them somewhere else already.

---

### Post by joewski on 2009-03-09
Hey thats scripts cool. Nice work with the icons too.

What I really wish for is that third party repositories would be built into Ubuntu. That way we could submit them to ubuntu proper. Then maybe ubuntu could send a MD5 for the files which could be compared to the repository. That way the internet download could be kept down to small files while the repository files could be large.

---

