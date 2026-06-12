---
title: "Locked Account???"
date: 2009-01-22
forum: General Help
---

### Post by BrandonBan6 on 2009-01-22
Oye! So, this afternoon I locked my screen and when I came back to sign on, my password doesn't work. I have only one password, I know I was typing it correctly (we've all heard that one right?). No biggie I think, I reboot into the recovery console drop to the root shell and type:

```

passwd username

```

And it returns the error:

```

passwd: Authentication token manipulation error
passwd: password unchanged

```

Soooo, I then decide to remove the password from the /etc/passwd file. Reboot and still no go. 

passwd -S returns a "NP" option.
passwd -u runs successfully.

Any thoughts?

---

### Post by JMJ_coder on 2009-01-22
/etc/passwd doesn't contain the passwords. On ubuntu, I believe the file is /etc/shadow. You need to be root to even look at the file. You can remove the password there, but don't replace it in that file as it is encrypted. But, you should be able to use passwd then.

---

### Post by BrandonBan6 on 2009-01-22
I had deleted it from the shadow file to, just didn't post it in first post. Still no go after that, same error....some research is showing something is hosed in the pam files possibly from installing likewise-open. I'll keep digging and see what happens :)

---

### Post by n5wy on 2009-02-11
B,
Did your problem start after UnInstalling Likewise-open, or after InStalling it?

I am having a problem similar to what you describe. I installed Likewise-open and have it running successfully to use my Ubuntu box on the MS Server 2008 AD for several days, both on and off the AD domain. However, my computer stopped letting me in suddenly and I cant figure out why, or how to get back in. I am pretty sure it has to do with Like-wise but I havent gotten too far with a resolution yet. 

Where you able to fix your problem?

---

### Post by BrandonBan6 on 2009-02-12
n5wy,

I did read somewhere in the "known bugs" on the Likewise-open forums that this was caused from Likewise. There is a command you can use to fix the bug, but I'm sorry I don't remember what it was....had to do with editing a library in the PAM files. I ended up re-installing, mostly because I wanted to give 64 bit architecture a go (and quite happy I did). Hope that is at least some help!

---

### Post by n5wy on 2009-02-12
Thanks Brandon. 

I have been trolling through the likewise forum looking for answers, too. I ended up reinstalling last night and that fixed my problem. However, I am locked out of my MSServer 2008 AD domain until I get the workaround in place. 

joe

---

### Post by BrandonBan6 on 2009-02-12
Oye, does not sound like fun! Good luck to you sir.

---

### Post by Pinkydead on 2009-03-16
I installed Likewise as well and didn't reboot for ages only to find myself locked out of my own account because of this error. :(

I don't know how to solve the problem with Likewise if you need it, but I didn't and as a sort of mismatch of various posts I found, I:

1. Uninstalled Likewise using aptitude on a recovery root account

(Still didn't work)

2. Copy all the *.lwidentity.orig files back over the Likewise versions in /etc/pam.d

Everything is now back to normal. :D

As I said, if you need Likewise, I can't help you - but if you don't this should work.

---

### Post by BrandonBan6 on 2009-03-16
Thanks Pinky! I ended up re-installing after an exhausting search. I'll stick to Samba and Virtualbox until something more stable comes out :) Fortunately, I've been anal about backups, so I was completely back up and running within 45 minutes.

---

