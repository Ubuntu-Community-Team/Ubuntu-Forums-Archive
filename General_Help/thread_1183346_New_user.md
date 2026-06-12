---
title: "New user"
date: 2009-06-10
forum: General Help
---

### Post by NachoKB on 2009-06-10
Hi everybody.

  I've installed Jaunty on a new DELL Inspiron. It works great (only problem is hibernating, and I don't care).

  I wanted to add another user for my gf, so each can have its own preferences etc etc etc. I created a new user from System > Administration > Users & Groups.

  It somehow works but I find a few issues:

* This user can't run compiz ("Desktop effects cannot be enabled").
* No Network Manager Applet (and others)
* Seems to have permission problems overall. I tried checking every box in its "User Privileges" tab (like "Connect wireless and ethernet", etc), even though the default user doesn't have many of them checked (even some privileges I know I've got!).
  * Does anyone know why the default user has some privileges for which it doesn't need to belong to the corresponding group? (vboxusers for example).
  * What's the best procedure to create an additional user with the same configuration as the installer creates the default one?

Thanks in advance!

-- nachokb

---

### Post by Bucky Ball on 2009-06-10
In users and groups, (System->Admin->Users & Groups), unlock. Check the original user's privileges (Properties->User Privileges). Create a new user and make sure the user privileges of the new user match the user privileges of the original and you should be set.

Easiest would be to copy the original user and then rename, of course, but I don't know any way of doing this.

---

### Post by NachoKB on 2009-06-10
> **Bucky Ball said:**
> In users and groups, (System->Admin->Users & Groups), unlock. Check the original user's privileges (Properties->User Privileges). Create a new user and make sure the user privileges of the new user match the user privileges of the original and you should be set.


That is exactly how I did it. I ended up with a user who cannot start Compiz, has no way to get the NetworkManager applet in her panel, and I'm sure there are lots of other privilege issues lurking (interestingly though, it can run VirtualBox, even if I uncheck its group).

Furthermore, and this is what troubled me, my default user doesn't belong to many groups (like the samba one) but still can do what they would allow (like mounting an smb share).

I tried checking exactly the same groups my user has (which are just a few), and later checked all of them. Nothing works...

Thanks!

nachokb

---

### Post by mixmaster on 2009-06-10
Just a thought, remember that changing the user permissions will only effect new instances of that user.  Any sessions/shells started before the change will retain the old permissions so you should ensure the user is logged out and any sessions where you have su'd to them are closed before testing the changes.

---

