---
title: "[SOLVED] OpenOffice upgrade broke the whole thing!"
date: 2008-12-09
forum: General Help
---

### Post by solwic on 2008-12-09
Using Kubuntu 8.10.  Tried to update OpenOffice 2.4 to 3.0.  Followed this [guide.]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")

Now when I try to open a document, or even just run the program, it tells me I have to recover a document - Untitled 1 - and asks if I want to cancel or start recovery.  

No matter which I choose, it tells me that "Due to an unexpected error, OpenOffice.org crashed.  All the files you were working on will now be saved.  The next time OpenOffice.org is launched, your files will be recovered automatically."

I hit OK, and the box goes away, and I'm left with nothing.  I tried rebooting.  Still nothing.  

If this is just a junk release, is there a way I can remove 3.0 and go back to 2.4?  I'm a writer, so not having office software will send me right back to Windows.  I don't want that, but I don't have a choice if I can't fix this. 

Any help would be great.  Thanks.

---

### Post by frankleeee on 2008-12-09
Check out caraboy's clear and install it worked for me, I had to add a few things in synaptic like the open office help British and English to get that working and the open office gtk to get a quick systray installed. If it works thank him. ;)
[http://ubuntuforums.org/showthread.php?t=993516](http://ubuntuforums.org/showthread.php?t=993516)

---

### Post by solwic on 2008-12-09
> **frankleeee said:**
> Check out caraboy's clear and install it worked for me, I had to add a few things in synaptic like the open office help British and English to get that working and the open office gtk to get a quick systray installed. If it works thank him. ;)
[http://ubuntuforums.org/showthread.php?t=993516](http://ubuntuforums.org/showthread.php?t=993516)

Trying his solution now.  So far so good, but it's not done reinstalling 2.4 from the repos yet.  

Will update with results.

UPDATE:  Well it's working now, so at least I can work...but the menus at the top are really really big and all text.  No graphics in the menu bars.  :(

Still, I can at least write now.  Maybe I'll wipe this 2.4 and try to install 3 from the OOo site.  

Will update.  And thanks for the point to that thread.  :)  I'll thank caraboy over there, too.  :)

Cheers!

---

### Post by frankleeee on 2008-12-09
> **jrock612 said:**
> Trying his solution now.  So far so good, but it's not done reinstalling 2.4 from the repos yet.  

Will update with results.

UPDATE:  Well it's working now, so at least I can work...but the menus at the top are really really big and all text.  No graphics in the menu bars.  :(

Still, I can at least write now.  Maybe I'll wipe this 2.4 and try to install 3 from the OOo site.  

Will update.  And thanks for the point to that thread.  :)  I'll thank caraboy over there, too.  :)

Cheers!

If it will help I will post everything I added to have OO3 working like the launchpad update on my 2 other computers, the install you did if your running intrepid should be OO3.

---

### Post by solwic on 2008-12-09
Guess I'm reformatting and reinstalling Kubuntu.

Teach me to try and upgrade something in Linux, right?  

Be back in a few hours.  :P

---

### Post by solwic on 2008-12-09
> **frankleeee said:**
> If it will help I will post everything I added to have OO3 working like the launchpad update on my 2 other computers, the install you did if your running intrepid should be OO3.

I appreciate it, but it's probably easier to reformat.  I'll just leave it at 2.4 next time.  

Thanks for the help, but I'm on a deadline lol.  Formats are fast.  :)  Thanks again.  :)

---

### Post by coffeedrinker on 2008-12-10
While waiting for a new upgrade to correct this bug, you can just uninstall the openoffice.org-kde package. The look will be a little ugly but it will work !
```
sudo apt-get remove openoffice.org-kde
```
Good luck !

---

### Post by CyberAngel on 2008-12-10
> **coffeedrinker said:**
> While waiting for a new upgrade to correct this bug, you can just uninstall the openoffice.org-kde package. The look will be a little ugly but it will work !
```
sudo apt-get remove openoffice.org-kde
```
Good luck !


Looks very ugly but at least works...

---

### Post by solwic on 2008-12-10
> **CyberAngel said:**
> Looks very ugly but at least works...

Yeah it was very ugly.  I ended up formatting and reinstalling Kubuntu.  Very sad that the old Windows fix-all applies to Kubuntu, as well.  

Ah well...at least I learned an important lesson.  It's *still* not safe to upgrade programs in Linux.  :P

But hey, it's free..can't beat the price, no matter the bugs.  :cool:

---

### Post by ajcham on 2008-12-10
> It's still not safe to upgrade programs in Linux.

That's a bit harsh.  The bug in question, in my experience, only occurred in KDE - I could still use OOo3 in Gnome, although I've now decided to revert to 2.4 until the newer version is supported in the repositories.

In any case, if you are unhappy with an upgrade, it is simple (and quick) enough to uninstall it and reinstall the old package from the repos.  The reformat/reinstall was entirely unnecessary.

