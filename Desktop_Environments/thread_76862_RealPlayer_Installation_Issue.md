---
title: "RealPlayer Installation Issue"
date: 2005-10-15
forum: Desktop Environments
---

### Post by dwessell on 2005-10-15
Hey all.. When I try to install RealPlayer, I get this.. Any suggestions?

david@ubuntu:~$ sudo apt-get install realplayer
Reading package lists... Done
Building dependency tree... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate

Thanks
David

---

### Post by stoffe on 2005-10-15
$ aptitude show realplayer

> Description: Real Player (installer)
 Real Player is a streaming sound and video player from RealNetworks.

 RealNetworks does not allow redistribution of their software. Therefore, this
 package requires the user to fetch the real player archive separately from
 their web site. When you install this package you will be guided through that
 process.

 This package installs the file rp8_linux20_libc6_i386_cs2_rpm from the
 real.com website (look for the Unix player).


---

### Post by dodongo on 2005-10-15
If you go to real.com and look for their downloads, you can get their Linux install in an RPM file.

You have to do things a little differently to install software from an RPM file (but I've been using this package myself for months without any issues at all).  Your best bet is to download it to the desktop, then in the terminal do the following:

```
cd ~/Desktop

sudo alien -i [RealPlayer RPM file name]
```

Sorry if this is pedantic, but to explain, the first line just goes inside your home directory (the ~) to the Desktop folder.  The second line runs alien, which is a program that tries to convert an RPM file to the DEB files Ubuntu uses to install software.  Finally, the -i argument for alien tells it to not just convert the file, but to go ahead and install it.

Then, you should be good to go, with the latest greatest RealPlayer.

---

### Post by taurus on 2005-10-15
Actually, if you fire up synaptic and click on the search field on the upper right, type in realplayer and it will come back with realplayer version 8.0.11!  But if you want to install the latest version, then you have to download it either in bin or rpm from [http://www.real.com](http://www.real.com) then...

---

### Post by dwessell on 2005-10-15
Hey all, thanks for the comments.. I tried the alien command, but was not that the command was not recognized:

david@ubuntu:~/Desktop$ sudo alien -i RealPlayer10GOLD.bin
Password:
sudo: alien: command not found

As well I tried searching in the Package Manager, but nothing is ever found when I search for RealPlayer... ?? 

Any other suggestions or follow ups?

Thanks
David

---

### Post by The Headhunter on 2005-10-15
sudo apt-get install alien

and then go ahead and do what was stated above for the realplayer package.

---

### Post by gabhla on 2005-10-15
Hello.  Followed the same steps, as above, and RealPlayer was installed, but how do I get it to appear in the Applications menu?  Thanks.

---

### Post by hajk on 2005-10-16
The easiest way to get RealPlayer working is to install it from Christian Marillat's Debian repository -- just make sure that you remove it from the sources.list right after downloading the realplayer package (since other packages there might break Ubuntu). The realplayer package in universe/multiverse is now an empty one, expecting users to download RealPlayer (in rpm form) themselves from elsewhere...  

So,

1. sudo vi /etc/apt/sources.list and add:
       deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main
2. sudo apt-get update
3. sudo apt-get install realplayer
4. sudo vi /etc/apt/sources.list and comment out
       ## deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main
    don't remove it, you may want to use it later to download the 
    w32codecs package.
5. sudo apt-get update (don't forget this line).
 
and you're all set. Marillat even included some older codecs in the realplayer package that some sites still use but that are no longer included by Real Networks in their downloads. 

It worked for me. :)

---

### Post by dodongo on 2005-10-16
> but how do I get it to appear in the Applications menu?

Did you restart GNOME (i.e., log out, log in again)?  If that still doesn't fix it (and I'm not honestly sure it will).  I installed off the RPM, and I'm almost sure it auto-generated the icon -- which isn't to say you've done anything wrong, just that you'll have to use Menu Editor to add the icon manually.

And PS, thanks to whoever above noted that alien isn't included by default.  I just thought it was, but I fiddle with things incessantly, so it probably got installed by me at some point in the distant past!

---

### Post by bionnaki on 2005-10-16
Marillat's worked for me - real player works great now.
I disabled the repo (deleted actually), so no worries of it breaking my system.

---

### Post by Omnios on 2005-10-16
Hi im having problems geting realplayer from 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main 
 
 Gives me the following errors.

```
Err ftp://ftp.nerim.net stable/main Packages
  Unable to fetch file, server said 'Can't open /debian-marillat/dists/stable/main/binary-i386/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]
Fetched 191B in 3s (48B/s)
Failed to fetch ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz  Unable to fetch file, server said 'Can't open /debian-marillat/dists/stable/main/binary-i386/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]
Reading package lists... Done
W: GPG error: http://ca.archive.ubuntu.com breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Couldn't stat source package list ftp://ftp.nerim.net stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by dwessell on 2005-10-16
Same thing here. I'm glad I'm not the only one having issues :)

[QUOTE=Omnios]Hi im having problems geting realplayer from 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main 
 
 Gives me the following errors.

```
Err ftp://ftp.nerim.net stable/main Packages
  Unable to fetch file, server said 'Can't open /debian-marillat/dists/stable/main/binary-i386/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]
