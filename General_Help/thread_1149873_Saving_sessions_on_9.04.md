---
title: "Saving sessions on 9.04"
date: 2009-05-05
forum: General Help
---

### Post by Acapulco on 2009-05-05
Hello. On previous versions of Ubuntu I could set the panel they way I needed and then go to System > Preferences > Sessions and save the way the panel is configured. 

On 9.04 this menu is missing and now my panel icons keep moving around.

Is there a way to bring this menu back again? or how can I save my session on this version of Ubuntu?

Thanks!

---

### Post by Acapulco on 2009-05-07
Also, I noticed I can't use the Ctrl-Alt-Backspace combo to reload my session...is this a bug or a "feature"?

It certainly is annoying...

---

### Post by Linux&amp;Gsus on 2009-05-07
> **Acapulco said:**
> Also, I noticed I can't use the Ctrl-Alt-Backspace combo to reload my session...is this a bug or a "feature"?
This is a feature. In Jaunty this is disabled by default.
I can't tell you where you find that in Ubuntu/Gnome but it can be enabled again.

Cheers,
L&G

---

### Post by Acapulco on 2009-05-07
Yes!.

Thanks.

I found it. You have to edit the /etc/X11/xorg.conf file and add the following lines

```

Section "ServerFlags"
Option "DontZap" "false"
EndSection

```

However, I still can't find the option to save sessions in Jaunty, not even googling around :(. Please. Anyone? I hate how I have to move around my icons *every* time...

---

### Post by AlexW573 on 2009-05-07
If someone has the answer to the original question, please post. I just noticed the System>Preferences>Session is missing in 9.04. I really liked that in 8.10, has anyone seen where it hid?

---

### Post by meist3r on 2009-05-07
> **AlexW573 said:**
> If someone has the answer to the original question, please post. I just noticed the System>Preferences>Session is missing in 9.04. I really liked that in 8.10, has anyone seen where it hid?

I actually looked for that myself just now and some blog post told me (which he regarded a good move) that they have renamed the sessions manager to "Startup Applications" you can still find it in the Preferences menu. Works same as before (well, I hope they fixed the session saving by now EDIT: Turns out they still don't remember window positions).

---

### Post by Acapulco on 2009-05-07
I executed the Startup Applications Preferences like you said but I still can't find the option to save the sessions settings. Not to save which programs are open, but to save the position of the icons in the gnome-panel.

Still, thanks for the idea :)

---

### Post by Acapulco on 2009-05-09
So...no one has any idea on how to save the gnome-panel icon places?

Does no one else has their icons moving around?

Anyone? :(

---

### Post by DeMus on 2009-05-09
> **Acapulco said:**
> So...no one has any idea on how to save the gnome-panel icon places?

Does no one else has their icons moving around?

Anyone? :(

No, sorry. My icons stay on the place I put them.

---

### Post by Shaks on 2009-05-28
Hi, 

I am also facing the same issue.
I have to add the icons in my session every time I log-in.

Can anybody nail it down to provide the solution.

Thanx in advance.

---

### Post by DodgeV83 on 2009-08-25
Incase anyone is still looking

System -> Preferences -> Startup Applications -> Options Tab -> Check Automatically remember running applications when logging out

Have fun!

---

### Post by wyznr on 2009-08-26
> **DodgeV83 said:**
> Incase anyone is still looking

System -> Preferences -> Startup Applications -> Options Tab -> Check Automatically remember running applications when logging out

Have fun!
Thanks, life saver!

---

