---
title: "How to shutdown using fluxbox menu?"
date: 2007-12-09
forum: Desktop Environments
---

### Post by rado3105 on 2007-12-09
I set up /etc/sudoers file using nano to give root privilegs to shutdown to other users
It looks like this: 

# Cmnd alias specification
Cmnd_Alias      SHUTDOWN = /sbin/shutdown
root    ALL=(ALL) ALL

%admin ALL=(ALL) ALL
r-c ALL = NOPASSWD: SHUTDOWN

I used the command: sudo visudo -f /etc/sudoers
and then save using shortcuts: CTRL+O

I put this line in fluxboxmenu config file:
 [exec] (shutdown) {shutdown -p now}

and it doesn´t work, could you help what is wrong????

---

### Post by staticvoid on 2007-12-09
> sudo apt-get install obmenu
 launch it from a terminal and put
>  gksu sutdown now
 for your command to shutdown, or > 
sudo shutdown now

i furget which one... then "reconfigure" your menu

---

### Post by mali2297 on 2007-12-09
> **rado3105 said:**
> 
I put this line in fluxboxmenu config file:
 [exec] (shutdown) {shutdown -p now}

and it doesn´t work, could you help what is wrong????

Try with the line
```

[exec] (shutdown) {**sudo** shutdown **-P** now}

```

The edit of the sudoers file will permit shutdown to run without password, but you still have to add sudo. Also, the flag -p is invalid, it should be -P.

---

### Post by rado3105 on 2007-12-12
It is not possible to install obmenu, package cannot be find(using terminal)

second answer: shutdown P, doesn't work

---

### Post by mali2297 on 2007-12-12
Try what works from the terminal, perhaps
```

sudo shutdown -h now

```

---

### Post by cknight on 2007-12-12
> **rado3105 said:**
> It is not possible to install obmenu, package cannot be find(using terminal)

second answer: shutdown P, doesn't work

This works for me:
```
[exec] (Shutdown) {sudo shutdown -P 0} 
```

Just to clarify, its -P not just P.  And if it doesn't work from the command line, it won't work from the menu.

---

### Post by ghc0000 on 2008-01-19
My problem is so similar with this one I decided not to open a new thread but to continue with this one.

So, I am using Fluxbox and wish to enable shutdown for all users. I have added myself and other users to %users group, and edited /etc/sudoers (with sudo visudo command). /etc/sudoers looks like this:

```

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Poweroff and reboot for all users
%users  ALL= NOPASSWD: /sbin/shutdown
%users  ALL= NOPASSWD: /sbin/reboot
```

When I try to run shutdown or reboot from command line, it works as expected. Then I added following lines to ~./fluxbox/menu :
```

        [exec] (Reboot) {sudo reboot}
        [exec] (Shutdown) {sudo shutdown}
```

Now, reboot works fine, but shutdown does not do anything. Let's say I try first to poweroff the system and then reboot the system: after reboot I can see the following from the /var/log/auth.log :
```

Jan 19 18:29:40 ghc sudo:      ghc : TTY=unknown ; PWD=/home/ghc ; USER=root ; COMMAND=/sbin/shutdown
Jan 19 18:29:56 ghc sudo:      ghc : TTY=unknown ; PWD=/home/ghc ; USER=root ; COMMAND=/sbin/reboot
Jan 19 18:29:56 ghc gdm[5639]: pam_unix(gdm:session): session closed for user ghc
```

So as far as I can understand, the sudoers works correctly. But for some weird reason, the shutdown just will not happen. I've been battling with this for some weeks already but without any success - any ideas?

---

### Post by mali2297 on 2008-01-19
> **ghc0000 said:**
> My problem is so similar with this one I decided not to open a new thread but to continue with this one.

So, I am using Fluxbox and wish to enable shutdown for all users. I have added myself and other users to %users group, and edited /etc/sudoers (with sudo visudo command). /etc/sudoers looks like this:

```

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Poweroff and reboot for all users
%users  ALL= NOPASSWD: /sbin/shutdown
%users  ALL= NOPASSWD: /sbin/reboot
```

When I try to run shutdown or reboot from command line, it works as expected. Then I added following lines to ~./fluxbox/menu :
```

        [exec] (Reboot) {sudo reboot}
        [exec] (Shutdown) {sudo shutdown}
```

Now, reboot works fine, but shutdown does not do anything. Let's say I try first to poweroff the system and then reboot the system: after reboot I can see the following from the /var/log/auth.log :
```

Jan 19 18:29:40 ghc sudo:      ghc : TTY=unknown ; PWD=/home/ghc ; USER=root ; COMMAND=/sbin/shutdown
Jan 19 18:29:56 ghc sudo:      ghc : TTY=unknown ; PWD=/home/ghc ; USER=root ; COMMAND=/sbin/reboot
Jan 19 18:29:56 ghc gdm[5639]: pam_unix(gdm:session): session closed for user ghc
```

So as far as I can understand, the sudoers works correctly. But for some weird reason, the shutdown just will not happen. I've been battling with this for some weeks already but without any success - any ideas?

You need to specify a time. For example:
```

sudo shutdown now

```
If you want to turn the computer off, add **-P**. That is:
```

sudo shutdown -P now

```
Alternatively, use **sudo poweroff**.

---

### Post by ghc0000 on 2008-01-19
> **mali2297 said:**
> You need to specify a time. For example:
```

sudo shutdown now

```
If you want to turn the computer off, add **-P**. That is:
```

sudo shutdown -P now

```
Alternatively, use **sudo poweroff**.

Thank you for your prompt reply. I actually managed to make it work by using **sudo shutdown -P now**. With the previous Ubuntu versions I have used the **sudo poweroff** command without problems but this time it behaved just like shutdown (worked fine from command line, did not work from the Fluxbox menu). 

But this shows me a new problem. Omitting the -P parameter and using **sudo shutdown now** sent my pc into a rather unexpected state: The X server and some other processes were stopped. PC did not turn off but instead it gave me a tty with root privileges (there was no login prompt, it went directly to **root@localhost:** and it seemed to be identical state if PC was started to single user mode). Now, this is not that big issue really since I can change shutdown command to be enabled only for %admin. But in principle, if I did not change the sudoers file, other users could easily gain root privileges if they happen to try the **sudo shutdown now** command. I'm just interested if this is the expected behaviour for the shutdown command? man page for shutdown did not inform about this.

---

### Post by b0rka7a on 2008-03-08
I want to know how to lock my screen using fluxbox menu ?
I don't know the command :\
[exec] (Lock Screen) {*???*}

---

### Post by CREEPING DEATH on 2008-03-08
Last time I had issues on a Debian system I learned to just log out to GDM and shut down from there LOL

CD

---

### Post by mali2297 on 2008-03-08
> **b0rka7a said:**
> I want to know how to lock my screen using fluxbox menu ?
I don't know the command :\
[exec] (Lock Screen) {*???*}

You can use **xscreensaver** or **gnome-screensaver**, which are available in the repos. The commands for locking the screen are
```

xscreensaver-command -lock

```
and
```

gnome-screensaver-command -l

```
respectively.

An alternative is **xtrlock**, also available in the repos. The command is
```

xtrlock

```
This app will just change the mouse cursor into a padlock. The screen is still visible but locked until you type your password and hit Enter.

---

### Post by b0rka7a on 2008-03-08
10x :)

---