Fetched 191B in 3s (48B/s)
Failed to fetch ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz  Unable to fetch file, server said 'Can't open /debian-marillat/dists/stable/main/binary-i386/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]
Reading package lists... Done
W: GPG error: http://ca.archive.ubuntu.com breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Couldn't stat source package list ftp://ftp.nerim.net stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```[/QUOTE]

---

### Post by dodongo on 2005-10-16
> You may want to run apt-get update to correct these problems

From your code snippet above...  have you (both dwessel and Omnios) run

```
sudo apt-get update
```

or done "Refresh" in Synaptic (it does exactly the same thing as the code line above)?  The GPG error might persist, but the "couldn't stat" business should go away.

**EDIT:** No, I just did it myself and got the error.  It seems like a server issue.  Give it a day and see if he's back up.  Alternatively, use the alien install method I describe above.

---

### Post by Omnios on 2005-10-16
I wanted the extra codecs but I installed the rpm must say alien rocks, is there a legal way to add codecs to realplayer I have legal copies of realplayer and windows media. Nothering special just need for multimedia web stuff.

---

### Post by dodongo on 2005-10-16
The RealPlayer software should have all the RealMedia support  you need (I think it does everything from the version 4 codecs on).  As for the Windows Media stuff, that's trickier -- and ironically, the place you'd most likely be directed to get the codecs is from Marillat's repo.  Maybe it's best to wait to see if his site comes back up?  :)

---

### Post by skoal on 2005-10-16
For best results, IMO:

1. Download the latest Realplayer binary installer from the realplayer website, and save it somewhere:
```
skoal@morpheus:///data/apps/internet/realplayer/v10-101605 $ ls -l
total 5662
-rw-r--r--  1 skoal skoal 5789348 2005-10-16 20:05 RealPlayer10GOLD.bin
```
2. Copy to /tmp directory, run the installer as sudo...

3. Choose a path like /opt/Realplayer (for example)...

4. Either add that /opt/Realplayer/bin path to your $PATH or just symlink (as sudo) in your /usr/bin:
```
skoal@morpheus:///usr/bin $ ls -l realplay 
lrwxrwxrwx  1 root root 24 2005-10-16 20:26 realplay -> /opt/Realplayer/realplay
```
*5. If you've installed the mplayer plugin for firefox, don't let mplayer handle Realmedia .rpm files:
```
skoal@morpheus:///usr/lib/mozilla-firefox/plugins $ ls -l
total 2054
-rwxr-xr-x  1 root root     856 2005-10-16 20:30 flashplayer.xpt
-rwxr-xr-x  1 root root 2096844 2005-10-16 20:30 libflashplayer.so
lrwxrwxrwx  1 root root      43 2005-10-16 17:52 mplayerplug-in-gmp.so -> ../../mozilla/plugins/mplayerplug-in-gmp.so
lrwxrwxrwx  1 root root      44 2005-10-16 17:52 mplayerplug-in-gmp.xpt -> ../../mozilla/plugins/mplayerplug-in-gmp.xpt
lrwxrwxrwx  1 root root      42 2005-10-16 17:52 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx  1 root root      43 2005-10-16 17:52 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx  1 root root      39 2005-10-16 17:52 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx  1 root root      43 2005-10-16 17:52 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx  1 root root      44 2005-10-16 17:52 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx  1 root root      40 2005-10-16 17:52 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
lrwxrwxrwx  1 root root      34 2005-10-16 20:26 [COLOR="DarkRed"]nphelix.so -> /opt/Realplayer/mozilla/nphelix.so[/COLOR]
lrwxrwxrwx  1 root root      35 2005-10-16 20:26 [COLOR="DarkRed"]nphelix.xpt -> /opt/Realplayer/mozilla/nphelix.xpt[/COLOR]
```
...which has 2 symlink files *missing*, since I've _deleted_ them.  I believe those are 'mplayerplug-in-rm.so' and 'mplayerplug-in-rm.xpt', which are still available but in the /usr/lib/mozilla/plugins path (so if you want to later use them, just symlink those two back).

