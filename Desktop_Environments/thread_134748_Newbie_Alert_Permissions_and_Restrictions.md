---
title: "*Newbie Alert* Permissions and Restrictions"
date: 2006-02-22
forum: Desktop Environments
---

### Post by Robo116 on 2006-02-22
I am a very new Linux and Ubuntu user, but still somewhat computer literate.  I have my own dedicated server that I want to get it set up for gaming.  I am trying to transfer various files and folders to the linux server via tightVNC.  My network computers show up fine but sometimes when I goto copy and paste it says I do not have permission to do so.  Also when I access various foldes within ubuntu it also locks them because I don't have permission.
     My main user has all the permissions check so that I can use them but its under the "home" catagory.  How can I just create one single user to access anything and allow me to do everything with no restricitions?

---

### Post by The Headhunter on 2006-02-22
The main user that has all the permissions is known as the root account.  It is disabled in ubuntu for security reasons.  It is instead replaced by something known as "sudo".  How sudo works is this: the first account created in ubuntu would have the admin permissions BUT, you can't get all the permissions immediately by just logging in.  When you do things that require admin permissions, it'll ask you for the password to the first account (the one that sudo is associated with).  With installation, you can do this through the GUI but copying and pasting files into locations other than your home account involves usage of the terminal window (Applications->Accessories->Terminal).   You have to type in "sudo mv [file you want to move] [directory where it should go]".  There are other ways of doing this.  There is the option of enabling the root account although that is not recommended.

---

### Post by Robo116 on 2006-02-22
Great thanks for the super fast response!  Ok now once I understand how Ubuntu   You mentioned that enabling the root account isn't recommended...Is it just because of security issues (because this is just my home server and Im not too worried about that).  Just out of curiosity  how could I enable the root account so I can install all my progs. then just disable it when Im done?

Thanks

---

### Post by polpak on 2006-02-22
Just use sudo 

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by stevea1210 on 2006-02-22
> When you do things that require admin permissions, it'll ask you for the password to the first account (the one that sudo is associated with).

Not to sound picky, but it actually is asking for the password of the logged in user.  If you authenticate properly, it then checks to ensure that account is in the sudoers file.  

EX.
userA was created during install, and by default has sudo permissions.
userB is a user created after initial install, and isn't in sudoers (by default)

If userB is logged onto the pc, and enters sudo <any command>, when the password prompt comes up, and they enter userA's password, it'll tell them wrong password.

If userB enters their own password at that prompt, it'll reply that <paraphrase>userB isn't in sudoers and this will be reported. </paraphrase>

I'm not trying to offend, just correcting an oversight.:)

---

### Post by jchau on 2006-02-22
to enable the root account:
```
sudo passwd root
``` to set the root passwd

to disable the root account:
```
sudo passwd -l root
```

to just get a bash shell with root privs:
```
sudo bash
```

to become root without setting the root password:
```
sudo su
```

to become another user (named *user*) w/o root passwd & w/o normal login:
```
sudo su *user*
```

to run a program (lets say it is named *prog*)as root:
```
sudo *prog*
```

to end sudo session (require passwd again for next sudo):
```
sudo -k
``` or ```
sudo -K
```
(note: they are almost the same)

---

### Post by Morbett on 2006-02-22
What command do I use to unlock a locked file?

---

### Post by jchau on 2006-02-22
Do really mean lock or do you mean files that you do not have permissions to edit?

For permissions, see chmod:
```
man chmod
```

For locked files, see lockfile-progs:
```
man lockfile-progs
```

---

### Post by ancient_ee on 2006-02-23
[QUOTE=Robo116] How can I just create one single user to access anything and allow me to do everything with no restricitions?[/QUOTE]

Same question/problem: I have been trying to insall GEDA from CDROM. (I tried installing the deb package from synaptic, but got the same _geda:2519): Gtk-WARNING **: horizontal scrolling not implemented_ error that others have gotten. Maybe installing from CDROM will sidestep this problem,) I start the terminal, then do sudo -i, then I try opening the install .exe file on the CDROM. I get the following error: _(nautilus:7867): Eel-WARNING **: Error starting command ''/media/cdrom0/installer.exe'': Failed to execute child process "/media/cdrom0/installer.exe" (Permission denied)_:cry: . It appears that the root terminal access does not extend far enough into the system to allow this "child process" to proceed. I am tempted at this point to create a root login and go from there, but is there a more elegant (more Ubuntu-like) way to do this?

---

### Post by The Headhunter on 2006-02-23
[QUOTE=stevea1210]Not to sound picky, but it actually is asking for the password of the logged in user.  If you authenticate properly, it then checks to ensure that account is in the sudoers file.  

EX.
userA was created during install, and by default has sudo permissions.
userB is a user created after initial install, and isn't in sudoers (by default)

