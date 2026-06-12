---
title: "Updating applications"
date: 2009-05-04
forum: General Help
---

### Post by pinguino99 on 2009-05-04
I love ubuntu and the linux phylosophy.
But, at least in ubuntu  (don't know many distros) i think there is a bbbig limitation.

For example: Let's suppose i have a dapper  . It's june 2006, so not soo old. It comes with firefox 1.5.    Firefox 3 is not in the repo. So installing/upgrading it is rather hard  (compare it with windows).

Another example, i am in hardy  (LTS , one year old) and i have gnome-do.
It's version 0.4 from repos.
In Intrepid is 0.6.
In Jaunty 0.8  (i suppose).
So...if i want gnome do 0.8 in hardy what shoud i do ?

Question is... is it normale that if i want recent versions of apps, i need to upgrade the distro version ?

Is there any other distro where this task is easier?
If i want to deploy many linux desktops in my company, i cannot upgrade every desktop any time i need a software update !!

The same thing is for the hardware drivers... they are included in the kernel.
If i have recent hardware , i am obliged to upgrade kernel  (update distro??)

But not very easy  (like in windows) to "install from cd"

I think linux is not mature in the desktop, unfortunately.

Thanks for any suggestion...

---

### Post by KhaaL on 2009-05-04
usually you need to update several packages in order to update the application you use. for example, gnome do might need a new functionality in a updated library and therefore need it in order to update.

But you might still update certain applications or have the latest, bleeding edge if they have a PPA set up. you can look for them in launchpad or use this search engine: [http://ppa-search.appspot.com/](http://ppa-search.appspot.com/)

---

### Post by mb_webguy on 2009-05-04
Well, first of all, the primary difference between releases *is* the software.  

Second, upgrading from one release to the next, or from any release to an LTS release (even if it skips a normal release) is extremely easy, and doesn't require a complete reinstall of the OS.  Unlike Windows, where each release is a completely different OS, Ubuntu's releases are incremental.  Each release is same OS as the previous release, but updated and improved.

Third, if you want to keep a certain version of Ubuntu but upgrade a specific application, you have several options.  PPAs are available for many of the more common applications.  Debs are also available for most major software projects.  And in a worst-case-scenario, you can compile the software from source.

---

### Post by pinguino99 on 2009-05-04
> **KhaaL said:**
> usually you need to update several packages in order to update the application you use. for example, gnome do might need a new functionality in a updated library and therefore need it in order to update.

But you might still update certain applications or have the latest, bleeding edge if they have a PPA set up. you can look for them in launchpad or use this search engine: [http://ppa-search.appspot.com/](http://ppa-search.appspot.com/)

gnome-do was just an example.
Another practical example is the "gnome screenshot" : from Intrepid, it allows to "copy to clipboard". It's a very useful function for paste screenshot into an email body message.
In Hardy this "copy to clipboard" is not allowed...

In general, i have fear to massive deploy ubuntu desktops in my company : We have lot of XP desktops that are 6-7 years old.  If i need to update (for example) firefox, or openoffice, it's rather easy. Very typical "next-next-next-finish" installation.
But let's be honest, if i give ubuntu to some users in a company, and i need to someday soon upgrade to firefox 3.5 or openoffice 3.1 what should i do ?  If i have a new hardware and kernel has not drivers, what should i do ?
Let's face it... i adore the ubuntu/linux spirit but i have to face the reality and understand that the "Year of linux in desktop" has to come.

Maybe there are other distros where upgrading apps version is easier ?

---

### Post by mb_webguy on 2009-05-04
Again I say, upgrading from one version to the next is simply a matter of a simple click of a button.  And with the proper network setup, changes to software sources (and thus the addition of PPAs) can be mirrored simultaneously across multiple computers.

Especially given the existence of PPAs, I would say that maintenance of Ubuntu desktops is actually *easier* than Windows desktops.  *All* software can be updated and upgraded as easily as Windows installs system updates -- actually moreso, since Linux rarely requires a restart after installing updates.

However, some other distributions, specifically those with rolling releases, *would* make upgrading software easier.  But it is at the cost of stability.  Without fixed repositories, testing packages is aiming at a constantly moving target.  With PPAs, you can be specific in the software which you want to be continuously upgraded, while maintaining overall system stability.

---

### Post by pinguino99 on 2009-05-05
> Again I say, upgrading from one version to the next is simply a matter of a simple click of a button. 

Rather optimistic ... upgrade is never a 100% painless operation. Just read in this forum how many users complain after an upgrade. An install from zero is always suggested. You can do it daily in your home pc's, but in a company with dozens of desktops you cannot do that.


>  And with the proper network setup, changes to software sources (and thus the addition of PPAs) can be mirrored simultaneously across multiple computers.

It means that i have to manage a PPA for every application ??
Anyway it's interesting...where i can learn how to download only once the updates and apply them simultaneously ?


> Especially given the existence of PPAs, I would say that maintenance of Ubuntu desktops is actually *easier* than Windows desktops.  *All* software can be updated and upgraded as easily as Windows installs system updates -- actually moreso, since Linux rarely requires a restart after installing updates.

Can you give me an example to maintain ppa, for example, of gnome screenshot, or wine , or vinagre, or openoffice, or firefox, in a so "easier way than windows" ?? I am not looking for flames, i just want to understand limits (and advantages) of a massive linux deployment. It can be a painful boomerang going back to my forehead.


> However, some other distributions, specifically those with rolling releases, *would* make upgrading software easier.  But it is at the cost of stability.  Without fixed repositories, testing packages is aiming at a constantly moving target.  With PPAs, you can be specific in the software which you want to be continuously upgraded, while maintaining overall system stability.

Can you give me an example of a distro where i can easily upgrade versions of applications, when needed ??

Thanks for all
Regards

---

### Post by KhaaL on 2009-05-05
> 
Can you give me an example to maintain ppa, for example, of gnome screenshot, or wine , or vinagre, or openoffice, or firefox, in a so "easier way than windows" ?? I am not looking for flames, i just want to understand limits (and advantages) of a massive linux deployment. It can be a painful boomerang going back to my forehead.



For wine: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

I dont have the other mentioned apps PPA so I cannot give you more examples. while the theory that ubuntu can always stay up to date with a PPA, the PPA will require to be maintained for every release (hardy, intrepid, jaunty etc) or there might be breakage/incompability between the packages and the installed release... Sorry I can't shed more light on massdeployment.

---

### Post by mcduck on 2009-05-05
> **pinguino99 said:**
> 
Can you give me an example to maintain ppa, for example, of gnome screenshot, or wine , or vinagre, or openoffice, or firefox, in a so "easier way than windows" ?? I am not looking for flames, i just want to understand limits (and advantages) of a massive linux deployment. It can be a painful boomerang going back to my forehead.
If you want to update that many rather generic applications you really end doing exactly the same, if not more, work it would take to update the whole distribution. Even if you'd do it by making a fresh install of the new version. Really, how long would it take to do the windows-style updating of all those programs, by hand, on each computer? Quite likely more than the ~20 minutes it takes to upgrade Ubuntu to new version..

It just doesn't make sense to try to stick with outdated OS release while at the same time wanting to have latest versions of all your programs. Even less s when the difference between updating just the programs and updating everything is usually very small.

Like already mentioned, the main thing in new Ubuntu releases is new versions of all programs. And in the same way one of the main features of Ubuntu (not Linux) is that after release packages are only updated for security reasons and to fix serious bugs, never just to add new features. If you prefer less focus on stability and more latest program versions use some distribution with rolling releases instead of Ubuntu.

---

### Post by pinguino99 on 2009-05-05
> Really, how long would it take to do the windows-style updating of all those programs, by hand, on each computer? Quite likely more than the ~20 minutes it takes to upgrade Ubuntu to new version..

Well, let's face the reality.... 20 minutes for a distro-upgrade ??
I am trying to do a dist-upgrade from hardy to intrepid. And almost 2 hours just for downloading. The whole process will take hours.
Maybe there are quick ways to do it (a local repo, maybe).


> It just doesn't make sense to try to stick with outdated OS release while at the same time wanting to have latest versions of all your programs. Even less s when the difference between updating just the programs and updating everything is usually very small.

That's  the problem : you say "outdated version" because 6 months means outdates. In Windows world things are different : we have XP desktop from 2004 and they are still there, almost untouched. Because every application install in the same way, after 5 years.

I think you try to put in a condition to be sysadmin, you cannot daily worry about updating. For linux servers is exactly as it should be: we have some linux servers here, that never need to be touched. But it's "another world" and another topic.
Try to compare : an XP desktop and a ubuntu desktop in a company. XP desktop in a LAN (with a good firewall/antivirus structure of course) don't need to be periodically updated.
With ubuntu, it's the only way for having the possibility to upgrade apps version.

---

### Post by mcduck on 2009-05-05
20 minutes is what it takes for me. Of course depends on your internet connection, but if you have a slow connection then you definitely don't want to download the update separately on all machines but instead do the upgrade using the CD image, or a local repository.

But consider the amount of time updating all those programs alone would take. Then remember that updating those programs would really take you to almost the same situation you would end if you updated the whole system, with updating the OS itself being smaller change than what you already did. Most of the stuff you need to download for the update comes from those very same, big software packages (like OpenOffice) anyway.

What comes to outdated OS versus outdated software, how often can you say that you really need the new features in all those programs you have? But you never ever need the new features the OS update would bring? I mean I can understand wanting to stick with the OS version for long time (at least in some situation) but the reasons for that would be exactly the same reasons for sticking with the same program versions as well. At least in Linux world, where updating packages is pretty much automatic and you don't usually have to worry about compatibility issues and things changing too much if you update (as in updating from Win XP to Vista).

But in the end I still have to repeat, stable, tested and thus fixed package versions with the distribution release offering latest program versions every 6 months is just the way Ubuntu selected to balance between up-to-date stuff and stability. If you feel that it's not what you want then there are endless amounts of other distribution, with  almost very possible updating method you could imagine ranging from newer-update to rolling releases which make automatically sure you always have the latest possible version of every program you use. Just pick one with the system that fits your needs.

---

### Post by pinguino99 on 2009-05-05
> 20 minutes is what it takes for me. Of course depends on your internet connection, but if you have a slow connection then you definitely don't want to download the update separately on all machines but instead do the upgrade using the CD image, or a local repository.


The time needed for the upgrade depends on many things: the main are internet connection speed , the other is Ram/CPU.  Anyway a good study would be the "local repository". Did not try, yet.
Anyway, from hardy to intrepid lasted in total about 2 hours.
And upgrade "asked" me some things about keeping of overwriting some configuration files.
But this forum is full of person that have not succesfull upgrade. I also had some issues. So the total time depends also on this.


Anyway, for what i saw until now, times are not mature enough for a massive linux deployment.
There are also other problems, depending on situation.  
One BBIG problem is interoperability. My company has many servers M$ 2003, and samba/winbind/likewise can do something, but there are always problems.
Some example ?
- Centralizing logon scripts  (for automounting shares, for example)
- Network samba printers : they require authentication when creating (samba/likewise open don't pass username/password/domain)
- Ultravnc client and server non existing for linux. There are others viewer/servers, but cannot be compared to ultravnc (connect at GDM logon screen for example, even X11VNC can do it, but not very well).
- Business applications seldom has a linux client. Eg. Zetafax.  Or  the SAP Gui ... it's a Java app.
Remember that in business enviroment, 99,99% of desktops have windows, so it's not easy to find good proprietary linux client from software houses.
- 5250 emulator for connecting to Iseries.  Nothing very good (compared to Client Access or Mocha 5250 for example).  And tn5250j is "dead".
- MS Office not with linux client  (don't consider wine...). So , again, interoperability with .doc and .xls  (the de facto standard) is never 100% sure.
- Some missing drivers for new or particular hardware.

I could go on and on...
I have linux desktop as my workstation  (i moved from fedora to ubuntu) and we have some Centos server.
But i cannot propose to my boss to move to linux for the reasons above.


Regards
Pinguino99

---

