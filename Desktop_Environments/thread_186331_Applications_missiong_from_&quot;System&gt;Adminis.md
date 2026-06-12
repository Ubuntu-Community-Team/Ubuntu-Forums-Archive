---
title: "Applications missiong from &quot;System&gt;Administration&quot; menu"
date: 2006-06-01
forum: Desktop Environments
---

### Post by caspian on 2006-06-01
When I go to System > Administration, some applications are missing, such as Synaptic, GDM config, Update notifier, etc.

So, I right-click on the menu (on the taskbar), click "Edit menus", and drill down to "System > Administration", and these applications *are selected*.

I tried deselecting and re-selecting them, and they still don't show up.

Is this a bug? Or is this user-ignorance? ;)

---

### Post by Rackerz on 2006-06-01
If you clicked 'Revert' then yes :D.

---

### Post by caspian on 2006-06-01
No, I haven't touched the revert button...

I tried deselecting all the applications that show up in the Administration menu, so the only ones that are selected are the ones that aren't showing up.

When I go to System>Administration, nothing's there.

I go back into "Edit Menu", the apps are still selected.

I don't know what I'm doing wrong...

---

### Post by cpapadopoulos on 2006-06-02
I had this problem when I installed gnome on a kubuntu install. I thought I just messed up when removing kde packages, waited till 1st June to see if the official release would fix this, but no luck. I just got a clean install of the new ver and still have the same problem. I'd really appreciate it if anyone posted any ideas what might be causing this.

Thanks!

Chris

---

### Post by Kza on 2006-09-14
Hi the same thing happened to me, after I accidentally removed myself from the admin group, (or whatever group it is that lets you sudo). I readded myself both to the group and the sudoers file, and now my System Administration menu contains the restricted list of programs that non-sudoers get.

Anyone know how to restore it?

---

### Post by tim-e on 2006-09-14
> **Kza said:**
> Hi the same thing happened to me, after I accidentally removed myself from the admin group, (or whatever group it is that lets you sudo). I readded myself both to the group and the sudoers file, and now my System Administration menu contains the restricted list of programs that non-sudoers get.

Anyone know how to restore it?I've done exactly the same thing. :(

---

### Post by Kza on 2006-09-15
Well it seemed to have sorted itself out now.. Now I get the full list, and I didnt even do anything.

---

### Post by Murwiz on 2006-09-25
I'm having a similar problem. At first I thought it was because my sysadmin friend had added me to the sudoers file explicitly, so I commented out my username from there. But after "update-menus", and logging out and in, and even restarting X, still nothing in the System|Administration menus except: 

Device Manager
Network Tools
Printing
System Log
System Monitor

Can anyone help? I'm mystified.

---

### Post by Murwiz on 2006-09-25
It was indeed that my account no longer belonged to "admin". I booted into recovery mode, did this:

```
$ adduser {myname} admin
```

and the menus were restored.

---