### Post by NachoKB on 2009-06-10
I know, I always tried new logins :(

---

### Post by asmoore82 on 2009-06-10
Fast User Switching could be the problem.
I would imagine that the first user to log in has exclusive control of the NetworkManager and Accelerated 3D Video.

---

### Post by NachoKB on 2009-06-10
> **asmoore82 said:**
> Fast User Switching could be the problem.
I would imagine that the first user to log in has exclusive control of the NetworkManager and Accelerated 3D Video.

You are right, that's it. In a multi user setting, only the first logged in user has access to Compiz and NetworkManager :(... A pity...

Compiz could be fixed in the transition to the new graphics stack (KMS, GEM, DRI2, UXA, and perhaps some other 3-letter acronym I'm forgetting), but why can't a second user interact with NetworkManager? (I imagine a multiseat setup, if two user have rights to do it why couldn't they?)

Thanks all for your answers!

-- nachokb

---

### Post by Bucky Ball on 2009-06-11
Can't you just log out and log back in as the other user? Takes seconds. As mentioned, when you make changes to a user, you need to log out and back in before any effect.

---

### Post by NachoKB on 2009-06-11
> **Bucky Ball said:**
> Can't you just log out and log back in as the other user? Takes seconds. 

Sometimes one user has open apps and leaves the machine for the other. I'm not saying that it is something *I* can't live without, but it's a gotcha a beginner stumble upon.

> **Bucky Ball said:**
> As mentioned, when you make changes to a user, you need to log out and back in before any effect.

That's not the problem (as a matter of fact, I *was* loggin out and back in, after making changes).

Thanks again!!

P.S. launchpad: [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/185599](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/185599)
nachokb

---

### Post by nandemonai on 2009-06-11
Umm weird. Works fine here I must say. User switch with compiz running on three logged in accounts fine. No network manager because they're not admin users I assume (could be wrong) but I run wired anyway so it's no drama for me as they don't need access to NM anyway.

The only issue I've come across is transparency with compiz on my account:

[http://ubuntuforums.org/showthread.php?t=1138043](http://ubuntuforums.org/showthread.php?t=1138043)

---

### Post by SoftwareExplorer on 2009-06-11
The network manager has a bug that only allows it to run on one user at a time. 

If you really need it on a specific user, you can do ```
sudo killall nm-applet
``` and then ```
 (Alt+F2) nm-applet
```

---

### Post by nandemonai on 2009-06-11
> **SoftwareExplorer said:**
> The network manager has a bug that only allows it to run on one user at a time. 

If you really need it on a specific user, you can do ```
sudo killall nm-applet
``` and then ```
 (Alt+F2) nm-applet
```

Ahh I'd wondered about that myself, never had much need to look into it. Cheers for the info. ;)

---

### Post by NachoKB on 2009-06-11
> **nandemonai said:**
> Umm weird. Works fine here I must say. User switch with compiz running on three logged in accounts fine.

Sure? That's weird, as [1] confirmed the behaviour I'm having. Doesn't seem to be related to the video driver...

Just to be sure:

1. Start Ubuntu
2. Log in with user A
3. Switch to user B through the Fast User Switch Applet
4. The new user has desktop effects

> **nandemonai said:**
> No network manager because they're not admin users I assume (could be wrong) but I run wired anyway so it's no drama for me as they don't need access to NM anyway.

If you could try it, that would be very helpful...

Thanks!

nachokb

[1] [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/161106](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/161106)

---

### Post by nandemonai on 2009-06-11
> **NachoKB said:**
> Sure? That's weird, as [1] confirmed the behaviour I'm having. Doesn't seem to be related to the video driver...

Just to be sure:

1. Start Ubuntu
2. Log in with user A
3. Switch to user B through the Fast User Switch Applet
4. The new user has desktop effects



If you could try it, that would be very helpful...

Thanks!

nachokb

[1] [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/161106](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/161106)

Confirmed it works with user switch fine here. Both users have compiz effects running (even tested with 3 users, all logged in at once and all three have compiz working as expected between switching). As I said, the only issue I have there is that my account has customized transparency for all windows and upon switching back to my account the screen goes white (screen lock, enter password for already logged in user etc) while slightly transparent. Can still enter in my password and the desktop refreshes fine so functionally it works, just if you didn't know better you'd assume it crashed or some such ;)

A thought occurs.. Have you given said user 'Capture Video from TV or Webcams and use 3D' user privileges?

As for nm-applet I confirmed that you need to kill the nm-applet as sudo and re-invoke it for it to work on another user if it's already loaded.

---

### Post by NachoKB on 2009-06-16
> **nandemonai said:**
> Confirmed it works with user switch fine here. 

It might have to do with the video drivers (I have an Intel GMA 3100, you are using nVidia...).

> **nandemonai said:**
> Both users have compiz effects running (even tested with 3 users, all logged in at once and all three have compiz working as expected between switching).

Good.

> **nandemonai said:**
>  As I said, the only issue I have there is that my account has customized transparency for all windows and upon switching back to my account the screen goes white (screen lock, enter password for already logged in user etc) while slightly transparent. Can still enter in my password and the desktop refreshes fine so functionally it works, just if you didn't know better you'd assume it crashed or some such ;)

Weird... I assume you tried disabling transparency to find it as the cause.

> **nandemonai said:**
> A thought occurs.. Have you given said user 'Capture Video from TV or Webcams and use 3D' user privileges?

Actually, I tried everything: setting every privilege, and setting only those in common with my primary user (which, interestingly, didn't have some which seemed necessary).

> **nandemonai said:**
> As for nm-applet I confirmed that you need to kill the nm-applet as sudo and re-invoke it for it to work on another user if it's already loaded.

Sorry, hadn't read that.

Thanks a lot,

nachokb

---