---

### Post by CyberAngel on 2008-12-10
I think I can live with this ugliness until the fix comes out in the repository :)

---

### Post by solwic on 2008-12-10
> **ajcham said:**
> That's a bit harsh.  The bug in question, in my experience, only occurred in KDE - I could still use OOo3 in Gnome, although I've now decided to revert to 2.4 until the newer version is supported in the repositories.

In any case, if you are unhappy with an upgrade, it is simple (and quick) enough to uninstall it and reinstall the old package from the repos.  The reformat/reinstall was entirely unnecessary.

Well you're half right.  It was a bit harsh.  I was still a little peeved at having to redo the entire system.  

As for uninstalling the upgrade and reinstalling the old package, it was neither simple nor quick:  every version I installed after I updated crashed except for one, and it was a pure text-based version that had no icons, graphics, or other non-text elements.  I'm sorry, but this is 2008, and that very outdated copy of version 2.4 that did work looked like it belonged in 1988.  Yeah, maybe that's nitpicking over the aesthetics, but keep in mind the update should never have broken it in the first place.  And once it did, it should have been simple to remove...but it wasn't.

Yeah, the reformatting wasn't *necessary*; in the end, with enough time to scour Google and these forums, I'm sure I could have fixed the problem.  But like I said, I'm a writer, and I have deadlines; reformatting was *faster* than troubleshooting and (hopefully) fixing the bug.  

But I'm back with a fresh install of Kubuntu now, and the knowledge that it doesn't pay to deviate from the Ubuntu repositories.  Yeah that makes me feel a little leashed, but it beats the alternative (Windows) and is cheaper than the only upgrade I know of (Mac). 

I remain a happy, satisfied Kubuntu user.  After all, *I'm* the one who tried to upgrade OOo; it's not like Kubuntu tried to upgrade it.  I brought the problem on myself.  Can't blame anybody but me for that.  :P

---

### Post by CyberAngel on 2008-12-11
> **jrock612 said:**
> Well you're half right.  It was a bit harsh.  I was still a little peeved at having to redo the entire system.  

As for uninstalling the upgrade and reinstalling the old package, it was neither simple nor quick:  every version I installed after I updated crashed except for one, and it was a pure text-based version that had no icons, graphics, or other non-text elements.  I'm sorry, but this is 2008, and that very outdated copy of version 2.4 that did work looked like it belonged in 1988.  Yeah, maybe that's nitpicking over the aesthetics, but keep in mind the update should never have broken it in the first place.  And once it did, it should have been simple to remove...but it wasn't.

Yeah, the reformatting wasn't *necessary*; in the end, with enough time to scour Google and these forums, I'm sure I could have fixed the problem.  But like I said, I'm a writer, and I have deadlines; reformatting was *faster* than troubleshooting and (hopefully) fixing the bug.  

But I'm back with a fresh install of Kubuntu now, and the knowledge that it doesn't pay to deviate from the Ubuntu repositories.  Yeah that makes me feel a little leashed, but it beats the alternative (Windows) and is cheaper than the only upgrade I know of (Mac). 

I remain a happy, satisfied Kubuntu user.  After all, *I'm* the one who tried to upgrade OOo; it's not like Kubuntu tried to upgrade it.  I brought the problem on myself.  Can't blame anybody but me for that.  :P

I like such happy users :D

---

### Post by ITC on 2008-12-11
Have a look at [https://answers.launchpad.net/ubuntu/+source/openoffice.org/+question/14961](https://answers.launchpad.net/ubuntu/+source/openoffice.org/+question/14961)

---

### Post by hyper_ch on 2008-12-11
> **jrock612 said:**
> It's *still* not safe to upgrade programs in Linux.

It is safe to upgrade in linux but you chose to use applications that are not in the official repos ;)

Btw, wanna update to KDE 4.2? ^^

---

