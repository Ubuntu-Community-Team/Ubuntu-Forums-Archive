---
title: "Likewise-Open and local linux groups"
date: 2008-09-25
forum: Desktop Environments
---

### Post by AquaQuieta on 2008-09-25
I have added computers to our AD domain manually before...but
this time I decided to try likewise-open instead of the manual process.
On a clean install of Hardy Heron, I installed Likewise-open and connected to my AD domain (easy breezy, I like it :) I added my LinuxAdmins AD group to the sudoers file, and things were looking good.

However, after logging in as a domain user, I was not a member of any local linux groups...and I searched high and low for a solution. Since I only saw a couple of old posts with people asking for this solution, I figured I'd post what worked for me...

To add AD domain users to local accounts automatically upon login when using likewise-open:


First, add this line to the /etc/security/group.conf file (change the groups as you see fit):

*;*;*;Al0000-2400;floppy,video,audio,cdrom,plugdev,users,scanner

Step 2) add this line to the /etc/pam.d/common-auth file:

auth    required    pam_group.so use_first_pass

I'm not sure if order is important, but I put that line at the top of the file, right *above* this line:
auth    sufficient    /lib/security/pam_lwidentity.so


Step 3) Log out and log back in as an AD user, open a terminal and type "groups". You should see all your AD groups and all the groups specified in /etc/security/group.conf :)


Thats it. I hope it helps somebody else....it took forever to figure out step 2 :)

---

### Post by likeWiseGuy on 2008-09-25
This is pretty creative work. I'm glad this worked out well for you. :-)

---

### Post by AquaQuieta on 2010-06-24
Things have changed a bit with likewise setup since my Hardy install, but overall I am pleased :)

It took a little bit of fiddling to get everything right this time, but still much better than it used to be...one day I'll learn to read all the comments in the config files! Regardless, I am far too lazy to manually add hundreds of Domain users to the /etc/group file, and despite all the cursing and booting into recovery mode, it was well worth the effort. 

Anyway, my above instructions  are for Hardy Heron...now that Lucid Lynx is out (huzzah! :guitar:), it's time for the Lucid Lynx redux:


First, setup you /etc/security/group.conf file (I had to remove scanner group, since it's not setup by default any more):

*;*;*;Al0000-2400;floppy,video,audio,cdrom,plugdev,users

Next, you have to update your /etc/pam.d/common-auth file, but this time I'm pretty sure the order is VERY important. Read the Comments regarding 
pam-auth-update in the commaon-auth file for more information.

It should look like this:

```
# here are the per-package modules (the "Primary" block)
auth    [success=2 default=ignore]      pam_unix.so nullok_secure
auth    [success=1 default=ignore]      pam_lsass.so try_first_pass
# here's the fallback if no module succeeds
auth    requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
#
# since the modules above will each just jump around
auth    required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
#
###################ADD THIS LINE HERE#######################
auth required pam_group.so use_first_pass
############################################################
#
#
# end of pam-auth-update config
```


I believe (can't remember exactly) I had to run:

sudo pam-auth-update 

after I updated the file. 

Anyway, that's it. The only other problem I had with likewise was the lsassd deamon refuses to start on reboot...I think its because it is trying to start before I have network connection. I tried staring it later
via the update-rc.d  command, but no go...it still starts before I have network. So rather than login with my admin account, start lsassd and then log in with my AD account, I kludged it by adding:

/etc/init.d/lsassd start

to my /etc/rc.local file. Not the most elegant solution, but it works for me. YMMV, but hopefully this helps somebody out ):P

---

