---
title: "can you have both KDE and gnome ?"
date: 2005-04-21
forum: Desktop Environments
---

### Post by railz68 on 2005-04-21
I would like to try out ubuntu, and would really like to have both gui's.
Can anyone offer some advise on which way is best to do this.

I can download ubuntu, then install KDE. Or Kubuntu, then gnome.
Maybe either way gets the same results. But had to ask if one way is the better. Am I asking for troubles having both installed ?.

Sorry if this has been asked before, but doing a search on kde/gnome brought many many hits.

thx for any advice.

---

### Post by James Brown on 2005-04-21
[QUOTE=railz68]
I can download ubuntu, then install KDE. 
[/QUOTE]
Thats the way...  \\:D/

---

### Post by jdodson on 2005-04-21
[QUOTE=railz68]I would like to try out ubuntu, and would really like to have both gui's.
Can anyone offer some advise on which way is best to do this.

I can download ubuntu, then install KDE. Or Kubuntu, then gnome.
Maybe either way gets the same results. But had to ask if one way is the better. Am I asking for troubles having both installed ?.

Sorry if this has been asked before, but doing a search on kde/gnome brought many many hits.

thx for any advice.[/QUOTE]

your question is no problem.  

i would suggest downloading the main ubuntu CD here: [http://us.releases.ubuntu.com/releases/5.04/](http://us.releases.ubuntu.com/releases/5.04/)

from there you can open up the synaptic package manager and install the "kubuntu-base" package, which will install kde to your system.

from there you can either choose (at the login screen) to run kde or gnome.

---

### Post by Vache on 2005-04-21
[QUOTE=railz68]I would like to try out ubuntu, and would really like to have both gui's.
Can anyone offer some advise on which way is best to do this.

I can download ubuntu, then install KDE. Or Kubuntu, then gnome.
Maybe either way gets the same results. But had to ask if one way is the better. Am I asking for troubles having both installed ?.

Sorry if this has been asked before, but doing a search on kde/gnome brought many many hits.

thx for any advice.[/QUOTE]
 The short answer? Yes. You can have as many window managers or desktop environments as you want, installed at the same. You can switch between them on the fly (kind of).

I would go with the 'normal' Ubuntu install (Not Kubuntu) and then you can apt-get install 'whatever' to your heart's content. See the link in my signature for the unofficial Ubuntu guide.

---

### Post by railz68 on 2005-04-21
thanks all. I'll start my download of ubuntu right now.

I'm currently running Mandrake 10 with KDE. My wife and kids have a logon as well, and would to make the switch easy for them. Gonna try and get the desktops just like they are now (or very close to).
Myself, I really want to try gnome for a while.

---

### Post by dewey on 2005-04-21
Try backing up your /home directory, and it should save all of those configurations for your family, like address books, themes, icons, etc etc.  As long as you give them the same username on the ubuntu installation.

---

### Post by XDevHald on 2005-04-21
Also railz, check out **xnest** this is a great window based almost like Wine where you can log into windows and linux at the sametime, BUT this does not do that. Let's say you're on Gnome, and you want to check out KDE, well, load up xnest in your Applications > System Tools > Xnest. And you can log into KDE from there while being on Gnome :)

---

### Post by railz68 on 2005-04-21
[Q]Try backing up your /home directory, and it should save all of those configurations for your family, like address books, themes, icons, etc etc. As long as you give them the same username on the ubuntu installation.[/Q]

yes, I've looked into this. From what I've found, I'm hoping this works.

[Q]tar -cvpf /tmp/home.tar /home to tar up all of the files in /home under /tmp, preserving permissions (the p flag).

To undo it properly, after you have the new distro installed:
cd / tar -xvpf home.tar[/Q]

I'm hoping this works, and yes, I'll name the new accounts the same.

Thanks everyone, seems like a great distro, with fantastic support.

---

