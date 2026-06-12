---
title: "How to - disable screen lock on resume from hibernate"
date: 2009-09-20
forum: Desktop Environments
---

### Post by realn on 2009-09-20
Hello all,

I have a problem which drives me crazy on a Kubuntu 8.04 box: if i go to "Log out - Hibernate" button, it hibernates OK.
 When I restart the computer - the screen is locked. PLEASE, PLEASE, PLEASE - can someone help me? It's very frustrating to still have this kid of issues after at least 3 years of Ubuntu.
 The only option I found in the GUIs regarding this is the "lock screen before suspend or stand by" in the KPowersave applet, in general settings. I checked/unchecked it so many times with no apparent effect.
I also like to say that if I hibernate through "sudo /etc/acpi/hibernate.sh" command, when I restart the computer the screen is not locked. I would like to use the "Log out" button from the menu. I would also like to know which are the scripts called by this button, cause I have no idea what happens when I click on "hibernate" - apparently not the same as "/etc/acpi/hibernate.sh". Please help me.
 Please also note - it is KUBUNTU, cause I found the same problem on ubuntu boxes, apparently fixed successfully.

Thanks a bunch!

---

### Post by krazyd on 2009-09-20
sounds like a bug in 8.04. it works correctly in 9.04 / KDE 4.3. probably due to the new powerdevil management applet.

---

### Post by realn on 2009-09-21
Thanks for the reply. Not necessarily a bug - it works OK on my laptop. 
Anyway, the question remains: how come that on a "hibernate.sh" command it works ok, but not when going through the logout menu/buttons? Where does this difference come from ?

 Thanks a lot!

---

### Post by realn on 2009-10-04
Could someone please help??

 Thanks a lot

---

### Post by realn on 2009-10-29
Bump, up, please help !

---

### Post by realn on 2010-02-17
PLEASE, Help

I still have the problem and it frustrates me at max. I did more digging, this is what I found:

1) the logout dialog box is controlled by a program called smserver

For instance if you change in ~/.kde3/share/config/ksmserverrc in section [General]

offerShutdown=true to false, the suspend/hibernate/logout options are not presented anymore

2) if I run /etc/acpi/sleep.sh --force OR suspend from kpowermanager, the resumed session is not locked

3) the only thing which now locks the session on resume is when I click "suspend" from KDE logout dialog

I found a workaround - apparently is /usr/bin/kdesktop_lock which is called. I renamed it and session no longer locks.
 I would still like to know exactly how and where and WHY this script is called. Maybe I should open a bug in lauchpad?

 PLEASE HELP
Thanks a lot

---

### Post by Zorael on 2010-02-17
Doesn't unchecking *Lock screen on resume* in System Settings -> Advanced tab -> Power Management -> General Settings -> Settings and Profile tab do the trick? It's not locking for me.

---

### Post by realn on 2010-02-18
Hey Zorael, thanks a lot for your quick reply.
 Unfortunately I don't have a Power management in the advanced tab - I use KDE3.5.10 on Kubuntu HH. You might be using KDE4, I suppose?
 I have unchecked lock screen in KPowerSave and, as I said, if I resume from kpowersave (right click -> suspend to RAM, everything is OK). It's only when I suspend from the logout dialog box that I have this problem.

Off-topic - I tried several times to take the jump to KDE4, but it seems it's a too big leap for me (I find it awkward, frustrating and amazingly poor designed - I'm talking here from the user point of view, technically it might be a gem, but a useless one, at least for me - ranting again, just sorry that on the eve of Kubuntu LL I'll have to switch back to HH - now I have a KK installation with KDE 3.5 which is quite unstable). Please note that my problem occurs on my server, which is a Kubuntu 8.04 release.

 Thanks, please note that the problem is still UNSOLVED.

---

