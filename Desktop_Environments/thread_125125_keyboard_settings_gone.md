---
title: "keyboard settings gone"
date: 2006-02-03
forum: Desktop Environments
---

### Post by JvdS45 on 2006-02-03
after upgrade kde 3.5.to 3.51 I can' t set my keyboard al these settings I had before are gone. Even the the screen of keyboard settings all keyboard models are gone
so "e I meen above the e is not possible now :| so I need that quick because i need to write a lot i use this pc in office as well

I wonder who can help me with that

yours

Johan

---

### Post by Heliix on 2006-02-03
hi johan
as root, edit your 
/etc/X11/xorg.conf
file, section "InputDevices", line "XkbLayout". try "us, nl" for US and Netherlands keyboard. you may also set a keyboard shortcut to toggle between these layouts.. "XkbOptions" "grp:alt_shift_toggle"
save, restart X. if gnome argues with you, use xwindow settings as default.
good luck, 
Heliix

---

### Post by 0xBulbizarre on 2006-02-03
The above mentionned fix is correct, but you also need to delete your ~/.kde/share/config/kxkbrc if it exists (do a backup of that file if you wish).

---

### Post by JvdS45 on 2006-02-03
[QUOTE=0xBulbizarre]The above mentionned fix is correct, but you also need to delete your ~/.kde/share/config/kxkbrc if it exists (do a backup of that file if you wish).[/QUOTE]


Both is still not working :|

I even changed XkbLayout "us_intl" 
all this is not working in kde

---

### Post by branco on 2006-02-03
> after upgrade kde 3.5.to 3.51 I can' t set my keyboard al these settings I had before are gone. Even the the screen of keyboard settings all keyboard models are gone

Hi, I've got the same problems. The layouts I had set up previously were all there in the system tray, but the configuration screen looks like the attached pic: all layouts and keyboard models are blank, and as soon as I hit Apply button, the 'Enable keyboard layouts' checkbox is unchecked automatically. The tray icon doesn't display any country names, and when I hit Apply for the first time the layout icon was gone and it never came back... :(

Anyways, this is not really KDE 3.5.1 related. I experienced this even before the update, but I kept the layout settings intact so I could use the settings I had from before... Now it's all gone, I'm afraid.

EDIT:
I also have this when I launch 'sudo kate' from Konsole (among numerous error messages):

skim: WARNING: KLocale: trying to look up "" in catalog. Fix the program

and in ~/.xsession-errors I have many lines of:

kio_http: WARNING: KLocale: trying to look up "" in catalog. Fix the program

I got this a lot when I tried to compile SCIM from source yesterday, too.

As far as I know, Klocale is supposed to be a library from translating strings into correct localized ones... But I think KDE 3.5.1 is broken in other places as well, so this may not be the issue. I think it's something to do with kde-core packages because I started experiencing problems after I installed it.

I'll try to remove it and see it works.

---

