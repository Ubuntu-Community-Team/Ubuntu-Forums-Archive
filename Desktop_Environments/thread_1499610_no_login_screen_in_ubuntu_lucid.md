---
title: "no login screen in ubuntu lucid"
date: 2010-06-02
forum: Desktop Environments
---

### Post by sat.vivek on 2010-06-02
gdm starts...but login screen does not appear..cursor moves but no HDD activity also. can anyone help ???

---

### Post by Elie-M on 2010-06-04
well no one seems to have my problem.. my problem is kinda weird. the login screen appears most of the times normally, but the problem is that sometimes, IT IS THERE but not visible. I just enter my password and tap enter, and poof enter to the desktop normally. it's like an invisible screen, it is there I can enter my pass but I just cannot  see it. anyone?

---

### Post by Elie-M on 2010-06-19
bump

---

### Post by prylux on 2010-06-19
I don't know if these will help you but...

  You could go into recovery mode and see if "xfix" is available and run it
------------------------------------------------------------
You could see if you can set it up to automatically login

Try starting in the recovery mode by holding the shift key during startup.
Choose root not netroot
then:
[INDENT]cd /etc/gdm [Enter]
vi custom.conf [Enter]
[/INDENT]

then change
"AutomaticLoginenable=false"
to
"AutomaticLoginenable=true"

You do this by doing this:
[INDENT]Highlight the "f" in false and press [Shift+C] a "$" should appear at the end of the line "fals$"
Then type "true" and press [ENTER]
Then press [ESC]
Then [dd]
Then hold [Shift] and press [ZZ]
[/INDENT]

then reboot the system
------------------------------------------------------------
You could try to go in to recovery mode and choose "root"
and run

[INDENT]dpkg-reconfigure xserver-xorg[/INDENT]

In my opinion I'd try and auto login first then xfix then run dpkg

---

### Post by eddielad on 2010-06-25
Just a bit of support for the original post. I'm running Lucid on a Toshiba L450-18D and am having the same issue. It works most of the time but occasionally there is no login screen visible although I "think" I may have seen the screen flash up. Is it possible that it is actually hidden behind the background i.e. some sort of Z-coordinate error ? :confused:

I'm sure its just a cosmetic error but might annoying.

---

### Post by Elie-M on 2010-06-27
dude u didnt read my post I think. when that happens i want u to hit enter, and enter ur password and then hit enter, to see if u have the same issue as me. it must log u in even if u dont see the login screen

---

