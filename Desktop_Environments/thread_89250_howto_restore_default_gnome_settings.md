---
title: "howto restore default gnome settings?"
date: 2005-11-12
forum: Desktop Environments
---

### Post by lizardking on 2005-11-12
I noticed that gnome is beavhing in a strange way.I installed a lot of program ok (xfce,kde etc.) but i'm still using Gnome.
[B]The problem is that tht window are beavhing in a strange way:
[LIST]
[*]I move XMMS  only pressing ALT+I. And then the main window the playlist and equalizator don't stay togheter.
[*]The splashscreen programs like Eclispe or Anjuta are in the top left of the screen, and not in the center..
[/LIST][/B]
I thinking was a Metacity/Gnome problem....How can I do to restore default setting? I tried to reinstall nautlius and metacity and xmms but nothing..:confused: 
So I logged into root Desktop (never used) and I can confirm that his settings are default and Good! :KS 
How can do restore the settings like default in my super used normal user..?
bye and thnx

---

### Post by tseliot on 2005-11-12
Login as root and enter GNOME.

Create a new user:

select System/Administration/Users and Groups

Then select "Add User"

you can select your new username and password.

You might want ot click on your previous username and press "Properties" so as to see to copy the settings (user privileges, etc.). Make sure you use a different home directory (it should create it automatically).

Then you can move your files to your new home directory

---

### Post by lizardking on 2005-11-12
[QUOTE=tseliot]Login as root and enter GNOME.

Create a new user:

select System/Administration/Users and Groups

Then select "Add User"

you can select your new username and password.

You might want ot click on your previous username and press "Properties" so as to see to copy the settings (user privileges, etc.). Make sure you use a different home directory (it should create it automatically).

Then you can move your files to your new home directory[/QUOTE]

but without creating a new user?in other way?

---

### Post by Xian on 2005-11-12
[QUOTE=lizardking]but without creating a new user?in other way?[/QUOTE]
Ditch the hidden gnome user pref folders in your home directory.
When you log back into Gnome a new default set will be re-created.

The folders to remove are: .gconf, .gconfd, .gnome, .gnome2, etc.

You can also remove any of the application folders if you wish.
These might include .nautilus, .gdesklets, and so forth.

---

### Post by lizardking on 2005-11-13
[QUOTE=Xian]Ditch the hidden gnome user pref folders in your home directory.
When you log back into Gnome a new default set will be re-created.

The folders to remove are: .gconf, .gconfd, .gnome, .gnome2, etc.

You can also remove any of the application folders if you wish.
These might include .nautilus, .gdesklets, and so forth.[/QUOTE]
ok cool! thnak you very much..but what's the maeaning of ditch? remove?

---

### Post by mariosx on 2007-06-09
> **Xian said:**
> Ditch the hidden gnome user pref folders in your home directory.
When you log back into Gnome a new default set will be re-created.

The folders to remove are: .gconf, .gconfd, .gnome, .gnome2, etc.

You can also remove any of the application folders if you wish.
These might include .nautilus, .gdesklets, and so forth.

it's been 2 years since you did this post, but still... you have just saved an idiot (me) from a lot of trouble! :D

i removed the menu by mistake from the main panel :roll:

ditching the folders worked great ;) thx !

---

### Post by fakie_flip on 2007-06-26
Thanks. It worked for me too.

---

### Post by unprinted on 2008-05-04
Because this appears high up when doing searches for missing settings, I should add that if your gnome applications menu disappears, you want to delete .config/menus/applications.menu - mine had ended up as a zero byte file = no menu and System/Main Menu got very upset.

---

