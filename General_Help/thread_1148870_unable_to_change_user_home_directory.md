---
title: "unable to change user home directory"
date: 2009-05-04
forum: General Help
---

### Post by martinkoo on 2009-05-04
Hi, I'm just few days new with linux, but I already managed to do some radical errors.

I changed the primary user's home directory to "/root/"

-don't ask me why, I already don't remember what I was trying to achieve :). I just know, I forgot to put it back. So I turned on my computer today, Ubuntu loaded, but I could see just the desktop picture and the cursor, no panel, no nothing. (I suppose it's because it can't write into the /root/ directory.)
So I spent about eight hours trying to set the directory back where it was - no results.

I tried:    adduser --home /home/martinek/ martinek

It tells me that the directory already exists and the user also. Well thanks, I know.
Then I tried many different things as making a new user or using a different directory, login with root user etc etc...... no result. I don't even know how could I login to gnome with a different user.
My head is quite dull and mindless after the whole day of learning commands.

Anybody any suggestions please?

---

### Post by CMJ Tech on 2009-05-04
I would just start over with a clean install.

---

### Post by paradigm2 on 2009-05-04
Sure.  Don't worry we should be able to fix it.

First backup the old /etc/passwd file as root

```

sudo cp /etc/passwd /etc/passwd.backup

```

Now you need to change the entry for the main user which appears to probably be martinek, right?

```

sudo nano /etc/passwd

```

Look for the entry which starts with the name of the user.  Like:

martinek:x:BLAH BLAH WHATEEVER HERE ...

Colons (The :'s) seperate fields.  Find the part in that line which probably says '/root' and change it to /home/martinek keeping everything
else in that line and file the same.  This field tells the system where the user's hoem directory is.  Each line is for a separate user.

Save the file.  CTRL+O (note: this is the letter O, not zero) usually.

Now reboot.  IT will probably be fixed now. :)

If you have any doubts ask.  Make sure to backup the file first as mentioned above.  Make sure you have a copy of the Ubuntu CD to boot in case something goes wrong.

---

### Post by paradigm2 on 2009-05-04
> **CMJ Tech said:**
> I would just start over with a clean install.

Na. It can be fixed pretty easily provided he didn't run a lot of other weird commands.  I give it a 95% chance that doing what I said in the post above will fix it (Hopefully).

---

### Post by paradigm2 on 2009-05-04
Here is some info on how to get to rescue/recovery mode, etc to be able to enter these commands to fix it:

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

[http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/](http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/)

It is easier than it looks...

---

### Post by martinkoo on 2009-05-04
Wow! Thanks really much! :KS

Yes, I was thinking about a clean install also, but the circumstances forced me not to do it. And well, it worked. And it made me want to learn more in the command line.

Thank you again.

---

### Post by paradigm2 on 2009-05-04
> **martinkoo said:**
> Wow! Thanks really much! :KS

Yes, I was thinking about a clean install also, but the circumstances forced me not to do it. And well, it worked. And it made me want to learn more in the command line.

Thank you again.

Awesome. Glad to be of service. :)

Check out this if you want to learn a bit more about /etc/passwd:

[http://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/](http://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/)

Take care.

---

### Post by gamblor01 on 2009-05-04
Obviously, modifying the /etc/passwd file directly will work (and apparently did), but I would discourage doing that unless you really know what you are doing.  You can accomplish the same thing by using **usermod -d**.  See the man page for more details.

Also, if you screw something up to the point where you can't even login (or it hangs after you do login) you can generally pop the live CD back in and reboot.  As the live session user you can mount the hard drive and then make whatever changes you need to get it back into a bootable state.  Just something to keep in mind.  ;)

---

