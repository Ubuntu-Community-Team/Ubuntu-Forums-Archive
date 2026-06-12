---
title: "Refusing to initialize GTK+."
date: 2007-11-02
forum: Desktop Environments
---

### Post by peter73 on 2007-11-02
Hi,
I've seen this error message posted many times, with various hacks to get around the issue, none of which seem to solve my problems.

What I was doing:
I installed ubuntu a week ago, and have been working on it since without issue. I was using Intellij, trying to get the 'alt f8' feature to work, and clicked ctl-alt-f8, which caused everything to lock and eventually restart. 

Now,
when I try to log in, I get the "your session only lasted less than 10 seconds..." dialog with my
"xsesion-errors" file saying
Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session startup...
/etc/profile: 17: id: not found
/etc/gdm/Xsessio: 191: ls: not found
/etc/gdm/Xsession: Executing /usr/bin/gnome-session fialed, will try to run x-terminal-emulator
exec: 204: x-terminal-emulator: not found

I've seen the issues people have had w/ perms on /tmp-mine are fine and that didn't help
I've seen the uninstalling xserver-gl, that didn't help.
I've been through the circular references of "this is the same as that ticket" many times, nothing seems to help.

Thanks,
P

---

### Post by GeneralSunTzu on 2007-11-28
> **peter73 said:**
> Hi,
I've seen this error message posted many times, with various hacks to get around the issue, none of which seem to solve my problems.

What I was doing:
I installed ubuntu a week ago, and have been working on it since without issue. I was using Intellij, trying to get the 'alt f8' feature to work, and clicked ctl-alt-f8, which caused everything to lock and eventually restart. 

Now,
when I try to log in, I get the "your session only lasted less than 10 seconds..." dialog with my
"xsesion-errors" file saying
Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session startup...
/etc/profile: 17: id: not found
/etc/gdm/Xsessio: 191: ls: not found
/etc/gdm/Xsession: Executing /usr/bin/gnome-session fialed, will try to run x-terminal-emulator
exec: 204: x-terminal-emulator: not found

I've seen the issues people have had w/ perms on /tmp-mine are fine and that didn't help
I've seen the uninstalling xserver-gl, that didn't help.
I've been through the circular references of "this is the same as that ticket" many times, nothing seems to help.

Thanks,
P

Well, besides bumping this, maybe the previous poster could give me the pointers he refers to, as I have the same identical messages, am stuck as well, but haven't tried yet all the stuff he has tried...

---

### Post by jplinderman on 2007-12-10
I, too, was seeing the dreaded message.  I realized that the message hadn't appeared until I tried replacing the skeletal login created when I loaded 7.10 with the complete home directory I had been using before.  After a few false starts I tried moving my .profile out of the way, and, voila, I was able to log in.  I run ksh rather than bash, and it was clear that my .kshrc had been run, but that didn't seem to trigger the failure.  (If the error had persisted, I would have tried moving the .ksrch off to one side as well.)  After getting in, I was able to simply
  . profile  # I had moved .profile to profile
and that set up my environment as it used to exist.

I don't know why the .profile was causing the failure.  I have seen postings elsewhere that executing dircolors causes the problem (and I did, indeed have dircolors in my .profile).  Error messages suggested that ksh was not fully in control when the .profile was being sourced (ksh builtins like 'whence' were reported as not found, for example).

So my suggestion is this: if you see the error message, move your .profile (and any other files that may be sourced as part of initializing whatever shell you use) "off to the side" and, if you get in, source them manually.  -- jpl

---

### Post by jplinderman on 2007-12-19
Klausner, from another thread, was kind enough to try moving his .profile and .bashrc aside.  It didn't help him.  The bewildering variety of things that work for one person but don't work for others suggests that this is going to be very interesting bug!

I'm interested in hearing from anyone trying the .profile move approach, whether it works or not.  So far, all the information I have is that it worked for me, and didn't work for klausner.

---

### Post by pkpkpkpk on 2008-01-20
I too have this error.

I am unable to log in  ( ubuntu gutsy)


My problem started after I tried installing the ICA client for linux ( from Citrix)

Not sure how to fix this problem. Bumping this thread up.

EDIT: I fixed my issue by following instructions on this thread [http://ubuntuforums.org/showthread.php?t=288053](http://ubuntuforums.org/showthread.php?t=288053)

---

### Post by jplinderman on 2008-04-28
I just installed Hardy Heron 8.04 desktop, and now understand what my problem was, and why moving .profile to profile worked.  As background, I had been running Red Hat, and, after installing Ubuntu, I simply changed my home directory to the home directory I had been using under Red Hat.  But the processing of .profile appears to be quite different under Ubuntu.  It is not the login shell, ksh in my case, that processes .profile at login.  It is a restricted shell dialect that does not recognize all ksh builtins, "whence" being one such.  The login therefore failed, creating a login loop.  The simple solution is to rename legacy .profile files to be .profile.ksh or .profile.bash (or whatever your login shell is named).  Either copy the skeletal .profile that Ubuntu creates when adding a user at installation, or omit .profile altogether. This doesn't easily explain some of the fixes, like changing the modes on /tmp, mentioned in other threads, but it has me up and running under both Gutsy and Hardy.  -- jpl

---

