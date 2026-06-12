---
title: "xvncviewer &amp; xvnc4viewer with compiz : unable to input data"
date: 2006-12-14
forum: Desktop Environments
---

### Post by tousoxeu on 2006-12-14
Hi all,

I installed compiz yesterday on my dapper box, and it works fine. But since my job is to help users in my network, i'm to use vnc viewer to connect to their computers.

My problem is that when the 3D effects are enable, i cannot enter the IP adress in the dialog box on neither xvncviewer and xvnc4viewer. I can click on the buttons, but i can't select the text field. I tried also to launch the viewer from an xterm with the IP but i can*'t* type the password neither.
When i disable the 3D effects, i can enter the data again, and if i restart the 3D effects when vncviewer is connected, it works great also. There's just that text field that is unavailable with the 3D effects.

Any solution or workaround ?

---

### Post by bernied on 2006-12-14
I start vncviewer like:
vncviewer hostname:1
or
vncviewer 192.168.0.4::5901
where 5901 is the port.
Does this work?

---

### Post by tousoxeu on 2006-12-14
> **bernied said:**
> I start vncviewer like:
vncviewer hostname:1
or
vncviewer 192.168.0.4::5901
where 5901 is the port.
Does this work?

the problem is not to launch it, but to type in the adress and/or the password in the dialog box


Nota : i just noticed i made typo about the password : i can**_'t_** type the password neither

---

### Post by bernied on 2006-12-14
I wonder if you could start it from a real terminal - like from Ctrl-Alt-F1 - you might have to direct it to the X session though ???
EDIT: scratch that, it would still ask for the password in a popup window

Also when I start vncviewer from a Konsole terminal, if I use & to run it in the background it throws up a popup text window thingy for the password, but if I don't, it asks for the password in the terminal. That ties up a terminal, but who cares?

it sounds like a bug in any case - have you looked for a bug report? there might be a workaround

---

### Post by bernied on 2006-12-14
My guess would be that the problem is not so much with vnc, as with the widgetty things it uses to draw its text box things. Apologies for my lack of vocabulary.

You could try compiling your own from source ??

---

### Post by tousoxeu on 2006-12-15
i didn't try to compile it myself (and i wouldn't be able anyway) but as you said, it might be the components used for the drawing that cause the problem

now i have to find what components are involved...:-k

---

### Post by tousoxeu on 2007-04-16
I've upgraded to feisty now, and it works... but only if i click on the desktop before clicking insitde the text field... any other way, the input won't be taken.

---

