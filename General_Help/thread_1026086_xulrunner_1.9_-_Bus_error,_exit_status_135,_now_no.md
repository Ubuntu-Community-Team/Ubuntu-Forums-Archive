---
title: "xulrunner 1.9 - Bus error, exit status 135, now no Firefox"
date: 2008-12-30
forum: General Help
---

### Post by madmaxnj on 2008-12-30
Well it was telling met that there were a bunch of updates that I needed so I clicked to install them all.  Something failed during the installation of the updates.  It flagged and crash error, but I didn't write down what it was.  After that I rebooted and Firefox wouldn't launch.  It would start to, I would see it start on the status bar, but then would just go away.  I went into Synaptic Package Manager and tried to reload Firefox.  Here i get an error:
E: xulrunner-1.9:subprocess post-installation script returned error
exit status 135
E:firefox-3.0:dependency problems - leaving unconfigured (and a bunch more of these 'leaving unconfigured messages).

Digging into the detailed printout it starts to go south with:
Setting up xulrunner-1.9 (1.9.0.5+nobinonly-0ubuntu0.8.10.1)...
bus error
dpkg: error processing  xulrunner-1.9 (--configure):
  subprocess post-installation script returned exit status 135


So I tried to reload xulrunner and get the same thing.

I've gone through this now in a couple of different orders include deletes and new installs to no avail.

Any ideas?  Can I go back a version on xulrunner and Firefox somehow?  I don't see older versions in the Synaptic Package Manager.

Help?  I configured this box to be a web surfer and now I can't surf the web.  Thanks!

---

### Post by madmaxnj on 2008-12-31
Help.  xulrunner 1.9 is killing me.  How do I revert back to a previously operational version of xulrunner and FF?

I've been all over the forums and other people are having the same problem, but nobody has a fix.

---

### Post by madmaxnj on 2009-01-02
I've seen other posts with people having the same problems with this update, but nobody has a solution.  I had to uninstall xulrunner 1.9 and FF3 (and all their subcomponents) and install SeaMonkey 1.1.12 to get this box back online.  Now that it works, I'm worried to try to update anything since I suspect it will bring me right back to the state where nothing works.

anybody have any ideas on this?  I know its not just me.

---

### Post by Toshick on 2009-04-28
I have the same problem on fresh installed Ubuntu 9.04. Is any solution exists?

---

### Post by mooseydoom on 2009-04-28
I had this error when my computer crashed while in the middle of updating.  I had to force removal of xulrunner:
```
sudo dpkg --remove --force-remove-reinstreq --force-depends xulrunner-1.9
```
Then remove, and re-install firefox
```
sudo apt-get remove firefox*
sudo apt-get install firefox
```

---

### Post by sunilsattiraju on 2009-05-08
I am having the same problem, tried mooseydoom method, but still the same error.

has anyone found a solution to this problem?

---

### Post by forestwalkerjoe on 2009-07-14
ok.. i have been searching for a place to ask these questions.. but so far can not find any thing on this. 
xulrunner-1.9.1 and xulrunner-1.9.1-gnome-support files keep doing an update manger download.. of the exact same two files .. every single day.
 
What is up with this.. and where do I find help to solve this issue? 
is this a glitch i the 904 upgrade? what? i have done the download.. and again.. again , again again and again. BUT every day.. they show up again. 

I have no idea where to look for these to be solved.. i can find out what these are.. or what other troubles persons have had WITH the files themselves.. but not my issue. 
ANY ONE want to try and help me out here? 

i see in this thread others are having worse problems than i am.. mine is completing the download.. with no trouble there.. and its installing.. no trouble there.. but if you , before the install click the description of these files.. it says failed to find description. the second tab will tell me what it is.. but its failing to recognize my version of the OS .. i think. 
shall we just wait till the canonical folks get with it and send a down loadable fix? 


FWJ

---

### Post by dmazzone on 2009-07-22
> **mooseydoom said:**
> I had this error when my computer crashed while in the middle of updating.  I had to force removal of xulrunner:
```
sudo dpkg --remove --force-remove-reinstreq --force-depends xulrunner-1.9
```
Then remove, and re-install firefox
```
sudo apt-get remove firefox*
sudo apt-get install firefox
```

Spent nearly a half hour in this issue, thank you so much for the solution :D

---

### Post by chettyk on 2009-07-23
I too am having this problem. Even the solution suggested by mooseydoom doesn't work for me.

When I run 'sudo apt-get upgrade', I get the following error:> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up xulrunner-1.9.1 (1.9.1.1+build1+nobinonly-0ubuntu0.9.04.1) ...
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/xulrunner for update_mode ()
dpkg: error processing xulrunner-1.9.1 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of xulrunner-1.9.1-gnome-support:
 xulrunner-1.9.1-gnome-support depends on xulrunner-1.9.1 (= 1.9.1.1+build1+nobinonly-0ubuntu0.9.04.1); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing xulrunner-1.9.1-gnome-support (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 xulrunner-1.9.1
 xulrunner-1.9.1-gnome-support
E: Sub-process /usr/bin/dpkg returned an error code (1)
gopalraj@Laptop-Ub904:~$ 


I just don't know what to do to get Firefox running again; I am currently using Opera. I considered reinstalling the whole os, but then wondered if the same problem would recur. Any ideas anyone?

Thanks.

---

### Post by sleepingpeace on 2009-09-18
> **mooseydoom said:**
> I had this error when my computer crashed while in the middle of updating.  I had to force removal of xulrunner:
```
sudo dpkg --remove --force-remove-reinstreq --force-depends xulrunner-1.9
```
Then remove, and re-install firefox
```
sudo apt-get remove firefox*
sudo apt-get install firefox
```

No idea what that did, but it worked!

---

