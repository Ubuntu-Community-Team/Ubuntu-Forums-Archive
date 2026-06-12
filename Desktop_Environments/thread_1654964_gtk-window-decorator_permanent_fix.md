---
title: "gtk-window-decorator permanent fix?"
date: 2010-12-29
forum: Desktop Environments
---

### Post by mechanizedmedic on 2010-12-29
i turned on my computer today and POOF, no window decorations. :confused: i haven't changed ANY display/appearance settings since i installed 10.04 and did my initial setup over a month ago. now when i startup i have to "gtk-window-decorator --replace" in terminal and leave it open to have everything decorated. i had a similar problem when i used compiz but i haven't installed anything other than the nvidia driver this time.

is there a way to find out what caused this and correct it? if not am i stuck with some sort of autostart launcher?

---

### Post by mcduck on 2010-12-29
So are you now using Compiz or not? ..or actually that's a stupid question, since gnome-window-decorator is a Compiz plugin and doesn't even work without Compiz... :D

Anyway, open CompizConfig Settings Manager (install it if you haven't got it already), go to Window Decoration-plugin's settings and make sure the "Command"-filed is set to "/usr/bin/compiz-decorator".

---

### Post by mechanizedmedic on 2010-12-29
> **mechanizedmedic said:**
> i had a similar problem when i used compiz but i haven't installed anything other than the nvidia driver this time.

i'm trying to avoid compiz... as much as is possible, i want to use what comes with ubuntu upon install.

---

### Post by kellemes on 2010-12-29
metacity --replace &

---

### Post by mcduck on 2010-12-29
> **mechanizedmedic said:**
> i'm trying to avoid compiz... as much as is possible, i want to use what comes with ubuntu upon install.

Compiz and Metacity are both included in the default install.

If you use visual effects you are using Compiz, if you turn them off you are using Metacity.

---

### Post by mechanizedmedic on 2010-12-29
...i was just coming back to call myself an idiot...

is this issue a gconf setting that i can fix?

also, can i remove compiz and just use metacity like i was before this occured?

---

### Post by kellemes on 2010-12-29
> **mechanizedmedic said:**
> ...i was just coming back to call myself an idiot...

is this issue a gconf setting that i can fix?

also, can i remove compiz and just use metacity like i was before this occured?

gconf-editor
desktop -> gnome -> session -> required-components -> windowmanager = metacity

---

### Post by mcduck on 2010-12-29
The first thing you should try is setting the visual effects to "none" in System/Preferences/Appearance. That really should switch you to Metacity.

If it doesn't work, for some strange reason I can't think of, you can force Gnome to use Metacity by changing the */desktop/gnome/session/required_components/windowmanager* key to "/usr/bin/metacity" in gconf-editor.

---

### Post by mechanizedmedic on 2010-12-29
> **kellemes said:**
> gconf-editor
desktop -> gnome -> session -> required-components -> windowmanager = metacity
this is what gconf-editor already shows.

> **mcduck said:**
> The first thing you should try is setting the visual effects to "none" in System/Preferences/Appearance. That really should switch you to Metacity.

If it doesn't work, for some strange reason I can't think of, you can force Gnome to use Metacity by changing the */desktop/gnome/session/required_components/windowmanager* key to "/usr/bin/metacity" in gconf-editor.
aside from gtk-window-decorator --replace i haven't used compiz. when i installed 10.04 i enabled the proprietary nvidia driver but left visual effects "none". i double checked and it's still set to none.

changed the gconf entry to /usr/bin/metacity and nothing changed, even after a restart.:confused:

---

### Post by mechanizedmedic on 2010-12-30
i tried switching to compiz with the full settings manager and fusion icon. the only way i can get it to work on startup is with the autostart command "fusion-icon --force-compiz"

...this is not at all what i wanted to end up with but until i get a real fix this will have to do. if anyone has any ideas please help! i would much rather keep things simple with metacity.

---

### Post by mcduck on 2010-12-30
> **mechanizedmedic said:**
> this is what gconf-editor already shows.


aside from gtk-window-decorator --replace i haven't used compiz. when i installed 10.04 i enabled the proprietary nvidia driver but left visual effects "none". i double checked and it's still set to none.

changed the gconf entry to /usr/bin/metacity and nothing changed, even after a restart.:confused:

Well, like I said, gtk-window-decorator is not a window manager, it's a Compiz decoration plugin so running "gtk-window-decorator --replace" would immediately switch you to using Compiz as your window manager (and load all confgured Compiz plugins as well, of course). 

What happens if you open a terminal and run "metacity --replace"?

---

### Post by mechanizedmedic on 2010-12-30
understood... everything works IF i use the terminal, fusion icon, or visual effects options to activate them. none of these changes survive reboot. (aside from forcing with an autostart entry)

i'm thinking that i have something wrong other than settings, either hardware or one of the many bugs in 10.04... i've had a couple of rare freeze ups in the last few months since i upgraded/reinstalled. ever since this decorator thing started last night it's been freezing every few hours. seems video related because the screen goes all wacky. <--that's a technical term!

are there any log files that i can check to verify my hunch?

---

### Post by mcduck on 2010-12-30
I'd check the ~/.xsession-errors first, and then perhaps /var/log/Xorg.0.log.

Of course syslog and messages might have something as well, if it's a driver issue. (both are in /var/log/)

---

### Post by mechanizedmedic on 2011-01-01
thanks for your help mcduck! i never ended up figuring out the cause but i learned that kubuntu is the desktop for me! :D

---

### Post by a-user on 2011-01-02
the reason was you doing stuff without the knowledge what you were doing: "gtk-window-decorator --replace"

if you continue like that you will get problems with kubuntu too.

there is no os that you cant **** up if you enforce commands that when you don't really know what you are doing.

---

