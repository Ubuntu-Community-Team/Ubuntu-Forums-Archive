---
title: "LXpanel Loses width setting on reboot"
date: 2016-01-02
forum: Desktop Environments
---

### Post by the_mulletator on 2016-01-02
Hi guys,

I'm using Lubuntu 15.10.  I have an extra panel which I use like a dock on the left side.  I have it set to disappear when not in use.

I'm using the Application Launcher to put shortcuts on the panel like a dock for my favourite apps.

Here's a description of my problem.

I set the width of the panel to one icon wide (40px) so the icons appear nicely along the side of my screen.  When I reboot the setting is lost and it defaults to 150px wide.  This makes the dock kind of useless.

I noticed if I mess around with the position (ie. set it to top instead of side) it defaults to 150px too.

What can I do to make the setting permanent?  All the other settings I pick for the panel remain in place.

Thanks

FYI, I am not actually new to this forum I just haven't used it in a long time and they changed the login system.  I guess I lost all my old posts and whatnot.

---

### Post by ajgreeny on 2016-01-02
You can probably get all your old login and posta back if you start a thread in the Resolution Centre
[http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)
stating what email was used in the past, and the forum username you used previously.

I can not help with your LXpanel problem, I'm afraid.  Have you looked in the links that are shown at [https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks) which could help you?

---

### Post by the_mulletator on 2016-01-05
Come on guys.  This is driving me crazy.  I'm sure there is a simple solution.

Has anyone else had this problem?

---

### Post by chicob2 on 2016-02-09
I have the same problem.
Left panel is set to be 34 px wide, but on reboot/lxpanel crash/lxpanel reset it defaults to 150 px.

I've tried changing the available options, with no results.
After editing the panel, when I check ~/.config/lxpanel/Lubuntu/panels/left, it reads

Global {
   edge=left
   monitor=0
   **height=34**
   transparent=1
   background=0
   tintcolor=#6a6a6a
   alpha=255
   width=91
   iconsize=32
   autohide=1
   heightwhenhidden=2
   setdocktype=0
}

so why does it change back to 150 px?
I'm on Lubuntu 15.10.

---

### Post by mr-tin-man on 2016-02-14
You might of already seen this, don't know. Seems to go into a lot of detail on your subject.  (Good luck) I run lubuntu on one machine, but seldom get on that machine.  Here is the link  : [http://wiki.lxde.org/en/LXPanel](http://wiki.lxde.org/en/LXPanel)


mr tin man

---

### Post by LaneLester on 2016-03-19
I'm one more person suffering from this bug. I fiddled with a bunch of stuff without success. I see that my preferred width on the second panel is preserved in .config/lxpanel, but it seems the program ignores the value for its preferred 150. Very annoying.

Lane

---

### Post by meltingpot2015 on 2016-03-20
Have had many issues with lxpanel on Ubuntu 14.04. See my postings on this site. Haven't had any replies to them. Kinda like talking to a brick wall. (lack of support for lxpanel is clearly visible)


I will be installing ubuntu 15.10 soon, but will be staying well away from lxpanel. 


Thanks for the heads-up guys.

---

### Post by LaneLester on 2016-03-21
For other reasons, I'm pleased with my new installation of **Lubuntu 15.10**, so I'll be sticking with **lxpanel**. I've decided to give up on the side panel and configure the lxpanel along the bottom to look like my Windows 10 partition. It has the shortcut icons along the bottom on the left, and icons-only for running programs to the right on the taskbar.

Another drawback to lxpanel is that its GUI config lists only the shortcuts that were created during installation. So programs that are added later never show up as available for the panel, even though they have files in /usr/share/applications. I'm getting around this shortcoming by editing ~/.config/lxpanel/Lubuntu/panels/panel manually to add the new shortcuts. Here is one such addition:
[INDENT]Button {
      id=menu://applications/Internet/filezilla.desktop
    }[/INDENT]

Lane

---

### Post by vasa1 on 2016-03-21
> **LaneLester said:**
> ...
Another drawback to lxpanel is that **its GUI config lists only the shortcuts that were created during installation**. So programs that are added later never show up as available for the panel, even though they have files in /usr/share/applications. ...
Hi, can you clarify what you mean by the part in bold? Is what I'm showing in the attached image what you're referring to? That should update automatically.

---

### Post by LaneLester on 2016-03-21
> **vasa1 said:**
> Hi, can you clarify what you mean by the part in bold? Is what I'm showing in the attached image what you're referring to? That should update automatically.

No, the menu (shown in the graphic) does update when programs are added. When you right-click on the panel and select **Add-Remove Panel Items**, a small **Panel Preferences** window comes up. If you select **Application Launch Bar** and click **Preferences**, a small **Application Launch Bar** window comes up. On the right are **Installed Applications**, from which you can select items to add. It is this right-hand list that shows only the programs that were installed during the installation of Lubuntu, at least on my system.

Lane

---

### Post by vasa1 on 2016-03-21
Thank you for explaining so clearly. I'm still on 14.04 and my list does update. As you can see there at least two items, mkusb and unetbootin, there that aren't part of a default Lubuntu install. I'll check with a 16.04 Live USB later because I plan to move to 16.04 as soon as it is released.

I've never had to use this, but I've come across *lxpanelctl restart* being suggested. I don't know if it will help.

---

### Post by meltingpot2015 on 2016-03-21
There is more than one panel out there. (No need to become boxed-in to one panel) Unless you are a habitual computer user that prefers the same old, same old.


Have a look at pypanel, fbpanel, or tint2.

---

### Post by vasa1 on 2016-03-22
> **meltingpot2015 said:**
> There is more than one panel out there. (No need to become boxed-in to one panel) Unless you are a habitual computer user that prefers the same old, same old.


Have a look at pypanel, fbpanel, or tint2.Why don't you start a thread comparing panels? That would be most welcome. I'm sure it will benefit many users.

---

### Post by Dennis N on 2016-03-22
> LXpanel Loses width setting on reboot

I can't reproduce this width setting problem in Lubuntu 16.04 beta1. Possibly the problem has been fixed, as there is a newer version of LXPanel. Try it out and see.

EDIT
Bug report located - status is fixed with lxpanel 0.8.2 (which is what I have in Lubuntu 16.04 beta1)
[https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/1534438](https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/1534438)

---

### Post by meltingpot2015 on 2016-03-24
> **vasa1 said:**
> Why don't you start a thread comparing panels? That would be most welcome. I'm sure it will benefit many users.

Probably could, but seem to spend forever tweaking privacy settings.


BTW, I've been using Ubuntu 15.10 with xfce desktop v4.12 and xfce4-panel for 4 days and can highly recommend it. Only had a minor wobble when the file manager froze once. Had to close it and re-open. That's it.

---

