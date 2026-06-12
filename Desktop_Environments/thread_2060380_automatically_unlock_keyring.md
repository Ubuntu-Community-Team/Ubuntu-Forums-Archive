---
title: "automatically unlock keyring"
date: 2012-09-20
forum: Desktop Environments
---

### Post by rybnik on 2012-09-20
I run Lucid Lynx, and I use both Gnome and KDE--mostly KDE.  I recently switched from GDM to KDM, and immediately after I did so, the keyring no longer automatically unlocked.  How do I get the keyring to automatically unlock again?

I have already checked that autologin is disabled and my login password is the same as the keyring password.

---

### Post by sharathkumar on 2012-09-20
It's been discussed in an earlier post: [http://ubuntuforums.org/showthread.php?t=1616370](http://ubuntuforums.org/showthread.php?t=1616370)

hope that helps

---

### Post by rybnik on 2012-09-20
> **sharathkumar said:**
> It's been discussed in an earlier post: [http://ubuntuforums.org/showthread.php?t=1616370](http://ubuntuforums.org/showthread.php?t=1616370)

hope that helps

Thank you!

---

### Post by spaceshipguy on 2012-09-21
Didn't work for me.
I have only Passwords: Login, and it is set as default, but I am still bothered by this dialogue. 
Every version of Ubuntu I've ever run has started to do this after a while. I've just gotten used to it.

---

### Post by cmcanulty on 2012-09-21
my machine started this a few days ago and none of the fixes stops it, very irritating

---

### Post by rybnik on 2012-09-21
The above two posters say it doesn't work.  Make sure you actually DELETE the keyring password (by setting it to a null field), not just switch some setting.

---

### Post by cmcanulty on 2012-09-21
I did that and also deleted the files in,gnome2/keyrings folder still persists

---

### Post by rybnik on 2012-09-21
> **cmcanulty said:**
> I did that and also deleted the files in,gnome2/keyrings folder still persists

You have kdm, right?  If you're willing to switch to gdm, that might fix it.

But if that doesn't work, I don't know what to tell you.

---

### Post by cmcanulty on 2012-09-22
I am using ldm

---

### Post by rybnik on 2012-09-22
I don't know enough to be able to be of help, but I haven't marked this thread [solved], so hopefully someone else can offer help.

---

### Post by rybnik on 2013-08-05
This might shed some light on this:

I used to use Ubuntu 10.04 with KDE installed on top.  When I logged into Gnome2 (which is what Ubuntu used by default back then), the keyring unlocked automatically.  It didn't when I logged into KDE.

Now I use Kubuntu 12.04 with LXDE and XFCE installed on top.  When I log into KDE, the keyring unlocks automatically.  When I log into LXDE or XFCE, it doesn't!

So it seems that a keyring is unlocked automatically only for the first desktop environment that you've installed.  I don't know anything about changing that, though.

---

