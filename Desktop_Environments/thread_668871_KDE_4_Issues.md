---
title: "KDE 4 Issues"
date: 2008-01-15
forum: Desktop Environments
---

### Post by Redscare on 2008-01-15
I've just recently installed KDE 4 from the launchpad repositories, and it's great except for a few errors. 

The first and worst error is that when I try to run a KDE 4 application with root privleges I get an error. First I tried it through the terminal with the command "sudo [kde 4 program]". This is the output I got:
```
redscare@redscare-desktop:~$ sudo systemsettings-kde4
[sudo] password for redscare:
QMutex::lock: Deadlock detected in thread -1236805952
```
And no window appeared. The next error came when i tried to use kdesu. This time I also ran from the terminal and got only the window that asks for the password; after that there was no more output except for:
```
redscare@redscare-desktop:~$ kdesu systemsettings-kde4
kbuildsycoca running...
kio (KService*): WARNING: Invalid Service : media_decrypt.desktop
Invalid entry (missing '=') at /home/redscare/.kde4/tmp-redscare-desktop/kconf_updateJBhM2a.tmp:1
kdecore (KProcess): WARNING: _attachPty() 15
QInputContext: no input method context available
QInputContext: no input method context available
passprompt


QMutex::lock: Deadlock detected in thread -1236830528
```
Please help with this. 

The other issue I ran into was that when i activated screen-lock, i get this error message:
```
Will not lock session, as unlocking would be impossible:
No appropriate greeter plugin configured.
```. It may be worth mentioning that i do not have any screensavers on my KDE 4 apart from blank screen and random.

Thank you in advance.

---

### Post by Redscare on 2008-01-16
Is there really no solution?

---

### Post by rune0077 on 2008-01-16
For the password issue, you need to have an actual root-user password. I had the same issue, but in Gnome I had created a user account. While KDE4 refused to accept my ordinary password, feeding it the root-account password did the trick for me.

---

### Post by Redscare on 2008-01-16
It's not an issue of accepting the password. I get the password right but whenever i run a kde 4 program under root, although the password is accepted, there is some exception in the code.

---

### Post by Redscare on 2008-01-18
It seems to me that these are basic problems with the system? But if there truly isn't a solution could someone say so?

---

### Post by mac71 on 2008-01-19
I had similar problems, i found it so annoying that i removed all kde4 stuff.
I then tried:
```
sudo aptitude update
sudo aptitude install kde4
```

Everything installed effortlessly and running (almost) as smoothly as 3.5.

---

### Post by z0mbie on 2008-01-19
KDE4 packages are constantly being updated. So a lot of the issues might be fixed already.

---

