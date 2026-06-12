---
title: "Could not find mime type"
date: 2006-01-17
forum: General Help
---

### Post by gbullit on 2006-01-17
Hi every time i open Konquerer I get a message saying: 
Sorry - Konquerer
Could not find mime type
application/octet stream
How do I fix this and what is the reason for the message? :confused:
My hardware:
MSI  K8N Neo4, AMD Athlon 64 3500+, Corsair 2x512 DDR400 Dual Channel, Gainward FX 6600 GT 256 Mb PCI-express, Maxtor S-ATA 160 Gb, 17&#8221; TFT screen

---

### Post by sharke on 2006-01-17
KDE returns "Couldn't find MIME type application/octet-stream" at startup and/or Konqueror returns the same error message when launching whatever application.

Start the Control Center With sudo kcontrol in terminal and open KDE Components/File Associations, 
Expand "application", you will probably see that there's no entry for "octet-stream".
Click on "Add...", for "Group" select "application" and for "Type Name" fill in "octet-stream". This should fix it.
Regards
Sharke

---

### Post by gbullit on 2006-01-17
Hi Sharke, I did what you said and get the following message:
 WARNING: KServiceType::offers : servicetype application/octet-stream not found
regards
GB

---

### Post by Rog131 on 2006-01-18
Error: Could not find mime type application/octet stream

Sometimes ~/.kde/share/mimelnk/application/octet-stream.desktop get messed.

Solution: Rename (/delete) octet-stream.desktop -> KDE make new.

---

### Post by tabinin on 2006-01-28
Thank you Rog131!  I was having this problem and wasn't able to fix it until I read your post.  It was getting really annoying to click OK to the error message about 20 times a day.

---

### Post by Seàn1 on 2006-11-26
> **Rog131 said:**
> Error: Could not find mime type application/octet stream

Sometimes ~/.kde/share/mimelnk/application/octet-stream.desktop get messed.

Solution: Rename (/delete) octet-stream.desktop -> KDE make new.

Well, as is usually the case I come crawling back to these forums for a decent solution when the shrapnel hits the fan. :)

Thanks a million for that perfect solution -really. This (apparently long-standing -years) bug made booting problematic and caused _many_ error dialogues to occur on top of each other for me and this eliminates that symptom immediately (no reboot or closing apps needed etc). 'twas odd too, this is a new KDE install (trying it out for accessibility support over gnome) and my best guess was Kaffeine changing something upon first start as that's about the only thing I'd done before this started and it does change file types (mms association etc.

Perhaps of interest (or not!) to other passersby:

[http://www.redhat.com/archives/rhl-list/2005-July/msg00230.html](http://www.redhat.com/archives/rhl-list/2005-July/msg00230.html)
[http://www.linuxforums.org/forum/215619-post1.html](http://www.linuxforums.org/forum/215619-post1.html)
[http://webservertalk.com/message1710394.html](http://webservertalk.com/message1710394.html)
[http://lists4.opensuse.org/opensuse/2006-04/msg02869.html](http://lists4.opensuse.org/opensuse/2006-04/msg02869.html)

Common thread there in that sample size 4/~30 I saw? Often, no response for over a year and counting (RedHat et al.) and all ultimately lacking solutions. Unlisted ones include lonely nerds deriding newbies and not attempting to be helpful (doubtful they could be anyway) but instead trolling and talking in circles with new participants. I'm quite certain that is why Ubuntu is the new fangled shining star of distros -fantastic people in forums like this. I'll be careful here, else I could start being a one distro fan boy soon... (-;
[SIZE="1"]
BTW, *yes* that qualifies as a rant but I just spent well over an hour trying to figure this out and I wanted to vent because I'm grateful![/SIZE]

---

### Post by 4ebees on 2007-03-19
Was this bugging me or what? :)

Thanks for the information. I must admit though that I was confused by what you meant here:

> ... -> KDE make new.

I'm not quite sure by what means one 'makes new'.

I ended up rebooting  :redface:

This appears to have fixed the problem, though I wouldn't mind further clarification.

Many thanks,




> **Rog131 said:**
> Error: Could not find mime type application/octet stream

Sometimes ~/.kde/share/mimelnk/application/octet-stream.desktop get messed.

Solution: Rename (/delete) octet-stream.desktop -> KDE make new.

---

### Post by soccermonstar13 on 2007-07-20
Yes a reboot seems to have been what he meant and Rog131's solution worked for me too :)

---

### Post by frokki on 2007-10-10
> **Rog131 said:**
> Error: Could not find mime type application/octet stream

Sometimes ~/.kde/share/mimelnk/application/octet-stream.desktop get messed.

Solution: Rename (/delete) octet-stream.desktop -> KDE make new.This worked for me also. Thank you very much!

---

### Post by Baka Dasai on 2007-10-26
Since upgrading from Feisty to Gutsy I have the same problem with *all* KDE apps.  All KDE apps are now completely non-functional.

I cannot run kcontrol - it crashes when run from the Kmenu, and is "empty" when run from the command line.

I cannot rename or delete ~/.kde/share/mimelnk/application/octet-stream.desktop as it doesn't exist.

Both apt-get and Adept tell me that there are no more packages to be installed, but it seems like KDE might have gotten itself in a mess during the update.

Any ideas?

---

### Post by wankel on 2007-10-26
> **Baka Dasai said:**
> Since upgrading from Feisty to Gutsy I have the same problem with *all* KDE apps.  All KDE apps are now completely non-functional.

(...)


Same here. I just added the octet-stream mime type via 
 Konqueror/Settings/Configure Konqueror/File Associations/Add (under Known Types)
 group application
 type name "octet-stream"

If I start Kcontrol per CLI, it seems the menu "Settings" is empty. Actually there are three items left in the settings entry in my menu, but those are no KDE entries. Editing the programs menu using KDE`s front end, does not show any item at all (no office, internet or whateverr either).

Updating from Feisty to Gutsy gave some problems, as the upgrade tool hang a few times. I ended doing:
 kill one of the http threads that root has running ( sudo ps -ef | grep apt )
 starting adept and fetch updates (entries are are altered to gutsy, no "new version" button)
 (doing a "safe" upgrade via the file menu hang somewhere as well, so I quit adept)
 sudo apt-get update gave some warnings, suggested me to run apt-get update, so did it twice)
 sudo apt-get install
 sudo apt-get upgrade
 sudo apt-get update (twice again)
 sudo apt-get dist-upgrade
 sudo apt-get autoremove

And now I am here,,, :-)

I will perform a reboot and post back to tell whether it solved the octet-stream message.

---

### Post by k2t0f12d on 2007-10-26
> **wankel said:**
> Same here. I just added the octet-stream mime type via 
 Konqueror/Settings/Configure Konqueror/File Associations/Add (under Known Types)
 group application
 type name "octet-stream"

Worked for me, thanks.

---

### Post by wankel on 2007-10-26
k2t0f12d, good to hear :-)

Luckily enough, it worked for me as well (I rebooted, maybe just logging out/in had done the trick).

After the reboot, there was a complaint about a file system check, but ignoring seemed to work.

Now all menus and KDE-specifics are in place again.

Good luck to others!

---

