---
title: "Ubuntu in cyber cafes/internet shops"
date: 2005-09-19
forum: Desktop Environments
---

### Post by Nicolai on 2005-09-19
\\:D/ 

We use Ubuntu 5.04 for an Internet cafe. Yipee! We closed one weekend and migrated all the workstations to Ubuntu. 

We configured a guest account to login automatically. On our second day, we've realized that new users experimenting with Linux (or worse, just want to play around) will reconfigure our desktop configuration and move around the icons and stuff!

The next user who uses the computer gets a messy desktop (if s/he's lucky) or worse, something unusable and unfriendly.

Any solution for this?

How about other apps for keeping time and stuff?

---

### Post by 91004 on 2005-09-19
[QUOTE=Nicolai]\\:D/ 

We use Ubuntu 5.04 for an Internet cafe. Yipee! We closed one weekend and migrated all the workstations to Ubuntu. 

We configured a guest account to login automatically. On our second day, we've realized that new users experimenting with Linux (or worse, just want to play around) will reconfigure our desktop configuration and move around the icons and stuff!

The next user who uses the computer gets a messy desktop (if s/he's lucky) or worse, something unusable and unfriendly.

Any solution for this?

How about other apps for keeping time and stuff?[/QUOTE]
 I am a Ubuntu Linux Newbie, and with limited knowledge, however after playing around with it for a couple of weeks I think you can probably disallow user access by going to the following:

System====>Administration====>Users and Groups 

There are options to allow/disallow users interfacing with the system ...

Give it a try.... I don't believe you can hurt a user account by changing that particular user account only.....

---

### Post by Nicolai on 2005-09-19
Already done that. The default Desktop user is a guest account using the Desktop Profile only.

---

### Post by Deekin on 2005-09-20
[QUOTE=Nicolai]\\:D/ 

We use Ubuntu 5.04 for an Internet cafe. Yipee! We closed one weekend and migrated all the workstations to Ubuntu. 

We configured a guest account to login automatically. On our second day, we've realized that new users experimenting with Linux (or worse, just want to play around) will reconfigure our desktop configuration and move around the icons and stuff!

The next user who uses the computer gets a messy desktop (if s/he's lucky) or worse, something unusable and unfriendly.

Any solution for this?

How about other apps for keeping time and stuff?[/QUOTE]
 Hiya!

Any harm in running them off of live CDs? A power cycle makes everything all nice and purty, and will reduce your downtime when someone futzes with something under the hood.

---

### Post by heimo on 2005-09-20
I don't know much about this subject, but I can give you one good search phrase: "kiosk mode". I believe KDE has better support for locking desktop changes. Here's Linux Journal article about it:
[http://www.linuxjournal.com/article/7718](http://www.linuxjournal.com/article/7718)

I'd also check if Edubuntu is going to implement something which could help setting up and recovering from misconfigured workstations. (network boot, kiosk mode..) It would be great to here more about your setup, how customers like Ubuntu (any problems?) and so on. :)

---

### Post by Nicolai on 2005-09-20
I thought about the liveCD option. One problem though, we don't have CDROM drives on public workstations.

All computers run Ubuntu, including ancient P166 router with a large 92 MB of RAM. 

We also have a printer shared via Samba on another workstation used by the staff for printing. The router also acts up as a file server for the 30-odd machines in the network.

Immediate **Issues / Concerns**[list]
[*]Messed up computer desktop. 
Some customers drag and move around the menus, leaving it in a sorry state, if we're lucky.

Our Linux "expert" (who's only into linux by a few months ahead of us) says that he might recommende using XFCE but it might be too radical for most customers.

[*]data on floppy drives
We have edited our fstab to read vfat instead of autodetecting floppy drive filetypes. The default seems to be msdos, and we have trouble reading long filenames.

We also have issues recognizing some floppies, and customers not unmounting ther floppies.

[*]openoffice
Our customers keep on complaining about the difficulting in saving their files on floppies (or retrieving their data from it)

Is there an easier way of making OO friendlier in this regard?
[/list] 

The move was so radical, to say the least. The whole staff is always busy answering questions and supporting users - sometimes, we don't even know the answers ourselves. (Thank you Google)

I think some scripts for cleanup would be nice (if that's the solution for the messed up desktop)

We still need a good solution for data on floppies (which are formatted in FAT or DOS)

---

### Post by kblood on 2005-09-20
Ok, I am also quite a newbie, but I know that at least for the Gnome menus there is a hidden file in the home folder of the user.

Perhaps the solution is "as simple as" creating a shell script that overwrites this file with a clean version every time the Guest user logs on.

I think that if you look around the home folder, you will see a lot of hidden files and folders (starting with .) that could also be backed up when they are clean, and restored every time you log on.

Just an idea.

---

### Post by daveisadork on 2005-09-20
[QUOTE=kblood]Ok, I am also quite a newbie, but I know that at least for the Gnome menus there is a hidden file in the home folder of the user.

Perhaps the solution is "as simple as" creating a shell script that overwrites this file with a clean version every time the Guest user logs on.

I think that if you look around the home folder, you will see a lot of hidden files and folders (starting with .) that could also be backed up when they are clean, and restored every time you log on.

Just an idea.[/QUOTE]

Yeah, just write a script that deletes everything from the home folder on logout and then copies everything back from a dummy account or something.

---

### Post by osioke on 2006-09-09
> **Nicolai said:**
> \\:D/ 

We use Ubuntu 5.04 for an Internet cafe. Yipee! We closed one weekend and migrated all the workstations to Ubuntu. 

How about other apps for keeping time and stuff?

Hello Nicolai,

How has your Internet Cafe been running with Ubuntu so far?  I would like feedback from you as I am about to do the same with xubuntu.  I am also interested in how you are accomplishing the following:

1. Keeping time

2.  Instant messaging; basically managing user expectation when they want to do voice and video/webcam on yahoo or msn but gaim doesn't support this yet.

3. Locking the system; i.e. running in kiosk mode so that users don't change system settings yet allowing the user to run any program he or she needs to.

4. Anything else you have learned from you experience so far, including if you would switch to xubuntu (as it is more efficient for system resources [so I read]) or remain with ubuntu.

You may reply here or (preferrably) send me email: [email]osioke@gmail.com[/email]

Cheers!
-Osioke

---

### Post by osioke on 2006-09-09
> **Nicolai said:**
> \\:D/ 

We use Ubuntu 5.04 for an Internet cafe. Yipee! We closed one weekend and migrated all the workstations to Ubuntu. 

How about other apps for keeping time and stuff?

Hello Nicolai,

How has your Internet Cafe been running with Ubuntu so far?  I would like feedback from you as I am about to do the same with xubuntu.  I am also interested in how you are accomplishing the following:

1. Keeping time

2.  Instant messaging; basically managing user expectation when they want to do voice and video/webcam on yahoo or msn but gaim doesn't support this yet.

3. Locking the system; i.e. running in kiosk mode so that users don't change system settings yet allowing the user to run any program he or she needs to.

4. Anything else you have learned from you experience so far, including if you would switch to xubuntu (as it is more efficient for system resources [so I read]) or remain with ubuntu.

You may reply here or (preferrably) send me email: [email]osioke@gmail.com[/email]

Cheers!
-Osioke

---

### Post by sabitha on 2006-09-09
i already do that ---- use ubuntu for all (server and client) on my internet cafe. all fine :
1. keeping time (billing sofware) i use manual time (OO0-spreedsheet):(
2. Instant Messanging --- GyachI (Yahoo client with webcam support)
3. use gnome (ubuntu)

---

### Post by sabitha on 2006-09-09
i already do that ---- use ubuntu for all (server and client) on my internet cafe, all running from Ubuntu 5.04 till now Dapper 6.06.1. all fine :
1. keeping time (billing sofware) i use manual time (OO0-spreedsheet):(
2. Instant Messanging --- GyachI (Yahoo client with webcam support)
3. use gnome (ubuntu)

---

### Post by booleanB on 2008-07-04
Thanx for the info on the kiosk mode *heimo*, i'll try that in my cyber cafe

---

