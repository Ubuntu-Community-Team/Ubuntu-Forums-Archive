---
title: "Installing Gnome and KDE Together and Menu Problems"
date: 2005-07-18
forum: Desktop Environments
---

### Post by audax321 on 2005-07-18
I have Gnome right now and want to install KDE. The problem is that I want to keep both the menus separate. I know the commands for the various applications and if I absolutely have to use, for example, a Gnome app in KDE, I can just use the run dialog. But I don't want any Gnome apps in the KDE menu and vice versa. Is there a way to do this?

I was thinking about creating a new user and then just use KDE with that user and Gnome with my current one. But, then I started thinking that KDE might look at the root installation and get the default Gnome menu from there and Gnome might look at the root installation and get the default KDE menu. Am I wrong here? Also, how do I add/delete users?


Thanks..  :)

---

### Post by dave9191 on 2005-07-18
If you have ubuntu and install KDE it will have its own menu that you can customise. And vice versa.

As for adding and removing users there are 2 commands for that. 

adduser
deluser

Dave

---

### Post by audax321 on 2005-07-18
I was hoping there was just a config file or something I could edit and tell it not to import any menus from other desktops. Oh well, I guess I'll just manually edit the menus... no real point for two user either I guess.

Thanks...

---

### Post by everettattebury on 2006-01-27
[QUOTE=audax321]I was hoping there was just a config file or something I could edit and tell it not to import any menus from other desktops. Oh well, I guess I'll just manually edit the menus... no real point for two user either I guess.

Thanks...[/QUOTE]

I found the following here: [http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/]("http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/")

> 
So you have Ubuntu installed and want to try out Kubuntu instead?

Easily Done!

Install the “kubuntu-desktop” meta-package, and you will have the option to log in to a KDE session the next time you boot up (Choose KDE from among the session options, before you enter the username and password in the graphical login screen)

You can install kubuntu-desktop by seraching for it in Synaptic, or simpler still, using the command:
$sudo apt-get install kubuntu-desktop

kubuntu-desktop is an architected collection of carefully selected KDE applications that creates a unique “desktop” experience, much like Ubuntu - it has one software utility for each function, again, like Ubuntu. So installing kubuntu-desktop will not give you all the KDE utilities, just like installing Ubuntu did not give you all the Gnome applications. There is another meta-package called “KDE” which, when installed will give you a different set of software. So if, after installing kubuntu-desktop, you find some of your favorite KDE apps missing, install the entire KDE suite, by installing the kde metapackage. I find this unneccassary, as kubuntu-desktop provides me with the minimal set of tools to get my work done. If I need something extra, like, kile, that very useful LaTeX editor, then I just install kile. Less baggage, better trip!

If you already knew all that was written above, and are beginning to think that it was a waste of time reading so far, fear not! I have a tip (not my original idea) that will make it worth your time.

The biggest annoyance for me, with having both gnome and KDE installed is that some KDE apps show up in the Gnome menus and some Gnome apps show up in the KDE menus. While this is not a “bad” thing, I would rather do without this.

To prevent KDE apps from showing up in Gnome menus and vice-versa, do the following before you install kubuntu-desktop :

(you can also create a small cleaner.sh script witht he following and run it as root)
$ sudo -s -H
#cd /usr/share/applications
#for i in *.desktop; do \
# if ! grep -q ^OnlyShowIn= $i; then \
# echo ‘OnlyShowIn=GNOME;’ >> $i \
# fi
#done

Now, after installing kubuntu-desktop do:

$cd /usr/share/applications/kde
$sudo -s -H
#for i in *.desktop; do
# if ! grep -q ^OnlyShowIn= $i; then
# echo ‘OnlyShowIn=KDE;’ >> $i
# fi
#done

What we did above was to tell the Gnome apps to only show in the gnome menus, and later, the KDE apps to only show in KDE menus. 

---

