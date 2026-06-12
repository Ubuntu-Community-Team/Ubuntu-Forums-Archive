---
title: "Help needed for manual installation of preload 0.6.4 in Jaunty 9.04 64bit"
date: 2009-06-11
forum: General Help
---

### Post by DanglingPointer on 2009-06-11
Hi Experts,

I have attempted to manually make and install preload v0.6.4 which I downloaded from Source Forge.
I am new to ubuntu and linux in general and am still getting used to the way things are organised and done.

After following the instructions to the best of my understanding from the included README and INSTALL text files; I believe I still do not have it working properly.

Preload does not automatically start after reboot.  And after login, it only started working after I added a new Startup Program (System->Preferences->Startup Applications).  However it runs as myself instead as root when I check System Monitor.  I am not sure whether it matters or not however, when I check the preload log I see this repeatedly after each and every logout (or restart of the program):

"[COLOR=Blue][Thu Jun 11 21:15:55 2009] loading conf from /usr/local/etc/preload.conf
[Thu Jun 11 21:15:55 2009] loading state from /usr/local/var/lib/preload/preload.state
[Thu Jun 11 22:06:43 2009] exit requested
[Thu Jun 11 22:06:43 2009] saving state to /usr/local/var/lib/preload/preload.state
[Thu Jun 11 22:06:43 2009] [COLOR=Red]cannot open /usr/local/var/lib/preload/preload.state.tmp for writing, ignoring: Permission denied[/COLOR][/COLOR]"

It appears that since it is running as myself and not as root, it is constantly unable to save state information for the next login, therefore each time it restarts, it restarts like "brand new" with no history.

Could someone give me a hand and guide me?  Thanks!

---

### Post by knattlhuber on 2009-06-11
I don't know nothing about preload but you could try making the preload.state.tmp file writable for everybody:

```
sudo chmod +w /usr/local/var/lib/preload/preload.state.tmp
```

Or alternatively, check the preload.conf file if you can change the file path for the preload.state.tmp file and place it your home folder.

---

### Post by DanglingPointer on 2009-06-13
> **knattlhuber said:**
> I don't know nothing about preload but you could try making the preload.state.tmp file writable for everybody:

```
sudo chmod +w /usr/local/var/lib/preload/preload.state.tmp
```Or alternatively, check the preload.conf file if you can change the file path for the preload.state.tmp file and place it your home folder.

Thanks I'll give it a shot.

---

### Post by DanglingPointer on 2009-06-13
Thanks knattlhuber, that did the trick!

I changed the permission of the folder[FONT=monospace] /usr/[/FONT]local/var/lib/preload/ to allow people in my group to read and write to the path including all files there already.

preload couldn't create a preload.state.tmp which it then amalgamates to the existing preload.state.

cheers

---

### Post by DanglingPointer on 2009-06-15
Ok, new problem.  Just when I thought that everything was running ok, well it isn't yet.

Each time I log out of my desktop then log back in, I get another instance of Preload.  As in:
-After reboot and login --> 1 instance running
-After log out and log back in --> 2 instances running
-After repeated log out and log back in of 'n' amount --> 'n' instances running

How do I fix this?

I was thinking perhaps, getting Preload to run right after boot before anyone logs in.  That way anyone who logs in already has preload loaded.  Does anyone know how I can set this up?

I have a program called BootUp-Manager but it doesn't let me add any new programs.  It only shows me existing ones.  How do I get Preload added to that list.

Lastly, if Preload was indeed added to the list and runs right after boot, will it work for everyone?  Will it actually prefetch, etc for everyone running as root I suppose?

---

### Post by DanglingPointer on 2009-06-16
bump

help someone?

---

### Post by DanglingPointer on 2009-06-17
bump

---

### Post by Arup on 2009-06-17
I have installed preload in the past from the repos and it worked without any hitches, is there any particular reason why you had to compile one?

---

### Post by DanglingPointer on 2009-06-17
> **Arup said:**
> I have installed preload in the past from the repos and it worked without any hitches, is there any particular reason why you had to compile one?

I wanted to try out the newest version which isn't available at the repos.  The version at the repos is 0.4.5.  While the newest version is 0.6.4.  Which according to the developer's release notes, has had a lot of fixes put in place.

So, by any chance mate, do you know how I can sort out my problem?  I have only used ubuntu for the last 4 weeks and am very new linux.

---

### Post by sdennie on 2009-06-17
There are a few problems here.

1) You should have run ./configure with the options "--prefix=/usr" (optional I suppose) and "--localstatedir=/var".  That will make preload use /var instead of /usr/local/var to store it's state information and logs.

2) You should *not* make the .state file world writable.  That is a huge security risk.  You should either run preload as root like it normally runs or run it as your user and point it to a local state file that is only writable by you.  A trick to do this would be to install the Ubuntu preload and then removing it (but not purging it).  That will keep the boot script for preload in tact and when you drop your new version in, everything will magically work as it should (not test but, it should).

---

### Post by DanglingPointer on 2009-06-20
Thanks sdennie,

How do you uninstall a program which was installed from source (configure, make, make install).  The "Install" text file says I can run "make uninstall" but when I try it even using sudo; it doesn't work.  It says that it is missing an uninstall routine.

I would like to uninstall preload 0.6.4.

---

### Post by DanglingPointer on 2009-06-20
> **sdennie said:**
> There are a few problems here.

1) You should have run ./configure with the options "--prefix=/usr" (optional I suppose) and "--localstatedir=/var".  That will make preload use /var instead of /usr/local/var to store it's state information and logs.

2) You should *not* make the .state file world writeable.  That is a huge security risk.  You should either run preload as root like it normally runs or run it as your user and point it to a local state file that is only writeable by you.  A trick to do this would be to install the Ubuntu preload and then removing it (but not purging it).  That will keep the boot script for preload in tact and when you drop your new version in, everything will magically work as it should (not test but, it should).

Ok I figured it out, what I did was I downloaded via Synaptic a program called "checkinstall"  I then ran through the motions again of installing the program...
1) ./configure
2) make
3) now instead of "make install"; I used "checkinstall" and it worked magically creating a deb file

I ran the deb file which upon successfully completion included the new program (preload 0.6.4) to synaptic package manager.
Now firing up Synaptic, I used it to completely remove preload 0.6.4.  done.

I have decided that I will not be using preload.  Ubuntu is fast already.  If canonical believes that their cache management system needs an upgrade, well I assume they would build it into the kernel bypassing the need to install daemons, etc.  This sort of stuff anyway should be running as part of the kernel and not an independent app.

Perhaps they are already thinking of adding it in?  Some sort of "superfetch" equivalent.  For now, I am happy with the way Jaunty is running natively.

Thanks to everyone who helped!
):P

---

