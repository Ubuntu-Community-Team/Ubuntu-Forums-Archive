---
title: "Failed update kdelibs-data"
date: 2005-04-21
forum: Desktop Environments
---

### Post by ceti on 2005-04-21
Tried to update kdelibs-data this morning, but it failed with this error message:

E:/var/cache/apt/archives/kdelibs-data_40x1.15c480000005ap-8863.4.0-0ubuntu3.1_all.deb:  trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf

Now the main menu is missing and KDE is useless. What to do?
Thanks
ceti

---

### Post by teumima on 2005-04-21
[QUOTE=ceti]Tried to update kdelibs-data this morning, but it failed with this error message:

E:/var/cache/apt/archives/kdelibs-data_40x1.15c480000005ap-8863.4.0-0ubuntu3.1_all.deb:  trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf

Now the main menu is missing and KDE is useless. What to do?
Thanks
ceti[/QUOTE]
 Hey man

I'm also having the same problem with the updating. The menu still works.

If you lost your K-menu button. Just right click on your bar>add to panel>Special button>K menu

---

### Post by coldsalmon on 2005-04-21
Same problem as well.  Does this qualify as a bug, and if so how should I report it?

---

### Post by jan.letko on 2005-04-21
I have this problem now:

not upgrade, not remove, not install ??? Where is problem ??? kdelibs-data problem ...
> 
root@letko:/home/letko # apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
kdelibs: Depends: kdelibs-data (>= 4:3.4.0-0ubuntu3.1) but 4:3.4.0-0ubuntu3 is installed
E: Unmet dependencies. Try using -f.
root@letko:/home/letko #
root@letko:/home/letko #
root@letko:/home/letko #
root@letko:/home/letko #
root@letko:/home/letko # apt-get -f install kdelibs-data
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
kdelibs-data
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
19 not fully installed or removed.
Need to get 0B/8013kB of archives.
After unpacking 0B of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 100018 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.4.0-0ubuntu3 (using .../kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb (--unpack):
trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf
Errors were encountered while processing:
/var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@letko:/home/letko #
root@letko:/home/letko #
root@letko:/home/letko #
root@letko:/home/letko #
root@letko:/home/letko # apt-get remove knetworkconf
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
kdelibs: Depends: kdelibs-data (>= 4:3.4.0-0ubuntu3.1) but 4:3.4.0-0ubuntu3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@letko:/home/letko #



heeeeeeeeeeeeeeeeeeeelp

---

### Post by gunnyman on 2005-04-21
methinks the repos just took a vacation.

---

### Post by Gianni Exile on 2005-04-21
Type the following ```
sudo apt-get install kdelibs=4:3.4.0-0ubuntu3 kdelibs-data=4:3.4.0-0ubuntu3
```

This should apply cleanly.

Don't update again until you see "knetworkconf" among the list of packages to be upgraded.

This is a genuine goof on Ubu's package release manager's part.

---

### Post by siebzehn on 2005-04-21
[QUOTE=Gianni Exile]Type the following ```
sudo apt-get install kdelibs=4:3.4.0-0ubuntu3 kdelibs-data=4:3.4.0-0ubuntu3
```

This should apply cleanly.

Don't update again until you see "knetworkconf" among the list of packages to be upgraded.

This is a genuine goof on Ubu's package release manager's part.[/QUOTE]
 Check this thread, you will find the solution...

[http://ubuntuforums.org/showthread.php?t=28721](http://ubuntuforums.org/showthread.php?t=28721)

---

### Post by Maikun on 2005-04-21
>  Check this thread, you will find the solution...

[http://ubuntuforums.org/showthread.php?t=28721](http://ubuntuforums.org/showthread.php?t=28721)

Well, i followed the link and did manage to upgrade kdelibs. BUT the taskbar is still empty (same as first post) wallpaper gone KDE start splashscreen is not Kubuntu but KDE 3.4, as says re-added kmenu... a freaking mess

Of course I can add again everything to the tasbar and restore my wallpaper but this is a frightening way to begin my first security update experience with Kubuntu

---

### Post by siebzehn on 2005-04-21
[QUOTE=Maikun]Well, i followed the link and did manage to upgrade kdelibs. BUT the taskbar is still empty (same as first post) wallpaper gone KDE start splashscreen is not Kubuntu but KDE 3.4, as says re-added kmenu... a freaking mess

Of course I can add again everything to the tasbar and restore my wallpaper but this is a frightening way to begin my first security update experience with Kubuntu[/QUOTE]
 I agree with you.

That's not supposed to happen

---

### Post by ceti on 2005-04-21
thanks, siebzehn. I followed that thread and it worked.
but what a mess: no more Kubuntu splashscreen and open applications don't minimize to panel.
I'll wait for a patch.

ceti

---

### Post by pvz on 2005-04-21
A mess indeed. Also, automounting of my USB-device seems to have gone after the upgrade. No icon appears on the desktop anymore. Bugger.

---

### Post by Gianni Exile on 2005-04-21
That thread doesn't have good advice.

When a new version of knetworkconf comes out, the common files will be deleted (on uninstall of the prior version).  If anthing should be forced, it's the new kdelib packages.  

Best to wait until they get this mess sorted out, stick with the "old" (like 1 week old) version with full fuction, then update when it's all fixed.  The problems are not that critical, IMHO, they can wait.

---

### Post by denzilla on 2005-04-21
Do this updates address the Konqueror crashes?

---

### Post by Gianni Exile on 2005-04-21
No, they address security issues in the image-loading code.  The issues in the code are not AFAIK being exploited in the wild, there's no KDE worm out there, so it can wait until a working update is released.

---

### Post by Gianni Exile on 2005-04-21
Here's why I'm saying wait a day.. notice urgency=low?

kdelibs (4:3.4.0-0ubuntu3.1) hoary-security; urgency=low     
                                                                     
  * Add kubuntu_04_kimgio_security.diff                        
  * SECURITY UPDATE: kimgio input validation errors  
  * kimgio contains a PCX image file format reader that does       
    not properly perform input validation. A source code audit       
    performed by the KDE security team discovered several 
    vulnerabilities in the PCX and other image file format       
    readers, some of them exploitable to execute arbitrary   
    code.                                                                             
  * References:                                                                
    [http://cve.mitre.org/cgi-bin/cvename.cgi?name=CAN-2005-1046](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CAN-2005-1046) 
    [http://bugs.kde.org/102328](http://bugs.kde.org/102328)                                                        
    [http://www.kde.org/info/security/advisory-20050421-1.txt](http://www.kde.org/info/security/advisory-20050421-1.txt)
                                                                                                     
 -- Jonathan Riddell <jr@jriddell.org>  Thu, 21 Apr 2005 04:46:47 +0000   
                                                                                                     
kdelibs (4:3.4.0-0ubuntu3) hoary; urgency=low             
                                                                                                     
  * Move TextEditors from Utilities More to Utilities          
                                                                                                     
 -- Jonathan Riddell <jr@jriddell.org>  Thu, 24 Mar 2005 04:32:44 +0000

---

### Post by sadiini on 2005-04-21
[QUOTE=Gianni Exile]Type the following ```
sudo apt-get install kdelibs=4:3.4.0-0ubuntu3 kdelibs-data=4:3.4.0-0ubuntu3
```

This should apply cleanly.

Don't update again until you see "knetworkconf" among the list of packages to be upgraded.

This is a genuine goof on Ubu's package release manager's part.[/QUOTE]
 Well! I updated also and got kernel panic after 7 minutes or so. Only thing pending was kdelibs-data. 
So I wonder - how was only one (1) pack able to mess up whole system??? No just kde related apps. I can still boot to KDE, Gnome, IceVW, but after ca 3-4 minutes, the system crashes totally. Kernel is affected. How the (6) is it possible?
Any clues????

---

### Post by roffles on 2005-04-21
I wish I came to this thread before I did an apt-get upgrade :( 

It was a pain to get all my applet buttons/trays/taskbar back the way I like it, but I'm just worried that there was some behind-the-scenes breakage that I don't know about. Does anyone know what can possibly be broken as a result of trying to upgrade kdelibs-data? 

-On a similar note, are the selected packages when you do apt-get upgrade supposed to be safe, or are we supposed to go along the lines of 'if it aint broke, don't fix it' ? I guess I'm still used to the Microsoft Update way of doing things: If you see an update get it or else bad things might happen.

---

### Post by ceti on 2005-04-21
I saw this in other thread:

[i]The reason none of your programs are showing up on your taskbar is because you don't have a taskbar anymore! Right click on your panel and select Add To Panel->Applet->Taskbar. That should fix it. \\:D/ 
[/i]
Thanks, windymiller. It works.

ceti

---

### Post by ozar on 2005-04-21
[QUOTE=roffles]I wish I came to this thread before I did an apt-get upgrade :( 
[/QUOTE]

Yeah, me too!

I installed Kubuntu a month or two back and it needed lots of work so I removed it from my system.  I figured it was better by now with the new official release, so a fresh install went on the hard drive today.  I immediately upgraded the 3 kde files indicated as needing upgrading by Kynaptic and all went to hell on first reboot.   :sad:

---

### Post by !nkubus on 2005-04-21
I'm in the same boat i have screwed all my kubuntu i do not have the time to reload it back :S

now the autopopup of devices is gone it's pretty baaaaaaad

hope it's gonna be fixed soon :S

---

### Post by !nkubus on 2005-04-21
ok i have fixed it it's just the option in configure desktop -> Behavior -> Device Icon and click on show device icon.

---

### Post by A-star on 2005-04-22
no more kde for me, I'm going to stick with gnome, seems to be a bit more stable.

---

### Post by ltmon on 2005-04-22
[QUOTE=A-star]no more kde for me, I'm going to stick with gnome, seems to be a bit more stable.[/QUOTE]

I'm not worried too much about KDE itself.  It seems to me that the Kubuntu packaging and implementation of KDE is a bit off.

Gnome's more stable in Ubuntu because it's been worked on a lot longer by more people.

I think Kubuntu needed a little more time in "beta".

That said, I will keep using it because my installation is pretty much stable (lucky me i guess) and I think it has the potential to be a fantastic distro when this all gets sorted ... thanks devs.

L.

---

### Post by ubuntu UsER on 2005-04-22
I uninstalled knetwork package and then i installed kde-libs package. It works.

---

### Post by paul_jp on 2005-04-22
Yes, this worked for me too.  I then reinstalled knetworkconf.

---

### Post by scottk88 on 2005-04-23
also did the same thing as most of you guys - got error on update, and then just decided eh, screw knetworkconf.....got rid of it, and installed kdelibs and everything else, and of course bottom bar was gone....not necessarily good, right? NO
i then figured out after sitting here for almost 19 consecutive hours, reinstalling ALL kde files, removing conf files, getting rid of everything completely did me no good, i still had no bar.....so i just decided to make the bar manually, and i guess thats not so bad, right? WRONG
now i have some major problems.....i have no sound - nothing coming out of speakers - and sound is configured on here, so this seems horrid, not to mention, Kmix wont even show up in taskbar....so this is my decision : shit......

---

### Post by rufnut on 2005-04-24
This problem caused me much grief too   ](*,) 

I now have a huge gnome desktop environment on my system which helped me restore the KDE setup after some some CLI apt-get as I removed all the kde lib libraries.

KDE is now running ok.

I locked the kdelibs to 3.0 instead of 3.1 till we get a better understanding of the catastrophe.

All in all Kubuntu has a better implementation of KDE than SuSe (which is quite a statement)

Just dont upgrade kdelibs for a while.

---

### Post by Oxy42 on 2005-04-24
hello guys,
I got the problems described here.
So I uninstall knetworkconf and have been able to upgrade the system.
I then erased the directory .kde and so I get back the kde default configuration.

However, most of the applications are not working from the kdemenu, as described in another thread i got the hourglass and then nothing. The system also appears pretty unstable.

Does anybody know how to go back ? (is it only possible?)
For the meantime how can I get back at least the kubuntu desktop configuration? I mean the menu, and everything else.
thank you for your help

---

### Post by Bagleemo on 2005-04-24
Yes- What is the best way to go back, using apt-get? 
I did the upgrade yesterday and it installed part of KDE but not the kdelibs-data. (can't remember what the name of the other kde file was or I'd apt-get remove it).
So now I have the knetworkconf problem and can't complete the kde install and my desktop has gone goofy.  Sounds like if I do complete the upgrade, things will still be goofy.

How best to return the system to its previous state?

---

### Post by coldsalmon on 2005-04-24
Have the developers noticed this?  Do they read the forums?  It seems like a serious problem that they should have fixed immediately.

---

### Post by Seatux on 2005-04-27
i did this instead

Scanned the Ubuntu Hoary 5.04 release CD in synaptic (mine was installed from the alpha cd)

I went to quit synaptic, but it said i had changes pending

Clicked apply and saw the KDE stuff and Kubuntu being removed.

Went back to install kubuntu-desktop

A ok here. though my gaim and firestarter looks like crap.

---

### Post by herbdoc215 on 2005-04-27
Hey I had same problem but just figured it was my screw-up and chalked it up to being out of practice with linux...BUT it completely screwed my installation...so after re-installing 4 times and upgrading each a different way (each getting same result) I started trying to compile me a fix and stumbled onto the coolest toolbar I've ever had, I never realized I could make my own....so after 5 hours work I now have a hybrid gnome/kde system thats rock solid with everything working for the first time dual booting XPpro...I have to say the more I use Ubuntu the more impressed I am...not to mention I've already set-up 8 boxes for friends with the warty distro and am going to move them all up as soon as I get these system crash bugs worked out cause thats the LAST thing I want to happen on peoples boxes I'm trying to wean off window$...with many of them having way more money in software for windows to work than they paid for hardware. I am looking forward to wiping windows from my drives someday for good...and this community has brought me one more step closer to my dream:) thanks.....steve

---

### Post by troywill1 on 2005-04-27
I had to wrangle my way out of this mess as well.  Needless to say, it was not fun reconfiguring my KDE.

Here's to hoping that this will be resolved **soon** upstream...

Troy

---

### Post by Frihet on 2005-04-27
I did this:

-----

Originally Posted by Gianni Exile
Type the following
Code:

sudo apt-get install kdelibs=4:3.4.0-0ubuntu3 kdelibs-data=4:3.4.0-0ubuntu3

This should apply cleanly.

Don't update again until you see "knetworkconf" among the list of packages to be upgraded.

This is a genuine goof on Ubu's package release manager's part.

-----

I had to add everything back to the panel, but that was easy.  I actually learned some things.  I have not found the desktop switcher yet.  Anyone know haw to add that back to the panel?

Thought I was toast for a while.

Thanks.

---

### Post by Frihet on 2005-04-27
Ok.  I found theswitcher and dropped it onto the panel.

All is well!

---

### Post by jakel2k on 2005-05-02
Is this being looked into?  Does anyone have a reference from a developer?  On first install the system was great but since the upgrade I find it a hassle to use the system with a boggled KDE system.  Not good since I know some users might switch due to this... :???:

This issue seems like a huge issue and really should be attended to ASAP.

](*,)  ](*,)  ](*,)

---

### Post by epb613 on 2005-05-02
[https://bugzilla.ubuntu.com/show_bug.cgi?id=10035](https://bugzilla.ubuntu.com/show_bug.cgi?id=10035)

---

### Post by bluefrog on 2005-05-04
no fuss solution.

assuming you have already downloaded kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb

cd /var/cache/apt/archives
sudo dpkg -i --force-overwrite kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb

---

### Post by sprucio on 2005-05-07
Haven't tried using the force command but this sounds like something that needs to be fixed. Reading the bug page, it looks like it still hasn't been looked at by the developers.

I guess this is just really dependency problem issuse that needs to be resolved within the apt database.

---

### Post by jeremy on 2005-05-08
The developers are aware of it, but, for some unfathomable reason, haven't done anything about it yet. I wonder how many Kubuntu/ubuntu users are giving up because of this. Ubuntu's astonishing rise in popularity over the past 7 or 8 months needs to be consolidated, not put at risk.

That said, I had no serious problems due to this "update", but I am not "yer average user".

---

### Post by wwwolf on 2005-05-08
I thought I was loosing my mind!  ](*,) 
I just happen to install new memory after having ran the update. when I turned the power back on the kpersonalizer popped up and I thought it was because I added memory. I selected a few things and then BOOM! No taskbar. I added the clock and kpager, but couldn't figure out how to show minimized programs or the icons in the system tray. I kept thinking it was something kpersonalizer had done but I couldn't ever rerun it because all I remember is that is was some kind of wizard. After two days of searching I found it but it didn't return my menu the way I had it.

I finnally found it this morning when I added the applets 'system tray' and 'taskbar'

I wish I found this message before I updated. Now I am paralyzed in fear. I don't know how to revert back and forcing the overwrite may make it worse. I have noticed that also I can no longer mount CDs and removable media.

How does something like this get fixed? will I eventually be able to select the kdelibs-data package after running 'sudo apt-get update' and everything will work again or will I have to go in manually and remove the data package? Will there be some instructions or will this fix be automated?  :? 

wwwolf

---

### Post by dodger on 2005-05-08
well, here's what I did (after forcing the upgrade of kde-libs (which I do NOT recommend):

as root (or sudo all following commands)

1. edit /etc/apt/sources from list and comment all ftp or http repos (so that only the cd remains as repo)
2. apt-get remove --purge kde*
3. apt-get install kubuntu-desktop

4. as normal user: rm -r .kde (might not be necessary)
5. rebuild your desktop  ;-) 

6. upgrade everything but kdelibs :-)
7. wait for the problem to get fixed

dodger

---

### Post by Segovia on 2005-05-17
LOL, this issue is still not fixed.  Wondering if anyone is at the wheel anymore?  Or have they abandoned kubuntu?

---

### Post by dodger on 2005-05-17
[QUOTE=Segovia]LOL, this issue is still not fixed.  Wondering if anyone is at the wheel anymore?  Or have they abandoned kubuntu?[/QUOTE]

I don't think they have abandoned Kubuntu but this is slowly starting to annoy me. Don't get me wrong, I really appreciate the effort that the kubuntu team put in the release and it is really working perfectly for me. 
well, apart from that update bug.  I am not a developer, but when the problem can be fixed with a script (as is mentioned on the kubuntu irc) then I do not understand what prevents this bug from being fixed in the repositories.

but I think that eventually there will  be a solution and  until then I just don't upgrade kde.

---

### Post by Segovia on 2005-05-17
I don't mean to sound like I'm complaining either, but I do have a great desire to see Kubuntu working as well as Ubuntu does.

---

### Post by SanderAnt on 2005-05-18
Overall, I've been very happy with Kubuntu. I installed Hoary a couple of months ago and upgraded to KDE, so I didn't get the complete Kubuntu effect, but KDE 3.4 along with Ubuntu's excellent hardware support and sensible security settings has been great.

That said I do think there is some legitimate concern of the future of Kubuntu. I was on #kubuntu a while back chatting with Johnathan Riddell and he told me that neither he or Chris Halls were Canonical employees, which came as shock to me given what I though was the success of Kubuntu.

I posted a message to the kubuntu-users mailing list, which Jeff Waugh (Canonical employee/Gnome Release Manager) responded that they had registered kubuntu.org early on, implying that Canonical had planned support early on.

While this is good news, it's not the same as having a dedicated Kubuntu employee(s). I think Johnathan and the rest of the Kubunutu team have done a remarkable job with this release, but without the proper resources I don't see all of the planned additions for Kubuntu (fixing Kynapic, KDE update manager, etc) happening any time soon. Without more support from Canonical it's safe to assume that Kubuntu will end up be as resource starved as Debian/KDE, if not more so given it has fewer developers.

I do think Canonical should clarify what their support for Kubuntu is, before they let us recommend it to people assuming it has some official support.

The placing of the forums and such imply it is a supported, official part of Ubuntu, but other parts (no CD, occasional mentions on ubuntu home page, etc.) aren't so clear.

---

### Post by philipacamaniac on 2005-05-18
Maybe we can petition Mark Shuttleworth to hire Riddell on, since the Kubuntu project has a lot of promise, and can potentially move a lot more people into the Ubuntu universe.

---

### Post by propagandhi on 2005-05-18
I also had this problem, but rather than taking any of the steps listed above, i simply removed the knetworkconf package, installed the kdelibs package and then reinstalled knetworkconf without incident.

---

### Post by jeremy on 2005-05-19
Oh dear me, here we go again...
[http://www.techworld.com/security/news/index.cfm?NewsID=3691](http://www.techworld.com/security/news/index.cfm?NewsID=3691)

---

### Post by ceti on 2005-05-19
[QUOTE=philipacamaniac]Maybe we can petition Mark Shuttleworth to hire Riddell on, since the Kubuntu project has a lot of promise, and can potentially move a lot more people into the Ubuntu universe.[/QUOTE]
 
Good idea, but how?
What does Riddell think?

---

### Post by philipacamaniac on 2005-05-19
[QUOTE=ceti]Good idea, but how?
What does Riddell think?[/QUOTE]

I'm not sure how he feels about it, but since he doesn't seem to browse these forums, we won't be able to ask him. Sure, someone could email him (his personal website is well known), but it seems like it would be a little invasive of his privacy. Maybe he hangs out on the IIRC? All in all, he's heavily involved with Kubuntu and the Ubuntu community. I bet he's happily hacking away at Breezy right now. 

If I was an experienced KDE hacker, I would join the development team and start fixing any known bugs right away, and get them pushed out to the main repositories. Hmm, this gives me good reason to go brush up my C++ and install KDevelop.

---

### Post by teumima on 2005-05-19
Man this sucks.

I personally stopped using kubuntu. This kde-libs issue is still not solved. So I stick to xfce. However, I like kubuntu so I give it to my customers, as it's the only thing that will keep them away from windows. I hope it gets sorted. How long has it been, a month?

---

### Post by ltmon on 2005-05-19
[QUOTE=philipacamaniac]I'm not sure how he feels about it, but since he doesn't seem to browse these forums, we won't be able to ask him. Sure, someone could email him (his personal website is well known), but it seems like it would be a little invasive of his privacy. Maybe he hangs out on the IIRC? All in all, he's heavily involved with Kubuntu and the Ubuntu community. I bet he's happily hacking away at Breezy right now. 

If I was an experienced KDE hacker, I would join the development team and start fixing any known bugs right away, and get them pushed out to the main repositories. Hmm, this gives me good reason to go brush up my C++ and install KDevelop.[/QUOTE]
 Try the kubuntu-devel mailing list and #kubuntu on IRC.  The devs seem to hang out there more so than on the forums.

---

### Post by nrayever on 2005-05-26
[QUOTE=Gianni Exile]Type the following ```
sudo apt-get install kdelibs=4:3.4.0-0ubuntu3 kdelibs-data=4:3.4.0-0ubuntu3
```

This should apply cleanly.

Don't update again until you see "knetworkconf" among the list of packages to be upgraded.

This is a genuine goof on Ubu's package release manager's part.[/QUOTE]

Thanks Gianni this work really good!!  \\:D/  \\:D/

---

