---
title: "NWN Diamond + Modules Installer"
date: 2009-05-06
forum: Gaming &amp; Leisure
---

### Post by Boondoklife on 2009-05-06
I was looking to play some NWN today and noticed there are a number of different scripts that have to be used to install all the final parts! So I just consolidated them all

This script will install NWN Diamond + the on DVD Modules + the movies that come with it and more.

**All in all it will install the following:**
NWN CORE
Updates
SoU
HotU
Wyvern Crown
Infinite Dungeons
Pirates of the sword coast
King Maker
Shadow Guard
Witches Wake
Darkness Over DaggerFord
Community Expansion Pack 2.2

It also will install the movies for your viewing pleasure

There are a few required apps that need to be installed and the script will do it for you.

**Fixes and Hacks:**
Fix for BinkPlayer freezing (occured on Jaunty don't know about others)
Skip Intro Movies

**NOTE:** 
After installing the CORE Neverwinter Nights (option a), launch it and input your keys, then continue with the rest of the install

Some of the sections are borrowed from others and if you have their name I'll be glad to give credit, but I figured this could come in handy.

---

### Post by u235sentinel on 2009-05-06
> **maletek said:**
> I was looking to play some NWN today and noticed there are a number of different scripts that have to be used to install all the final parts! So I just consolidated them all

This script will install NWN Diamond + the on DVD Modules + the movies that come with it and more.

All in all it will install the following
NWN CORE
Updates
SoU
HotU
Wyvern Crown
Infinite Dungeons
Pirates of the sword coast
King Maker
Shadow Guard
Witches Wake
Darkness Over DaggerFord

It also will install the movies for your viewing pleasure

There are a few required apps that need to be installed and the script will do it for you.

Some of the sections are borrowed from others and if you have their name I'll be glad to give credit, but I figured this could come in handy.

Dang.  where were you last week.  I had to figure out how to uncompress and copy everything for NWN Diamond which takes quite some time :-)

I appreciate it.  I'm buying a few more copies.  My kids got wind of my native linux commercial games (such as this one) and all want copies.  So I'm buying a few more NWN Diamond and setting up a server so we can play on :-)

Good work!

---

### Post by Boondoklife on 2009-05-06
Heh yea that was me too! Let me know how it goes for you, I am running Jaunty and have reinstalled it a few times to test it and all seems to be working for me.

---

