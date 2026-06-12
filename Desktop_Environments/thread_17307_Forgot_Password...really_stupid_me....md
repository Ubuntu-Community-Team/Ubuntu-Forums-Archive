---
title: "Forgot Password...really stupid me..."
date: 2005-02-27
forum: Desktop Environments
---

### Post by flamedog on 2005-02-27
OK...so I feel like a complete idiot.  I have never used any linux before (only near experience was running System 5 Rel 4 v.3 back in the early 90's)...let alone a nice GUI version.

So I downloaded and installed ubuntu without any problems a couple weeks ago.  So I fire up the laptop to start playing with it today and the desktop comes up and prompts for Username: and Password: and I'm completely stumped...I've tried everything I can possibly think of.

In the lower right hand corner by the time and date display it does have a "UserName //" where username is what I believe actually was the username I created during installation.  It does contain one uppercase letter too, if that matters??

Anyway, how do I get back into the laptop?  I don't care if it is this user account or just a brand new one.

When I make any of the choices under Session it just returns me to the Username: login prompt.

Sorry for such a stupid question...but hopefully someone will help.

Remember I know nothing about grub (whatever that is--I've seen it mentioned in the messages that came up during my searches in these forums) or how to access a command line during startup or anything...so please be specific.  Thank-you, thank-you, thank-you.

---

### Post by cwaldbieser on 2005-02-28
There are some standard things to try-- I've never done this with Ubuntu (yet!), but for some other distros, when you boot up at the Grub menu choose single user mode (or type "single" at the boot prompt).  This normally boots you into a kind of emergency mode where you are the root user.  You can then just execute
```
# passwd username
```
to reset your password.  

If your boot loader is password protected, you can try booting off the CD ROM usin a Live CD (like the Ubuntu Live CD or Knoppix).  Once you are booted up under the live CD, you should mount your Linux partition.  For example:

```
# mount /dev/hda1  /media/hda1
```

Once mounted, chroot and run passwd to reset your password:

```
# chroot /media/hda1 passwd username
```

Now you can shut down the live CD and boot back into your system normally.

This should also work with emergency Linux boot floppys like tomsrtbt or blueflops.

Hope this helps!

---

### Post by flamedog on 2005-02-28
OK...so during the boot process I was able to hit ESC and get to a root@machine # prompt.  I typed passwd <username> and it said no such user <username> or some such.  So I thought then did passwd root, it prompted for old [enter], new [I made a simple password]...type it again...[did it]...it responds user root password successfully changed...or something to that effect.

I reboot...it goes all the way through to the ubuntu GUI login I try username "root" with the new password and it gets denied.

Any more newbie newbie newbie tips.

When I was at that # prompt it did not appear to let me change directories and some items in the response to # ls were in different colors??  files vs directories ??  accessible vs denied ??  I don't know.

Help please.  How do I just make a new user without going through the whole installation all over again?

---

### Post by MaX on 2005-02-28
[QUOTE=flamedog]
Help please.  How do I just make a new user without going through the whole installation all over again?[/QUOTE]

Do #>ls /home/

that should tell you the username that you made during the installation.

now do: #>passwd username

Like I told my dad, Use a password you'll never forgett.

---

### Post by flamedog on 2005-03-14
Thank you...

It worked great.  Upon reboot to recovery mode...it prompted for root password.  I put in the simple one I had created.  Then did the 

#>ls /home/

which gave me the username...then did the

#passwd username

and reset the password.  Thanks again!

---

