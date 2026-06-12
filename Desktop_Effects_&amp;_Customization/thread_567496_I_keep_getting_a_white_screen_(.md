---
title: "I keep getting a white screen :("
date: 2007-10-04
forum: Desktop Effects &amp; Customization
---

### Post by ercyboo on 2007-10-04
I recently installed ubuntu, and i havn't been able to use desktop effects, nor beryl, nor compiz, the end effect is a blank white screen. :| i can still see cursor but nothing else. this is really bothering me, why would this be?

Comp Specs:
Intel Core Duo 2.8Ghz
evga nvdia 8600 GT 256mb
1 Gb of ram

---

### Post by Billy_McBong on 2007-10-04
[COLOR="Blue"]have you installed the nVidia drivers?[/COLOR]

---

### Post by ercyboo on 2007-10-04
i am not totally sure, i guess not, how would i install the nvidia driver?

---

### Post by Rupertronco on 2007-10-05
Go to the restricted driver manager:

System>Administration>Restricted Driver Manager

and enable it. 


Restart X (Ctrl + Alt + Backspace), and tell me what happens. I know for a fact it will work on your setup, it's just a matter of configuration. (I run an 8800 and it works beautifully. (I just wish I could get SLi working correctly)

---

### Post by ercyboo on 2007-10-06
> **Rupertronco said:**
> Go to the restricted driver manager:

System>Administration>Restricted Driver Manager

and enable it. 


Restart X (Ctrl + Alt + Backspace), and tell me what happens. I know for a fact it will work on your setup, it's just a matter of configuration. (I run an 8800 and it works beautifully. (I just wish I could get SLi working correctly)

Yeah up i tried getting into there and it said "Your hardware does not need any restricted drivers."

---

### Post by ercyboo on 2007-10-07
well now i need help fixing this,now its permently white screen after doing that Ctrl + Alt + Backspace

---

### Post by ercyboo on 2007-10-07
k, so i got out of that white screen being permanent, but i still can't even use them without getting white screen............ HELP!

---

### Post by Sico on 2007-10-07
Try this.  Before you login, go to "Options" in the lower left corner and choose "Change Session" and then choose "Failsafe Gnome". Continue to logon.  Does this work?

---

### Post by ercyboo on 2007-10-07
failsafe never worked, but its alright, i fixed it by clicking around meathod XD

---

### Post by Xernie on 2007-10-07
I have the same problem. Could you please post how you fixed it? You say something about "clicking around meathod", but I have no clue what you mean.

---

### Post by ercyboo on 2007-10-07
by clicking around method i mean , i put my cursor over where i thought system button would be, then i moved mouse down a bit to preferences then took a shot at where i thought it would be to open desktop effects, then i clicked enter and it turned it off, im sure theres some command you can type, but im not a linux person yet, XD first week of using, so yeah, try and click around if you think you can. to turn it off. i put stickies on my monitor so i would know where each of the 3 main things were

---

### Post by Wharf Rat on 2007-10-07
I installed Compiz and got the same results -- white screen.
But, I could use Alt-Crtl-R-arrow to flip to another white screen.

A few Alt+Crtl+Bkspace attempts at restarting and I was getting frustrated.

Each time X restarted I tried different options ..  In fail safe terminal mode
I uninstalled compiz

**sudo apt-get autoremove Compiz**

Be sure to use the Autoremove command.  It gets rid of Compiz and returns you to Gnome.

Whew!  Glad I didn't try this in Windows.

---

### Post by ercyboo on 2007-10-08
im able to turn them on, but the effects don't even happen now

---