### Post by CyberAngel on 2008-12-11
> **ITC said:**
> Have a look at [https://answers.launchpad.net/ubuntu/+source/openoffice.org/+question/14961](https://answers.launchpad.net/ubuntu/+source/openoffice.org/+question/14961)

I Tried the proposed solution but now it doesn`t work...
The only way to make it work (but ugly :P ) is to uninstall openoffice.org-kde

---

### Post by solwic on 2008-12-15
> **hyper_ch said:**
> It is safe to upgrade in linux but you chose to use applications that are not in the official repos ;)

Btw, wanna update to KDE 4.2? ^^

I ended up doing that, and it was quite simple.  Buggy (it *is* beta, though), but very easy.  In the end I ditched Kubuntu and went back to Ubuntu.  And I'm glad I did.  Turned out it was likely Kubuntu, not OOo, that was giving me all the grief.  :P

---

### Post by solwic on 2008-12-15
UPDATE:  I'm starting to think the problem wasn't with OOo...but with Kubuntu.  I followed the same instructions in Ubuntu that I used in Kubuntu (both versions 8.10)...the one for Kubuntu hosed the system, the one in Ubuntu is working like a charm.

So I guess it's a KDE problem?  I don't know enough about it to do more than speculate.

Anyway...cheers!  :)

---

### Post by KayakJim on 2008-12-17
> **jrock612 said:**
> UPDATE:  I'm starting to think the problem wasn't with OOo...but with Kubuntu.  I followed the same instructions in Ubuntu that I used in Kubuntu (both versions 8.10)...the one for Kubuntu hosed the system, the one in Ubuntu is working like a charm.

So I guess it's a KDE problem?  I don't know enough about it to do more than speculate.

Anyway...cheers!  :)

You are correct in that the problem is with KDE. I have 2 laptops - one running Ubuntu and the other Kubuntu.

OpenOffice 3 in Ubuntu runs fine but in Kubuntu it dies with the document recovery error.

I have encountered fewer errors with Ubuntu than with Kubuntu.

---

### Post by mvanlint on 2009-01-02
> **coffeedrinker said:**
> While waiting for a new upgrade to correct this bug, you can just uninstall the openoffice.org-kde package. The look will be a little ugly but it will work !
```
sudo apt-get remove openoffice.org-kde
```
Good luck !


After installing OpenOffice 3.0 in KUbuntu 8.10, I got the "unexpected error". Removing the /home/.OpenOffice directory did not help. I then uninstalled en reinstalled OpenOffice using Adept to no avail.

Next, I tried "sudo apt-get remove openoffice.org-kde" from the command line. Perhaps, Adept wasn't removing everything, I wondered? It occurred to me, however, that using this command only about 300 Kb was going to be freed. After apt-get had finished, all of the links to the OpenOffice suite were still in the menu.

However, clicking on one of them, started OpenOffice without any "unexpected errors". I now have a working OpenOffice 3.0 in KDE, but I don't understand what happened, why it is working and what was actually removed...

---

### Post by CyberAngel on 2009-01-02
> **mvanlint said:**
> After installing OpenOffice 3.0 in KUbuntu 8.10, I got the "unexpected error". Removing the /home/.OpenOffice directory did not help. I then uninstalled en reinstalled OpenOffice using Adept to no avail.

Next, I tried "sudo apt-get remove openoffice.org-kde" from the command line. Perhaps, Adept wasn't removing everything, I wondered? It occurred to me, however, that using this command only about 300 Kb was going to be freed. After apt-get had finished, all of the links to the OpenOffice suite were still in the menu.

However, clicking on one of them, started OpenOffice without any "unexpected errors". I now have a working OpenOffice 3.0 in KDE, but I don't understand what happened, why it is working and what was actually removed...

The openoffice KDE integration has been removed... That`s all.
Now it look quite ugly.. Isn`t it?
Huge letters on the menus...
Weird colors...

---

### Post by mvanlint on 2009-01-03
> **CyberAngel said:**
> The openoffice KDE integration has been removed... That`s all.
Now it look quite ugly.. Isn`t it?
Huge letters on the menus...
Weird colors...

Yes, it has a unique look...
I managed to reduce the font size (Tools/Options/View/Scaling)
At least the neighbours from across the street can no longer read along... :-)

---

### Post by littlepear on 2009-01-03
New:
Oops. Spoke too soon. Still getting the error.
It seems to want to open a new document, but doesn't quite finish, so when I click the Writer icon again, it begins a document entitled Untitled2. The firstborn document Untitled1 is still half there in memory, though, and he wreaks havoc sometimes when - in a jealous rage - he tries to wrestle control over Untitled2.

Old:
:KSAmazing. Thanks for the answer. My Oo 3.0 is very happy now, though I'm not sure what happened. And, I see no ugliness!

> $ sudo apt-get remove openoffice.org-kde
...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openoffice.org-kde is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libservlet2.4-java libxalan2-java bsh-gcj libhsqldb-java bsh
  libxalan2-java-gcj
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by vankaszaner on 2009-01-07
I installed openoffice.org-kde from debian repository. Seems to work and is integrated with kde.

I took the package from: [http://http.at.debian.org/debian/pool/main/o/openoffice.org/openoffice.org-kde_3.0.1~rc1-2_i386.deb](http://http.at.debian.org/debian/pool/main/o/openoffice.org/openoffice.org-kde_3.0.1~rc1-2_i386.deb)

---

### Post by CyberAngel on 2009-01-14
After the last upgrade the problem with the "Document Recovery" has been fixed but I found another one when I`m installing the package openoffice.org-kde

I can open documents and everything but when I`m trying to export a pdf or save, then openoffice is freezing (Sometimes the whole plasma shell)!

Anyone else has a similar behavior?

When I unistall the package openoffice.org-kde everything is normal again including the ugliness of openoffice :P

I am using KDE 4.2 RC1 from the kubuntu-members-kde4 repositories.

---

