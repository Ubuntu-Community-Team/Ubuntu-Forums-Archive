---
title: "bash_profile won't run on login"
date: 2009-02-08
forum: General Help
---

### Post by sadovsky on 2009-02-08
Hi,

I'm trying to load my monitor's icc profile on login.

I created a .bash_profile in my home dir and added the following line to it:
/usr/local/Argyll_V1.0.3/bin/dispwin -L

This command works if I run it from command prompt. It also runs if I 'source ~/.bash_profile'. However, it refuses to run when I login (locally) to my system. I tried making my .bash_profile executable (chmod 755), but that didn't fix the problem. Why won't my .bash_profile run on login!? 

Thanks,
Adam

---

### Post by taurus on 2009-02-08
Try adding that command to ~/.bashrc.

---

### Post by sadovsky on 2009-02-08
I don't want to add the command to my .bashrc, because then it would get run every time I open a terminal. I only want it to run once, when I log in, and so .bash_profile is exactly where it belongs.

---

### Post by sadovsky on 2009-03-03
Ping. If I run 'source ~/.bash_profile' right after startup, my color profile is loaded correctly. When does .bash_profile get sourced normally? Since the command in my .bash_profile refers to a file on a mounted drive (specified in /etc/fstab), is it possible that the file is not available when .bash_profile is sourced?

---

### Post by anystupidname1 on 2009-08-23
I'm seeing the same behaviour in karmic and it bothers me. What am I missing?

Should I be worried / puzzled that neither .bash_profile nor .bashrc are present on a fresh install of karmic until I created them?

---

### Post by loomsen on 2009-08-23
Hello.

bash_profile is probably the wrong file for your purpose. Either add it to ~/.profile or /etc/profile, as I assume you want your settings to be loaded upon session-start.

The description of /etc/profile:
> 
# System wide environment and startup programs, for login setup
# Functions and aliases go in /etc/bashrc


For instance, I created a ~/.profile and added 
```

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

# load nvidia settings if available
if [ -e "$HOME/.nvidia-settings-rc" ]; then
	/usr/bin/nvidia-settings -l
fi

```

to it. Both options shall only be executed once at session start.

---

### Post by samaricsm on 2009-09-18
I am running both (on two different machines) 8.04 and 8.10 and I am see the same behaviour: none of the start scripts run (*.bash_profile*, *.bash_login*, or *.profile*).  If I source the files, then they execute correctly.

I was reading in "A Practical Guide to Ubuntu Linux" that .bash_* are only executed when bash is started with the *--login* option.  I am unable to find in the init.d scripts where the bash shell is started to add that option.

How do I get the *.bash_profile* to execute automatically on startup?

---

### Post by alien21010 on 2009-09-19
This link may solve your problem...  Seems you need to add a source ~/.bash_profile to ~/.xprofile to get it to load on graphical login...  Stupid really.

[http://benakiva.blogspot.com/2006/09/ubuntu-bashprofile-does-not-get-run-at.html]("http://benakiva.blogspot.com/2006/09/ubuntu-bashprofile-does-not-get-run-at.html")

---

### Post by Steve White on 2010-05-28
I just verified that .bash_profile is not read in X sessions, but it is read in other login sessions.  This is new behavior since Ubuntu 9.10, is still present in 10.4, and different from other Linux distros I am using.  A work-around using ~/.xprofile might be the ticket.

I would like to know why this behavior has been altered in Ubuntu.

From the bash man page, under INVOCATION:

When bash is invoked as an interactive login shell, or as a  non-interactive  shell with the --login option, it first reads and executes commands from the file /etc/profile, if that file exists.   After  reading that file, it looks for ~/.bash_profile, ~/.bash_login, and ~/.profile, in that order, and reads and executes commands from the first one  that exists  and  is  readable.  The --noprofile option may be used when the shell is started to inhibit this behavior.

---

### Post by Steve White on 2010-05-28
The work-around I used is to put in the file 
    ~/.xprofile 
a line
    . ~/.bash_profile

As mentioned in one of the links above, it is the Gnome desktop manager to blame.
    /etc/gdm/Xsession
It's not totally a bad thing.  With this mechanism, one could have different behavior for graphical and non-graphical logins.  

It's just lousy to spring this stuff on us.  I wonder if there may have been a way to have done it that was compatible with existing configurations.

Some people seem not to like the ~/.bash_profile mechanism.  The Debian Wiki actually says it is "historical".  This seems to be simply ignorance.  The issue is proper association of initializations with different kinds of sessions: login and non-login sessions graphical and non-graphical sessions, and easy control over whether commands are executed just once at login or in each session.

---

### Post by CliffS on 2011-06-06
If you're seeing this issue, it's probably because you're opening a terminal session.

In terminal, go to Edit -> Profile Preferences -> Title and Command and tick "Run command as a login shell".

Then new terminal windows will run .bash_profile on startup.

---

### Post by ranjit. on 2011-11-10
all u guys new to ubuntu be very careful when editing .profile because it may cause ur  GUI to be stuck:(, I tried to test out my .profile by adding another commmand gnome-panel as a test and found that the User profile loads with only the gnome panel and nothing else, luckly i changed it by editing via level 3 init and logging off the user, so be very careful when editing the .profile:KS

---

### Post by oldos2er on 2011-11-10
Closed, please don't bump old threads.

---

