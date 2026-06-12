---
title: "login stuck in loop"
date: 2009-03-21
forum: General Help
---

### Post by themusicalduck on 2009-03-21
Whenever I try to login to Ubuntu, I put in my correct details and just get sent straight back to the login page. This happened pretty randomly as far as I can tell. The only changes to the system I made before this happening were to try and get a printer to work and to change the default sound device for the volume control.. While trying to fix the printers, I added a line to the a .conf file which was listed as a fix on another thread, but I deleted the line again before the problem started occuring.

What happened before this started happening was that my list of installed printers dissapeared, so I tried to restart gnome in the hope they would be listed again, which is when the login problem started. I can't even get to a command prompt because it won't let me login on in the command line either. There is no error message shown when I try this.

I've tried running 'fix broken packages' from recovery mode, but I cannot download files as I need a gui to 'login' to an internal network first for external internet access. I tried filesystem clean which didn't help, and I tried to 'fix x' which re-wrote over my xorg, but hasn't made any difference apart from disabling my other screen.

I've seen people have this problem after doing fresh installs of Ubuntu, but I've been running it for nearly a year without having this problem before.

I have an nvidia 9800GT if it makes a difference and the printer that wouldn't work was a Brother DCP-135C.

---

### Post by themusicalduck on 2009-03-21
bump

---

### Post by themusicalduck on 2009-03-21
bump

---

### Post by hansdown on 2009-03-21
Hi themusicalduck.

It's likely a problem with the forum server.

I've had the same problem on a number of occasions.

Just so you know it's not just you.

---

### Post by themusicalduck on 2009-03-21
Thanks for the reply. Do you mean this forum? I'm talking about not being able to log into my Ubuntu install, not the forum.

---

### Post by cholericfun on 2009-03-21
sounds really oddd
what did you do to log in?
did you try ctrl-alt F3
?

to login and insatall/ modify packages?

---

### Post by themusicalduck on 2009-03-21
Haven't tried ctrl+alt+f3, what does it do? I tried ctrl+alt+f1, but it still wouldn't let me login and didn't give me any error message. I haven't been able to log in at all yet, I'm just using my windows install at the moment.

---

### Post by themusicalduck on 2009-03-21
Just tried ctrl+alt+f3 and it seems to do the same as ctrl+alt+f1.. So can't get access that way either.

---

### Post by cholericfun on 2009-03-21
ok 
ctrl-alt-f3 prob useless as you seem to be unable to login full stop
just in case though:

once you boot
(login ...)
broke...
try ctr-alt-F3

it should be command line, asking you to log in
just check if this works at all

IF it does
theres a lot you can do from there, unfortunatly you'll have to wait until someone more knowledgeable comes around....


ALTERNATIVELY:
try booting from CD as a Live CD
and see if you can access all parts of your HD/ installation


maybe a little gparted check/repair will do wonders

give us some more details on what you can and not do at your comp at the mo...

EDIT:
sorry i'm just after reading your post more carefully now.
just check what the Live CD gives you, 
+ *"maybe"* 
 - see if you can access all sorts of files from the HD (could simply be corrupted do to "cosmic rays" or whatever)
 - find out how to switch off user login
 - search on... sounds like a painfull computer experience....

---

### Post by themusicalduck on 2009-03-21
Logging in from the command line does not work as I said in my original post. Thanks for the suggestions though. I'll try a filescan and see if it helps.

EDIT: I just read your edit, heh. :p

---

### Post by cholericfun on 2009-03-21
wishing you good luck and us some more info as to whats going on!
this sounds like a painfull bit of work,
 i am retty sure i am as unconstructive as can be (going to bed now) but
check your X11/config for keybord setting (UK/US/GER /Bengali)

otherwise there sould be some file edoting way o getting rid of the login screen during boot up. though this may not be ideal.

afterthought:
when youre failing to login and type ctrl-alt-F1
do you get the login promt?
try out your keyboard at the loginname part

---

### Post by John_T on 2009-03-22
I seem to have the same situation.

Whichever console I attempt to log in at, I'm bounced straight back.  It's not a password issue, as I get a proper error message if I get the password wrong.

I booted from a live CD, everything seems to be working OK, and there disk is nowhere near full.

Does anyone have any other ideas?

---

### Post by themusicalduck on 2009-03-23
Well I did a disk scan but it didn't help. It's starting to look like the only way to fix this is just to re-install.

Interesting that John_T is having the same problem. Maybe it's down to a recent update or something?

---

### Post by John_T on 2009-03-23
> **themusicalduck said:**
> 

Interesting that John_T is having the same problem. Maybe it's down to a recent update or something?

Interesting is one word ;)

Some notes on things I've tried:
1. Rebooting in recovery mode
2. Rebooting to an earlier kernel (recovery and normal modes)
3. Creating a new user account on the same system.
4. Running external disk checking utilities.

I have another HDD I can boot to on this system, so it's not life threatening for me to sort this out right now, so I;'d really like to get to the bottom of it rather than just re-installing.

FWIW, I was using the system on Friday, shut it down for the weekend, and couldn't log in from first boot Monday morning.  I had applied updates, with no reboot required on Thursday and/or Friday, nothing unuusal, just whatever was recommended by the system.

---