### Post by Duskao on 2009-05-09
I'm using Intrepid and it doesn't seem to want to install for me at all really. I'm fairly new to ubuntu so maybe I'm doing something wrong, but I have tried a few different things with it. 
First: I double clicked it and choose to "run in terminal" and it seemed to be running fine till the point of it installing. I got errors all the way down pretty much. (all options I left black with the exception of "is this a Debian based distrobution?" I put y. 
Second: I tried starting it in a terminal with "sh nwninstall.sh" it didn't like that, instant errors that seemed to never end. Exited terminal. 
Third: Same as second but with "sudo sh nwninstall.sh" same result as second.
Fourth: double clicked on it again and ran it in terminal again, but then copied all the options letter for letter, but got the same errors as with the first time I tried it. 

Any thoughts? Maybe a walkthough. Sorry guys. Like I said, I'm new...

---

### Post by mousestalker on 2009-05-09
Great installer!

Only issue I had was that it continued running after finishing its job. Being a total newb, I likely didn't do something I should have.

But Neverwinter nights is up and running, so thank you very much for doing this.

---

### Post by Boondoklife on 2009-05-09
> **Duskao said:**
> I'm using Intrepid and it doesn't seem to want to install for me at all really. I'm fairly new to ubuntu so maybe I'm doing something wrong, but I have tried a few different things with it. 
First: I double clicked it and choose to "run in terminal" and it seemed to be running fine till the point of it installing. I got errors all the way down pretty much. (all options I left black with the exception of "is this a Debian based distrobution?" I put y. 
Second: I tried starting it in a terminal with "sh nwninstall.sh" it didn't like that, instant errors that seemed to never end. Exited terminal. 
Third: Same as second but with "sudo sh nwninstall.sh" same result as second.
Fourth: double clicked on it again and ran it in terminal again, but then copied all the options letter for letter, but got the same errors as with the first time I tried it. 

Any thoughts? Maybe a walkthough. Sorry guys. Like I said, I'm new...

Hey, sorry ta hear ya having an issue, can you tell me what the answers you are giving to the script when it prompts? I know this may be kinda a dumb question but you are using a Diamond DVD right? Also if you have more than one cdrom drive or have custom mounts, iso's etc. then make sure you are giving the script that instead of /media/cdrom.

Lemme know

Run in terminal is fine or you can launch it from the command line. you should not have to run it as sudo as I have sudo calls in the script where needed.

---

### Post by Duskao on 2009-05-10
Here are some of the errors.

checkdir error:  cannot create texturepacks
                 unable to process texturepacks/xp2_tex_tpc.erf.
error:  cannot create xp2.key
--2009-05-10 01:50:02--  [http://nwdownloads.bioware.com/neverwinternights/linux/gold/nwclientgold.tar.gz](http://nwdownloads.bioware.com/neverwinternights/linux/gold/nwclientgold.tar.gz)
Resolving nwdownloads.bioware.com... 204.50.199.10
Connecting to nwdownloads.bioware.com|204.50.199.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7559227 (7.2M) [application/x-tar]
nwclientgold.tar.gz: Permission denied

Cannot write to `nwclientgold.tar.gz' (Permission denied).
--2009-05-10 01:50:02--  [http://files.bioware.com/neverwinternights/updates/linux/169/English_linuxclient169_xp2.tar.gz](http://files.bioware.com/neverwinternights/updates/linux/169/English_linuxclient169_xp2.tar.gz)
Resolving files.bioware.com... 204.50.199.15
Connecting to files.bioware.com|204.50.199.15|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://na.llnet.bioware.cdn.ea.com/u/f/eagames/bioware/neverwinternights/updates/linux/169/English_linuxclient169_xp2.tar.gz](http://na.llnet.bioware.cdn.ea.com/u/f/eagames/bioware/neverwinternights/updates/linux/169/English_linuxclient169_xp2.tar.gz) [following]
--2009-05-10 01:50:03--  [http://na.llnet.bioware.cdn.ea.com/u/f/eagames/bioware/neverwinternights/updates/linux/169/English_linuxclient169_xp2.tar.gz](http://na.llnet.bioware.cdn.ea.com/u/f/eagames/bioware/neverwinternights/updates/linux/169/English_linuxclient169_xp2.tar.gz)
Resolving na.llnet.bioware.cdn.ea.com... 208.111.128.7
Connecting to na.llnet.bioware.cdn.ea.com|208.111.128.7|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 506025948 (483M) [application/x-tar]
English_linuxclient169_xp2.tar.gz: Permission denied

Cannot write to `English_linuxclient169_xp2.tar.gz' (Permission denied).
tar: nwclientgold.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
tar: English_linuxclient169_xp2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
/home/james/Desktop/nwninstaller/nwninstall.sh: line 242: ./fixinstall: No such file or directory
sed: can't read nwn: No such file or directory
rm: cannot remove `nwclientgold.tar.gz': No such file or directory
rm: cannot remove `English_linuxclient169_xp2.tar.gz': No such file or directory
Installation Complete


I get similar "checkdir" errors with what looks to be like almost every file that tried to get installed. 

The answers I am giving are what you have in the brackets, minus the brackts. When it says (root) I was putting "root" I thought that was weird, but I wasn't sure of what else to put. I also tried leaving them blank. Yes I am using the NWN Diamond DVD. The DVD looks to be mounted in /media/cdrom0 so that is what I put, but I have also tried /media/cdrom and just left it blank.


Edit: Nevermind, I seem to have got it working. 
Sorry for wasting your time, but thanks for being willing to help. And amazing work with this BTW.

---

### Post by Boondoklife on 2009-05-10
> **Duskao said:**
> Here are some of the errors.

checkdir error:  cannot create texturepacks
                 unable to process texturepacks/xp2_tex_tpc.erf.
error:  cannot create xp2.key
--2009-05-10 01:50:02--  [http://nwdownloads.bioware.com/neverwinternights/linux/gold/nwclientgold.tar.gz](http://nwdownloads.bioware.com/neverwinternights/linux/gold/nwclientgold.tar.gz)
Resolving nwdownloads.bioware.com... 204.50.199.10
Connecting to nwdownloads.bioware.com|204.50.199.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7559227 (7.2M) [application/x-tar]
nwclientgold.tar.gz: Permission denied

Cannot write to `nwclientgold.tar.gz' (Permission denied).
--2009-05-10 01:50:02--  [http://files.bioware.com/neverwinternights/updates/linux/169/English_linuxclient169_xp2.tar.gz](http://files.bioware.com/neverwinternights/updates/linux/169/English_linuxclient169_xp2.tar.gz)
Resolving files.bioware.com... 204.50.199.15
Connecting to files.bioware.com|204.50.199.15|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://na.llnet.bioware.cdn.ea.com/u/f/eagames/bioware/neverwinternights/updates/linux/169/English_linuxclient169_xp2.tar.gz](http://na.llnet.bioware.cdn.ea.com/u/f/eagames/bioware/neverwinternights/updates/linux/169/English_linuxclient169_xp2.tar.gz) [following]
--2009-05-10 01:50:03--  [http://na.llnet.bioware.cdn.ea.com/u/f/eagames/bioware/neverwinternights/updates/linux/169/English_linuxclient169_xp2.tar.gz](http://na.llnet.bioware.cdn.ea.com/u/f/eagames/bioware/neverwinternights/updates/linux/169/English_linuxclient169_xp2.tar.gz)
Resolving na.llnet.bioware.cdn.ea.com... 208.111.128.7
Connecting to na.llnet.bioware.cdn.ea.com|208.111.128.7|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 506025948 (483M) [application/x-tar]
English_linuxclient169_xp2.tar.gz: Permission denied

Cannot write to `English_linuxclient169_xp2.tar.gz' (Permission denied).
tar: nwclientgold.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
tar: English_linuxclient169_xp2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
/home/james/Desktop/nwninstaller/nwninstall.sh: line 242: ./fixinstall: No such file or directory
sed: can't read nwn: No such file or directory
rm: cannot remove `nwclientgold.tar.gz': No such file or directory
rm: cannot remove `English_linuxclient169_xp2.tar.gz': No such file or directory
Installation Complete


I get similar "checkdir" errors with what looks to be like almost every file that tried to get installed. 

The answers I am giving are what you have in the brackets, minus the brackts. When it says (root) I was putting "root" I thought that was weird, but I wasn't sure of what else to put. I also tried leaving them blank. Yes I am using the NWN Diamond DVD. The DVD looks to be mounted in /media/cdrom0 so that is what I put, but I have also tried /media/cdrom and just left it blank.


Edit: Nevermind, I seem to have got it working. 
Sorry for wasting your time, but thanks for being willing to help. And amazing work with this BTW.


Not a prob, but what was it that fixed the issue for you?

---

### Post by Duskao on 2009-05-11
During the questions and it says (root) I put my name both times and it worked.

---

### Post by Boondoklife on 2009-05-11
> **Duskao said:**
> During the questions and it says (root) I put my name both times and it worked.

Ah ok and I am assuming that you were not running it while logged in as root? If so then yes the permissions issue would be normal. Ill look into switching to the chosen user for the length of the install if this seems to be an issue for more people.

---

