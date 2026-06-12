---
title: "[SOLVED] I knew I shouldn't have done it but I just couldn't help myself..."
date: 2008-02-23
forum: Desktop Environments
---

### Post by itsjustarumour on 2008-02-23
I KNOW, I KNOW, BUT... :redface:  

I'm on Gutsy, and I installed Firefox 3.0 Beta 3 from the Hardy repos.  Then I decided to uninstall it and reinstall Firefox 2.0 again.  Except now I can't, as I get this:

> ian@COOLERMASTER:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xulrunner-1.9 xulrunner-1.9-dom-inspector libwv-1.2-3 libgsf0.0-cil
Use 'apt-get autoremove' to remove them.
Suggested packages:
  firefox-gnome-support latex-xft-fonts
Recommended packages:
  ubufox
The following NEW packages will be installed
  firefox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/9176kB of archives.
After unpacking 26.6MB of additional disk space will be used.
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
Setting up libc6 (2.7-5ubuntu2) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error processing libc6 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libc6
E: Sub-process /usr/bin/dpkg returned an error code (1)
ian@COOLERMASTER:~$ 

I've tried 

> sudo apt-get autoremove

and

> sudo apt-get -f install

but I stll get the same message about libc6 returning an error code.  I've looked in /var/cache/debconf/ and the config.dat doesn't exist which is presumably why its throwing a wobbly at this point.

Anybody got any ideas?

itsjustarumour

---

### Post by benerivo on 2008-02-23
Have you tried
```
sudo dpkg --configure -a
```

---

### Post by harold4 on 2008-02-23
If you want to play around with FF3, try [this]("http://www.mozilla.com/en-US/firefox/all-beta.html")

---

### Post by chrisccoulson on 2008-02-23
FF3 beta 3 is also in gutsy-backports now.

Did you install FF3 by downloading the deb package from packages.ubuntu.com and installing using gdebi-gtk, or did you add a Hardy repo to your /etc/apt/sources.list? If you've done the latter, then it's probably upgraded a whole load of core packages (like libc6) to the versions currently in Hardy. That means your system will be in a right mess. You will need to downgrade those packages again after removing the Hardy repo from your sources.list, as that won't happen automatically.

---

### Post by harold4 on 2008-02-23
Yeah, using the hardy repo will definitely bomb your package versions.  Once you're back to gusty versions of packages, the above should  link will allow you to use FF3 as stand-alone.  Currently unable to test this.

---

### Post by itsjustarumour on 2008-02-23
> **benerivo said:**
> Have you tried
```
sudo dpkg --configure -a
```

Hi Benerivo, thanks for the poost.  I gave that a try and get:

> ian@COOLERMASTER:~$ sudo dpkg --configure -a
Setting up libc6 (2.7-5ubuntu2) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error processing libc6 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.7-5ubuntu2); however:
  Package libc6 is not configured yet.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6
 libc6-dev
ian@COOLERMASTER:~$ 


Not sure what that means, if how to configure libc6!

---

### Post by itsjustarumour on 2008-02-23
> **harold4 said:**
> If you want to play around with FF3, try [this]("http://www.mozilla.com/en-US/firefox/all-beta.html")

Hi Harold, I'll go have a look...

:-)

---

### Post by itsjustarumour on 2008-02-23
> **chrisccoulson said:**
> FF3 beta 3 is also in gutsy-backports now.

Did you install FF3 by downloading the deb package from packages.ubuntu.com and installing using gdebi-gtk, or did you add a Hardy repo to your /etc/apt/sources.list? If you've done the latter, then it's probably upgraded a whole load of core packages (like libc6) to the versions currently in Hardy. That means your system will be in a right mess. You will need to downgrade those packages again after removing the Hardy repo from your sources.list, as that won't happen automatically.

Thanks for the post, yeah I added the Hardy repo and then deactivated it straight away afterwards, so I fear it may have updated libc6 etc - OOPS!! (the size of an elephant) #-o#-o#-o 

I did try the Gutsy backported version, but it was only v3.0 Alpha8, which was weird....

---

### Post by itsjustarumour on 2008-02-23
> **harold4 said:**
> Yeah, using the hardy repo will definitely bomb your package versions.  Once you're back to gusty versions of packages, the above should  link will allow you to use FF3 as stand-alone.  Currently unable to test this.

OK, just going to give that a try now, will report back on how I get on.

Thanks again for all your posts chaps!

:-D

---

### Post by steveneddy on 2008-02-23
> **harold4 said:**
> If you want to play around with FF3, try [this]("http://www.mozilla.com/en-US/firefox/all-beta.html")

Do this, then just open the folder and run it from there if you just want to try it out.

This was you won't hose your other Firefox.

In Terminal, just cd to the directory that the FF3 is in and then run Firefox

```
cd ~/Desktop/Firefox/Firefox
```

if it is in a folder on the Desktop.

---

### Post by chrisccoulson on 2008-02-23
The version of FF3 in gutsy is alpha8, but the version in gutsy-backports is beta3. You need to enable gutsy-backports though. Check out: [http://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=gutsy-backports&section=all]("http://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=gutsy-backports&section=all")

---

### Post by fracturedmorals on 2008-02-23
To run that version in gutsy, you just have to uncomment the backported repos in your sources.list

---

### Post by itsjustarumour on 2008-02-23
> **chrisccoulson said:**
> The version of FF3 in gutsy is alpha8, but the version in gutsy-backports is beta3. You need to enable gutsy-backports though. Check out: [http://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=gutsy-backports&section=all]("http://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=gutsy-backports&section=all")

Chris,
You're absolutely right, I've just realised that the Gutsy Backports option was missing from my souces list in Synaptic - DOH! - I checked my /etc/apt/sources.list and it was in there but somehow got corrupted or something (but wasn't showing in Synaptic as either activated or deactivated - it just wasn't there - more weirdness!)

---

### Post by itsjustarumour on 2008-02-23
OK, heres a brief summary of what I've tried so far:

- I've had a cleanout on my system of everything I can find relating to Firefox, uninstalled everything I can, deleted old cached downloads etc.

- I've tried installing v3.0 Beta 3 from the Mozilla site, but still get an error message about being unable to configure libc6.

- I've tried installing v3.0 Beta 3 from packages.ubuntu.com, but still get an error message about being unable to configure libc6.

- I've tried reinstalling v2.0 again, but still get the error message about being unable to configure libc6.

- and I've tried re-enabling the Hardy repo again and reinstalling v3.0 Beta 3 from there, but I still get the same error message about being unable to configure libc6...

I guess I'm hosed!  Or at least an official Opera user until I reinstall when Hardy comes out :lolflag:

Anyhoo, I've been sat here for 14 hours so before I'm overtaken by any more attacks of forehead-slapping numptiness I'm calling it a night.

Thanks again for all your posts on this, and of course any other advice would be gratefully received!

Cheers,

itsjustarumour

---

### Post by itsjustarumour on 2008-02-23
I just had to have one more try at this and... YAY, EVERYTHING IS BEAUTIFUL AGAIN!

Its was something that Chrisccoulson said, about having to downgrade packages... the full significance of that was lost on me as I'd never known how to!  But suddenly it clicked, and a quick Google search found this post:

[http://ubuntuforums.org/showthread.php?t=672906](http://ubuntuforums.org/showthread.php?t=672906) 

on how to downgrade individual packages.  Synaptic>Package>Force Version, select "libc6" and "Downgrade to original Gutsy version", and voila!  Everything works again, Firefox is now reinstalled and everthing is peachy :guitar:

---

### Post by chrisccoulson on 2008-02-23
Glad you've got it fixed now:)

---

