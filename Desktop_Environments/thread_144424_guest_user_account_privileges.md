---
title: "guest user account privileges"
date: 2006-03-14
forum: Desktop Environments
---

### Post by m666 on 2006-03-14
I created additional user account to let my friends websurfing/emailing using my machine. 
However, I noticed the user is able to shut the system down. How to disable it?

---

### Post by taurus on 2006-03-14
Did you include that guest user in group adm?  Also, check your /etc/sudoers to make sure you haven't allowed everybody on your system to run things as root using sudo...

---

### Post by m666 on 2006-03-14
[QUOTE=taurus]Did you include that guest user in group adm?  Also, check your /etc/sudoers to make sure you haven't allowed everybody on your system to run things as root using sudo...[/QUOTE]


sudo doesn't work as the user is not on sudoers list.
I created it using:

sudo useradd -m user

so it belongs to 'users' group
 
although some functions are not included in menu (add/remove, administration tools), anybody logged on this account is able to shutdown the machine just clicking:
system,logout,shutdown.

anyway I am using dapper (installed  yesterday) so I think I am in wrong place looking for help...

---

### Post by aysiu on 2006-03-14
Every user is able to shut down the system. That's the default.

---

### Post by m666 on 2006-03-14
[QUOTE=aysiu]Every user is able to shut down the system. That's the default.[/QUOTE]
how to change it then?

---

### Post by radames on 2006-03-14
supposing you have only 2 groups : admin and users
So you may change the group only to admin at the  shut-down "executable" and that's may be a solution, that was tested by me 5 years ago on redhat 7.x [ don't remenber x =?]..... on the lynx aplication... so you may try on redhat  forums for details,  but this is the idea.
If this is not working in ubuntu, please accept ( all of you ) my apologies!

Radames

---

### Post by Gustav on 2006-03-14
you could do something like this:

sudo chmod 744 /sbin/shutdown
sudo chmod 744 /sbin/reboot

---

### Post by aysiu on 2006-03-14
Does a traditional shutdown use the actual /sbin/shutdown command?

If I'm in Gnome, using KDM, I need to use the /sbin/shutdown command to shut down, and it requires sudo privileges *and* a password.

If I'm in KDE, using KDM, I can shut down graphically, and I don't need sudo privileges.

Does the regular graphical shutdown not use the /sbin/shutdown command? If so, what command *does* it use?

---

### Post by Gustav on 2006-03-14
you can use the init command aswell so to disable that do:

sudo chmod 744 /sbin/init

---

### Post by m666 on 2006-03-14
[QUOTE=Gustav]
sudo chmod 744 /sbin/shutdown
sudo chmod 744 /sbin/reboot
sudo chmod 744 /sbin/init[/QUOTE]

don't work :(

I can't believe gnome is so unsecure...
shall I switch back to blackbox?

---

### Post by aysiu on 2006-03-14
[QUOTE=m666]don't work :(

I can't believe gnome is so unsecure...
shall I switch back to blackbox?[/QUOTE] It's not really a Gnome issue, as far as I know.

If you don't want to make it obvious how to shut down, you can make KDM your default instead of GDM. Then people will at least have to log out before shutting down (which is not an obvious way to shut down).

XFCE requires a password to shut down, but I'm not sure if that means only *sudoers* can shut down or if anyone can type in her password and shut down.