### Post by themusicalduck on 2009-03-23
One last shameless bump to see if anyone knows any answer to this :(

I even had a quick search on launchpad to see if any bug had been filed, but it's a bit difficult to find anything with a search term as vague as "login loops" and without much more information about it.

---

### Post by tobydeemer on 2009-04-03
Hi all-

Unfortunately, I have found myself in the same situation as the OP.

This started after I had some issues trying to connect to a network printer.

I've tried to reconfigure X as other users have to no luck. Before the login loop had started, I had an issue with Firestarter firewall not starting properly, and it showed an error at boot. I did manage to get to the root terminal with recovery mode, and removed Firestarter. This solved the Firestarter startup error but did not help with the login loop.

-My next thought is to try troubleshooting the issues with CUPS, since my printer list also disappeared before the loop started.

Any more progress on this from anyone? I cannot afford to reinstall this machine, as it's used in production. (I do have backups, but I also have way too many apps installed on this thing to wanna have to rebuild...)

-I'm writing as I'm trying to fix, so... next thing I did was @ root prompt, ~/etc/cups/# mv cupsd.conf cupsd.conf.bakTLD

then

~/etc/cups/# mv cupsd.conf.defaut cupsd.conf

This did not work, so the CUPS config appears to be a symptom as well.

Next I'm trying to rewrite the UFW config to default...
     >> I ran both dpkg-reconfigure gdm [and]
                   dpkg-reconfigure ufw
This did not fix the issue either.

I'm still working on it... I'm being stubborn this time and don't want to reinstall, because I know the system works- it will boot to a root terminal in recovery mode. There's got to be a config SOMEWHERE that is causing this login error...

Anyone else have any ideas?

---

### Post by John_T on 2009-04-03
> **tobydeemer said:**
> Hi all-

Unfortunately, I have found myself in the same situation as the OP.

This started after I had some issues trying to connect to a network printer.
I too had been messaging with CUPS to connect to a network printer shortly before I had the problem.  I was getting "unable to connect to localhost" sort of messages, IIRC. I could ping localhost, and all other network connectivity was OK.

> **tobydeemer said:**
> 
I'm still working on it... I'm being stubborn this time and don't want to reinstall, because I know the system works- it will boot to a root terminal in recovery mode. There's got to be a config SOMEWHERE that is causing this login error...

Anyone else have any ideas?
I'm out, sorry.

---

### Post by tobydeemer on 2009-04-04
Well, after much wailing and gnashing of teeth, I relented.

I have started a reinstallation. I dug everywhere to find a resolution to this. 

There are filed bugs related to this issue, possibly caused by an error in Likewise Open (which I had installed on this machine) interfering with PAM authentication modules. 

So now I'm reinstalling. Again.

It's one thing for knowledgeable Linux users to reinstall whenever they feel like it. Linus himself is rumored to do so every 6-8 months or more. 

However, if the long-awaited Year of the Linux Desktop is ever going to happen or if Canonical's push into the enterprise space is going to grow past "gaining momentum", then things like Active Directory authentication / Unix PAM Modules / CUPS issues / breaking systems/ HAVE to be solved. 

While this is an issue that easily has an equivalent in the Windows world, it's also something that "we" can't be bringing to the table when trying to take space from Windows. 

Sorry for this bit of a rant. But today was the only day in almost two years of full Linux desktop use that really, truly frustrated me to the point of almost going back to Win XP for my work machine.

I didn't. But I was damn close.

Here's to a better install this time around...

-td.

---

### Post by Keith Klos on 2009-04-26
I am new to Ubuntu and had the same problem after trying to find a printer driver for my Cannon MP470 printer.  I have Ubuntu 8.1 loaded and it has been working fine until I went here: [http://www.cups.org/](http://www.cups.org/) to try to get my printer to work better.  During the process, my printer list "went away" and when I tried to reboot,  I now am stuck in the login loop.  I have tried ctrl+alt+f1 and also ctrl+alt+f3 but same result.  I can get to a root prompt but I am not good in terminal mode so don't know how to proceed.  I don't mind a reinstall but am assuming I will loose data on my harddrive?   How about booting with a live CD?  Any help would be appreciated.
Keith

---

### Post by perrti-y02 on 2009-04-26
Do you have a separate partition for data? If you do then DON'T FORMAT IT!!! you can use a partition as it is during an installation. If your data is on the same partition then boot into the live cd and create a new partition that you can shove all your data onto. then do a fresh install and hopefully everything will be wonderful once more.

---

### Post by Keith Klos on 2009-04-26
I do not believe I had a separate partition for data. I believe I installed to as one partition.  So I will boot into a live CD and then create a new partition to keep data and then do a fresh install- correct?   Should I reinstall 8.10 or 9.04?  Also I confess, how do I create a new partition and then move my data into it?   If I get it up and running with the live cd, I am assuming my local network would still work so I could transfer those files to my other pc (windows)?  

Thanks.  I am downloading 9.04 now and will when done create a live CD for 8.10.

---

### Post by Keith Klos on 2009-04-26
I found the documentation on creating a new partition.  Will study up and try some things and give a report.

---

### Post by Keith Klos on 2009-04-27
OK I booted into a live CD (9.04) without any problems and created a new partition.  I can access all the files that I had before but now want to move some into the new partition and then do a fresh install.  I can not seem to move those folders or create a new folder on the new partition.  It has one folder "lost + found" but I am not able to create a folder or move things onto that partition.  What am I doing wrong?   Another question would be:  When I do the fresh install will I be able to use the guided partitioning and just choose the correct partition to do the install or will I need to go the manual route?
Thanks
Keith

---