If userB is logged onto the pc, and enters sudo <any command>, when the password prompt comes up, and they enter userA's password, it'll tell them wrong password.

If userB enters their own password at that prompt, it'll reply that <paraphrase>userB isn't in sudoers and this will be reported. </paraphrase>

I'm not trying to offend, just correcting an oversight.:)[/QUOTE]

That's actually what I meant but I just didn't know how to phrase it correctly while making it clear that even though you're logged into your account, you still have to type your password.

---

### Post by ancient_ee on 2006-02-23
I understand your response, but should not I be prompted for the password if the installation process runs into a file/directory permissions problem? Instead, the intallation just quits/fails.

Just to have "tried everything" In terminal, I did: gksudo nautilus. Nautilus started, but I also got the terminal error: 
[U](nautilus:11425): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
[/U] Then, when I (as in "damn the torpedoes, full speed ahead!) tried to open the install.exe file on the CDROM, I got the similar terminal message: _(nautilus:11425): Eel-WARNING **: Error starting command ''/media/cdrom0/installer.exe'': Failed to execute child process "/media/cdrom0/installer.exe" (Permission denied)_.

I installed this OS, and I am the only user. There has got to be a better way.

---

### Post by jchau on 2006-02-23
[QUOTE=ancient_ee]Same question/problem: I have been trying to insall GEDA from CDROM. (I tried installing the deb package from synaptic, but got the same _geda:2519): Gtk-WARNING **: horizontal scrolling not implemented_ error that others have gotten. Maybe installing from CDROM will sidestep this problem,) I start the terminal, then do sudo -i, then I try opening the install .exe file on the CDROM. I get the following error: _(nautilus:7867): Eel-WARNING **: Error starting command ''/media/cdrom0/installer.exe'': Failed to execute child process "/media/cdrom0/installer.exe" (Permission denied)_:cry: . It appears that the root terminal access does not extend far enough into the system to allow this "child process" to proceed. I am tempted at this point to create a root login and go from there, but is there a more elegant (more Ubuntu-like) way to do this?[/QUOTE]
.exe files are windows executables, not linux executables.  You should not try to run them alone in linux and you should not try to make them executable (except if ur running wine or something like it).

---

### Post by jchau on 2006-02-23
[QUOTE=ancient_ee]I understand your response, but should not I be prompted for the password if the installation process runs into a file/directory permissions problem? Instead, the intallation just quits/fails.

Just to have "tried everything" In terminal, I did: gksudo nautilus. Nautilus started, but I also got the terminal error: 
[U](nautilus:11425): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
[/U] Then, when I (as in "damn the torpedoes, full speed ahead!) tried to open the install.exe file on the CDROM, I got the similar terminal message: _(nautilus:11425): Eel-WARNING **: Error starting command ''/media/cdrom0/installer.exe'': Failed to execute child process "/media/cdrom0/installer.exe" (Permission denied)_.

I installed this OS, and I am the only user. There has got to be a better way.[/QUOTE]


It should not automatically ask for a sudo password.  This way, it forces the user to realize that he or she is doing something that only root or another admin should do.  (Doing something wrong under root may have great consequences. For example, if you made the .exe (windows executable) executable & ran it with root privs, the program may just execute some arbritrary code and mess up your system.  )

---

### Post by Madpilot on 2006-02-23
Why are you messing with a Windows exe anyway? It won't run in Linux without using wine or Cedega...

---

### Post by ancient_ee on 2006-02-24
[QUOTE=Madpilot]Why are you messing with a Windows exe anyway? It won't run in Linux without using wine or Cedega...[/QUOTE]
Being a newbie (I am a harware engineer - only dabbled in (windows) software), I trusted the CDROM .iso image that I downloaded from [http://www.geda.seul.org/download.html](http://www.geda.seul.org/download.html) would only contain (even marginally) appropriate files. Then, when I file browse to the CD, I saw this .exe file with a gnome icon pasted over it. Sooo - golly gee - fooled me! In any case, I see there is also an install file written in python, which does seem appropriate. So I am running this over and over, plodding thru the error messages one by one. I really wish the .deb package worked on ubuntu, but it does not. The latest (terminal) error message is: [U](gedit:12393): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/U]
and _(gnome-terminal:13268 ) : GnomeUI-WARNING **: While connecting to session manager:Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed._. If anyone can shed a little light on this vexing error, I would REALLY appreciate it.

---

### Post by ancient_ee on 2006-02-26
Thanks for your help, all, but I finally threw up my hands in frustration at fixing the fauly GEDA (electronic design software) installation on Ubuntu. Reasoning that it should :rolleyes: work, I blew away Ubuntu and installed straight Debian. It was a struggle as X did not detect my mouse until I edited the config file, but then it was as simple as "apt-get install", and GEDA is now working on my system.

Apparently some tweak the Ubuntu team does to Debian does a number on GEDA. And that particular software package was my major motivation for learning linux.

---