You could also try setting up KDE in Kiosk mode, so that you can get rid of the "shut down" entry from the KMenu.
[http://developer.kde.org/documentation/tutorials/kiosk/index.html](http://developer.kde.org/documentation/tutorials/kiosk/index.html)

Have you also thought about just telling people, "Please don't shut down my computer. I like to keep it on"? You did say these were friends, right? They're probably just shutting down because they think that's what they're *supposed* to do.

---

### Post by m666 on 2006-03-14
I don't want to install any KDE-package ;)
I used to run blackbox+gdm before reinstall, (in breezy), where
user had 'logout' option only in menu and he was not allowed to reboot/shutdown in gdm
Is there any way to edit gnome menu manually?

---

### Post by aysiu on 2006-03-14
Well, if you use KDM with Gnome, users will have only "log out" as an option (no "shut down").

---

### Post by m666 on 2006-03-14
[QUOTE=aysiu]Well, if you use KDM with Gnome, users will have only "log out" as an option (no "shut down").[/QUOTE]
OK ,I'll try kdm
but what if I want to remove kdm later?
I mean how to remove kdm along with all the packages it installs with?
(kdebase, kdelibs etc)

---

### Post by aysiu on 2006-03-14
[QUOTE=m666]OK ,I'll try kdm
but what if I want to remove kdm later?
I mean how to remove kdm along with all the packages it installs with?
(kdebase, kdelibs etc)[/QUOTE] Remove as in uninstall or remove as in replace with GDM? Are you tight on disk space?

Well, if you want to later remove it, just make note of what packages get installed. Type ```
sudo apt-get update
sudo apt-get install kdm
``` before saying "yes," highlight the packages to be installed and then copy them to a text file called *removekdm.txt* and save it somewhere safe. Then, if you later decide to get rid of KDM, do ```
sudo apt-get remove
``` and paste in the package list.

If you just want to change from KDM back to GDM, ```
sudo gedit /etc/X11/default-display-manager
``` and change /usr/sbin/kdm to /usr/bin/gdm.

Keep in mind, though, that if you have Gnome installed and KDM installed, you will also have *logout* as the only option in Gnome unless you use [some kind of workaround](http://www.ubuntuforums.org/showthread.php?t=142183) just for yourself or log out and then shut down from the login screen.

---

### Post by m666 on 2006-03-14
[QUOTE=aysiu]

Well, if you want to later remove it, just make note of what packages get installed. [/QUOTE]

That's exactly what I usually do while installing anything
I just thought  there should be easier way to remove it

and I don't want to face 'out of disk space' error soon :mrgreen: 


$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/hda1              3.7G   2.3G   1.3G  64% /

---

### Post by m666 on 2006-03-14
I think I found the solution:
sudo apt-get install wdm
nobody is able to shutdown within gnome and (unlike in kdm) only root can shutdown/reboot in login screen

thank you all for support!

---

### Post by m666 on 2006-03-14
unfortunately wdm doesn't allow user switching, I am back with gdm

---

### Post by aysiu on 2006-03-14
What about my earlier suggestion--the non-technical solution?

Can't you just tell your frends, "Please don't shut down my computer when you're done using it. Thanks"?

These are your friends, right, not just random people walking off the street? I suspect they probably shut down because that's what they think they *should* do. If you tell them otherwise, they should respect that, I think.

Otherwise, using KDM should discourage them enough.

---

### Post by m666 on 2006-03-14
> **aysiu]
These are your friends, right, not just random people walking off the street? [/QUOTE]
well, currently I live in big shared house, where people move in and out quite often.
thus some of the users are virtually 'random', having no previous experience with linux environment,
 so  I would be happy to secure my session in  technical way 
rather than sticking a note on monitor ''PLEASE DO NOT SHUTDOWN''  said:**
> Otherwise, using KDM should discourage them enough
thanks  but it's 'too blue' for my taste :p

---

### Post by aysiu on 2006-03-14
[QUOTE=m666]
thanks  but it's 'too blue' for my taste :p[/QUOTE] KDM doesn't have to be blue. I'm using a [Tux-Mania KDM theme](http://www.kde-look.org/content/show.php?content=22187&PHPSESSID=f6cee) that's totally black (and extremely cute). In fact, when I was using GDM, I used the same theme (Tux-Mania, but it was designed for GDM).

There's an option in the KDM config (/etc/kde3/kdm/kdmrc) to change who can shut down: ```
[Shutdown]
HaltCmd=/sbin/halt
RebootCmd=/sbin/reboot

[X-*-Core]
AllowNullPasswd=false
AllowRootLogin=true
**AllowShutdown=Root**
AutoReLogin=false
ClientLogFile=.xsession-errors-%s
Reset=/etc/kde3/kdm/Xreset
Session=/etc/kde3/kdm/Xsession
Setup=/etc/kde3/kdm/Xsetup
Startup=/etc/kde3/kdm/Xstartup

[X-:*-Core]
AllowNullPasswd=true
**AllowShutdown=All**
NoPassEnable=false
NoPassUsers=
ServerArgsLocal=-nolisten tcp
ServerCmd=/usr/X11R6/bin/X
```

---

### Post by m666 on 2006-03-14
cute indeed! 
what we all like in linux is the wide customization. 

I was big fan of KDE when I discovered linux (autumn 2004, debian 3.0 then ubuntu 4.10, both on ppc powermac)
then I fell in love with Mac OSX, yet recently I returned to linux and after testing  blackbox/fluxbox/fvwm/windowmaker 
 (on intel-based low-end PCs such as pentium 1,2,3) finally the time has come to test gnome, 
which in ubuntu -by default- is provided in nice cocoa-caramel colours I like very much :)

---

### Post by Gustav on 2006-03-15
since the commands are availible for normal users the can use the shutdown command in the terminal anyway if you don't chmod it (at least I think so). 

And I forgot one command, you can use halt aswell to shut of your computer, do this to get rid of that:

sudo chmod 744 /sbin/halt

To sum it up you need to:

sudo chmod 744 /sbin/halt
sudo chmod 744 /sbin/shutdown
sudo chmod 744 /sbin/reboot
sudo chmod 744 /sbin/init

(at least I think thats all of them)

I always thought that the /sbin directory were for root commands only could someone please enlighten me.

---

### Post by aysiu on 2006-03-15
KDM makes it very easy to disallow shutdown for non-root users.

So all you do is just create a launcher in your own account (not the guest one) for the command ```
sudo shutdown -h now
``` (be sure to have it run in terminal), and you can have Gnome and not allow guests to shut down your computer.

---

