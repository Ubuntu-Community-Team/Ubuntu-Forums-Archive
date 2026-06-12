---
title: "XFCE cannot manage Desktop"
date: 2006-08-14
forum: Desktop Environments
---

### Post by ali_baba_69 on 2006-08-14
Hi there,

I have a german version of xubuntu (latest version installed), hopefully I can translate correctly..

The problem is, that everytime I logon using an xfce session, I have to go to Settings -> "Desktop Preferences" and set the option "Let XFCE manage the desktop".

It worked fine until I did anything I can't remember but certainly not concerning xfce..

The option for saving my session is always set and everything is restored after login, except xfce managing my desktop - I get the standard gnome style.

I'm new to Linux and ubuntu, so I have no idea.. ;)

Cheers!

---

### Post by earobinson on 2006-08-14
is xubuntu-desktop installed?

---

### Post by ali_baba_69 on 2006-08-14
Yes.

It's strange, because everything worked fine until one day... ;)

I set the option to have xfce manage my desktop, but it's not restored after I login again.

---

### Post by dolby on 2006-08-15
do u "save session for futures logins" when logging out?

---

### Post by brechacik on 2006-08-15
i believe i got the same problem: i have xubuntu (xfce) as default,   with the xubuntu desktop (with xfce - rodent icons on it), xfce's bars, menus and all... than i started playing a little gnome applications, i think i had even opened the kde-settings... think is now when i run xfce, i have xfce menus and bars but gnome desktop, with gnome icons and the right mouseclick on the desktop works like in gnome (ubuntu)... the 'let xfce manage your desktop' option doesn't help...  (got the feeling that xinitrc got something with it...)

---

### Post by ali_baba_69 on 2006-08-15
I do "save session for futures logins", but no effect - Everything is restored except xfce managing my desktop. :(

---

### Post by ali_baba_69 on 2006-08-17
no ideas anyone...?

---

### Post by Ziox on 2006-08-17
> **ali_baba_69 said:**
> no ideas anyone...?

I have Xubuntu running as well, and it is working perfectly well so...

open terminal and see if this command has any effect:

xfdesktop

---

### Post by brechacik on 2006-08-17
i copyed /etc/X11/xinit/xinitrc to ~/.config/xfce4/xinitrc, commnented everything out, and added: 
exec xfwm4 &
exec xfce4-panel &
xfdesktop

it kinda works (at least for me), but it's a little owkvard... got to logout by killall xfdesktop and change the keyboard-layout by setxkbmap...

---

### Post by ali_baba_69 on 2006-08-20
I tried this, but all settings seem to be gone after that, logout button wants to shut down xfce panel, ...

Typing xfdesktop doesn't help for retrieving xfce desktop after login.

Seems I have to stick with M$... ](*,) 

> **brechacik said:**
> i copyed /etc/X11/xinit/xinitrc to ~/.config/xfce4/xinitrc, commnented everything out, and added: 
exec xfwm4 &
exec xfce4-panel &
xfdesktop

it kinda works (at least for me), but it's a little owkvard... got to logout by killall xfdesktop and change the keyboard-layout by setxkbmap...

---

### Post by dolby on 2006-08-20
since u r using xubuntu & not just xfce with a gnome or kde previously installed u might wanna try the 6.06 and not the 6.06.1 cd installation. just a guess cause i havent tried 6.06.1 but there might be something wrong with it. ive never experienced such problems. ~80 of updates will require downloading afterwards

---

### Post by Ziox on 2006-08-20
> **ali_baba_69 said:**
> I tried this, but all settings seem to be gone after that, logout button wants to shut down xfce panel, ...

Typing xfdesktop doesn't help for retrieving xfce desktop after login.

Seems I have to stick with M$... ](*,)

Make sure you save your session before log out, that way, xfdesktop will always start after login...

---

### Post by argotnaut on 2006-10-14
Note that the original poster IS saving sessions, but still having the problem.

Same problem for me. 

I'm using the German version too -- maybe I'll switch back to English and see what happens.

---

### Post by argotnaut on 2006-10-14
Okay, this is what worked for me. Temporarily, at least -- we'll see if it sticks.

**I'm using the German locale so menu and dialogue text might not be exact.**

[LIST=1]
[*]In the XFCE session manager (Settings > XFCE4 Session and Startup Settings), check the box that says "Show session selection at startup."

[*]Log out and log back in.

[*]Click 'New Session' when the session selector appears, and name it whatever you want.

[*]The next time you log in, select the session you created in the previous step. XFCE should be managing the desktop right at startup, with no need to re-check the "Allow XFCE to manage desktop" box.
[/LIST]

---

