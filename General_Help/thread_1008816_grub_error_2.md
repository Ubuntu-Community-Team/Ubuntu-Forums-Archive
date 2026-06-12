---
title: "grub error 2"
date: 2008-12-11
forum: General Help
---

### Post by Biophile on 2008-12-11
I have had Ubuntu on my laptop for about a month. Not long ago I turned off my computer without stopping the update which I forgot I had running (I don't know if this is related or just a coincidence). The next day Ubuntu booted up fine but when I tried to resume the update and/or install software I got an error which said I needed to run 'dpkg --configure -a' manually. I tried (as root) and it returned an error. I checked irc and was told to boot from a live cd and run fsck. At first the live cd wasn't working. I rebooted and got 'error 2' from grub and I have been ever since.

---

### Post by Herman on 2008-12-12
My suggestion is to try running e2fsck instead of just fsck.

Try running '[SIZE=-1][FONT=Bitstream Vera Sans Mono]sudo e2fsck -C0 -p -f -v /dev/sda2'from a live CD and see if that helps,
[/FONT][/SIZE]```
sudo e2fsck -C0 -p -f -v /dev/sda2
```Where: 'dev'sda2' is your Ubuntu partition containing an ext3 file system. If your Ubuntu partition has a different partition number then feel free to change the command to suit.

If this command doesn't fix your problem it will tell you what else to do. Please record any error message from this command might return as it may be useful if you will need more help.
Regards, Herman :)

---

### Post by Biophile on 2009-01-27
It returned this:
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?

P.S. I don't know which partition my install is on, I used the defaults if that helps.

P.P.S. yes, that is foolish of me.

---

### Post by Herman on 2009-01-28
Another way to do almost the same thing is to boot your Live CD and open GParted, ('System'-->'Administration'-->'Partition Editor'), and right click on your Ubuntu partition and click 'Check'.
Then click 'Apply, and in the confirmation panel, click 'Apply' once more.
Wait for a while and your file system will be fixed, or at least nearly every time it will be.
This way, it's 'graphical', so you can 'see' what you're doing, (or at least a graphical representation).

---

### Post by Biophile on 2009-01-28
Grub is working now but when I tried to boot it had several fails and then gave this message:
Server Authorization directory (daemon/ServAuthDir) is set to /var/lib/gdm but this does not exist. please correct GDM configuration and restart GDM.

Thank you for your patience and help, Herman.

---

### Post by Herman on 2009-01-29
:-k Hmmm, either the file system check has needed to remove some of your files to the /lost+found, or there are some problems due to the the update having been interupted or a little of both.
The 'gdm' is your Gnome Destop. (Graphical User Interface). Since you can't boot into your Gnome Desktop, you should try to boot into Recovery mode instead. You'll just have a command line.

If you can boot into recovery mode successfully, there is hope that you'll still be able to fix your system with the right commands.
You could try some of these commands: 'sudo apt-get update' and 'sudo apt-get upgrade', 'sudo dpkg --configure -a', and 'sudo dpkg-reconfigure gdm'.

Also worth a try are 'sudo apt-get -f install', 'sudo apt-get -f remove' (without specifying any particular package, to try to force re-installation of the half-installed package), sudo apt-get install gdm.

If it seemed like one or more of those commands may have worked, (or even if it doesn't,  try rebooting into your normal mode and see if you can. 

You could also just try another file system check too, on top of the one yopu already did, just in case that might help.

---

