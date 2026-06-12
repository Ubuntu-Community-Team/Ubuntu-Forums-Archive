---
title: "Some apps won't start."
date: 2005-02-17
forum: Desktop Environments
---

### Post by morpheuz on 2005-02-17
This started happening 2 days ago. Whenever I click on some applciations to launch them, such as the Terminal or Ooo, it looks like they will start, but then they suddenly die. Any ideas???

---

### Post by rufius on 2005-02-17
[QUOTE=morpheuz]This started happening 2 days ago. Whenever I click on some applciations to launch them, such as the Terminal or Ooo, it looks like they will start, but then they suddenly die. Any ideas???[/QUOTE]
 What release are you using? (Warty or Hoary)

---

### Post by morpheuz on 2005-02-17
I'm using Warty.

---

### Post by Xian on 2005-02-17
[QUOTE=morpheuz]Whenever I click on some applciations to launch them, such as the Terminal or Ooo, it looks like they will start, but then they suddenly die. Any ideas???[/QUOTE]
I guess the best place to start would be to try and determine if there is a problem with the launcher or with the actual application. Let's start with the terminal program and try to get it running via the command window.

From the taskbar goto Applications > Run Application
In the dialogue box type "gnome-terminal"
Click Run

Does the terminal open under these conditions?

---

### Post by morpheuz on 2005-02-17
Same thing happens. Terminal will not open. You see the hard drive activity that looks like it is going to do something, but nothing happens.

---

### Post by Xian on 2005-02-17
Hmmm...I'm stumped. But now I wonder if this might be just something that would apply to your user name or if it is a system-wide problem. Maybe this is just some kind of a permission issue that needs to be resolved. The easiest way to check this would be to create a new user:

Computer > System Configuration > Users and Groups

After your new user is set-up, reboot (for the heck of it) and login under that name.
Again, try to start Terminal and some of your other applications.

Any change?

---

### Post by morpheuz on 2005-02-17
This is the other thing happening. When it asks for the root password in the Add User window, as soon as I press the first key on the keyboard, the window freezes and then closes down.

---

### Post by nanaban on 2005-02-17
[QUOTE=morpheuz]This is the other thing happening. When it asks for the root password in the Add User window, as soon as I press the first key on the keyboard, the window freezes and then closes down.[/QUOTE]
 I had that before, start a gnome-term (not the root term), and do a update.

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

Also, check whether there's a file called .gksudo.lock in your home directory. Remove it if there's one.

---

### Post by Xian on 2005-02-17
If what nanaban suggested doesn't work, I would try the following:

Go to your /home folder and be sure you can view the hidden files.
If in Nautilus click View > Show Hidden Files.

Re-name each of the following folders in your /home directory.
Just append an x at the end or something (.gocnfx, .gconfdx):
.gconf
.gconfd
.gnome
.gnome2

Then delete the entire contents of you /tmp folder, including any hidden files.
Now reboot the system and see if there is any change.

Note: Re-naming those folders will mean that your personal configs will be lost and you will instead login to a default looking gnome desktop (just like after a fresh installation). If the initial problem isn't resolved then you can just rename the folders back (delete the newly created ones) and re-boot into the same settings you had previously.

---

### Post by nanaban on 2005-02-17
I just encountered the same problem (can't type in password) *again*, but my system is up-to-date. I was able to fix it by reinstalling gksu

sudo apt-get install gksu --reinstall

hope that helps.

---

### Post by gylf on 2005-02-20
I had this problem in Hoary.  When I tried to run gksu <app> from a terminal I got:
** (gksu:9230): WARNING **: Lock found: <homedir>/.gksu.lock
deleting that file fixed the problem for me.  I'm guessing the lock came from killing an app with the system monitor.

---

