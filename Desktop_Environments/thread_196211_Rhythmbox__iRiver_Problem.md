---
title: "Rhythmbox / iRiver Problem"
date: 2006-06-13
forum: Desktop Environments
---

### Post by Jonathan Wiebe on 2006-06-13
Since upgrading to Dapper I have had a problem accessing my iRiver iFP-780 ogg/mp3 player.

Prior to upgrading access worked just fine with the ifp-line program in Breezy. During my upgrade the ifp-line package was uninstalled however. When I checked the new Dapper repositories I found and installed the ifp-line-libifp package which seemed to have the same functionality. Unfortunately this is not working.

Now when I plug my iRiver player into a USB port the Rhythmbox application is automatically launched. In Rhythmbox I see all the files from my usual music library but I don't see any way to access my iRiver player.

When I try to access my player using the ifp program from the ifp-line-libifp package I get the following response:

$ ifp ls
Device is busy.  (I was unable to claim its interface.)

This response is consistent whether I leave Rhythmbox running or shut it down after is auto-launches.

I don't know whether this is a Ubuntu issue or whether I should file this as a bug upstream with Rhythmbox / ifp-line-libifp.

Any help or pointers to help would be appreciated.

Regards,

Jonathan Wiebe

---

### Post by jISh on 2006-06-13
I can't help with your exact problem, as I'm pretty new to this, but I can tell you that I use ifp-gnome for my iRiver flash player, works great.

[http://ifp-gnome.sourceforge.net/](http://ifp-gnome.sourceforge.net/)

---

### Post by Jonathan Wiebe on 2006-06-14
No joy I'm afraid.

After installing ifp-gnome I still get errors. It looks like rhythmbox is hijacking the connection to my flash player from the moment it is connected.

Thanks anyway for your tip.

---

### Post by handdog on 2006-06-20
I'm having issues as well... One thing I noticed was that when I was logged in as root, I could run ifp-gnome and it would list content (but I still couldn't update the music on the player) Without root, I couldn't even load the device.

My rhythmbox opens too, but has no access to my iRiver. The user is in the hotplug group, but this doesn't help. Any ideas?

---

### Post by mtpadilla on 2006-07-12
I've been having similar issues using my iRiver ifp-790 (with the factory installed firmware). I've also found that Rhymbox is automatically fired up, which is annoying and something I'd like to stop from happening. ifp-Gnome, however, works whenever I run it. ifp-line fails for me with the exact same "Device is busy. (I was unable to claim its interface.)" message. However, when I run as root it works beautifully. The same can be said for the program  ifpgui, which is a KDE app much more powerful that ifp-gnome. I would recommend checking out ifpgui. One useful reference for iRiver issues that might be worth a look, although it doesn't seem to address our rhythmbox woes is www.tuxmagazine.com's Oct 2005 issue (mentioned on another thread related to iriver). you can do a quick regisistration and then download the pdf file for that issue.

---

### Post by cwalte on 2006-07-22
I've got the same problem as well. Rhythmbox opens and I get the "device is busy" message when I run ifp -ls.

---

### Post by silux on 2006-07-26
I have the same issue or at least symptoms... a couple of notes of things I have noticed that I didn't see commented on:

I get an error when running as non root to add the user to plugdev which makes no difference whatsoever.

You can disable rythmbox from starting up automatically by going to system->prefrences->removable drives and media->multimedia and uncheck the play music files when connected... this seems to make no difference as well though.

---

### Post by ToniVR on 2006-08-29
It is a permission problem. Try to do 'ifp ls' as root (sudo ifp ls). That works here.

I know how to solve this with hotplug, but that seems to be kicked out from Dapper. No idea how to acomplish the permission on Dapper :(

---

### Post by kxs on 2006-11-08
> **Jonathan Wiebe said:**
> 
$ ifp ls
Device is busy.  (I was unable to claim its interface.)

same problem here. isn`t there a way to solve this? accessing my ifp-895 only as root is really annoying - I have to change files` permissions as well when I download them from ifp to my pc ](*,)

---

### Post by crimesaucer on 2006-12-11
-off topic--

hey kxs, where is Homer's crayon?

---

### Post by macinnisrr on 2007-01-16
try going to system>preferences>removable drives and media, click on the multimedia tab, and uncheck the option "play music files when connected", in the portable media player section.  This should stop rhythmbox from starting when you connect your iriver.

---

### Post by RDiamond on 2007-02-20
Being able to access the iRiver device only as root can be fixed by creating a udev rules file for it. See this message for details: [http://ubuntuforums.org/showpost.php?p=2185978&postcount=4](http://ubuntuforums.org/showpost.php?p=2185978&postcount=4)

---

### Post by maxwellcom on 2007-02-24
thanks for the info in this thread - having the same problems but got it to work by:

1. installing ifpgui via synaptic
2. going to System --> Preferences --> Menu Layout
3. double clicking on "ifpgui" and adding "sudo" to the beginning of the command line.

it works great - better than iriver's music manager :)

./ndm

---

### Post by PowerlessRacing on 2007-05-15
> **maxwellcom said:**
> thanks for the info in this thread - having the same problems but got it to work by:

1. installing ifpgui via synaptic
2. going to System --> Preferences --> Menu Layout
3. double clicking on "ifpgui" and adding "sudo" to the beginning of the command line.

it works great - better than iriver's music manager :)

./ndm

You left out that you have to check to run in a terminal.
The better solution is to uncheck the box to run in a terminal and add gksudo instead of sudo to the beginning of the line.  Good luck!

---

