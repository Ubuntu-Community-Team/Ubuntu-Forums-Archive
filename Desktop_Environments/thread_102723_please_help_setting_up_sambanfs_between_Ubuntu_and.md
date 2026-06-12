---
title: "please: help setting up samba/nfs between Ubuntu and OS X"
date: 2005-12-12
forum: Desktop Environments
---

### Post by megamania on 2005-12-12
I'm literally going crazy... I've been searching the forum and the web, but I'm still without a clue.

I need to set up a samba or nfs share between an Ubuntu PC and a OS X Tiger Powerbook G4.

I'm relatively new to linux, but I share folders between two Ubuntu machines (via NFS) with no problem, and in the past I set up a samba share between mandrake and windows in a few minutes.

Has anybody done this Ubuntu-OsX connection? Can you point me to a step-by-step procedure? As I said, I've seen other posts (probably too many) in the forum, but I'm lost.

Any help will be *sincerely* appreciated.

---

### Post by Arador on 2005-12-12
[QUOTE=megamania]I'm literally going crazy... I've been searching the forum and the web, but I'm still without a clue.

I need to set up a samba or nfs share between an Ubuntu PC and a OS X Tiger Powerbook G4.

I'm relatively new to linux, but I share folders between two Ubuntu machines (via NFS) with no problem, and in the past I set up a samba share between mandrake and windows in a few minutes.

Has anybody done this Ubuntu-OsX connection? Can you point me to a step-by-step procedure? As I said, I've seen other posts (probably too many) in the forum, but I'm lost.

Any help will be *sincerely* appreciated.[/QUOTE]
I know next to nothing about Mac OS X, but I know that it supports both.
Since it is a UNIX-like OS, it should be the same as mounting NFS or SMB from linux.
When using smb url's, keep in mind that you will have to use *[noparse]smb://host/folder[/noparse]* urls, not *[noparse]file://host/folder/[/noparse]* style url's like windows uses.

---

### Post by megamania on 2005-12-12
thank you. I've just managed to *read* my mac's folders on the ubuntu machine by entering the following in Firefox:

smb://192.168.1.65/user/

but how can I *write* from Ubuntu to my Mac?

(I still can't access my ubuntu machine's shared folders from the mac, but that's a different story...)

---

### Post by megamania on 2005-12-19
One week has passed and... well, I'm still stuck.

When I try to connect from the mac to the ubuntu pc ("connect to server" from mac osx) I get the following message (I'm translating it into english)  "unable to connect because some elements are missing". 

If I enter the wrong password, the error message changes accordingly, so I assume that when I enter it correctly it *does* recognize username and password, but does not connect.

Trying from the Ubuntu machine, I'm not even able to connect to the mac via firefox (that only worked once).

Some info:
- I did create the samba user and password on the ubuntu machine.
- I enabled "windows folder sharing" on the mac
- From the mac, the domain/workgroup shows up on the "network" windows, but if I click "connect" the finder freezes (as I said above, if I try "connect to server" I get a "elements missing" message)

Any ideas? Is there anybody out there who's currently sharing a directory between Ubuntu and a Mac OS X machine? Can I have your smb.conf file and other details that made it work?

I'm so frustrated that I'm considering selling the mac...  :-|

---

### Post by thekurst on 2005-12-19
Hey, there is a compatablility issue with the version of Samba that shipped with Ubuntu 5.10 and OS X Finder which is why the Finder crashes when you try to browse to the Ubuntu Samba share.

I simply set up my samba file share with a full read/write permissions, I created a user only for the share and gave that user full control.

Use "Command + K" in the finder and user smb://192.168.1.1/share and you should be able to connect no prob.

The Ubuntu developers should release a Samba update to fix this issue but they don't seem to think it is a big enough deal.

---

### Post by megamania on 2005-12-20
First of all, thank you for trying to help. Looks like this thread doesn't arouse people's curiosity  :-) , or maybe not so many people have ubuntu and mac os x running side by side.

Unfortunately, it doesn't work. Can you please post/send your smb.conf file? I keep getting the "elements missing" error...

---

### Post by ducman on 2005-12-21
I haven't had any trouble connecting to an SMB share on the linux box from a Mac OS X machine. Easiest way to do it is simply right-click on a folder in Natuilus and share it. 

In my testing, AFP seems to work better and faster, so I'm acually using netatalk instead of samba to allow access to my server from the Macs. I used "aptitude install netatalk" to install and then added some shares to the /etc/netatalk/AppleVolumes.defaults file. Here's a snippet from that file:

~/                      "Home Directory"
/home/shared/music      Music           allow:@itunes

The first line was there already, and may be all you need. I added the second line to let multiple machines access one shared folder, and to limit access to that folder to people in the itunes group.

Then, on a Mac, I use command-K in the Finder and enter "afp://{servername}" to connect.

---

### Post by shelbydz on 2006-02-01
This worked like a charm for me. Don't use finder, and make sure you use your username/password from your ubuntu box.

thanks for the help. . .shawn

---

### Post by nosarembo on 2007-06-10
I had the same problem as megamania (Feisty / OSX 10.4) and ducman's technique worked a treat for me.

I shared a folder on my Ubuntu Desktop called "Downloads":

1. Installed netatalk through System > Administration > Synaptic
2. Opened Applications > Accessories > Terminal, typed "sudo gedit"
3. In gedit, opened /etc/netatalk/AppleVolumes.defaults
4. Added the line "/home/<account name>/Desktop/Downloads allow:@users"
5. Setup a generic account and added it to the "users" group in System > Administration > Users And Group
6. On the Mac, in Finder, pressed Apple-K and entered the address as "afp://192.168.1.<digit>" (the IP of my Ubuntu box)

Done!

Cheers, -- Noz

---

### Post by thousandrobots on 2007-06-14
i am having the same problem. i keep getting an "incorrect password" error. i would really like to get SMB working (rather than AFS), so i can share with windows users, too, and also just because it *should* work. 

on an old debian box a few years ago, i got SMB working just fine using an OS X client, so I'm confused why it's not working easily now.

could it have anything to do with default workgroup? my mac (i think) was part of one workgroup, and the linux box seems to be defaulting to the workgroup "mshome". i guess i could change this in smb.conf or whatever it's called, but i'd rather change it on the mac. i've done it before, but i'm having trouble remembering how to do that, and for some reason, i can't find it via google right now.

update: i have them in the same workgroup now (by editing smb.conf), but i am still getting the incorrect password error. i tried turning off password encryption, but that had no effect.

i found [an old wiki page]("http://wiki.thousandrobots.com/index.php?title=Samba") i started on this topic a while back, so i will check it for tips.

---

### Post by kugn on 2007-06-14
In my experience smb sharing between ubuntu and mac I had to set up a SMB account and password in terminal. See this thread [http://ubuntuforums.org/archive/index.php/t-37386.html](http://ubuntuforums.org/archive/index.php/t-37386.html)

---

### Post by thousandrobots on 2007-06-14
kugn,

Thank you SO MUCH. That fixed my problem instantly.

For future reference, all you have to do is go into terminal, then login as root (su), then:

smbpasswd -a newusername

the newusername can be the name of an existing user on your box.

after that, i restarted samba just to be sure:

/etc/init.d/samba restart

then i logged in from the mac with no problem!

---

