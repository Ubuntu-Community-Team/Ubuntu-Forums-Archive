---
title: "Installing Quake 2 -- I have the full version"
date: 2008-08-01
forum: Gaming &amp; Leisure
---

### Post by jukingeo on 2008-08-01
Hello, 

I read that I can install Quake 2 into an Linux distribution and I was to type this in the Terminal:

sudo aptitude install quake2

So I did that, it loaded something up, but where is it?  There is no Quake 2 icon in the Games menu.   I tried to look it up 'manually' in /user/bin, but it isn't there either.

Can someone tell me where it went?

Also, I am assuming this is for the shareware version of Quake II.  I DO have the store bought disc and would like to know how to use that version in Linux.



EIDT, Ok, I found some additional information regarding the install of the full version and I did this in my terminal:

geo@home:~$ sudo apt-get install quake2-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  quake2-data
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.5kB of archives.
After this operation, 156kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse quake2-data 13-0.2 [17.5kB]
Fetched 17.5kB in 0s (35.9kB/s)    
Preconfiguring packages ...
Selecting previously deselected package quake2-data.
(Reading database ... 121331 files and directories currently installed.)
Unpacking quake2-data (from .../quake2-data_13-0.2_all.deb) ...
Setting up quake2-data (13-0.2) ...

geo@home:~$ sudo dpkg-reconfigure quake2-data
Installing data from CD-ROM
Point release already installed
geo@home:~$ 


However, I have yet to see an icon or where to launch the thing.  So I still need help there.

Thanx,

Geo

---

### Post by jukingeo on 2008-08-03
Bump

Can anyone help, please?

---

### Post by reidbold on 2008-08-03
I have found using linux installers for q2 don't work. I copied the game folder from windows and replaced the binaries with ones from ftp.idsoftware.com. Maybe try installing with wine?

---

### Post by jukingeo on 2008-08-04
> **reidbold said:**
> I have found using linux installers for q2 don't work. I copied the game folder from windows and replaced the binaries with ones from ftp.idsoftware.com. Maybe try installing with wine?

Hmmm, I thought that Quake II was supposed be able to be play through Linux?  It 'looked' like it installed, but there are no icons or anything that launches the program anywhere.  Which I found odd.

At any rate, I don't know how to use Wine as of yet, so I don't know the first thing about going that route.

Geo

---

### Post by KenMac on 2008-08-04
I'm not sure as I don't have Quake installed but it may be that it is launched from the terminal.  Have you tried:
> quake
from the terminal?

---

### Post by Brebs on 2008-08-04
Look in /usr/**games**/bin/ ;)

I recommend kmquake2 - see my Fedora .spec file and .src.rpm file in [my ftp dir](ftp://brebs.me.uk/fedora/9/). You'll have to compile it yourself though.

---

### Post by jukingeo on 2008-08-05
> **Brebs said:**
> Look in /usr/**games**/bin/ ;)

I recommend kmquake2 - see my Fedora .spec file and .src.rpm file in [my ftp dir](ftp://brebs.me.uk/fedora/9/). You'll have to compile it yourself though.

Yeah, I am new to Linux...I don't know the first thing about recompiling.

I was really looking for a quick/easy install just to see how Quake II looks set up in Linux, but if it is going to be a royal pain in the butt, I probably will leave it for Windows.  It sets up 1-2-3 there.

It is not that I am avoiding a challenge or learning something new, but with over 2 months on Linux trying to solve problems with setting up a Digital Audio Workstation (which still hasn't been resolved yet), I am looking for a quick fix to 'let off some steam'!

Slightly off topic:  Would you know if Doom sets up any easier?  (I should have my Doom disc floating around somewhere).  If THAT is an equal royal pain to set up as well, then I am open to any native Linux alternative FPS games that are similar to Doom and Quake. Any suggestions?  Remember, I am looking for those games that are easy to set up...point and click install and I am good to go.

Thanx,

Geo

---

### Post by jukingeo on 2008-08-05
> **jukingeo said:**
> Yeah, I am new to Linux...I don't know the first thing about recompiling.

I was really looking for a quick/easy install just to see how Quake II looks set up in Linux, but if it is going to be a royal pain in the butt, I probably will leave it for Windows.  It sets up 1-2-3 there.

It is not that I am avoiding a challenge or learning something new, but with over 2 months on Linux trying to solve problems with setting up a Digital Audio Workstation (which still hasn't been resolved yet), I am looking for a quick fix to 'let off some steam'!

Slightly off topic:  Would you know if Doom sets up any easier?  (I should have my Doom disc floating around somewhere).  If THAT is an equal royal pain to set up as well, then I am open to any native Linux alternative FPS games that are similar to Doom and Quake. Any suggestions?  Remember, I am looking for those games that are easy to set up...point and click install and I am good to go.

Thanx,

Geo

---

### Post by rajeev1204 on 2008-09-11
Up until feisty, the engine -quake2 and the installer quake 2 data were both available , but the engine had too many network security issues so debian dropped the quake 2 package out. (the engine).


U can try using the feisty packages from packages.ubuntu.com but its best to use wine to run quake 2.

I have some issues saving resolutions but still it runs fine.



OK it doesnt work on anti cheat servers. it just hangs.

---

### Post by PrimoTurbo on 2008-09-12
I suggest you just use wine, it works well and you can use all the newer engines for Quake2.

---

### Post by rajeev1204 on 2008-09-12
> **PrimoTurbo said:**
> I suggest you just use wine, it works well and you can use all the newer engines for Quake2.

I did that but the anti cheat module from r1ch.net doesnt work.

So no multiplayer luck. :(

Need to google more now .

---

### Post by PeterBBB on 2008-09-12
> I was really looking for a quick/easy install 

Try the tutorial here. It should be easy enough, and I explain how to set up the icon.

_[http://ubuntuforums.org/showthread.php?t=890091](http://ubuntuforums.org/showthread.php?t=890091)_

Let us know how you get on. With useful feedback, the tutorial could get improved if need be.


Pete

---

### Post by jukingeo on 2008-09-17
Hello guys,

I just want to get Quake 2 to run that is all.  Skulltag looks similar to Doom, but I am not sure how close it is.

At any rate, I don't care about multi-player deathmatch modes.  Running the single player campaigns is fine with me.

Geo

---

