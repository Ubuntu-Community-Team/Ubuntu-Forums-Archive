---
title: "fluxbox startup"
date: 2005-05-18
forum: Desktop Environments
---

### Post by LINJEinc on 2005-05-18
Hi everyone!

I'm woundering how I make Fluxbox autostart some programs for me.

my [COLOR=Red].Xinitrc[/COLOR] looks like this now:

```

#Fluxbox startup

#Slit.sh
exec slit.sh &

#gKrellm
exec gkrellm &

#fluxbox
exec fluxbox

```

and that dosen't work. I have tryed everything I can think about  :-x 

Can someone please help me to make this work

---

### Post by Stormy Eyes on 2005-05-18
[QUOTE=LINJEinc]Hi everyone!

I'm woundering how I make Fluxbox autostart some programs for me.

my [COLOR=Red].Xinitrc[/COLOR] looks like this now:

```

#Fluxbox startup

#Slit.sh
exec slit.sh &

#gKrellm
exec gkrellm &

#fluxbox
exec fluxbox

```

and that dosen't work. I have tryed everything I can think about  :-x 

Can someone please help me to make this work[/QUOTE]

The only line that should start with "exec" is the "exec fluxbox" line. You want the others to run in the background, not to be the "magic process" that ends your X session upon termination. Get rid of "exec" for slit.sh and gkrellm, and do "ln -s ~/.xinitrc ~/.xsession" if you're using GDM to login.

---

### Post by LINJEinc on 2005-05-18
[QUOTE=Stormy Eyes]The only line that should start with "exec" is the "exec fluxbox" line. You want the others to run in the background, not to be the "magic process" that ends your X session upon termination. Get rid of "exec" for slit.sh and gkrellm, and do "ln -s ~/.xinitrc ~/.xsession" if you're using GDM to login.[/QUOTE]
 Now I tried that, and it doesn't work at all. :(
Any other idéas ?

---

### Post by Stormy Eyes on 2005-05-18
[QUOTE=LINJEinc]Now I tried that, and it doesn't work at all. :(
Any other idéas ?[/QUOTE]

Is there a "Custom Session" entry in your GDM menu?

---

### Post by LINJEinc on 2005-05-18
[QUOTE=Stormy Eyes]Is there a "Custom Session" entry in your GDM menu?[/QUOTE]
 no, only "default system..." GNOME, fluxbox and two terminal entries :(

---

### Post by Stormy Eyes on 2005-05-18
[QUOTE=LINJEinc]no, only "default system..." GNOME, fluxbox and two terminal entries :([/QUOTE]

Try "Default system" then.

---

### Post by LINJEinc on 2005-05-18
[QUOTE=Stormy Eyes]Try "Default system" then.[/QUOTE]
 okey! will try that.
brb with results :)

EDIT:

It work's.....thank's man !!!  \\:D/

---