### Post by hyapadi on 2005-04-22
I have Ubuntu installed in my computer. But I want to try kde too. So I follow this tutorial [http://www.ubuntulinux.org/wiki/InstallingKDE](http://www.ubuntulinux.org/wiki/InstallingKDE) . And successfully get the kde working. but during the installation ( i use apt-get install kubuntu-desktop ) it show some errors. Some of the liblary can't be installed. but everything works well.
But soon as I entered the kde, i found that the menu have no application in list. I know that I can input the shorcut one by one. But is there any configuration tool that can set all these?

Thx

---

### Post by derrick1985 on 2005-04-22
[QUOTE=hyapadi]I have Ubuntu installed in my computer. But I want to try kde too. So I follow this tutorial [http://www.ubuntulinux.org/wiki/InstallingKDE](http://www.ubuntulinux.org/wiki/InstallingKDE) . And successfully get the kde working. but during the installation ( i use apt-get install kubuntu-desktop ) it show some errors. Some of the liblary can't be installed. but everything works well.
But soon as I entered the kde, i found that the menu have no application in list. I know that I can input the shorcut one by one. But is there any configuration tool that can set all these?

Thx[/QUOTE]

Wow, that's weird. I did the same thing the other day and didn't get that for a problem. Did you choose to keep GDM or did you go with KDM?

---

### Post by hyapadi on 2005-04-22
[QUOTE=derrick1985]Wow, that's weird. I did the same thing the other day and didn't get that for a problem. Did you choose to keep GDM or did you go with KDM?[/QUOTE]
I have managed the problem by using "sudo apt-get -f install".
Then I do update and upgrade.
Everythings works fine now.
Thx

---

### Post by Cool_dude_Prav on 2005-04-23
Is it possible to install GDM on KUbuntu?
And change it as and when I log in?(each time?)

---

### Post by crazybill on 2005-04-28
I was running Ubuntu with Gnome and wanted to try KDE.

So I typed **sudo apt-get install kubuntu-desktop** 
I chose the kde desktop as default. ... but on the login screen, it gives me the option to choose my type of desktop/terminal (with kde ... kubuntu) as the default.

---

### Post by foxy123 on 2005-04-28
I've got Gnome, KDE and XFCE on my PC, so my son runs Gnome, my wife uses KDE and I have xfce. The only problem is that in KDE there is only on option for exiting the system: logout. No "switch user", "reboot" or "turn off". Does any one know how to add those options?

---

### Post by Nu-Buntu on 2005-04-28
I did "sudo apt-get install kde" and have KDE 3.4 working fine. Am I missing something by not having done "sudo apt-get install kubuntu-desktop"? If so, what else do I need to add it now that I already have KDE running?

---

### Post by tread on 2005-04-28
kbuntu-desktop probably contains some more applications .. it will be like a pseudo package depending on other packages to provide you with a fully functional desktop environment.

If you arent missing any applications or feeling the need for any more .. you should be fine :)

You can also fire up synaptic (or kynaptic), search for kbuntu-desktop and see what it depends on.

---

### Post by Nu-Buntu on 2005-04-28
[QUOTE=tread]kbuntu-desktop probably contains some more applications .. it will be like a pseudo package depending on other packages to provide you with a fully functional desktop environment.

If you arent missing any applications or feeling the need for any more .. you should be fine :)

You can also fire up synaptic (or kynaptic), search for kbuntu-desktop and see what it depends on.[/QUOTE]
 Thanks, tread!

---

### Post by railz68 on 2005-04-29
[QUOTE=foxy123]I've got Gnome, KDE and XFCE on my PC, so my son runs Gnome, my wife uses KDE and I have xfce. The only problem is that in KDE there is only on option for exiting the system: logout. No "switch user", "reboot" or "turn off". Does any one know how to add those options?[/QUOTE]

Ok, so I chickened out of doing the change over last weekend. Making sure I've backed everything up and stuff. Still reading on how to make the change easier. Is this menu somehow added, is everyone using kde and gnome missing the "logout" from kde. I gotta have that  :neutral: 

foxy123, did you find a way to add it ?.

---

### Post by foxy123 on 2005-04-29
[QUOTE=railz68]Ok, so I chickened out of doing the change over last weekend. Making sure I've backed everything up and stuff. Still reading on how to make the change easier. Is this menu somehow added, is everyone using kde and gnome missing the "logout" from kde. I gotta have that  :neutral: 

foxy123, did you find a way to add it ?.[/QUOTE]

"logout" is not missing, while "reboot" and "switch user" are. I have not found a way to add them.

---

