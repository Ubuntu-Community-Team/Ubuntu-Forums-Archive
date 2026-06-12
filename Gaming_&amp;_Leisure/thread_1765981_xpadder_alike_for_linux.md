---
title: "xpadder alike for linux??"
date: 2011-05-23
forum: Gaming &amp; Leisure
---

### Post by WiKiDCLown456 on 2011-05-23
so im new to ubuntu and the linux world(was pc) and i use to use a program most of yous know of called xpadder to map my controller keys to sim the keyboard or mouse for games that have lil or no gamepad support(game im playing has no gamepad support) and ive tryed installing xpadder useing wine gives me error that it cannot take priority over my controller and shows the searching for controller sign and after looking around for a linux i found qjoypad and downloaded it ...couldnt get it to install and seems it is really old (b4 ubuntu 6.06 from what ive found) so is there any more up tp date programes i can use for linux

---

### Post by thatguruguy on 2011-05-23
Get [qjoypad from www.playdeb.net]("http://www.playdeb.net/updates/ubuntu/11.04/?q=qjoypad").

---

### Post by WiKiDCLown456 on 2011-05-23
> **thatguruguy said:**
> Get [qjoypad from www.playdeb.net]("http://www.playdeb.net/updates/ubuntu/11.04/?q=qjoypad").

i click install now and it opens my software centre and seys not found could not find package "QjoyPad"in your current sofwear sources and i did install the deb package

---

### Post by thatguruguy on 2011-05-23
> **WiKiDCLown456 said:**
> i click install now and it opens my software centre and seys not found could not find package "QjoyPad"in your current sofwear sources and i did install the deb package

That's because you have to set up the playdeb repository.  

Did you see on the page I linked where it said:
**[Click here to learn how to install games from PlayDeb]("http://www.playdeb.net/updates/ubuntu/11.04/?q=qjoypad#how_to_install")**?

You need to click on that link to learn how to install games (and utilities, like qjoypad) from playdeb.

---

### Post by WiKiDCLown456 on 2011-05-23
> **thatguruguy said:**
> That's because you have to set up the playdeb repository.  

Did you see on the page I linked where it said:
**[Click here to learn how to install games from PlayDeb]("http://www.playdeb.net/updates/ubuntu/11.04/?q=qjoypad#how_to_install")**?

You need to click on that link to learn how to install games (and utilities, like qjoypad) from playdeb.

o ok i see what i did wrong i only installed the package when i seen it sead or config it manually i thought it was option 2 not step 2 will give it a try

---

### Post by WiKiDCLown456 on 2011-05-23
awesome got it to work thanks for all your help this was a fast and easy way to install the program that its self is very easy to use

---

### Post by thatguruguy on 2011-05-24
NOTE: This was addressed in some private messages between the OP and myself.  QJoyPad runs, by default, in the systray.  There is, of course, no systray in Natty.  To get around this problem, run QJoyPad with the following command from the terminal, if you want to access the gui:
```
qjoypad --notray
```

---

### Post by Geezanansa on 2011-10-19
Big THX thatguruguy ```
qjoypad --notray
``` allowed me to configure then use qjoypad whereas previous running qjoypad meant little more than an icon up in top right corner of screen with broken/unusable menu.(on Oneiric)  

When I run qjoypad from terminal i get this > (qjoypad:5175): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",It still does run and as mentioned earlier the --notray allows configuration.

YKWTNQI... Any pointers how to fix Gtk-WARNING?


Have used qjoypad on natty n maverick before that with no probs so know that it worth a bit of effort this time round after just updating to oneiric which is going well if a bit buggy (finding updates fixing things pretty quickly though)DS3 controller is last hardware installation for everything i want or need right now so it a bonus i am this far on.

---

