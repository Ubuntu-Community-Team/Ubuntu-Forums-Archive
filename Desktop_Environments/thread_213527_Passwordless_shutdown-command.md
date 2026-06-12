---
title: "Passwordless shutdown-command"
date: 2006-07-11
forum: Desktop Environments
---

### Post by daller on 2006-07-11
Hi There,

Isn't there a passwordless command, to shutdown the pc?

I know about editing /etc/sudoers, but there must be another way! (kicker can:D - And AFAIK it isn't running with superuser privs!)

Any ideas?

---

### Post by jimbren on 2006-07-11
Are you running more than one flavor of Ubuntu? Like Kubuntu and Ubuntu?  Because the only time I've heard of this being an issue is if you have two or more installed and you're wanting to shutdown when you're not in a secondary desktop environment.

Does that makes sense?  It has been a while since I did this type of a set up, so I don't remember it well.

---

### Post by daller on 2006-07-11
I don't get your drift!

Is there a command?

...It's not me who should shutdown the pc, it's kcron! - Therefore I need a command!

---

### Post by glinsvad on 2006-07-11
> **daller said:**
> 
...It's not me who should shutdown the pc, it's kcron! - Therefore I need a command!

Then why not use scheduling within the shutdown command?
```

sudo shutdown -hP time

```

The time argument can have different formats. First, it can be an absolute time in the format hh:mm, in which hh is the hour (1 or 2 digits) and mm is the minute of the hour (in two digits). Second, it can be in the format +m, in which m is the number of minutes to wait. The word now is an alias for +0.

---

### Post by glinsvad on 2006-07-11
From manpages for shutdown:
> ACCESS CONTROL
shutdown can be called from init when the magic keys CTRL-ALT-DEL
are pressed, by creating an appropriate entry in /etc/inittab. This
means that everyone who has physical access to the console keyboard can
shut the system down. To prevent this, shutdown can check to see if an
authorized user is logged in on one of the virtual consoles. If shut
down is called with the -a argument (add this to the    invocation of
shutdown in /etc/inittab), it checks to see if the file /etc/shut
down.allow is present. It then compares the login names in that file
with the list of people that are logged in on a virtual console (from
/var/run/utmp). Only if one of those authorized users or root is logged
in, it will proceed. Otherwise it will write the message

shutdown: no authorized users logged in

to the (physical) system console. The format of /etc/shutdown.allow is
one user name per line. Empty lines and comment lines (prefixed by a #)
are allowed. Currently there is a limit of 32 users in this file.

Note that if /etc/shutdown.allow is not present, the -a argument is
ignored.


---

### Post by firefly2442 on 2006-07-11
"sudo shutdown -h now"


This shuts down the computer immediately from the commandline. HTH. :)

---

### Post by daller on 2006-07-12
> **firefly2442 said:**
> "sudo shutdown -h now"


This shuts down the computer immediately from the commandline. HTH. :)

That's NOT passwordless!

---

### Post by Lunar_Lamp on 2006-07-12
The only way I can think is to make the shutdown command not require a password.

---

### Post by daller on 2006-07-12
But what about the kicker shutdown button?

Can't I call the command though that?

---

### Post by Lunar_Lamp on 2006-07-12
If you find out, let me know.  I think I may be trying/thinking of doing the same thing as you!

I was trying to write a basic bash script that enabled me to click a button to shutdown as in xgl/compiz setup you lose the shutdown button and have to logout and shutdown.

---

### Post by philippe_carlo on 2006-07-12
This does not work (see next post)

You could write s small script which is owned by root and with the SUID bit set. Note that this is not really good practice and quite unsafe though.

---

### Post by philippe_carlo on 2006-07-12
Since Linux will not allow shell scripts with the SUID bit set, you have to take a detour:

1) write a small c-program like this (myreboot.c):

main() {
  system("reboot");
}

2) compile with 
gcc -o myreboot myreboot.c

3) change ownership
sudo chown root myreboot

4) change permissions (SUID)
sudo chmod 4755 myreboot

5) rune myreboot

Ta-taaa

---

### Post by daller on 2006-07-12
> **philippe_carlo said:**
> 
  system("reboot");


And what command for shutdown?

---

### Post by daller on 2006-07-12
While writing a c-program anyway, is it easy to make a c-program, that shuts down the pc at given times each day?

Monday - Friday at 18:00
Saturday at 14:00
Sunday at WHATEVER (If computer is turned on at sundays - it should turn of immediately!)

---

### Post by philippe_carlo on 2006-07-12
> **daller said:**
> While writing a c-program anyway, is it easy to make a c-program, that shuts down the pc at given times each day?

Monday - Friday at 18:00
Saturday at 14:00
Sunday at WHATEVER (If computer is turned on at sundays - it should turn of immediately!)

I'm not a C-expert, but cannot you take the program, change "reboot" into "shutdown -h now" and load it into cron?

In cron, you can run tests/programs at very flexible intervals, I think. Seems the best way to do this.

---

### Post by Lunar_Lamp on 2006-07-12
Heh, I just wrote a quick shell script activated by a custom launcher as I don't know C, so I have to type in a password.  Here it is for anyone who is new to linux (or bash scripting) and stumbles accross it:

```

#!/bin/sh
# for a nice icon use icon from /usr/share/icons/Human/48x48/apps 
echo "                Type 'y' to shutdown, or any other key to cancel"
read INPUT
if [ "$INPUT" = "y" ]; then
sudo shutdown -h now
else exit
fi

```

---

