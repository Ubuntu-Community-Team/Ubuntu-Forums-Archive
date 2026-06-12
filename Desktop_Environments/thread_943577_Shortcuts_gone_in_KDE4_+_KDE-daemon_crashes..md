---
title: "Shortcuts gone in KDE4? + KDE-daemon crashes."
date: 2008-10-10
forum: Desktop Environments
---

### Post by ProbablyX on 2008-10-10
Hello!

All of my desktop shortcuts seem to have stopped working, for instance I cant alt+f4 to close programs!

Also when I start up the KDE daemon "kded4" crashes (I get a message about it). I cant launch programs with shortcuts either, like F12 for yakuake; and I cant alt+tab!

Any ideas what might cause this?

Thanks!

PS: If I start "kded4" from a terminal I get this, though this comes up (and causes the kaded4 to quit) only after I press Ctrl+tab:

> kded(13200) Solid::Control::ManagerBasePrivate::loadBackend: Backend loaded:  "Nätverkshantering"
ASSERT: "d->keyToAction.value(key) == ad" in file /build/buildd/kde4libs-4.1.2/kdeui/shortcuts/kdedglobalaccel.cpp, line 412
KCrash: crashing... crashRecursionCounter = 2
KCrash: Application Name = kded4 path = <unknown> pid = 13200
sock_file=/home/bjorn/.kde4/socket-bjorns-dator/kdeinit4__0
kded(13199): Communication problem with  "kded" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)"

kded(13206) Solid::Control::ManagerBasePrivate::loadBackend: Backend loaded:  "Nätverkshantering"
ASSERT: "d->keyToAction.value(key) == ad" in file /build/buildd/kde4libs-4.1.2/kdeui/shortcuts/kdedglobalaccel.cpp, line 412
kded(13204): Communication problem with  "kded" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.ServiceUnknown" : " "The name org.kde.kded was not provided by any .service files" "


the "Nätverkshantering" part means Network management above.

Thanks

---

### Post by GeneralZod on 2008-10-10
This is a very severe bug that managed to creep in to 4.1.2:

[https://bugs.kde.org/show_bug.cgi?id=171870](https://bugs.kde.org/show_bug.cgi?id=171870)

It's been (retroactively!) marked as a showstopper for 4.1.2 and David Faure has called for an early 4.1.3 release for it.  In the meantime, distros will hopefully patch it themselves and offer updates.

---

### Post by lodp on 2008-10-13
I'm also missing some of my keyboard shortcuts (Ctrl+K for starting Konsole hurts the most). I tried re-assigning the shortcut via kmenuedit (which incidentally can't be started by right-clicking the respective kmenu item), and in the system settings (both thru Keyboard&Mouse as well as Advanced> Input Actions.

So .. since this has been recognized as a major thing -- can we expect a quick fix for this? what do you think?

---

### Post by GeneralZod on 2008-10-13
> **lodp said:**
> I'm also missing some of my keyboard shortcuts (Ctrl+K for starting Konsole hurts the most). I tried re-assigning the shortcut via kmenuedit (which incidentally can't be started by right-clicking the respective kmenu item), and in the system settings (both thru Keyboard&Mouse as well as Advanced> Input Actions.

So .. since this has been recognized as a major thing -- can we expect a quick fix for this? what do you think?

The "launch apps with a shortcut" feature is fixed in trunk, but I'd be fairly surprised if it were backported - the whole "shortcuts" portion of KDE4 seems to be pretty hairy :/

---

### Post by ProbablyX on 2008-10-17
The deal is simple - DONT USE AMAROK!

If you stop amarok, and run "kded4" or just avoid starting it at boot, the errors disapperar :)

---

### Post by lodp on 2008-10-17
i don't use amarok at all, but i still can't start apps with a keyboard shortcut..

---

### Post by JulianLx on 2008-10-20
> **ProbablyX said:**
> The deal is simple - DONT USE AMAROK!

If you stop amarok, and run "kded4" or just avoid starting it at boot, the errors disapperar :)

I also had porblems with KDE-daemon and it did the job for me.

Thanks!!

Julian

---

### Post by tarahmarie on 2008-10-21
I have the exact same problem.  I also start Amarok at startup.  This is a big problem.

---

### Post by pebo on 2008-10-21
> There have been a few users reporting that kded4 crashes when starting
Amarok 2. This is caused by conflicting global shortcuts with the same
shortcut sequence, and has been fixed in KDE 4 trunk

there is a fix for this here:
[http://lists.kde.org/?l=amarok&m=122312836413611&w=2]("http://lists.kde.org/?l=amarok&m=122312836413611&w=2")
at least it worked for me...

---

### Post by tarahmarie on 2008-10-23
Pebo's fix worked like a charm.

---

### Post by zenith001 on 2008-10-23
[Crusher](http://www.crusher.south.am)[Jaw Crusher](http://www.crusher.south.am/Crushing-Equipment/Crusher/Jaw-Crusher/Jaw-Crusher.html)[Cone Crusher](http://www.crusher.south.am/Crushing-Equipment/Crusher/Cone-Crusher/Cone-Crusher.html)[Cone Crusher](http://www.crusher.south.am/Crushing-Equipment/Crusher/HPC-Cone-Crusher/HPC-Cone-Crusher.html)[Impact Crusher](http://www.crusher.south.am/Crushing-Equipment/Crusher/Impact-Crusher/Impact-Crusher.html)

---

### Post by ksamanta on 2008-10-31
I upgraded to Intrepid yesterday and my KDE 3.5.9 was replaced by 4.1.2. It looks very shiny, but where are my custom keybindings??? I checked in the launcher that all the custom shortcuts are there in the menu editor, but they just don't seem to work. I have both kded and kded4 running. I have amarok installed but it does not set to run at startup. Any help will be greatly appreciated. Thanks!

PS: I had to restart the kded4 in order to get rid of irritating screen flickering (after restarting kded4, the flickering was gone!).The original (not custom) keybindings, e.g. Alt+F2, Alt+F4, etc still work.

---

