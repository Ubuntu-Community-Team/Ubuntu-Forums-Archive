---
title: "Administrator Mode Fails"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Dromio on 2005-10-13
In the new system configuration, clicking on the "Administrator Mode..." brings up a dialog which asks for my password.  After I enter the password, nothing happens.  I'm certain it's the correct password.

It looks like KDE su doesn't actually do anything.  Can anyone get this to work?

---

### Post by Asraniel on 2005-10-13
same here, i always do it like that:
sudo kcontrol

---

### Post by GeneralZod on 2005-10-13
This was a much-complained-about problem in the original 5.04; I would have thought it would have been fixed by now! Is this definitely on 5.10?

If it's not fixed, then follow Asraniel's advice; I'll ask an admin to make a sticky for it :)

---

### Post by Navyblue on 2005-10-13
Yes this is broken since Hoary in my PC, till I fed up and enabled my root account just to access the control panel. I know this is not good but I prefer surfing with web browser rather than with text editors. :p

It seems that Kubuntu is still pretty buggy at this point of time, probably more so than Hoary.

---

### Post by avk25 on 2005-10-13
Strange thing.. At the very first time I tried to activate administrative mode - all were ok. The second and next attempts failed:confused:

---

### Post by metoo on 2005-10-13
Hm, kdesu and sudo work both here (i386 and amd64, different machines).

As usual you supply your user password, not the root password, but you surely know that.
su in a shell needs the root password, kdesu in a shell needs the user password.
But I tried this settings thing too, changed the kdm from showing a pic to showing the clock. Accepted the user password.

Don't know, whether I installed anything unusual. sudo of course, but that's for 'sudo xy' .

And your /etc/sudoers ends like:

root	ALL=(ALL) ALL
theuser	ALL=(ALL) ALL

considering that your user name is 'theuser' ?

---

### Post by pepster on 2005-10-13
My /etc/sudoers is 

User privilege specification
root    ALL=(ALL) ALL
xxxxxx  ALL=(ALL)  NOPASSWD: ALL

Still, administrator mode may fail or succeed, no obvious pattern.

I love Kubuntu, but it has enough bugs which make it impossible to recommend to anyone who is not a hacker.

-> Joseph

---

