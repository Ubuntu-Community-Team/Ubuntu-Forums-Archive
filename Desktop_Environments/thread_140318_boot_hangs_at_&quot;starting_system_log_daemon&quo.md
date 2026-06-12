---
title: "boot hangs at &quot;starting system log daemon&quot;"
date: 2006-03-05
forum: Desktop Environments
---

### Post by blanks on 2006-03-05
Hi
I'm running 5.10 with kernel 2.6.12-10-386.  When I boot the system, it hangs at the "Starting system log daemon" step. I am able to boot using recovery mode but I get the error "HAL fails to initialize".

(I tried these steps from Ubuntu bugzilla bug #13333 comment 16:
sudo update-rc.d -f dbus remove
sudo update-rc.d dbus defaults 12
but they didn't help. 
[http://bugzilla.ubuntu.com/show_bug.cgi?id=13333](http://bugzilla.ubuntu.com/show_bug.cgi?id=13333) )

When I try either "/etc/init.d/sysklogd start" or /etc/init.d/sysklogd reload" from recovery mode, it just hangs. The file /var/run/syslog.pid does get created with a pid number, but 'ps aux | grep -i logd' shows nothing.  I've applied all updates to the system. I can post dmesg output from recovery mode boot, if anyone thinks that'd be useful...

The last thing I did before shutting my system down at it's last working configuration was to upload some stuff to my ipod. I did a right-click on the ipod icon on the desktop and did 'eject' which failed with something like "Unable to eject..." So I just shut the system down. On the next boot, the problems started happening.

Thanks for any help

---

### Post by blanks on 2006-03-07
I'm still having the above problem.  Does anyone have an opinion on the potential for disaster if I try something along the order of:
$> apt-get remove --purge sysklogd
$> apt-get install sysklogd
after backing up syslog.conf ??  I don't think syslog is the problem - I think some hardware problem (the HAL message...) is keeping syslog from starting, but I'm getting desperate.

Thanks for any advice

---

### Post by bpasdar on 2006-05-01
I just installed gtkpod for my ipod yesterday and now my reboot hangs as well at the starting system log message.

Babak

---

### Post by TimelessRogue on 2006-05-01
Now I've got the same problem along with 'Failed to initialize HAL'and am still at a loss as to a 'fix-it' other than to log in in recovery mode ... anyone have any ideas?

As others have noted, if I excercise a bit of patience the boot process will continue after about 5 minutes or so ... but it still should not be happening.  I have done some 'updating' recently so perhaps therein lies the problem ... I'll do some checking and post back.

Well, I've followed another suggestion to reload HAL ... no difference, still hangs at 'system log daemon' but eventually boots ... gonna keep trying!

Addendum:  Since I originally posted this I have done a 'dist-upgrade' to Dapper Drake Beta ... with excellent results, by the way ... and the HAL problem has gone away but the 5 minute pause while 'Starting system log' and/or 'Starting system log daemon' persist.  Still trying to figure this one out as it originally started after a simple 'update' of Breezy.

---

### Post by pescio on 2007-10-31
Hi,

hey I've got the same problem after updating from feisty to gutsy.
Did you solve the problem?

thanks

---

### Post by loadeddreams on 2007-11-03
I am also having the same problem.. I am hesitant to start my own thread because there are many other threads up, but none with real answers from what I can see.

I have tried a lot of different methods, but the only one that seems to work is removing syslogd and samba from startup which I'd really.. really.. rather not do.

I think there was a mix up on which items should start when and am looking for some way to set them all back to defaults if possible...

anyways.. did you get this resolved?

---

### Post by karenL on 2007-12-29
> **blanks said:**
> Hi
I'm running 5.10 with kernel 2.6.12-10-386.  When I boot the system, it hangs at the "Starting system log daemon" step. I am able to boot using recovery mode but I get the error "HAL fails to initialize".


Thanks for any help

So has anyone resolved this, just installed server 7.1 and installed the GUI and once it updated I got the same errors :-(

---

### Post by chadmiller on 2007-12-30
Let it time out.  It should take 5 minutes.

After that, go to a shell and type "*dmesg*".  Do you then see "Audit" lines containing warnings that syslogd tried to lock a particular file, "*syslogd.pid*"?  If so, then the kernel auditing functionality is on, and refused to perform an action that syslog required.

One possible reason for that strange restriction is that you've installed (but not configured?) "*apparmor*".  Try removing it, if you have it installed.  Or, if you know you really need it, then configure it correctly. Otherwise, you'll have to figure out kernel auditing on your own.

---

### Post by carpy on 2008-02-01
I don't suppose you are running LDAP-authentication locally?

I had this problem with my LDAP server, when using "loglevel 424" in slapd.conf.  This was a consistent problem, regardless of when I loaded sysklogd... it would cause hang problems.  using strace, I found that even "w" was causing a hang at the call to sysklogd (using ldap in nsswitch.conf for passwd and group).  

Disabling the logging entry (setting it back to the default of loglevel 0) allowed the system to boot and not hang when running sysklogd.  Setting loglevel 424 is ok for troubleshooting, but don't try to boot with it.

YMMV

---

