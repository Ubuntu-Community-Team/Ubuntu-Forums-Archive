---
title: "numeric pad doesn't work"
date: 2005-08-09
forum: Desktop Environments
---

### Post by TreckNa on 2005-08-09
Hi

I installed Kubuntu 5.04 on a standard desktop PC with a 104 US Keyboard.
I have a problem with the numeric pad on the keyboard, it doesn't work
under KDE once logged. However the num pad works under console
or before logging, in the KDM login area.
Before posting here of course I tried to search. I installed also numlockx
and it turn-on the light, but won't solve my numpad issue.
The Return key is the only one that works. I tried another keyboard, same results. 
When I press NumLock, the LED turn on but there's no effect, I am
not able to type-in any digit. If I switch-off numlock, same effect.
I tried to change my keyboard layout with no success. 
KDE Setup Control shows me that I am using a generic-104 keyboard
with us_intl layout.
Here are more details:

Command "xprop -root | grep XKB" returns = 
_XKB_RULES_NAMES(STRING) = "xorg", "pc104", "us_intl", "basic", ""

And if I go to KDE Start Menu -> Control Center and then I select
"Regional & Accessibility" under Keyboard Layout I have:
     Keyboard Model -> Generic 104-key PC
     Active Layout  -> U.S English w/deadkeys (us_intl) 

It seems to match the content of xorg.conf.
I think it might be a KDE issue since in the console it works.
I don't have GNOME installed and don't want to test with it (Kubuntu) 

I also tried with a french and a standard us layout, same problem.
The numpad doesn't work
 
I haven't tried yet apt-get upgrade but I'll also try this.

If you can help... 
Thanks 

TreckNa

---

### Post by TreckNa on 2005-08-10
More details: 

I just installed GNOME with the following:
  sudo apt-get install ubuntu-desktop
  logout | end session
  Session or Session Type choose GNOME, then login.

And now my numpad works like a charm. So it's definitly a KDE problem...

My xorg.conf contains 
Section "InputDevice"
        Identifier      "Generic Keyboard"
        # Driver                "keyboard"
        Driver          "kbd"
        #Option         "CoreKeyboard"
        #Option         "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us-intl"
EndSection

I tried to switch from "keyboard" to "kbd" and to comment-out the XknRules
but it won't solve my KDE problem

I'll try later

 ](*,)

---

### Post by jeremy on 2005-08-10
In KDE don't use numlockx, rather set it in the Control Centre under 'Peripherals' -> 'Keyboard'.

---

### Post by jazzwhistle on 2006-01-27
I've got the same problem on KDE - can't get my number pad to do anything other than act as arrows, and I've got the same problem with Gnome  I've tried sudo kcontrol to change the setting, but no joy.

Any Ideas? 

Cheers,
Neil

kxkbrc file reads:

[Layout]
Additional=
EnableXkbOptions=true
Includes=
Layout=fr
Model=microsoftoffice
Options=
ResetOldOptions=false
ShowFlag=true
ShowSingle=false
StickySwitching=false
StickySwitchingDepth=1
SwitchMode=Global
Use=true
Variants=fr(basic)

---

### Post by jazzwhistle on 2006-01-27
Although I'd already seen this solution for Gnome, I never use it and didn't realize it would work for all X sessions, and thus for my KDE too.  Easily fixed with 

sudo apt-get install numlockx

Just in case I get shot down in flames for not searching the forums....

Cheers,
Neil

Happy convert from Mandrake to Kubuntu :)

---

### Post by marwich on 2008-05-06
Hi all
I got the same problem here. I'm using an Hardy Heron (8.04) with GNOME and I got the same problem. I tried changing layouts (I'm using a 104 USA keyboard with international layout), and also installing numlockx from apt, but nothing happens: my numpad doesn't work. Just the enter key does his job. Any idea?

---

### Post by purefan on 2008-05-09
Having the same problem in hardy heron.... installed numlockx and didnt help...

---

### Post by PixEye on 2008-05-19
> **purefan said:**
> Having the same problem in hardy heron.... installed numlockx and didnt help...Same problem here but under debian, Gnome 1:2.20.2.2 and with XOrg 1:7.3+10... :(

---

### Post by ClosAttack on 2008-05-19
Try this, in System > preferences > keyboard under the Mouse Keys tab uncheck the "Allow to control the pointer with keyboard"  I think thats the solution for those running 8.04.

---

### Post by CREEPING DEATH on 2008-05-19
> **ClosAttack said:**
> Try this, in System > preferences > keyboard under the Mouse Keys tab uncheck the "Allow to control the pointer with keyboard"  I think thats the solution for those running 8.04.

Thank you!  What a dumb default though...

CD

---

### Post by PixEye on 2008-05-21
> **ClosAttack said:**
> Try this, in System > preferences > keyboard under the Mouse Keys tab uncheck the "Allow to control the pointer with keyboard"  I think thats the solution for those running 8.04.
Works fine as well on debian, thanks a lot ClosAttack! :)

---

### Post by jessald on 2008-05-30
> "What a dumb default though..."

Seriously.  I've pounded on the numpad so many times trying to get it working, and not once did I notice it was moving the mouse.  I hope they set the default to the standard numpad behavior.

---

### Post by Evolution-06 on 2008-07-03
> **ClosAttack said:**
> Try this, in System > preferences > keyboard under the Mouse Keys tab uncheck the "Allow to control the pointer with keyboard"  I think thats the solution for those running 8.04.


worked like a charm! i bet vnc connect toggled it on or something!

---

### Post by tootlet on 2008-07-06
> **ClosAttack said:**
> Try this, in System > preferences > keyboard under the Mouse Keys tab uncheck the "Allow to control the pointer with keyboard"  I think thats the solution for those running 8.04.

Thanks, this worked for me and 8.04 using Gnome! 
Tom

---

### Post by emiliolopez on 2008-07-12
sorry, but i cant find:
[I]
 in System > preferences > keyboard under the Mouse Keys tab uncheck the "Allow to control the pointer with keyboard"[/I]

how can i do that?

---

