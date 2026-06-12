---
title: "log in screen does not show up"
date: 2008-12-05
forum: General Help
---

### Post by DaveKlynch615 on 2008-12-05
Hi, I'm new to the forum and fairly new to Ubuntu.  I really like Ubuntu, it has really breathed new life into an older machine that I have laying around the house.

Now to my problem:  I am currently unable to get into Ubuntu.  Everything was going find until I accidentally clicked on "change user" or whatever the menu item is to perform that function.  Now, I do not have multiple users set up on that machine.  The result of doing that caused Ubuntu to just hang there with a blank screen.  

I rebooted thinking that Ubuntu would boot up like normal, but the login screen does not appears.  All that does appear is a black screen with the circular hourglass mousepointer.

When I turn on the machine, select Ubuntu in Grub, the screen with the Ubuntu logo and progress bar then appears, and then the black screen with the circular hourglass.

Any help fixing this would be greatly appreciated.  Thanks!

Dave

---

### Post by kuhlbeans on 2008-12-05
What happens if you hit ctrl+alt+delete once the screen with the hourglass comes up?  That's the command to kill X and should take you to a command prompt.  If that doesn't work try hitting alt+F2 (or another F key) to go to one of the other virtual consoles.  I would bet that your Xorg configuration got hosed.  

You can try dpkg-reconfigure xserver-xorg at the prompt (once you are logged in) as the easy solution.

If that doesn't fix things go to /etc/X11 directory and remember all the following commands must be done with sudo. There should be a file here called xorg.conf, which is the X configuration file. You may have some backups in the directory of the form xorg.conf.#. You can try replacing your existing xorg.conf with these one by one to see if any of them work (using the mv or cp commands). To see if it works just type startx at a command line to fire up X, when it starts it will read whatever is in xorg.conf. If you find one that works, great!, make a backup of it in your home directory so if this ever happens again you can easily cp it from home into /etc/X11. If one doesn't work you'll have to create/edit one by hand. There are plenty of resources on the web to help, just ask Google. Arch Linux has a very good resource on X here: [http://wiki.archlinux.org/index.php/Xorg](http://wiki.archlinux.org/index.php/Xorg)

---

### Post by jerrykenny on 2008-12-05
Was it a painfull reboot ?   ie switching the machine off at the wall ?

If yes, then the system will be checking and repairing your filesystems, . . . just leave it ~10 mins

If not, can you reboot into single-user mode ?  and login . . . from there you'll get some info asto whats the specific problem with the machine . . . 

You can shut it down with either "halt" or "sudo halt" commands.

Incidentally, to do a "soft" shutdown on any linux with a hung screen, press

<ctrl> <alt> <f1> simaultaneously, then login at the prompt as yourself (again) and type sudo halt

---

