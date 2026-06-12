---
title: "sudo fails-- &quot;Sorry, try again&quot;"
date: 2009-03-26
forum: General Help
---

### Post by daking874 on 2009-03-26
sudo has stopped working for me. I've everything I could find in the forums and I'm thinking I'm going to have to reinstall (drag).

When I try sudo it fails to authenticate. I'm certain I'm using the correct password (logs on ok).

Last thing I did was to install the thinkfinger-tools package (tf-tools command). I'm using ubuntu 8.10 on an IBM thinkpad x41. I removed the package but no change.

when I try to use sudo this is the output:
sudo ls
[sudo] password for ian: 
Sorry, try again.
[sudo] password for ian: 
Sorry, try again.
[sudo] password for ian: 
Sorry, try again.
sudo: 3 incorrect password attempts

I'm certainly a member of the admin group. id gives me:

uid=1000(ian) gid=1000(ian) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(ian): 

I've chmod 0440 /etc/sudoers (had those permissions anyway).
/etc/group and /etc/passwd also have rw-r-r permissions.

and I've tried editing sudoers with ian= ALL(ALL) ALL.

su also fails:su
Password: 
su: Permission denied

gksu also doesn't work (not surprising).

If anyone has any ideas at all I would appreciate it- trying to avoid the reinstall (thinkfinger-tools was the final package!)

thanks

---

### Post by aktiwers on 2009-03-26
Maybe a stupid question.. but have you checked CAPSLOCK and NUMLOCK?

---

### Post by Bachstelze on 2009-03-26
Paste the contents of your sudoers file (you'll most likely have to use a live cd to access it).

---

### Post by daking874 on 2009-03-26
Thanks guys. I've basically solved the problem but its not perfect. It was thinkfinger-tools that was causing it.

It requires the package libpam-thinkfinger despite the instructions for intrepid explicitly saying it's not required.

Now sudo asks for a password, then asks for a password or fingerswipe. A fingerswipe doesn't work but I can put anything in or just press enter for the second request and it authenticates.

Not ideal but at least I don't have to reinstall. Looks like the thinkfinger package is buggy.

I referenced this [http://blog.aliencam.net/2008/11/thinkpad-fingerprint-reader-in-ubuntu-810-intrepid/](http://blog.aliencam.net/2008/11/thinkpad-fingerprint-reader-in-ubuntu-810-intrepid/)

---

### Post by daking874 on 2009-03-26
Really quirky. Now once I've used sudo once it never asks me for my password again even if I close the terminal and open another.

And opening synaptic package manager it asks for my password, but does nothing once I've put it in. Then the third time it opens without asking for my password.

Any ideas to get it back to normal? or at least so it won't remember the authentication once a terminal has been closed?

---

### Post by daking874 on 2009-03-26
now synaptic isn't working at all.

log entries:

Mar 26 23:37:07 ian-laptop kernel: [  985.800028] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input18
Mar 26 23:37:07 ian-laptop kernel: [  986.109300] sudo[9213]: segfault at 35 ip b7de8472 sp b744d360 error 4 in libc-2.8.90.so[b7d77000+158000]

looks like a really screwed package. Problem is, if I remove it, sudo doesn't work at all. If anyone has any suggestions- I'd love to hear them.

---

### Post by daking874 on 2009-03-27
Does anyone know how to reinstall sudo?

---

### Post by kimberlite on 2009-03-27
Try this: [http://ubuntuforums.org/showthread.php?t=889496](http://ubuntuforums.org/showthread.php?t=889496)

---

### Post by daking874 on 2009-03-27
Thanks! Before I reinstall sudo I'm giving thinkfinger one more try.

I've modified /etc/pam.d/common-auth and it now *seems* to be working.

I moved the line:

auth   sufficient      pam_thinkfinger.so

as the first non-commented line.

I'll keep testing but if it doesn't work will reinstall sudo.

---

### Post by daking874 on 2009-03-27
Ok solved! It appears thinkfinger-tools package works ok but when installed it doesn't edit the /etc/pam.d/common-auth file correctly.

It should look something like:

(after initial comments)

# here are the per-package modules (the "Primary" block)
auth	sufficient	pam_thinkfinger.so
auth	[success=1 default=ignore]	pam_unix.so try_first_pass nullok_secure
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

thinkfinger alters it so that the important lines:
auth	sufficient	pam_thinkfinger.so
auth	[success=1 default=ignore]	pam_unix.so try_first_pass nullok_secure

are added at the end. This is incorrect as the first line: 
auth	[success=1 default=ignore]	pam_unix.so nullok_secure

Is still there which is why thinkfinger asks for passwords twice and gets confused. Since I changed it the problem has been solved.

Thanks for the suggestions.

---

