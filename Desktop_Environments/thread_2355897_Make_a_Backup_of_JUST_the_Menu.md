---
title: "Make a Backup of JUST the Menu"
date: 2017-03-17
forum: Desktop Environments
---

### Post by poisonfor3 on 2017-03-17
I just installed Xubuntu from Ubuntu Mate (so far love it) but spent going on 2 days just on setting up my menu (see pic below) to get it just the way I like it. All the programs I need are in the little drop down menu.

I seem to remember there was a way to backup just the menu. I found the "Xfce Panel Switch" ( More on it here: [https://smdavis.us/2015/10/12/xfce-panel-switch-introduction/](https://smdavis.us/2015/10/12/xfce-panel-switch-introduction/) ) but it does not seem to back up the Menu layout, that I can tell.

I back up my home folder all the time but I do not know if my menu layout is stored in there someplace.

What I want to do is to back up just my basic "Application Menu". OR if it is stored in my Home folder know where it is so when I move to another linux (or do a fresh install) I can restore it just the way it is now . . . without doing a 2 day fix.

I been googling but not getting any answers. All my hits (both here and with DuckDuckGo) that I get, are stuff on how to back up other stuff. 

Thanks for any help,
-Annie
(P.S dont care about the whisker menu next to the "Application Menu" in the pic., I plan to remove it from my panel)

[[IMG]https://ubuntuforums.org/attachment.php?attachmentid=274202&stc=1&thumb=1&d=1489802727[/IMG]]("https://ubuntuforums.org/attachment.php?attachmentid=274202&d=1489804852")



UPDATE:

Been researching this all day. (The OCD in me) and seems to be a problem from day one, here is an OLD thread talking about it:

[https://ubuntuforums.org/showthread.php?t=1268667](https://ubuntuforums.org/showthread.php?t=1268667)

and way back to the dark ages of 2005 here:

[https://ubuntuforums.org/showthread.php?t=66040](https://ubuntuforums.org/showthread.php?t=66040)

The "Panel switcher" idea seems like a dead end.

I used alacarte and there is an alternative(s) to it but that is a different topic.

I did find 4 places where they talk about where the information is stored and or how to back it up. So as long as I use MenuLibre or Alacarte I should be able to get my "backup software" to go to the areas where it is stored and back them up and put them into one folder for me so all the settings are in one place. If I knew how to write programs I could make one to automate the whole thing but I can set up the backup program to backup once a month so it is never to old and should safe a lot of time the next time I do a reinstall. Here are 4 links I found helpful.

[http://askubuntu.com/questions/229200/where-does-alacarte-store-the-file-with-the-edited-menus](http://askubuntu.com/questions/229200/where-does-alacarte-store-the-file-with-the-edited-menus)

[https://answers.launchpad.net/menulibre/+question/248817](https://answers.launchpad.net/menulibre/+question/248817)

[https://ubuntuforums.org/showthread.php?t=531216](https://ubuntuforums.org/showthread.php?t=531216)

[https://ubuntuforums.org/showthread.php?t=1099239](https://ubuntuforums.org/showthread.php?t=1099239)

When I was doing my research "googling" with different terms, funny how THIS VERY thread was already coming up as a top hit LOL, so I will post my updates as I get new information. Hope it will help some other people.

---

### Post by oldos2er on 2017-03-18
> I back up my home folder all the time but I do not know if my menu layout is stored in there someplace. I'm pretty sure it is. From what I can find, ~/.config/xfce4 is the main folder you want to backup (see post #3 [here)]("https://forum.xfce.org/viewtopic.php?id=9133") so if you're backing up your entire /home/user folder you should have it already.

---

### Post by poisonfor3 on 2017-03-18
@[**[COLOR=#990303][B]oldos2er**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=338320")

Nice of you to find the nice link albeit a nice read, they are talking about backing up much more than JUST the menu. I lost count how many hours I have spent on this. Well over 20 working hours. As far as people that _do not know how to program_ (other than the long dead Basic) I may now be the worlds leading expert on backing up just the menu items for Ubuntu like systems ... at least i feel like it. Here is what my best guess is as to what needs to be backed up:


Files you will want to backup:
~/.config/menus/xfce-applications.menu
/etc/xdg/menus/gnome-applications.menu
/etc/xdg/menus/gnome-flashback-applications.menu
/etc/xdg/menus/kde4-applications.menu
/etc/xdg/menus/xfce-applications.menu
/etc/xdg/xdg-xubuntu/menus/xfce-applications.menu
/etc/xdg/xdg-xubuntu/menus/xfce-settings-manager.menu


Folders you will want to backup:
~/.local/share/desktop-directories/
~/.local/share/applications/
/usr/share/desktop-directories/


Folders that you may not want to past intact if you do/want a fresh install.I plan to pick and choose the ones I need out of them and put them in one by one.
/usr/share/app-install/desktop/
/usr/share/applications/
/usr/share/icons/
/usr/share/pixmaps/


I am building my son's (desktop) computer now for him. I plan to put xUbuntu on it. I will try to restore the menu that I have on here onto it. (then re-install Xubuntu; I am sure he will not want my menu) I will report back here to let, anyone that might care, know how well it goes. I still have no clue as to IF "Xfce Panel Switch" (~.local/share/xfpanel-switch/) backs up menu items too. I will try to install it first and see what it does. Maybe I can solve it myself.  :P

---

### Post by oldos2er on 2017-03-18
Lol, count me among the "people that _do not know how to program."_ I'm just an end user who's run so-called alternative OSes for a long time now. 

I did assume earlier that if you're backing up your home folder, that includes all its hidden files and folders.

I wish I was better versed in xfce4 settings to help you; at any rate, good luck.

---