### Post by Freddy on 2005-10-13
This is not a kubuntu specific problem, more a sudo and KDE problem (you don't have a real root account), since systemsetting or Kcontrol is a KDE gui app, it's better to use kdesu.
```
kdesu systemsettings (or)
kdesu kcontrol
```
You don't need a konsole for this just right click anywhere on the desktop and choose run command.   /// Freddan

---

### Post by pepster on 2005-10-13
A workaround is nice and I have been doing it since I got Kubuntu, but it is still annoying and still a bug. I have no idea if it is KDE or kubuntu specific. I don't remeber problems like that with KDE under RedHat 8.

-Joseph

---

### Post by mlomker on 2005-10-13
> This was a much-complained-about problem in the original 5.04; I would have thought it would have been fixed by now! Is this definitely on 5.10?

The problem went away for me about a week ago.  I'm left to wonder if some people haven't fully updated their machines or perhaps the packages didn't install 100%.  

Give this a shot:

```

sudo apt-get update
sudo apt-get install --reinstall kcontrol

```

---

### Post by Watter on 2005-10-14
[QUOTE=mlomker]The problem went away for me about a week ago.  I'm left to wonder if some people haven't fully updated their machines or perhaps the packages didn't install 100%.  
[/QUOTE]
I still have the "problem" and this is on a completely fresh Breezy install, not an upgrade. Honestly, if Breezy had been released with no changes from Hoary but with this one issue fixed, I would have considered it a successful release. Not being able to manage my network and Samba settings from the control center is just super annoying. Oh well, back to editing smb.conf manually.

---

### Post by GoldBuggie on 2005-10-14
I have this prob. as well. Not to sound to picky or something but this should have been isolated and fixed.

---

### Post by Freddy on 2005-10-14
> I still have the "problem" and this is on a completely fresh Breezy install, not an upgrade. Honestly, if Breezy had been released with no changes from Hoary but with this one issue fixed, I would have considered it a successful release. Not being to manage my network and Samba settings from the control center is just super annoying. Oh well, back to editing smb.conf manually.
This problem isn't for the Kubuntu developers to fix, the problem lays within KDE. I agree with you that this problem needs a real fix and not a only workaround and with (K)ubuntu's choice do disable the root account for the use of sudo maybe they should help the KDE team out and get this fixed.
> I don't remeber problems like that with KDE under RedHat 8.
KDE and Fedora haven't disabled the root account and therefore they aren't experiencing this bug.   /// Freddan

---

### Post by Watter on 2005-10-14
[QUOTE=Freddy]This problem isn't for the Kubuntu developers to fix, the problem lays within KDE. I agree with you that this problem needs a real fix and not a only workaround and with (K)ubuntu's choice do disable the root account for the use of sudo maybe they should help the KDE team out and get this fixed.
[/QUOTE]
You're right , of course. I'm just saying that that was one of the few really annoying things about my Kubuntu installation. Almost everything else "just worked", as we've  come to say.

---

### Post by Freddy on 2005-10-14
> You're right , of course. I'm just saying that that was one of the few really annoying things about my Kubuntu installation. Almost everything else "just worked", as we've come to say.
and ofcourse you're right to, it's plenty irritating that this bug is allowed to linger KDE update after KDE update , Kubuntu is pretty darn close to a perfect KDE based distro but to be perfect the kcontrol/sudo issue needs to be permenently solved.   /// Freddan

---

### Post by mlomker on 2005-10-14
> I still have the "problem" and this is on a completely fresh Breezy install, not an upgrade. 

Yup, I just did a fresh 32-bit install and it doesn't work.  For whatever reason it was working fine on my amd64 Hoary upgrade.  I guess we'll be using **kdesu kcontrol** for a little while longer.

---

### Post by Freddy on 2005-10-14
> Yup, I just did a fresh 32-bit install and it doesn't work. For whatever reason it was working fine on my amd64 Hoary upgrade. I guess we'll be using kdesu kcontrol for a little while longer.
The strangest thing is that sometimes it works and sometimes it's just doesn't, even kdesu kcontrol has failed for me (not often but it has). Hopefully someone smarter then me is looking into the problem as we speek :).   /// Freddan

---

### Post by gstrock on 2005-10-14
I did a fresh Kubuntu install as expert, so it asked me to define a root password.

I made the root password the same as my user password.

Now when ever I try to go into administrator mode on a gui,
like say the print manager it fails.  Always.  
In fact it gets to the point where just clicking on the administrator button 
pops up an error message:  "Conversation with su failed".
and the error message window is labeled "Sorry - KDE su".

I did two installs of Kubuntu in expert mode and they both exhibit this problem.

by the way "kdesu kcontrol" doesn't work for me.
However, if I su to root from a console window  I can 
invoke the command if I know it's name.

this is especially bad because I  installed one of these machines in a work place, 
where it is the sole Linux box and is used to demo software I am developing and 
frequently I need to get into administrator mode.  
I've resorted to logging in as root at the kde loging prompt.

I installed Ubuntu on my laptop, in non-expert mode, and I 
have no problem going   into administrator mode.

So this is just a KDE thing?

greg strockbine.

---

### Post by Freddy on 2005-10-14
I believe that Kubuntu has disabled the rootlogin in KDE, therefore you can't use it. I believe that you can enable it inside kcontrol.   /// Freddan

---

### Post by knappen on 2005-10-15
It is really strange that Breezy has been released at all. If this problem is not a show stopper, I don't know what is.

Aaaarrrggghhhh....so annoying!!!!

---

### Post by skyboy on 2005-10-15
Weird, I'm not having that issue at all and actually never had it. Neither with Hoary nor with Breezy. For me it always worked like a charme. 
That is weird !! :S

---

