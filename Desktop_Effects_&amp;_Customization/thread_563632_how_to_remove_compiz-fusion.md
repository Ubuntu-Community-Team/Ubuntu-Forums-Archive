---
title: "how to remove compiz-fusion?"
date: 2007-09-30
forum: Desktop Effects &amp; Customization
---

### Post by rapolas on 2007-09-30
I installed compiz fusion, but I didn't like it.. so I removed it, and now, my gnome metacity doesn't start, so I added to session to start it, but still it takes about two minutes, maybe even more, to start anything from sessions list.. so the desktop starts, I see my background, I can run programs from menu, but until metacity starts, where is no borders, no gnome shortcuts work and so on.. Can anybody help, how to solve this? Thanks in advance;)

---

### Post by tomski on 2007-09-30
I too have the same problem does anyone know how to do a clean uninstall of this ??

---

### Post by tomski on 2007-09-30
I have just fixed it for me so here is what i did:

system>preferences>sessions
in the sart up progams tab i clicked on the new button & added metacity to both feilds ( name & command)
clicked ok
then rebooted

all appears to be ok

---

### Post by tomski on 2007-09-30
not too take the risk and go up to gutsy!!

---

### Post by rapolas on 2007-09-30
> **tomski said:**
> I have just fixed it for me so here is what i did:

system>preferences>sessions
in the sart up progams tab i clicked on the new button & added metacity to both feilds ( name & command)
clicked ok
then rebooted

all appears to be ok

I did the same, but still it takes about couple minutes to load it after ubuntu boots, also I have gdesklets in session, they boot also after couple minutes (at the same time with metacity)

---

### Post by tomski on 2007-10-01
do you get the same delay if you login to a failsafe gdm session

---

### Post by rapolas on 2007-10-01
I don't have gdm, I have kdm, and in failsafe only terminal starts, so no delay:)

---

### Post by rapolas on 2007-10-02
> **tomski said:**
> do you get the same delay if you login to a failsafe gdm session

I installed gdm, and tried to login into failsafe gnome, and yes, I have the same delay..

---

### Post by ericartman on 2007-10-06
Running Gutsy had the same problem, removed all references to compiz(synaptic), added metacity to my sessions still didn't help, removed desklets, still no good, was stuck opening terminal and typing metacity --replace that would work for that session only. Then I went to appearance (system-preferences-appearance) clicked on visual effects tab, clicked on normal, was informed I  didn't have compiz installed (duh) and everything reset and has been fine ever since. No more compiz for me, pretty eyecandy not worth the effort. Will leave it on my test bed to show off.

Cart

---

### Post by rapolas on 2007-10-06
> **ericartman said:**
> Then I went to appearance (system-preferences-appearance) clicked on visual effects tab, clicked on normal, was informed I  didn't have compiz installed (duh) and everything reset and has been fine ever since. No more compiz for me, pretty eyecandy not worth the effort. Will leave it on my test bed to show off.

Cart

The same thing helped me also, thanks:)

---

