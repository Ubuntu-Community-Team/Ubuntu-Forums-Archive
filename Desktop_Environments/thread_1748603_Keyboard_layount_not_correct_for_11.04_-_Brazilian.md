---
title: "Keyboard layount not correct for 11.04 - Brazilian Portuguese"
date: 2011-05-03
forum: Desktop Environments
---

### Post by ispmarin on 2011-05-03
Hello all,

Im back to 2004. The keyboard layout for Brazilian Portuguese and a US keyboard is not working whatsoever in KDE 4.6 and Kubuntu 11.04. Apostrofe plus c should give cedilla, and now is not giving anything. Tried to change everything possible:

1) Language is set to Portuguese Brazilian in System Settings.
2) locale: pt_BR.UTF-8
3) env | grep LANG: LANG=pt_BR.UTF-8
LANGUAGE=pt_BR
4) Keyboard Layout: doesnt matter the one I try to use, no change.

What can I do? I just installed kubuntu from debian cause debian was giving too much trouble...:(


EDIT: Checking with my old debian installation, I changed the file /etc/default/keyboard field
XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT="alt-intl"
XKBOPTIONS=""

to 

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT="intl"
XKBOPTIONS=""

Will check to see if it's working.


Thanks

EDIT 2:
Inside Google Chrome, Firefox, Eclipse, the cedilla works fine: ç. But inside any KDE program I get the weird &#263;, that is completely wrong in Portuguese.

EDIT 3:
created a new user and tested it. The language is set correctly - Brazilian Portuguese - But the keyboard still gives the wrong cedilla character. 

PLEASE HELP!

---

### Post by Irish_canon on 2011-06-01
I have a simular problem as above the problem I have is that I am running kubuntu 11.04 and using a logitech mx5500 keyboard. The issue is the the "@" and the "/" do not work.

---

### Post by ispmarin on 2011-06-01
Interestingly enough, if you install Ubuntu and then install KDE via apt-get the keyboard layout is correct. Must be something especific for the Kubuntu version.

In the end I got so frustrated with the "Ubuntu way" - upstart, pulseaudio, keyboard and localization problems, etc - that I got back to Debian Sid.

---