### Post by dirac3000 on 2008-01-19
Following this:
[http://tombuntu.com/index.php/2008/01/17/start-applications-that-need-root-privileges-in-kde-40/]("http://tombuntu.com/index.php/2008/01/17/start-applications-that-need-root-privileges-in-kde-40/")
It should work as it did on kde3. 
Here a small abstract:
[LIST=1]
[*]nano ~/.kde4/share/config/kdesurc
[*]Paste the following: 
```
[super-user-command]
super-user-command=sudo
```[/LIST]

---

### Post by zaiyon on 2008-01-19
@All:
No one is reading the first post, aye?

It's not the root-password-instead-of-user-password-issue

It's a problem that occurs when running systemsettings with sudo.
I have the same problem, which makes it impossible to configure kdm-kde4.

@Redscare:
I had the same issue. Installing kscreensaver-xsavers-kde4 did the trick for me.

---

### Post by maestrobwh1 on 2008-01-21
Grrr grumble grumble.  Still no root access for systemsettings for me. The only reason I need it right now is that my clock keeps changing to odd times:-(  I don't understand why that has to be a root function anyway.

I am still having MAJOR issues with root IN SYSTEMSETTINGS ONLY.  All other commands sudo, kdesu and kdesudo fine.

I also created the kdesurc file.  Nada. It isn't a sudo issue.

kscreensaver-xsavers-kde4 was already installed so I purged it and the package kde4 went with it, I reinstalled it and I still have the issue.

I installed from the kde4 live cd.  I don't have a fallback window manager so unless I an willing to do everything from terminal, I am kind of stuck.

I get the "Deadlock detected" message when trying to run from terminal.  Whatever happened to the "administrator mode" button as in kde3?

I don't even know what that "Deadlock detected" is.  

I have to log out, dump myself to terminal, log in as root, kill x, startx, then work that way.  It is really annoying:-)

Is it that the package is flawed or do I have a configuration file issue?

---

### Post by markoloka on 2008-01-22
Logout & Lock screen are bugs aka not gonna work, yet. 
KDE4 runs nicely but after more bugs are fixed i'm gonna start to use it.

---

### Post by zaiyon on 2008-01-22
[quote=maestrobwh1]
 I am still having MAJOR issues with root IN SYSTEMSETTINGS ONLY. All other commands sudo, kdesu and kdesudo fine.
[/quote]

Really? It works for konsole-kde4 for you? I have the Deadlock issue with konsole and all other kde4 programs I tried as well. Smells like some lib-thingy to me.
 
[quote=maestrobwh1] 
 I don't even know what that "Deadlock detected" is. 
[/quote]

In case you're interested, it basically means that two parts of the program try to access the same resource (could be a file, whatever) at the same time, and wait for each other respectively forever. This isn't your fault, it is a message not intended for a user to see.

[quote=maestrobwh1]
 Is it that the package is flawed or do I have a configuration file issue?
[/quote]

I guess it's the package, but let's wait until we get better guesses by people involved :)

---

### Post by jimbo99 on 2008-01-22
KDE internally may be updated regularly but the updates are far and few in between.

I've not seen a single KDE4 update since it's initial public offering, period.

Also, KDE4 is so tremendously buggy it's amazing that everyone isn't screaming bloody murder at them.

One simple example is that often the desktop picture gets picked up and moved to the side without any option for putting the desktop picture back.

I had a problem getting update-manager to run.  In fact, it locked up.

I have watched the desktop freeze, I've seen the desktop icon overlay icons displayed on 8 icons at once. I can't for the life of me get a neatly aligned desktop. It's just pathetic.

This is NOT a product for the masses and it is not even a product for the developers.  They need to pull the damn thing and start over from scratch, IMHO.

---

### Post by zekica on 2008-01-22
KDE4.0 has been amazingly stable for me (no crashes etc...), but it does have bugs like not loading desktop wallpaper at login. I wouldn't recommend KDE4.0 for day-to-day work yet, but I don't think KDE4 is something that needs to be rewritten from scratch. It is just that KDE4.0 should be called RC or beta, not a final release, because it has some obvious bugs that need to be sorted out.

KDE4 has potential, and it is only a matter of time before it becomes visible to the end-user, I think I will wait until 4.1 and then see what has been done.

---

### Post by maestrobwh1 on 2008-01-22
zaiyon :  Well, yes and no.  I can't run kdesudo kwrite-kde4 as I get the deadlock thing, but I can run the file manager in root mode (by selecting from the menu) and open things which require root privileges from there using kwrite-kde4 and I find this odd. 

**Edit** I use krusader and when installed, it gives a start menu item for root mode.  Launch it, and then navigate to /usr/bin and type systemsettings-kde4.  Poof.  Root mode for systemsettings-kde4

 I can also sudo and kdesu any kde app that does not have the -kde4 extension.  I can kdesu kedit and I can open that.  I just installed a few old familiars from kde3 as a workaround from there.  Krusader has been a BIG help.

It is annoying, not debilitating.  Depends on my mood.  

I actually purged systemsettings-kde4,kdesudo, kde4-core and kde4 and reinstalled via the terminal, at the suggestion of a few @ kubuntu forums.  They have an updated kde4 from a kde3 gutsy/hardy.  Is this issue jsut occurring with live cd installers? 

