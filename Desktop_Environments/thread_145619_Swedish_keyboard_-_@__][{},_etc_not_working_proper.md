---
title: "Swedish keyboard - @ | ][{}, etc not working properly"
date: 2006-03-16
forum: Desktop Environments
---

### Post by obli on 2006-03-16
I'm unable to type some symbols on my Swedish keyboard, back in windows (or any other distro, for that matter), pressing leftCtrl+leftAlt+2 would for example produce an @. This combination was interchangeable with RightAlt (also known as AltGr)+2.

this goes for many other symbols, like {][}|\£$€~¶

On Breezy badger, however, only the latter (Right alt) will work, which is rather annoying, considering I've spent years typing away with the ctrl-alt-(key) combinations, so re-learning is hardly an option.

And just to answer the question before it arises; I haven't got an English keyboard installed, look: åäö!

---

### Post by ububaba on 2006-04-09
[QUOTE=obli]I'm unable to type some symbols on my Swedish keyboard, back in windows (or any other distro, for that matter), pressing leftCtrl+leftAlt+2 would for example produce an @. This combination was interchangeable with RightAlt (also known as AltGr)+2.

this goes for many other symbols, like {][}|\£$€~¶

On Breezy badger, however, only the latter (Right alt) will work, which is rather annoying, considering I've spent years typing away with the ctrl-alt-(key) combinations, so re-learning is hardly an option.

And just to answer the question before it arises; I haven't got an English keyboard installed, look: åäö![/QUOTE]
Is it silly to ask whether in your /etc/X11/xorg.conf does it look like:

[COLOR="RoyalBlue"]
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "**se**"
EndSection
[/COLOR]

---

### Post by Titorelli on 2006-04-25
Im writing in Swedish because I'm a bit tired... Sorry!

Jag hade samma problem tills nyligen. För mig fungerande heller inte vänster- och högerpiltangenterna! Du löser problemet (i "tangentbord) genom att ställa in att metatangenten inte ska vara mappad till båda windowsknapparna utan bara den vänstra. Andra problem med tangentbordet brukar bero på konflikter vid tangentbordsgenvägar. Hoppas du fixar det.

---

### Post by Jeff_forssell on 2006-06-19
Det funkade för mig. Efter att ha kollat xorg.conf (som var rätt) provade jag system> inställningar> tangentbordsinställningar  flik "layout alternativ"
Alt-Win tangent beteende
o Meta mappad till vänster Win-tangent
stäng

Funkar direkt utan omstart, även piltangenter i terminal.

(Kör Ubuntu 5.10)

---