6. You'll notice above (in maroon, whoop!) that the binary installer already creates the two realplayer plugin symlinks for you.

\\//_

---

### Post by Omnios on 2005-10-16
Im having a slight problem with the firefox plug in I did the set up and moz plugs but totem is trying to launch for my real content even though It cant handlw it. I had media connect installed before real player and it dont show the icon yet even after restarting x. Think the plug ins got borked.

---

### Post by Omnios on 2005-10-17
K got mozzila and firefox plug ins linked and still notta, Think there has to be a system link to the reapplayer binary but do not remember how to do that. Totem is still highjacking my brouser.

---

### Post by bionnaki on 2005-10-17
marillat is down for me as well.
anyone know of another source?

---

### Post by hajk on 2005-10-17
Try "sarge" or "etch" instead of "stable" in the Marillat repository, that should work.

---

### Post by sanman_nor on 2005-10-17
I used the below method to install realplayer... 

```
cd ~/Desktop

sudo alien -i [RealPlayer RPM file name]
```

it ran fine,  but I still can not play the files, or open realplayer.   
if i open synaptic it lists realplayer but if I go to run it... 
I get 
Cannot display location 'file://realplayer'

Details: There is no default action associated with this location.
any sugestions

---

### Post by Omnios on 2005-10-17
I think its a system wide symbolic links problem I could nto get the rpm to use my web properly Mplayer is highjacking everything and tryed media connect but that didnt work either. Also installing with the bin download got borked for system wide symbolic links as I put the default but got errors.

 Anyone have suggestions.

 I downloaded the realplayer bin and it was not launching real media web stuff, think mplayer was trying to cut in. Anyways I booted XP to check if the media was down and it wasn't so I booted up Ubuntu and Real Player was working. I think you have to restart x or reboot if its not working on the web.

---

### Post by Riverside on 2005-10-21
[QUOTE=Omnios]I downloaded the realplayer bin and it was not launching real media web stuff, think mplayer was trying to cut in. Anyways I booted XP to check if the media was down and it wasn't so I booted up Ubuntu and Real Player was working. I think you have to restart x or reboot if its not working on the web.[/QUOTE]I have just installed Real Player on Breezy, by downloading RealPlayer10GOLD.bin and then running it (sudo of course).  I had to first install libstdc++5 (sudo apt-get install libstdc++5), as initially running RealPlayer10GOLD.bin revealed this dependency.  I installed Real Player using RealPlayer10GOLD.bin into /usr/local/bin.

The Firefox plugin is installed automatically, but didn't appear to be.  Logging out of X (Blackbox in my case) and then logging back in again resolves this, and I now have the Real Player based BBC Radio Player burbling away in the background.

---

### Post by youngster1 on 2005-10-21
WARNING !

Dont install RealPlayer in the AMD64 verion of Ubuntu. It borks the system and you have to reload the OS from scratch.

---

### Post by l0c0dantes on 2005-10-21
ummm, When ever I try to use sudo Alien -i, it says command not found

---

### Post by jordilin on 2005-10-21
As Mr. Riverside points out, the best method to install Realplayer in Ubuntu is installing libstdc++5 by means of apt-get and then download realplayer from [http://www.real.com/linux](http://www.real.com/linux) and installing it by running the setup program. 
That's all

---

### Post by manicka on 2005-10-21
[QUOTE=bionnaki]marillat is down for me as well.
anyone know of another source?[/QUOTE]

The marillat repo will play havoc with your system. If you need to use it please make sure that it is **commented out after use**. Alternatively you could try the plf repos.

[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

---