Anyway, the purge/reinstall didn't work, as I suspected it might not.  I still have the same issue.

---

### Post by maestrobwh1 on 2008-01-22
> **zekica said:**
> KDE4.0 has been amazingly stable for me (no crashes etc...), but it does have bugs like not loading desktop wallpaper at login. I wouldn't recommend KDE4.0 for day-to-day work yet, but I don't think KDE4 is something that needs to be rewritten from scratch. It is just that KDE4.0 should be called RC or beta, not a final release, because it has some obvious bugs that need to be sorted out.

KDE4 has potential, and it is only a matter of time before it becomes visible to the end-user, I think I will wait until 4.1 and then see what has been done.

Yes, it is very stable.  I do agree here.  I am running virtualbox on it with XP, and it seems to handle that kind of thing with aplomb.

It looks really professional too.  MacOS watch out.

---

### Post by maestrobwh1 on 2008-01-22
> **jimbo99 said:**
> KDE internally may be updated regularly but the updates are far and few in between.

I've not seen a single KDE4 update since it's initial public offering, period.

Also, KDE4 is so tremendously buggy it's amazing that everyone isn't screaming bloody murder at them.

One simple example is that often the desktop picture gets picked up and moved to the side without any option for putting the desktop picture back.

I had a problem getting update-manager to run.  In fact, it locked up.

I have watched the desktop freeze, I've seen the desktop icon overlay icons displayed on 8 icons at once. I can't for the life of me get a neatly aligned desktop. It's just pathetic.

This is NOT a product for the masses and it is not even a product for the developers.  They need to pull the damn thing and start over from scratch, IMHO.

It is also too easy to accidentally remove a panel item, only to find you can't put it back to the same location where it was.

I don't put anything on the desktop.  I might say that is the one thing I do not like, the whole widget on the desktop doesn't seem to be pleasing to my eye, other than perhaps the clock.

And I am surprised that when I do an upgrade, it does not seem to be to any of the kde4 components.

---

### Post by maestrobwh1 on 2008-01-22
Temporary resolution:  I can launch systemsettings-kde4 as root if I do it from a file manager as root.

In krusader, in root mode (it installs a menu icon for this), navigate to /usr/bin and in the area a the bottom where you can issue commands type systemsettings-kde.

Poof, there it is.  No deadlock issue.

---

### Post by cleary on 2008-01-22
I have the same issue on a debian sid/kde4 from experimental, so it's not limited solely to *buntu

---

### Post by zaiyon on 2008-01-25
> **maestrobwh1 said:**
> Temporary resolution:  I can launch systemsettings-kde4 as root if I do it from a file manager as root.

In krusader, in root mode (it installs a menu icon for this), navigate to /usr/bin and in the area a the bottom where you can issue commands type systemsettings-kde.

Poof, there it is.  No deadlock issue.

Wicked, this works. Thanks a lot!

No idea why though, konqueror (3) e.g. doesn't do the trick...

---

### Post by changhua on 2008-03-14
Another work-around, without using Krusader.

In Kickoff, select Applications -> System -> More Applications -> File Manager - Super User Mode

This will launch Konqueror in root mode.

Immediately right-click anywhere in the folder whitespace (IE in the window but not on an icon), select Actions -> Open Terminal Here

You will then have a konsole in root... --without sudo involved.  Type "systemsettings" (without quotes), press Enter, and you've got it.

---

### Post by umecn2005 on 2008-04-27
In response to one of the original questions (about being unable to lock the screen in kde 4.0 ubuntu, installing KDM KDe 4.0 worked like a charm for me.

sudo apt-get install kdm-kde4

or running the Synaptic Package Manager and selecting the "kdm-kde4" package.
I found this solution here 

[http://www.nabble.com/Re:-KDE-4-unable-to-lock-screen-or-switch-user-How-to-Fix-td15355769.html](http://www.nabble.com/Re:-KDE-4-unable-to-lock-screen-or-switch-user-How-to-Fix-td15355769.html)

---

