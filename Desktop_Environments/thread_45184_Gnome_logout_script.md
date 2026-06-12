---
title: "Gnome logout script?"
date: 2005-06-29
forum: Desktop Environments
---

### Post by blixel on 2005-06-29
Is there a script that gnome can run when a user logs out?  I don't want a global logout script.  I want to unmount certain Samba shares when a user logs out.  I'm pretty sure I can use Desktop -> Preferences -> Sessions to create a script that will run when the user logs in ... to mount their personal shares.  But I don't see anything for when they log out.

Since the shares are different for each user, the script would need to be specific to each user on the system.

Or - If there's a better way to do it other than hacky shell scripts, I'd like to hear about it.

---

### Post by nocturn on 2005-06-29
[QUOTE=blixel]Is there a script that gnome can run when a user logs out?  I don't want a global logout script.  I want to unmount certain Samba shares when a user logs out.  I'm pretty sure I can use Desktop -> Preferences -> Sessions to create a script that will run when the user logs in ... to mount their personal shares.  But I don't see anything for when they log out.

Since the shares are different for each user, the script would need to be specific to each user on the system.

Or - If there's a better way to do it other than hacky shell scripts, I'd like to hear about it.[/QUOTE]

I have been looking arround for this to (CDE used to have.dtlogout).  No luck yet.
There is some hack by wrapping command arround gnome-session but I can't remember it exactly.

---

### Post by n888 on 2007-10-27
Anyone have an update for this?

> Or - If there's a better way to do it other than hacky shell scripts, I'd like to hear about it.

I'd be satisfied with a "hacky shell script" :)

---

### Post by JetPack on 2007-12-10
This thread may be well out of date but....

There is another thread that points to the location of the logout, shutdown, etc. scripts in Edgy:-

[http://ubuntuforums.org/showthread.php?t=471855&highlight=gnome+logout+script](http://ubuntuforums.org/showthread.php?t=471855&highlight=gnome+logout+script)

I haven't tried it but I will be looking at it this weekend as a possible solution to my scripting needs.

---

### Post by ziofil on 2008-02-09
i think the solution is to put the script you need to execute on logout  in ```
/etc/gdm/PostSession
```

---

