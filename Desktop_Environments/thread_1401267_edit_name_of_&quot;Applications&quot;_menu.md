---
title: "edit name of &quot;Applications&quot; menu?"
date: 2010-02-07
forum: Desktop Environments
---

### Post by =JeffH on 2010-02-07
Hi, 

I'm trying to figure out how to rename my applications menu from "Applications" to "Apps" in order to (hopefully) get the "main menubar" applet to take up less real estate in my panel. (thus I also will want to edit the name of the "System" menu to eg "Sys")

As far as I can determine, "applications.menu" is the requisite file, and on my Karmic 9.10 system it lives in...

  /etc/xdg/menus/applications.menu
  /home/hodges/.config/menus/applications.menu
  /usr/share/app-install/desktop/applications.menu

..and has this (single) associated .directory file..

  /usr/share/desktop-directories/X-GNOME-Menu-Applications.directory

I do not have XDG_CONFIG_HOME nor XDG_CONFIG_DIRS nor XDG_DATA_DIRS set in my environment, thus AFAICT from "GNOME Desktop System Administration Guide", the applications.menu file in ~/.config as well as the .directory file in /usr/share/desktop-directories ought to be the requisite files to edit. 

So I did so, changing   <Name>Applications</Name>  to   <Name>Apps</Name>   
in  /home/hodges/.config/menus/applications.menu, 

as well as changing   Name=Applications   to   Name=Apps   
in   /usr/share/desktop-directories/X-GNOME-Menu-Applications.directory.

And my "Applications" menu remains named "Applications" (after logging out and back in), rather than "Apps".  Later tonight or tomorrow I'll try a reboot, but I have some other stuff I have to do right now. 

Any clues as to what's going on and how I can effect these changes are very welcome. 

thanks,

=JeffH

---

### Post by =JeffH on 2010-02-09
turns out I received timely suggestions/thoughts over on [email]ubuntu-users@lists.ubuntu.com[/email]....

NoOp helpfully suggested:
 >
 > Rather than do that, why not just install the 'Main Menu' rather than
 > use the 'Menu Bar'?

doh.  just hadn't played around enuff with gnome as yet, thanks.

I just gunned "menu bar" and replaced with "main menu" (plus "lock screen" and
"logout").


sktsee thoughtfully provided:
 >
 > [http://tuananh.me/2009/12/a-complete-guide-to-customize-gnome-panel.html](http://tuananh.me/2009/12/a-complete-guide-to-customize-gnome-panel.html)
 >
 > I think the names are hardcoded in the gnome-panel binary (could be wrong
 > about that), but the website listed above used a trick with text
 > translations used to localize the messages that apps display into the
 > user's preferred language. Basically, the idea is to translate English
 > "Applications" into whatever string you choose.

ah, interesting suggestion, may followup on it at some point.

Seems kinda odd/broken for the strings to be bound into the executables when
the provided sysad docs imply such stuff can be altered via the config files,
but oh well...


thanks again,

=JeffH

---

