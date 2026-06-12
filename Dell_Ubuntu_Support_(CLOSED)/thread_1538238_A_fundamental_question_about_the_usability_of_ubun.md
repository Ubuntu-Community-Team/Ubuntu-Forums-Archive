---
title: "A fundamental question about the usability of ubuntu for the general public."
date: 2010-07-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kryo_helge on 2010-07-24
Why doesn't anybody answer a seemingly quite easy questinon and a
a very practical one, qoncerning the use of pen and/or finger touch sensibility on a tablet PC (dell latitude xt2). It should, according to my limited but soundly foundamented knowledge only be question about changing a few parameters in one or two files.  If this is a difficult question to answer, it raises some fundamental questions qoncerning the usability of ubuntu (linux) for the majority of the potential users.

This was the original question;

"**Disabling finger touch sensitivity** 			
 			 			 		   		 		 		I have  installed ubuntu 10.04 on a Latitude XT2. Everything works perfectly,  but I don't want the screen to be sensitive to finger touch. I only want  to use the pen. How can I disable the finger touch sensitivity":(

---

### Post by tkoco on 2010-07-24
> **kryo_helge said:**
> Why doesn't anybody answer a seemingly quite easy questinon and a
a very practical one, qoncerning the use of pen and/or finger touch sensibility on a tablet PC (dell latitude xt2). It should, according to my limited but soundly foundamented knowledge only be question about changing a few parameters in one or two files.  If this is a difficult question to answer, it raises some fundamental questions qoncerning the usability of ubuntu (linux) for the majority of the potential users.

This was the original question;

"**Disabling finger touch sensitivity** 			
 			 			 		   		 		 		I have  installed ubuntu 10.04 on a Latitude XT2. Everything works perfectly,  but I don't want the screen to be sensitive to finger touch. I only want  to use the pen. How can I disable the finger touch sensitivity":(

Nice unit! Two possibilities come to mind -

1) try disabling mouse/touchpad gestures in the System -> Preferences -> Mouse menu
2) Access the BIOS menu and see if it is possible to turn-off the touchpad capability. I do not have such a nice unit, so I can not advise you on how to access the BIOS or where to look. Dell documentation (or try Googling "Dell BIOS access" ) for additional help.

Please let the Forum know when you solve this one.

---

### Post by Favux on 2010-07-24
Hi kryo_helge,

See "5) Turning touch on and off" on the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").  My guess is you'll want to use the evdev commands since you're in Lucid.

---

### Post by tkoco on 2010-07-24
> **Favux said:**
> Hi kryo_helge,

See "5) Turning touch on and off" on the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").  My guess is you'll want to use the evdev commands since you're in Lucid.

Nice tip. Always something new to learn here at the Forums!

---

### Post by kryo_helge on 2010-07-24
Thank you very much for trying to answer my question
This was my first try;
"christer@christer-desktop:~$ xsetwacom set touch touch off
Cannot find device 'touch'".

This is my second try;
"christer@christer-desktop:~$ #!/bin/bash
christer@christer-desktop:~$ 
christer@christer-desktop:~$ STATUS=`xsetwacom get touch touch`
christer@christer-desktop:~$ if [ "$STATUS" == "0" ]
>   then
>     echo "Touch was OFF, enabling."
>     xsetwacom set touch touch on
h> else
>     echo "Touch was ON, disabling."
>     xsetwacom set touch touch off
> fi
Touch was ON, disabling.
Cannot find device 'touch'."

This is my third try;
"christer@christer-desktop:~$ #!/bin/sh
christer@christer-desktop:~$ 
christer@christer-desktop:~$ if [ `xsetwacom get touch Touch` -gt 0 ]
> then
> xsetwacom set touch Touch 0
> else
> xsetwacom set touch Touch 1
> fi
bash: [: too many arguments
Cannot find device 'touch'."

This is my fourth attempt;

xinput float "N-Trig Touchscreen"

It works!!

Thank you Favux.

I got the xt2 mostly in order to use xjournal or some similiar programme in order to organise my
It works!
Thank you Favux.
I bougth the xt2 primarily to be able to organize  my former hand written calculations.
It was impossible to use xjournal (or similar) with finger touch enabled.
My employer supplide me with the computer with Vista and a lot of security restrictions.
I chose to install ubunta via a portable usb hard drive. Now I can listen on spotify while im calculating and at the same time write in xjournal without truoble.

I have learned several things today, besides how to fix my computer. In order to be heard you have to scream. The last part is a bit disappointing.

Finally how can I indicate that my problem is solved?

---

### Post by Favux on 2010-07-25
Hi kryo_helge,

Glad you got touch off and Xournal is now usable for you.  I hope it isn't necessary to scream!

At the top on the right are Thread Tools.  In there you'll see mark thread as Solved.


Hi tkoco,

You're right.  I'm always learning here at the Ubuntu forums.

---

