---
title: "Is there a way to somewhat separate gnome/kde"
date: 2005-12-15
forum: Desktop Environments
---

### Post by pelle.k on 2005-12-15
As i understand it, menus built from:
**.desktop files are in ~/.local/share/applications, .directory files are in ~/.local/share/desktop-directories, .menu files are in ~/.config/menus**

So where do i change what path gnome uses to build it's menu structure? In that case i could have separate menus for gnome and KDE.
I do realize that if the path to where menu "stuff" should be installed is "hardcoded" in .deb packages you install, there's nothing to do about it, but if theres an enviroment variable synaptic / apt-get make use of, to correctly add it to the menu structure, then we could make things install to the menu of the current WM. Right?

[I]So if I install amarok in KDE,  amarok will not be visible in gnome menu.
If i install amarok in gnome, it will not be installed in KDE menu.
[/I]
or

[I]If I install amarok in KDE, amarok will be visible in KDE (+KDE menu in gnome).
If I install amarok in gnome, amarok will be visible in gnome(+GNOME menu in KDE).
(you just have to control where appz end up, KDE menu or gnome menu yourself by installing them using the correct session)
[/I]
or

A modified version, of the above:
(Is there a way to pass apt-get/synaptic command line switches, to tell where the menu they should end up on, is? Then you replace synaptic with "synaptic - gnome menu" or/and "synaptic - KDE menu")
*If I install amarok in gnome, amarok will be visible where i choose it to be. either in gnome menu, or KDE menu. (also, KDE appz end up in a subdirectory called KDE in gnome and vice versa)*

---

### Post by anil_robo on 2005-12-16
I am not a techie, but I guess you could use the **path** command to set the default paths. Isn't it? Please let all know if it does the trick, and also post details on how you did that.

---

### Post by soulestream on 2005-12-16
just pick one ;) 


soule

---

### Post by pelle.k on 2005-12-29
Take a look at these two:

[Gnome Menu Extended (Debian Sid Package)]("http://gnome-look.org/content/show.php?content=31035&forummode=2&forumpage=0&forumexplevel=3&PHPSESSID=f1e0098af05af95ffa7c8a1fb419f9c6")

and

[K Menu Gnome (Debian Package)]("http://www.kde-look.org/content/show.php?content=31031&forummode=2&forumpage=0&forumexplevel=3s")

Haven't tried neither of them out yet, but please go ahead and tell us if they work as supposed.. :)

That part about using the path command... i didn't get that at all. That isn't what the path command is for right?
All i know is that in my Kubuntu install, all .desktop files are in /usr/share/applications/kde, which is confusing because i was pretty sure they were supposed to be in ~/.local/share/applications ?

---

### Post by everettattebury on 2006-01-27
I'm not sure this will do exactly what you want, but maybe it will help you.

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

### Post by Daminator on 2006-01-28
[QUOTE=pelle.k]Take a look at these two:

[Gnome Menu Extended (Debian Sid Package)]("http://gnome-look.org/content/show.php?content=31035&forummode=2&forumpage=0&forumexplevel=3&PHPSESSID=f1e0098af05af95ffa7c8a1fb419f9c6")

and

[K Menu Gnome (Debian Package)]("http://www.kde-look.org/content/show.php?content=31031&forummode=2&forumpage=0&forumexplevel=3s")

Haven't tried neither of them out yet, but please go ahead and tell us if they work as supposed.. :)[/QUOTE]

Does anyone know how to use these two apps in Ubunto and Kubuntu? If they work as well as the screen shots look it'd be fantastic. My menus are really looking ugly, but I don't want to use the other proposed solution of just hiding KDE from Gnome and vise versa.

Damian

---

### Post by grafenberg on 2006-01-28
this is exactly what I've been rtying to figure out how to do; install kde into ubuntu.. unfortunately, I get dependency errors when I to a kubuntu-desktop install, both from within synaptic, and the terminal.. 

anyone know of an alternate way of doing this? I have a fresh install of ubuntu, btw. 

thanks, :-D 

g-

---

