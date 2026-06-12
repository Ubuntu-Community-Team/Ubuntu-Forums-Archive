---
title: "can't run Mir properly on ubuntu 13.04"
date: 2013-06-17
forum: Desktop Environments
---

### Post by 3wais on 2013-06-17
[COLOR=#333333][FONT=UbuntuRegular]I've recently tried to install Mir desktop on my ubuntu 13.04[/FONT]
[FONT=UbuntuRegular]I changed the /etc/lightdm/lightdm.conf to the following:[/FONT]

[FONT=UbuntuRegular]```

[SeatDefaults]
type=mir[/FONT]
[FONT=UbuntuRegular]#user-session=ubuntu[/FONT]
[FONT=UbuntuRegular]#greeter-session=unity-greeter[/FONT]
```

[FONT=UbuntuRegular]then I stop my lightdm and start it again. It does not open anything in tty7. just a blank black screen. I then tired startx instead of service lightdm start .. the gui started but with no launchers or menu or whatever. just the background.[/FONT]
[FONT=UbuntuRegular]My guessing is that commenting out the greeter-session line in lightdm.conf prevents lightdm from launching the start screen. so I changed the file to that:[/FONT]

[FONT=UbuntuRegular]```

[SeatDefaults][/FONT]
[FONT=UbuntuRegular]type=mir[/FONT]
[FONT=UbuntuRegular]#user-session=ubuntu[/FONT]
[FONT=UbuntuRegular]greeter-session=mir-greeter[/FONT]
```

[FONT=UbuntuRegular]but it still does not fix it and I'm still stuck with startx.[/FONT]
[FONT=UbuntuRegular]does anyone know how to change that ?? I've seen videos on youtube where people have successfully installed Mir and had it fully running with its greeter. [/FONT]


[/COLOR]

---

### Post by dino99 on 2013-06-17
***does anyone know how to change that ?? I've seen videos on youtube where people have successfully installed Mir and had it fully running with its greeter.****

if you beleive what you can see on youtube, then dont be so surprised  :lolflag:

---

### Post by 3wais on 2013-06-17
Is that all you can say ??

how about forgetting that last line and focusing on the rest of the post ??

---

### Post by grahammechanical on 2013-06-18
When 13.04 was under development a couple of us on Ubuntu+1 experimented with MIR. We gave up due to its limited development. The best I can offer is this:

[http://unity.ubuntu.com/mir/installing_prebuilt_on_pc.html](http://unity.ubuntu.com/mir/installing_prebuilt_on_pc.html)
[URL="http://unity.ubuntu.com/mir/using_mir_on_pc.html"]
http://unity.ubuntu.com/mir/using_mir_on_pc.html[/URL]

That second page says to change my lightdm.conf from this

> [SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter


to this

> [SeatDefaults]
type=unity
user-session=ubuntu
greeter-session=unity-greeter


not "type=mir"

My fellow Ubuntu+1 tester of MIR and I hope things will get better soon.

[http://www.omgubuntu.co.uk/2013/05/unity-8-mir-to-be-available-to-try-in-ubuntu-13-10](http://www.omgubuntu.co.uk/2013/05/unity-8-mir-to-be-available-to-try-in-ubuntu-13-10)

Regards

---

