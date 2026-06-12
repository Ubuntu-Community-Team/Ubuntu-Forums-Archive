---
title: "no menus or bars ???"
date: 2011-10-02
forum: Desktop Environments
---

### Post by ikakok on 2011-10-02
i have 11.04 installed without problem for about 2 weeks now.
i changed something in compiz, (not sure what) and now when i started up the computer there is no menu on the left or the top. the desktop is still there and i can open folders form there, and open programs by open files eg:(i opened the web browser by creating a .htm file and opening it.
but program and menu short cuts are not working.

---

### Post by Copper Bezel on 2011-10-02
Here's [_an excellent troubleshooting guide_]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html") for that very issue - let us know if you hit a snag and need further help.

---

### Post by ikakok on 2011-10-02
that sorted it. thanks for that.

---

### Post by Copper Bezel on 2011-10-02
Sweet. = )

---

### Post by Nanoxt on 2011-10-03
Hi,

> **Copper Bezel said:**
> Here's [_an excellent troubleshooting guide_]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html") for that very issue - let us know if you hit a snag and need further help.

I tried this, but it didnt solve my problem.

I'm using 11.04 as "normal" ubuntu, not the unity version. When i start it, window manager is always metacity at first. I have compiz fusion icon, where i then select the window manager to be compiz. Then the upper bar in window disappear (if i have one open). all the menu effects work fine. When i press the "reload window manager" it reloads, except for the upper bars.

The thing is, compiz used to work just fine. This problem came to me when i tried to use 3d-cube-effect in my computer (samsung N120). It didnt work and the upper bars no longer showed up. As an old windows user, i tried to re-install compiz, but it didnt have any effect. 

Can anyone help me with this one?

---

### Post by Krytarik on 2011-10-03
> **Nanoxt said:**
> I have compiz fusion icon, where i then select the window manager to be compiz. Then the upper bar in window disappear (if i have one open). all the menu effects work fine. When i press the "reload window manager" it reloads, except for the upper bars.
Make sure the "Window Decoration" plugin is enabled in "CompizConfig Settings Manager", and the "Command" is set to "/usr/bin/compiz-decorator"; as also described in that guide.

Greetings.

---

### Post by Nanoxt on 2011-10-05
> **Krytarik said:**
> Make sure the "Window Decoration" plugin is enabled in "CompizConfig Settings Manager", and the "Command" is set to "/usr/bin/compiz-decorator".

Greetings.

THANK YOU. I think the biggest challenge with this one was Finnish language. 

case closed and so solved

---

### Post by Krytarik on 2011-10-05
> **Nanoxt said:**
> I think the biggest challenge with this one was Finnish language.
What exactly do you mean by that? :p

Btw., didn't mention that those instructions are also included in that guide you visited before, guess because I didn't want to send you to a guide again that is actually meant for Unity, not for classic Gnome. ;-)

---

