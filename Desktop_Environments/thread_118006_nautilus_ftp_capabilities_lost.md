---
title: "nautilus ftp capabilities lost"
date: 2006-01-15
forum: Desktop Environments
---

### Post by borisattva on 2006-01-15
did a full breezy reinstall.

installed the following:
Official NVIDIA drivers, Sun Java, Azureus, Lexmark z52 printer, Full set of gstreamer plugins, Nero Linux, K3b, XMMS, MPlayer, EasyTag, Celestia, Grisbi

Installed and removed:
Firestarter (gave me problems with LAN), gnucash (eye sore)

and somewhere along this way my nautilus lost FTP capabilities.

i say lost because this was my 6th reinstall, and this is the FIRST reinstall with this problem.

i go to Places > Connect to Server

fill out all the credentials info, and save it into a mount on the desktop.
when i double click it to load i get:
```
Couldn't display "ftp:///"
```

when i try to acces it through Places > Connection name i get:

```
Cannot display location 'ftp://user@address:port'
Details: There is no default action associated with this location.
```

i checked in synaptics and i have 'ftp' installed.

from what i gathered so far the FTP handling i'm missing is actually built in to the nautilus,
so i went and did a reinstall on every Nautilus packege i saw, to no avail.

Looking forward to hearing some suggestion on this,
after going everything i wnet through to install the previous pacakges i'm really not looking forward to another reinstall.

---

### Post by borisattva on 2006-01-17
*&#1096;&#1080;&#1096;&#1082;&#1072;*

---

### Post by borisattva on 2006-01-17
to anyone with in depth knowledge of Nautilus/Gnome, can you tell me which package/dependnency could be missing that is causing this?
is there a command line i can run to reset all Nautilus settings to defualt and hopefully restore this?

i'm minimalist when it comes to application set in pcs and id hate having to install a dedicated ftp app since the build in feature was doing what i needed just fine.

---

### Post by cwaldbieser on 2006-01-17
[QUOTE=borisattva]to anyone with in depth knowledge of Nautilus/Gnome, can you tell me which package/dependnency could be missing that is causing this?
is there a command line i can run to reset all Nautilus settings to defualt and hopefully restore this?

i'm minimalist when it comes to application set in pcs and id hate having to install a dedicated ftp app since the build in feature was doing what i needed just fine.[/QUOTE]
```

$ sudo dpkg-reconfigure nautilus

```
maybe?

---

### Post by borisattva on 2006-01-18
no joy.

i also did sudo dpkg-reconfigure libgnomevfs2-0
as i found out that was suppose dto be reposnsible for this
and did the reinstall of it and the commons.

no luck..
thanks for responding

any other ideas?

---

### Post by borisattva on 2006-01-18
to anyone who is NOT experiencing this problem, can you go into gconf-editor and tell me if you have a bookmark 
desktop/gnome/url-handlers/ftp and what the values are?

mine is missing completely trying to figure out if that has anything to do with this

---

### Post by cwaldbieser on 2006-01-19
[QUOTE=borisattva]to anyone who is NOT experiencing this problem, can you go into gconf-editor and tell me if you have a bookmark 
desktop/gnome/url-handlers/ftp and what the values are?

mine is missing completely trying to figure out if that has anything to do with this[/QUOTE]
I don't have that setting, but ftp works fine from nautilus.

I have the following nautilus-related packages installed:
```

$ dpkg -l '*nautilus*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                   Version           Description
+++-======================-=================-============================================
rc  libnautilus-burn1      2.10.0-0ubuntu2   Nautilus Burn Library - runtime version
ii  libnautilus-burn2      2.12.1-0ubuntu1   Nautilus Burn Library - runtime version
ii  libnautilus-extension1 2.12.1-0ubuntu1.1 libraries for nautilus components - runtime 
un  libnautilus1.1-0       <none>            (no description available)
un  libnautilus1.1-2       <none>            (no description available)
rc  libnautilus2-2         2.8.1-0ubuntu1    libraries for nautilus components - runtime 
un  libnautilus2-dev       <none>            (no description available)
ii  nautilus               2.12.1-0ubuntu1.1 file manager and graphical shell for GNOME
ii  nautilus-cd-burner     2.12.1-0ubuntu1   CD Burning front-end for Nautilus
ii  nautilus-data          2.12.1-0ubuntu1.1 data files for nautilus
ii  nautilus-sendto        0.4-0ubuntu4      provide integration between nautilus, evolut

```
Maybe that will help you somehow.

---

### Post by borisattva on 2006-01-20
thanks. i found that i'm missing 

libnautilus-burn1
libnautilus1.1-0
libnautilus1.1-2
libnautilus2-2
libnautilus2-dev

but they do not com up with repository list i got from this forum.

can you tell me which repo's it came from ?

thanks for all your help on this.

---

### Post by cwaldbieser on 2006-01-20
[QUOTE=borisattva]thanks. i found that i'm missing 

libnautilus-burn1
libnautilus1.1-0
libnautilus1.1-2
libnautilus2-2
libnautilus2-dev

but they do not com up with repository list i got from this forum.

can you tell me which repo's it came from ?

thanks for all your help on this.[/QUOTE]

Here is my sources.list.  I normally have universe and multiverse turned off, but occasionally will switch them on to get a package then turn them off again.  There are also some old repositories from previous versions, etc. I never bothered to fully erase.
```

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu/ breezy main restricted  
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy main restricted  
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted  
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted  
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ breezy universe    
deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted   
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted 
# deb http://archive.ubuntu.com/ubuntu/ breezy multiverse      
## Backports
# deb http://ubuntu.tower-net.de/ubuntu/ warty java   
# deb http://www.falassion.de/unstable/ ./ 
# deb http://debian.wesnoth.org/sid/ ./ 

```
Hope that helps you out.

---

### Post by borisattva on 2006-01-22
the repo list you showed didnt have the missing packages, but i did find that the last two no longer appear to be up, just an FYI.

but ive been able to figure out what the problem was.
after i would install any new pacakge i would go back and remount a server in hopes of maybe something would patch up whatever was broken.

all to no avail until i due to force of habit typed in port 21 (my provider insists on using 904047 according to its settings page) and it worked!

i cross referenced this with other sites i have control over and looks like that when port is above 4 digits, it somehow exceeds the parametes and screws up the mouting record. interestingly enough the same appears to affect gFTP client that i installed and reported problems with [here]("http://ubuntuforums.org/showthread.php?t=119288").

so perhaps its something on the level below nautilus/gftp development, and could probably be easily patched up, and solve it for all applications using it.
i have no idea why would [PowWeb]("http://signup.powweb.com/powweb-bin/referer.cgi?account_id=31566") want to use such a drastically large port, and i will let them know of this find.

thanks for all your help cwaldbieser

---

