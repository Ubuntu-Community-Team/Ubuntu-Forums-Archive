---
title: "Unlock button in services is grayed out"
date: 2009-05-17
forum: General Help
---

### Post by iDaft on 2009-05-17
I disabled the graphical login manager in Services Settings and now I cannot unlock the services.  The unlock button is grayed out and I cannot even click it.  I've tried sudo services-admin and I enter in my password, but everything is still grayed out.  Not sure if this matters, but I am using Ubuntu Jaunty 64bit on an Intel core2duo.

Edit: I just noticed that I cannot mount my other partitions.

---

### Post by kerry_s on 2009-05-17
policykit is tied to the login managers.

add>  

```
** <return result="yes"/>**
```

to /etc/PolicyKit/PolicyKit.conf

example:

```
<config version="0.1">
 <return result="yes"/>
</config>

```

that should also fix the logout issues from hal.

no guarantees, it's what got me through when i did a base build up with no login manager.

---

### Post by iDaft on 2009-05-17
> **kerry_s said:**
> policykit is tied to the login managers.

add>  

```
** <return result="yes"/>**
```

to /etc/PolicyKit/PolicyKit.conf

example:

```
<config version="0.1">
 <return result="yes"/>
</config>

```

that should also fix the logout issues from hal.

no guarantees, it's what got me through when i did a base build up with no login manager.

I just checked my PolicyKit.conf and I already have that line in there.  Also check my edit I just noticed I cannot mount my other partitions.

---

### Post by kerry_s on 2009-05-17
> **iDaft said:**
> I just checked my PolicyKit.conf and I already have that line in there.  Also check my edit I just noticed I cannot mount my other partitions.

let me see what you got in your policykit.conf, they wouldn't put that line by itself it would be tide to a user/daemon, putting just that overrides everything, complete access no restrictions. 
for the mount you need to allow that in the users and groups, but you can't access that till you get access.

the policy crap is the main reason i ditched gnome for xfce4, it's just stupid, it's like being treated like an idiot who can't manage a computer system, if i wanted that i'd still be using windows.

---

### Post by iDaft on 2009-05-17
This is what is inside my PolicyKit.conf

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- XML -*- -->

<!DOCTYPE pkconfig PUBLIC "-//freedesktop//DTD PolicyKit Configuration 1.0//EN"
"http://hal.freedesktop.org/releases/PolicyKit/1.0/config.dtd">

<!-- See the manual page PolicyKit.conf(5) for file format -->

<config version="0.1">
    <match user="root">
        <return result="yes"/>
    </match>
    <define_admin_auth group="admin"/>
</config>[CODE]
```[/CODE]

---

### Post by kerry_s on 2009-05-17
> **iDaft said:**
> This is what is inside my PolicyKit.conf

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- XML -*- -->

<!DOCTYPE pkconfig PUBLIC "-//freedesktop//DTD PolicyKit Configuration 1.0//EN"
"http://hal.freedesktop.org/releases/PolicyKit/1.0/config.dtd">

<!-- See the manual page PolicyKit.conf(5) for file format -->

<config version="0.1">
    <match user="root">
        <return result="yes"/>
    </match>
    <define_admin_auth group="admin"/>
</config>[CODE]
```[/CODE]


just like i thought it's matched to root.

make it like this:

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- XML -*- -->

<!DOCTYPE pkconfig PUBLIC "-//freedesktop//DTD PolicyKit Configuration 1.0//EN"
"http://hal.freedesktop.org/releases/PolicyKit/1.0/config.dtd">

<!-- See the manual page PolicyKit.conf(5) for file format -->

<config version="0.1">
    <match user="root">
        <return result="yes"/>
    </match>
    <define_admin_auth group="admin"/>
    **<return result="yes"/>**
</config>
```

---

### Post by iDaft on 2009-05-17
Awesome, it worked, thanks so much.
Also for other people who have this problem. I added that line kerry_s said then enabled gdm, then removed the line. With that line added in, everything is unlocked without a password, but with gdm enabled again I could remove the line and the unlock button came back.

---

### Post by kerry_s on 2009-05-17
> **iDaft said:**
> Awesome, it worked, thanks so much.
Also for other people who have this problem. I added that line kerry_s said then enabled gdm, then removed the line. With that line added in, everything is unlocked without a password, but with gdm enabled again I could remove the line and the unlock button came back.

congrats, i told you bypass. 
your lucky i even came across that problem and worked around it.

i'm using debian xfce4 now and policykit.conf was just empty, so i just added that just incase, cause i plan on running mixed gnome & kde programs, don't want to deal with that again down the line.

is your mount okay now?

---

### Post by iDaft on 2009-05-17
Yep mounting works just fine now, thanks again:D

---

### Post by helix2301 on 2009-08-03
sweet this worked for me to man I had the same issue.
thanks a lot.

---

### Post by evdv on 2009-08-21
Thanks a lot, you nailed it!
This avoided a lot of misery.

evdv

---

### Post by youcanlinux on 2009-08-23
Editing PolicyKit.conf didn't allow me to change services, but this did the trick...
$ su -c services-admin

---

### Post by lns on 2009-09-24
***** BIG FAT WARNING *****

DO NOT DO THIS IF YOU EXPECT ANY USER SECURITY!!! The "fix" described above (blindly putting <return result="yes"/> in /etc/PolicyKit/PolicyKit.conf) will allow ANY USER to start/stop services.

THIS IS BAD ON MULTI-USER SYSTEMS!! I am sure there is a cleaner fix for this. Please do not advocate bypassing security for functionality.

---

### Post by lns on 2009-09-24
To *safely* work around this issue, please do the following:

```
sudo polkit-action --set-defaults-any org.freedesktop.systemtoolsbackends.set auth_admin
```

This will require authentication of a user of the 'admin' group to use the "unlock" button of Services specifically instead of blindly granting authentication for EVERY policykit action for EVERY user without asking for ANY credentials. 

Please note that you can use this command for other things as well, such as users-admin (which probably experiences the same issue if you're not logged onto the system console itself, such as if you're logged in via remote X, SSH, VNC, or an LTSP client). All you have to do is find the action identifier. For users-admin, it's "org.freedesktop.systemtoolsbackends.self.set".

---

### Post by highlander2 on 2009-10-24
Now I have upgraded to Karmic Koala and can't make "unlock " button enabled by editing /etc/PolicyKit/PolicKit.conf" simply because " Policy Kit" is deprecated in 9.10.  How to enable "unlock" button by default ? It is so annoying to enter my password every time, and I don't need that level of security for my notebook.

---

### Post by nik_nah on 2009-11-27
I've tried adding
    <return result="yes"/>

and...

sudo polkit-action --set-defaults-any org.freedesktop.systemtoolsbackends.self.set auth_admin


My "unlock" button in users-admin is still grey.

I'm logging in via vnc.

Thank god for command line.

:frown:

---

### Post by Bealer on 2009-12-26
I've started getting this issue, and have tried all of the above suggestions but not had any luck.

I'm running a completely fresh install of 9.10. It's another frustrating regression bug that always seem to slip in after a release.

---

