---
title: "Firefox 3.0.7 Crashing"
date: 2009-03-07
forum: General Help
---

### Post by HeretikSaint on 2009-03-07
I know there are a ton of threads with Firefox crashing but I haven't been able to find a solution to my specific problem as of yet.  I started Firefox and it informed me that I needed to update and I just decided to upgrade.  It upgraded.  I started it and I went to load the theme I always used, clicked on "add-ons" under the "Tools" menu and Firefox closes.  I went to search for the problem and noticed that the search engine bar does not work either.

I'm using Firefox 3.0.7
Ubuntu 8.04

I'm not a complete noob when it comes to linux but I've just got back into it so I'm a little rusty on some of this stuff.  Let me know if you require any other information and I will provide it.  Thank you.

---

### Post by dcstar on 2009-03-07
> **HeretikSaint said:**
> I know there are a ton of threads with Firefox crashing but I haven't been able to find a solution to my specific problem as of yet.  I started Firefox and it informed me that I needed to update and I just decided to upgrade.  It upgraded.  I started it and I went to load the theme I always used, clicked on "add-ons" under the "Tools" menu and Firefox closes.  I went to search for the problem and noticed that the search engine bar does not work either.

I'm using Firefox 3.0.7
Ubuntu 8.04

I'm not a complete noob when it comes to linux but I've just got back into it so I'm a little rusty on some of this stuff.  Let me know if you require any other information and I will provide it.  Thank you.

This is the second post today that I have seen with similar issues, I am now wondering if the latest 3.0.7 update is broken and people should not install it.

This update has not made it to all the mirror repositories yet, so hopefully some people will not have it yet (I am now locking my Firefox packages to 3.0.6 until I am happy the 3.0.7 is ok).

Is there anyone out there using FF 3.0.7 successfully?

---

### Post by HeretikSaint on 2009-03-07
> **dcstar said:**
> This is the second post today that I have seen with similar issues, I am now wondering if the latest 3.07 update is broken and people should not install it.

This update has not made it to all the mirror repositories yet, so hopefully some people will not have it yet.

Is there anyone out there using FF 3.0.7 successfully?

It's very frustrating.  I wish that I hadn't clicked on the update.

---

### Post by Gramps on 2009-03-07
Mine updated thru the repositories for 8.10 and it's doing fine. Sounds like you updated thru FF.

Maybe remove it and reinstall it from the repositories.

---

### Post by noxinvictus on 2009-03-07
The update is faulty.  I posted something else not long ago regarding my issues with it.  While it will work, most everything...does not.  I don't recommend any installations of it until the bugs are worked out or more information regarding it is issued.

---

### Post by mikewhatever on 2009-03-07
Sorry to hear there are problems with FF update. All is fine here though.

---

### Post by HeretikSaint on 2009-03-07
> **Gramps said:**
> Mine updated thru the repositories for 8.10 and it's doing fine. Sounds like you updated thru FF.

Maybe remove it and reinstall it from the repositories.

