---
title: "Huge Permissions Mistake"
date: 2006-08-21
forum: Desktop Environments
---

### Post by spvo on 2006-08-21
Okay, I messed up big time, and now I am not even able to log into my machine.  I had copied a bunch of text and picture files over from a fat32 partition into my home directory.  Well when copy from fat, it sets the permissions of all the files to 777.  And since I didn't want it to throw up prompts every time I double clicked on the text/jpg files, I decided to change all the attributes to 644.  So, I went to ~/ (where I copied all the files) and typed in 'chmod -Rv /.' not even thinking that it would change all the attribues of my hidden files as well.  Anyway, the system didn't like that at all, and after a reboot I wasn't able to even log into my directory anymore.  I looked at an old backup I had done, and tried to manually change all the attributes back to the way the were originally.  Yet it still crashes when I try to log in.  The error I'm getting as I try to log in is:

unable to create ~/.gnome2 directory: permission denied
could not create per-user gnome configuration directory '/home/john/.gnome2/' permission denied

I had already changed all the permissions in the ~/.gnome2 directory back to the way the backup was.  Well, all except a couple that were now new, I took the best guesses I could on those.  After that didn't work I even moved the directory all together in the hopes that gnome would recreate it.

Why would gnome be unable to write to the home directory?  I have my user folder /home/john set up as drw-r-r.  Can anyone suggest something I can do to get back into the computer.  I'm almost at the point of just creating a new home folder from scratch.  Would I be able to do that simply by moving /home/john to something like /home/bak and creating a new empty /home/john folder?

I would really apprectiate any help you all can give me.  Thanks.

---

### Post by xtknight on 2006-08-21
Go to a virtual terminal and type these commands:

sudo chown john:john /home/john
sudo chown -R john:john /home/john/.gnome2
chmod 755 /home/john
chmod 700 /home/john/.gnome2

Can you login now?

---

### Post by nalmeth on 2006-08-21
CNTL-ALT-F2 to get to virtual terminal. CNTL-ALT-F7 to get back.

Or, when GRUB is loading at boot, hit ESC, and go into recovery mode

---

### Post by spvo on 2006-08-21
Xtnight, I tried those commands and still received the exact same error.  Also I tried just creating an empty /home/john folder with the same pemissions, and I still received the same error.  In the case of an emty folder shouldn't gnome have recreated everything it needed to load?

---

### Post by xtknight on 2006-08-21
Do you have any free space on / (or /home if you made a separate partition)?  Check with **df -h**  If so, how much free space?  If not, that's a problem.

Restore your normal john directory into /home and then try these commands:

sudo chown root:root /home
sudo chmod 755 /home
sudo chown -hR john:john /home/john
sudo chmod 755 /home/john
sudo chmod -R 700 /home/john/.gnome2

If that doesn't work, I have no idea what's going on.

---

### Post by spvo on 2006-08-21
Well, that worked, I'm able to log in again.  Only now it shows every single file in my home directory as being of an unknown file type.  I just booted into windows, and all my files are still good.  But I think I'm going to do some backing up before I mess with it any more :P

Thanks for your help xtknight.  Nalmeth, that virtual terminal is a pretty cool trick, I had never heard of that before.  Only once you are in the virtual shell, how to you exit back out of it to the gui login screen again?

---

### Post by xtknight on 2006-08-21
OK, glad to hear that worked.  I thought I was going insane.

To fix the rest of your directory I guess you can just chmod 755 the whole thing.

sudo chmod -R 755 /home/john

Set these folders back to these permissions though:

sudo chmod -R 700 /home/john/.gnome2
sudo chmod -R 700 /home/john/.gnome2_private
sudo chmod -R 700 /home/john/.gnome_private

That'll probably do it.

> **spvo said:**
> Thanks for your help xtknight.  Nalmeth, that virtual terminal is a pretty cool trick, I had never heard of that before.  Only once you are in the virtual shell, how to you exit back out of it to the gui login screen again?

You mean get back to your desktop?  Ctrl+Alt+F7 (possibly F8~F12) should bring you back.  If gdm (gnome display manager) died, then:

sudo /etc/init.d/gdm restart

Should take you to the login (I think?)  It may just bring up GNOME for the current user (sudo killall gdm && sudo gdm does that for me).  I'm not sure, but your gdm shouldn't be dying anyway just by going to a virtual terminal.  Switching between Ctrl+Alt+F2 and F7 should be seamless.

Oh, and we do type sudo a lot here but don't get in that habit unless you need root (in this case we do).  :p

---

### Post by peabody on 2006-08-21
I can't help you with your current problem, but for future reference:

```

find ~/ -perm 777 -type f -exec chmod 644 {} \;

```

The above shell code finds all files that are permission mode 777 (skips directories, replace "f" with "d" in the above line to change directory permissions) and runs chmod 644 on them.

HTH.

---

