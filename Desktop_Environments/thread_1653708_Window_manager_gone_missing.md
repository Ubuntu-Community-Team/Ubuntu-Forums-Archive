---
title: "Window manager gone missing"
date: 2010-12-27
forum: Desktop Environments
---

### Post by frankzen on 2010-12-27
I recently installed then removed Compiz from my Maverick installation. A side effect has been for my window manager (Metacity) to disappear. I have re-installed Metacity but no change. If I run metacity ---replace from a terminal, the buttons re-appear, but disappear as soon as I close the terminal. I tried "metacity --replace &" but no change. 

What am I missing here ??

---

### Post by matt_symes on 2010-12-27
Hi

You can do it from the run dialog

ALT + F2 to display run dialog.

```
metacity --replace
```

From the terminal type (It should work)

```
nohup metacity --replace &
```

You also might want to add it to start up items.

System->Preferences->Startup Applications

Kind regards

---

### Post by mcduck on 2010-12-27
> **frankzen said:**
> I recently installed then removed Compiz from my Maverick installation. A side effect has been for my window manager (Metacity) to disappear. I have re-installed Metacity but no change. If I run metacity ---replace from a terminal, the buttons re-appear, but disappear as soon as I close the terminal. I tried "metacity --replace &" but no change. 

What am I missing here ??
Well, you removed Compiz but didn't switch the default window manager to Metacity.

(in case you didn't know, if you have visual effects enabled you are using Compiz. not Metacity. It's just configured to use Metacity's themes.)

Go to System/Preferences/Appearance, and on the Visual Effects-tab make sure it's set to "None". (The options there switch between Metacity and two different pre-configured Compiz setups).

If that doesn't work, then Hit Alt-F2 and launch *gconf-editor*, browse to desktop/gnome/session/required_components and change the "windowmanager"-key's value to "/usr/bin/metacity".

---

### Post by frankzen on 2010-12-27
> **mcduck said:**
> Well, you removed Compiz but didn't switch the default window manager to Metacity.

(in case you didn't know, if you have visual effects enabled you are using Compiz. not Metacity. It's just configured to use Metacity's themes.)

Go to System/Preferences/Appearance, and on the Visual Effects-tab make sure it's set to "None". (The options there switch between Metacity and two different pre-configured Compiz setups).

If that doesn't work, then Hit Alt-F2 and launch *gconf-editor*, browse to desktop/gnome/session/required_components and change the "windowmanager"-key's value to "/usr/bin/metacity".

Well the visual effects were already set to none, but you were right, the window manager was still set to Compiz in gconf. Changed it to metacity and the fix was instant.
Thanks very much.
:D

Why didn't removing Compiz do what it should have done ??? Bug???

---

### Post by mcduck on 2010-12-27
> **frankzen said:**
> Well the visual effects were already set to none, but you were right, the window manager was still set to Compiz in gconf. Changed it to metacity and the fix was instant.
Thanks very much.
:D

Why didn't removing Compiz do what it should have done ??? Bug???

No, not a bug.

The setting belongs to your user, and removing (or updating) packages will never, ever touch user's own configuration files.

(Imagine the fun if, on a multi-user setup, the admin had to remove Firefox to get a new version installed, and that would cause every user to loose all their bookmarks, settings and extensions. Or similar situation with an e-mail application or something...)

---

### Post by frankzen on 2010-12-27
> **mcduck said:**
> No, not a bug.

The setting belongs to your user, and removing (or updating) packages will never, ever touch user's own configuration files.

(Imagine the fun if, on a multi-user setup, the admin had to remove Firefox to get a new version installed, and that would cause every user to loose all their bookmarks, settings and extensions. Or similar situation with an e-mail application or something...)

Well I sort of agree, but when I installed Compiz, I had to do very little to get screen effects. and at no point was I warned the window manager was now Compiz. Although my common sense should have told me that.:confused:

---

### Post by mcduck on 2010-12-27
Is it a fresh install of Ubuntu 10.10 or upgraded from some previous version?

I just started thinking that you actually mentioned the windowmanager key was set to "compiz", while on default 10.10 setup it's actually "gnome-wm". Which is a script that should automatically switch you to Metacity if Compiz is unavailable...

I definitely see your point about how it should tell the user somehow that it's switching to another windowmanager. But on the other hand that would easily confuse many new users ("What is Compiz? What is a windowmanager?"). But perhaps with a carefully chosen words...

---

### Post by frankzen on 2010-12-28
> **mcduck said:**
> Is it a fresh install of Ubuntu 10.10 or upgraded from some previous version?

I just started thinking that you actually mentioned the windowmanager key was set to "compiz", while on default 10.10 setup it's actually "gnome-wm". Which is a script that should automatically switch you to Metacity if Compiz is unavailable...

I definitely see your point about how it should tell the user somehow that it's switching to another windowmanager. But on the other hand that would easily confuse many new users ("What is Compiz? What is a windowmanager?"). But perhaps with a carefully chosen words...

It's an upgrade from Lucid - yes the key was set to compiz not to gnome-wm. Strange but true.
Anyway it's resolved now and I thank you again. It had me baffled and I've run Linux for years now.:frown:

---