### Post by B.B on 2005-10-15
[QUOTE=mlomker]I guess we'll be using **kdesu kcontrol** for a little while longer.[/QUOTE]
Wow...that has to be awarded the 'most usefull information of the week' price. I was this -><- close to put my Suse image back on my laptop because of this problem (Wireless management ain't a charm without administrative rights)  

Out of 5 stars ill give it 6

:KS :KS :KS :KS :KS :KS

[Edit]
Btw, where has the KDE 3.5Beta repository gone to ? Perhaps an upgrade will solve the issue.

---

### Post by GoldBuggie on 2005-10-15
>  Btw, where has the KDE 3.5Beta repository gone to ? Perhaps an upgrade will solve the issue.

kde 3.5beta1 is ```
http://kubuntu.org/kde35beta1/ breezy main
``` but that does not solve the problem.

The thing that I that I have not experienced is the whol USB media hal thing that I have read about. Maybe this gets solved with 3.5?!?

---

### Post by escobar on 2005-10-15
Just wanted to update the thread and say I am having the same issue. Admin mode fails completely for me. Weird thing is, it worked perfectly when I first installed Breezy. Since I discovered "kdesu kcontrol" it's manageable so I won't raise a big stink about it. I still really like Breezy. Thanks.

---

### Post by pepster on 2005-10-18
I love KDE, but the kontrol center has so many bugs that I can't recommend Kubuntu to anyone who is not comfotable with the command line and reading man pages and editing conf files.

-Joseph

---

### Post by B.B on 2005-10-18
I just added the KDE 3.5 Beta 2 repository (Look  [here]("http://ubuntuforums.org/showthread.php?t=78226")) and did an upgrade. Problem gone. \\:D/

---

### Post by GeneralZod on 2005-10-18
[QUOTE=B.B]I just added the KDE 3.5 Beta 2 repository (Look  [here]("http://ubuntuforums.org/showthread.php?t=78226")) and did an upgrade. Problem gone. \\:D/[/QUOTE]

That's great news! :KS

---

### Post by chimaera on 2005-10-18
I found a more convenient workaround (at least for me): 

- set a password for root (sudo passwd) 

- tell kdesu to use su instead of sudo by adding 
```
[super-user-command] 
super-user-command=su 

``` 
to either*~/.kde/share/config/kdeglobals * or */usr/share/kubuntu-default-settings/kde-profile/default/share/config/kdeglobals *

---

### Post by raven on 2005-10-19
[QUOTE=mlomker]The problem went away for me about a week ago.  I'm left to wonder if some people haven't fully updated their machines or perhaps the packages didn't install 100%.  

Give this a shot:

```

sudo apt-get update
sudo apt-get install --reinstall kcontrol

```[/QUOTE]

just to confirm
I use hoary, kde 3.4.2
I used to have the same problem witn admin mode but I did mlomker advise
to reinstall kcontrol and it worked till now been some days with no problem
so for me just reinstall worked perfectly
hope this continues

---

### Post by chimaera on 2005-10-19
[QUOTE=raven]just to confirm
I use hoary, kde 3.4.2
I used to have the same problem witn admin mode but I did mlomker advise
to reinstall kcontrol and it worked till now been some days with no problem
so for me just reinstall worked perfectly
hope this continues[/QUOTE]

i did this two times, read: the problem came up again..

---

### Post by seattlegaucho on 2005-10-19
[QUOTE=chimaera]i did this two times, read: the problem came up again..[/QUOTE]

I know that this may be a late reply, but after dealing with this problem in several other distributions (it doesn't seem to an "Ubuntu-only" problem), I decided to enable **root** logins to KDE and never worry again.

My $.02
G

---

### Post by raven on 2005-10-19
[QUOTE=chimaera]i did this two times, read: the problem came up again..[/QUOTE]

It's wierd, cause today I upgraded from 3.4.2 to 3.4.3 on hoary
and the problem came again.
so I did reinstall kcontrol, the problem disapear
I tried the admin mode couple of time after reinstal kcontrol it worked
restart pc couple of time, kcontrol admin mode works perfectly
I guess there is no silver bullet for this issue
reinstalling kcontrol worked for me ................up to now

---

### Post by chimaera on 2005-10-20
for it seems to be an issue kdesu has with sudo, the workaround i posted  works flawlessly..

---

### Post by Watter on 2005-10-20
[RANT]
Workaround, smerkaround. It's ridiculous. Not the suggested workarounds of course (a big thanks is owed to everyone who submitted their experieces and workarounds), but the fact that they are needed.

It's just daffy that in a "Dekstop" focused distribution/window manager I cannot use the new "System Settings" or the good 'ole "Kcontrol" and configure important things like networking, shared folders, etc. 

I know that this isn't just a Kubuntu problem, but how can this be considered a "release" when these kinds of things don't work, regardless of whose fault it is? We're not talking about abstract, rarely used pieces of functionality here. These pieces being broken comeplety disqualifies Kubuntu from being used by anyone but tech-heads.

This is so frustrating because I WANT to be able to recommend Kubunto to my friends and family, but I can't. I should be able to go to my Kmenu, click System Settings, click Network Settings, and actually be able to do something. It's that simple
[/RANT]

Ranting aside, reinstalling kcontrol didn't work for me. In fact none of the workarounds allow me to actually use the "File Sharing" section. Some of the workarounds allow me to set the network settings, but this just reveals yet another bug as the /etc/network/interfaces file that gets written by that section when you apply your settings is invalid. It doesn't write the gateway and it doesn't set the "auto etho" command which actually starts your interface, 

The same is true about the Samba section. When I do use a workound that allows me to actually manipulate this area, it still doesn't work correctly. When I add a user and click apply, the user isn't actually added or saved anywhere. it just goes back to the same menu. The whole Samba section behaves in this manner.

Both the Samba and network settings bug existed in Hoary too (I'm on a fresh install of Breezy, not an upgrade).

Nuts...

---

### Post by BlueNoteMKVI on 2005-10-21
I've got to agree with Watter on this.

I know how to adjust these setting manually.  I can get into them using the workarounds posted here.  Why do I have to?

FYI, kcontrol's administrator mode works fine under Gentoo (my laptop) and Xandros (my wife's laptop, and previously my desktop).  I installed Kubuntu today (freshly downloaded ISO) and it does not work here.

In case anyone's watching this who wants to know, I'm running the AMD64 version of Breezy Badger, kernel 2.6.12-9-amd64-generic, hardly anything changed from the default installation settings.  I'm trying to access the network settings via the control center.  The first time I tried it did not work, I tried again with a different password and it did.  After a reboot it's kaput.  I cannot access administrator mode with the user password or the root password except by using "kdesu controlcenter."

---

### Post by knappen on 2005-10-22
Why can't a kubuntu developer comment on this issue?

---

### Post by aysiu on 2005-10-22
[QUOTE=knappen]Why can't a kubuntu developer comment on this issue?[/QUOTE] Because Kubuntu and Ubuntu developers don't hang out in these forums.

---

### Post by knappen on 2005-10-22
Maybe they should. 

Or are they too busy fixing this problem that has been around since kubuntu was released.

---

### Post by aysiu on 2005-10-22
[QUOTE=knappen]Maybe they should. 

Or are they too busy fixing this problem that has been around since kubuntu was released.[/QUOTE] Why should they? That's why we have Bugzilla. See the top-right corner of the forums screen?

---

### Post by knappen on 2005-10-24
Well it is always good to see what users are having problems with, even though it is not reported as a bug. 

However, this administrator problem does not bother me anymore as I have erased kubuntu.

---

### Post by Copter on 2005-10-28
[QUOTE=pepster]
I love Kubuntu, but it has enough bugs which make it impossible to recommend to anyone who is not a hacker.

-> Joseph[/QUOTE]
word! have the same sh*t here :(

copter :]

---

### Post by lips on 2005-11-02
[QUOTE=aysiu]Why should they? That's why we have Bugzilla. See the top-right corner of the forums screen?[/QUOTE]

This has been reported as a bug as early as April of this year.  Still isn't fixed and is carried over to Breezy Badger 5.10.  Why even release the version with these bugs?  Do they care?

If bugs like these are in a Windows release (or even beta) version the Linux people would jump all over it.

---

### Post by ltmon on 2005-11-02
Rejoice ye all and know that this bug may have finally been squashed.

Have a look near the end of this thread.  Jonathon has posted a couple of debs with a patch for people to use, and so far all are reporting success.

If you look at the KDE bugzilla entry for this you can see that the patch has now been applied upstream also (on 2nd November 2005).

Hopefully it will appear in the updates soon, but the impatient can just download it from the bugzilla attachment now.

Cheers,

L.

---

### Post by lips on 2005-11-02
[QUOTE=ltmon]Rejoice ye all and know that this bug may have finally been squashed. Have a look near the end of this thread. Jonathon has posted a couple of debs with a patch for people to use, and so far all are reporting success. If you look at the KDE bugzilla entry for this you can see that the patch has now been applied upstream also (on 2nd November 2005). Hopefully it will appear in the updates soon, but the impatient can just download it from the bugzilla attachment now. Cheers, L.[/QUOTE] Thanks. I'll try it tonight.

Edit -
Tried it.  After reboot it seemed to be fixed.

However the problem with Network Settings in System Settings is not fixed even after I successfully get into Administrator mode.  I still cannot update and save the gateway IP.

---

### Post by hil on 2005-11-18
Kubuntu is the one that I found most compatible with my IBM thinkpad T30 laptop. All the hotkeys worked after I follow the instructions on [http://www.columbia.edu/~em36/ubuntuhoarythinkpadt42.html]("http://www.columbia.edu/~em36/ubuntuhoarythinkpadt42.html")
I would recommend Kubuntu to other people. I attempted to install Fedora Core 4 on the laptop but the Intel Ethernet chip did not work although it was recognized by the kernel. I heard that other Fedora Core 4 users had their ethernet working after installation. Perhaps it was a installation process ethernet failure. I did not install Fedora Core 4 because I could not do net install. Ubuntu was smart enough to net install some Chinese specific packages after the regular installation.

---

### Post by hil on 2005-11-18
Changing the kdesu to use su instead of sudo did not work for me. I could input the root password in system settings but still got grayed out entries that I could not modify. I was still in user mode not administrator mode. [QUOTE=chimaera]I found a more convenient workaround (at least for me): - set a password for root (sudo passwd) - tell kdesu to use su instead of sudo by adding Code: [super-user-command] super-user-command=su to either~/.kde/share/config/kdeglobals or /usr/share/kubuntu-default-settings/kde-profile/default/share/config/kdeglobals [/QUOTE] After I reinstalled kcontrol by doing sudo apt-get install --reinstall kcontrol, I could enter administrator mode in system settings only once. After I rebooted, the problem came back. I could not enter administrator mode again. But there is always a workaround solution: ```
Alt-F2 kdesu systemsettings
``` There is one better solution: Click on KDE menu. Right click on the "System Settings". Choose "Edit Item". In the command field (Alt-m), add "kdesu" in the front. Mine looks like this: ```
kdesu systemsettings -caption "%c" %i %m
```

---

### Post by hil on 2005-11-19
Ultimate solution:

Someone on kubuntu channel on IRC told me to do a complete update in KDE. Here is the process: KDE menu=>System=>System update wizard (Adept updater)=>Fetch=>Commit. After that restart KDE and try the "Administrator mode" in "system settings". It should work.
Note: only updating the kdesu in the Adept updater does not help.

---

### Post by bluemuffin on 2005-11-23
[QUOTE=Dromio]In the new system configuration, clicking on the "Administrator Mode..." brings up a dialog which asks for my password.  After I enter the password, nothing happens.  I'm certain it's the correct password.

It looks like KDE su doesn't actually do anything.  Can anyone get this to work?[/QUOTE]

KUBUNTU has its reasons for not allowing us to log-in as ROOT but if you REALLY want to get around it then you have to modify the kdmrc file.

first, of course, you have to create a password for root:
 $ sudo passwd root

Then you have to modify the kdmrc file.

Go to kdmrc folder:
$ cd /etc/kde3/kdm 

Open the kdmrc file with a text editor (pico)
$ sudo pico kdmrc 

look for the line:
AllowRootLogin=False
change the value "False" to "True"
Hit keys Control X
Hit key Y
Hit Enter

Boot and register as root.

I hope this works for you.


:) 

BTW, try kubuntuforums.net

---

