---
title: "Another alacarte problem"
date: 2007-11-06
forum: Desktop Environments
---

### Post by 6eleven on 2007-11-06
Gutsy Gibbon, alacarte 0.11.3-1ubuntu1

As a regular user running alacarte, no changes take effect. I check a checkbox, it stays for about 3 seconds, then the check disappears. Have tried various things:

apt-get install --reinstall alacarte
apt-get install inotify-tools
apt-get install menu menu-xdg
Open xterm, run /usr/bin/alacarte (no output to xterm)
chown -R user:user $HOME/.config
chown -R user:user $HOME/.local
Replace 'gksu' with 'gksudo' (see below)

I should add that only entries containing "gksu" in the exec portion seem to be affected. If I run the *exact* command as in the Launcher Properties menu, the application (restricted driver manager, Software Sources, Services, Synaptic Package Manager, etc) works fine. gksudo vs. gksu has no effect.

Any hints appreciated. Gets slightly more annoying every day..

---

### Post by 6eleven on 2007-11-06
Ok, come on..I know alacarte is "boring" and broken or whatnot. But seriously..what the hell else is there to edit menus with? Or maybe its time to learn python and get to the bottom of what should be a blindingly simple program..

---

### Post by ridgeland on 2007-11-14
I'll subscribe to this problem as I have the same issue.
Alacarte changes will not stay.
I've tried running with $ sudo alacarte - changes don't stay.
I am in admin group - full user rights for everything.  Menu changes don't stick.
Ubuntu 7.10 broken
Ubuntu 7.04 was fine.

OK I fixed it once I thought of the 7.04 working.
I wanted System Tools in my menu, but everytime I clicked it on it automatically cleared the checkmark.
I solved it by $ sudo gedit /etc/xdg/menus/applications.menu
in gedit I searched for "system"
I found a section with weird code (like html code)
  <!-- System Tools-->
  <Menu>
    <Name>System</Name>
    <Directory>System-Tools.directory</Directory>
    <Include>
      <And>
        <Category>System</Category>
        <Not><Category>Settings</Category></Not>
      </And>
    </Include>
  </Menu>   <!-- End System Tools -->

I commented out the <Not> line with <!--  -->
<!-- <Not><.....</Not>  -->
Note don't use a # to comment out here.
Now I have the system tools in my menu.

There is a second file that may need editing:
/home/you/.config/menus/applications.menu

Good luck.
Post back if it helps or not.

Edited to add:
I now see that changing this global file also put "System Tools" in the menu of other users.  Alacarte is broken IMHO.  I think as System Admin I should be allowed to put anything in my menu that I want.  I got System Tools but see there are other options that are blocked but the names are not as clear.  In alacarte I still see the auto-uncheck interfering.

---

### Post by Amaranth on 2008-01-11
You can't make it show empty menus, that's probably what your problem was. If a menu has nothing in it why show it? Removing the <Not> just made things go in there that probably shouldn't have.

---

### Post by TeaSwigger on 2008-01-12
Hello, both of ye with menu woes. May I offer some suggestions?

- try this in a terminal

```
sudo update-menus
```

- Forget alacarte and the whole mess. 

The idea being to get back to the default menu - which works - and change what you want without alacarte. Some tips to that end:

Alacarte is a "middle-man" between the "freedesktop standard" menu system and the menu you see in ubuntu / Gnome. The "freedesktop standard" stuff consists of special text files put in certain folders where the menu scans for 'em. Most everything in your system has a something.desktop. These special files are for instance, firefox.desktop, which is probably in /usr/share/applications folder. If you opened it in a text program like gedit, you'll see notes on what category in a menu Firefox should go, what icon it should show, what to launch firefox with, what stuff Firefox could be set to open up like web pages, and that sort of thing. 

Of course, you could use sudo and change these files to go anywhere in the menus you want, or even make your own entries. Anything from altering one entry to radically re-making your menus. Peek at various ones and you'll soon make out what makes what do what.

There are also these .desktop files in your home folder. For instance in .local/share/applications. These can be customized copies since they supercede the ones in /usr/share/applications, or if only put there, for stuff meant for only your user to use. There's also stuff in ~/.config/menus and another area used system wide is /usr/local (sort of an alternative to /usr/share I guess we can say).

What alacarte does is put customized files in .local/share/applications and pre-empt the menu with special instructions in files put in... a hidden folder in your home folder, I forget where. Er, when and if it works that is. You could delete alacarte's stuff in your home folder to restore the "freedesktop standard" menu, in whatever mess it is in, so you can edit stuff on your own. 

Understand I don't often use ubuntu / Gnome, I use Kubuntu / KDE, so I'm sorry details are sketchy. That should give you some ideas though, to let you take control from the sometimes problematic alacarte. :)

---

### Post by ridgeland on 2008-01-14
At first Amaranth's post did not make any sense to me.  I want the System Tools menu that has several items in it, not an empty menu.  On a fresh install I still had the same issue of the check box clearing itself.  So I tried first opening the menu and turning on one of the items under the menu.  This turned on the menu and it stayed checked on.
I'll try again to say this as to me it's counter intuitive.  You cannot add a menu so you can turn on the items under the menu without first turning on at least one of the items under the menu.  Or in my specific case to turn on the System Tools menu I must first turn on an item in that menu (i.e. Root Terminal).  Then System Tools menu turns itself on.

---