I did remove it through apt-get and then installed it through the synaptic package manager (only because I read somewhere that Firefox2 was on it, which it wasn't).  Do you think that removing it and reinstalling it strictly through apt-get would make a difference?

---

### Post by sports fan Matt on 2009-03-07
I updated through the update manager..for about the 1st 6 hours after I couldnt get an address bar or be able to type in Google or even tab.  Without doing anything, it resolved itself but no idea how...

---

### Post by HeretikSaint on 2009-03-08
> **sox fan Matt said:**
> I updated through the update manager..for about the 1st 6 hours after I couldnt get an address bar or be able to type in Google or even tab.  Without doing anything, it resolved itself but no idea how...
Hmm this is really annoying.  I just removed and reinstalled Firefox through apt-get and still the same problems.  I can tell because I go to Tools>>Add-ons and it closes immediately.

---

### Post by Gramps on 2009-03-08
> **HeretikSaint said:**
> I did remove it through apt-get and then installed it through the synaptic package manager (only because I read somewhere that Firefox2 was on it, which it wasn't).  Do you think that removing it and reinstalling it strictly through apt-get would make a difference?

The way I read your original post I thought you did the upgrade thru FF and not thru the Ubuntu update manager, that is why I suggested removing it and installing it from the repros. If the upgrade was thru the update manager then no reinstalling it probably will not help. 

Looks like there is a bunch of reported bugs over at lanuchpad [https://launchpad.net/+search?field.text=firefox+3.0.7](https://launchpad.net/+search?field.text=firefox+3.0.7) might be able to find out how to backport to 3.0.6

You might try this
```
sudo apt-get purge firefox
sudo apt-get update
sudo apt-get autoremove
sudo apt-get install firefox
```

Be sure to backup you bookmarks as this will wipe them along with any other custom setting you might have made.

---

### Post by HeretikSaint on 2009-03-08
> **Gramps said:**
> The way I read your original post I thought you did the upgrade thru FF and not thru the Ubuntu update manager, that is why I suggested removing it and installing it from the repros. If the upgrade was thru the update manager then no reinstalling it probably will not help. 

Looks like there is a bunch of reported bugs over at lanuchpad [https://launchpad.net/+search?field.text=firefox+3.0.7](https://launchpad.net/+search?field.text=firefox+3.0.7) might be able to find out how to backport to 3.0.6

You might try this
```
sudo apt-get purge firefox
sudo apt-get update
sudo apt-get autoremove
sudo apt-get install firefox
```

Be sure to backup you bookmarks as this will wipe them along with any other custom setting you might have made.

Originally I did update through FF.  I then removed it through apt-get and installed it again through the synaptic package manager.  I then, again, removed it and reinstalled it strictly through apt-get.  I'll try your suggestion now.

---

### Post by HeretikSaint on 2009-03-08
I tried and no such luck.  This means I'm without addons until this is fixed.

---

### Post by DeMus on 2009-03-08
> **HeretikSaint said:**
> I know there are a ton of threads with Firefox crashing but I haven't been able to find a solution to my specific problem as of yet.  I started Firefox and it informed me that I needed to update and I just decided to upgrade.  It upgraded.  I started it and I went to load the theme I always used, clicked on "add-ons" under the "Tools" menu and Firefox closes.  I went to search for the problem and noticed that the search engine bar does not work either.

I'm using Firefox 3.0.7
Ubuntu 8.04

I'm not a complete noob when it comes to linux but I've just got back into it so I'm a little rusty on some of this stuff.  Let me know if you require any other information and I will provide it.  Thank you.

I use Hardy 8.0.4.2 and Firefox 3.07 and it is working very well. I just got a notice I could update FF through the Hardy update manager. No problems here, add-ons are working, all the menu's are working, nothing wrong.
It's so strange to hear (read) that for one all is OK and others have problems. It's the same program, it should be updated the same way but still the differences.
Good luck in finding the solution. Do report here when you find it so others can benefit from it.

---

### Post by Sorivenul on 2009-03-08
Just chiming in that my wife's secondary machine had issues with her Firefox after the repository update to 3.0.7 as well. She's waiting to update her main machine until issues are resolved.

---

### Post by HeretikSaint on 2009-03-08
> **Sorivenul said:**
> Just chiming in that my wife's secondary machine had issues with her Firefox after the repository update to 3.0.7 as well. She's waiting to update her main machine until issues are resolved.

Good idea.  Let me know if she resolves the issue.

---

### Post by HeretikSaint on 2009-03-08
I went back and found Firefox 2 in the synaptic package manager and downloaded that but it just plain wouldn't open.  I'm really frustrated.

---

### Post by HeretikSaint on 2009-03-08
Update:
Firefox 3.0.7 now works miraculously.  I've been using a broken browser for about 3 hours now and all of a sudden, I closed everything out and was about to reinstall ubuntu all together (because I have a few other issues) and went to look something up real quick and BAM, theme, extensions, search bar, everything works fine.  My bookmarks are back too.  The only other thing I can think of is that daylight savings just hit.  I don't know why that would have ANYTHING to do with it but I have to wonder.

---

### Post by camurgo on 2009-03-08
I'm on Ubuntu 8.10. Firefox 3.0.7(from repositories) is eating up all my memory and can't be closed by normal means. Firefox process alone reached 1.5GB of RAM usage here, that was when the computer crashed altogether. :mad:

I can already imagine the mayhem at my work tomorrow, since 70% of the people there run Ubuntu Intrepid as primary OS.

---

### Post by dcstar on 2009-03-08
> **HeretikSaint said:**
> Update:
Firefox 3.0.7 now works miraculously.
.......

Keep in mind that not all repositories receive updates at the same time, a subsequent fix may have now reached your repository which then got installed fixing your problem - or only a partial set of update packages were in the repository when you first updated FF, and the rest (which made everything work correctly) only arrived at a later time.

I would say that the first scenario probably happened, with a "fix" rushed out shortly afterwards it was realised that the original update had problems.

I still might wait a day or two before allowing my FF to update...   ;-)

---

### Post by Buffalo Soldier on 2009-03-09
Been using Firefox 3.0.7 since a few hours. Updated using apt. No problem so far. The only plugins I have is DownThemAll. Maybe that could be one of the reason.

uname -a output:
```
Linux solitude 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux
```

lsb_release -a output:
```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.2
Release:        8.04
Codename:       hardy
```

---

### Post by heffo_j on 2009-03-09
Like a fool I updated to the new version and it hangs on me when downloading large (5Mb+) PDF files. My CPUs are arunning at 100%. System locks up. 

Not sure of the issue is with the PDF plugin or FF.

Like you I went to Synaptic to reinstall the earlier version but it was gone.....

Regards
John

---

### Post by emarkay on 2009-03-09
Is this the same problem? 
[http://ubuntuforums.org/showthread.php?p=6863486](http://ubuntuforums.org/showthread.php?p=6863486)

---

### Post by EricPorkham on 2009-03-10
I've been having the same problems, but after choosing "Mark For Reinstallation" in Synaptic Package Manager on all of the Firefox modules that I have installed, it seems to have been fine, no crashes!:D

---

