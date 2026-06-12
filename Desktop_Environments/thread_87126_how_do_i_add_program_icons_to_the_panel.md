---
title: "how do i add program icons to the panel?"
date: 2005-11-07
forum: Desktop Environments
---

### Post by Llewxam on 2005-11-07
i just installed the opera browser but the icon is not showing on the start menu. how can i add this or fix it somehow?

---

### Post by 23meg on 2005-11-07
Do you want to put it into the applications menu or the gnome panel itself? For the first purpose SMEG, the gnome menu editor should help. For the latter, just create a launcher for your app and drag&drop it onto the gnome panel. To create a launcher, right click your desktop and choose "Create Launcher".

---

### Post by Llewxam on 2005-11-07
[QUOTE=23meg]Do you want to put it into the applications menu or the gnome panel itself? For the first purpose SMEG, the gnome menu editor should help. For the latter, just create a launcher for your app and drag&drop it onto the gnome panel. To create a launcher, right click your desktop and choose "Create Launcher".[/QUOTE]
app menu. smeg you say... hmm k gonna try that. thanks. suddenly feeling like an idiot... k ... i tried using the menu editing preferences nothing there. tried following the help file for adding launchers to the menu but i don't get the 'add new launcher' option.

---

### Post by Llewxam on 2005-11-07
well i put it on the panel. i'll leave it there for the time being. eventually i'll have it in the apps menu.

---

### Post by Hairy_Palms on 2005-11-07
in the menu theres an option under "Applications->System Tools->Applications Menu Editor" just open it and then you can add opera to the applications menu.

---

### Post by Llewxam on 2005-11-07
[QUOTE=Hairy_Palms]in the menu theres an option under "Applications->System Tools->Applications Menu Editor" just open it and then you can add opera to the applications menu.[/QUOTE]
that's the problem i don't have it -.- :confused:
edit: did a search for smeg on synaptic and i don't seem to have it in the repos either.... obviously that is what i need. any other way to get it?

---

### Post by poopdog on 2005-11-07
[QUOTE=Llewxam]that's the problem i don't have it -.- :confused:
edit: did a search for smeg on synaptic and i don't seem to have it in the repos either.... obviously that is what i need. any other way to get it?[/QUOTE]

I'm having this same problem.

Everyone is saying to use smeg.

I can't install or find smeg anywhere.

???

---

### Post by gw90se on 2005-11-07
Are you using Breezy (5.10)? Did you do an upgrade or fresh install? It almost sounds like you are still using Hoary.

---

### Post by 23meg on 2005-11-07
[QUOTE=poopdog]I'm having this same problem.

Everyone is saying to use smeg.

I can't install or find smeg anywhere.

???[/QUOTE]

SMEG = Applications Menu Editor. The latter is just Ubuntu's brand name for it.

---

### Post by poopdog on 2005-11-07
[QUOTE=gw90se]Are you using Breezy (5.10)? Did you do an upgrade or fresh install? It almost sounds like you are still using Hoary.[/QUOTE]

i am an idiot.
:rolleyes: 

thanks.

---

### Post by Llewxam on 2005-11-07
[QUOTE=gw90se]Are you using Breezy (5.10)? Did you do an upgrade or fresh install? It almost sounds like you are still using Hoary.[/QUOTE]
yea i am still using hoary. either way i have it on the panel so i guess i'll leave it there alltogether. there is still the thing about the lack of audio in streaming files (flash and mpgs, avi, etc) .... bleh.

---

### Post by gw90se on 2005-11-07
Now my question would be, "Can I add SMEG in Hoary?" I am not sure if you can or not. I am new to all of this, too. 

So don't consider yourself an idiot. We're all here to learn.

---

### Post by Llewxam on 2005-11-07
[QUOTE=gw90se]Now my question would be, "Can I add SMEG in Hoary?" I am not sure if you can or not. I am new to all of this, too. 

So don't consider yourself an idiot. We're all here to learn.[/QUOTE]
i know.. it's just so frustrating... -.- anyway... i'm guessing you can add smeg in hoary but it's no longer in the backports (as i previously checked) so there has to be another way.... that way in specific is the one i was searching for, and would still like to know.

---

### Post by 23meg on 2005-11-08
The deb file here might work: [http://www.realistanew.com/projects/alacarte/](http://www.realistanew.com/projects/alacarte/)

I think SMEG has changed its name to Alacarte.

---

### Post by manicka on 2005-11-08
Version 7.5 of smeg will work with hoary if version 8.0 (now called Alacarte) doesn't.

Get it here

[http://dev.realistanew.com/smeg/0.7.5/smeg_0.7.5-0ubuntu1_all.deb](http://dev.realistanew.com/smeg/0.7.5/smeg_0.7.5-0ubuntu1_all.deb)

download to a directory and from within that directory in a terminal, run

sudo dpkg -i smeg*.deb

---

### Post by Llewxam on 2005-11-08
[QUOTE=manicka]Version 7.5 of smeg will work with hoary if version 8.0 (now called Alacarte) doesn't.

Get it here

[http://dev.realistanew.com/smeg/0.7.5/smeg_0.7.5-0ubuntu1_all.deb](http://dev.realistanew.com/smeg/0.7.5/smeg_0.7.5-0ubuntu1_all.deb)

download to a directory and from within that directory in a terminal, run

sudo dpkg -i smeg*.deb[/QUOTE]

conflict with python-xdg, older version installed. tried updating and as always no such luck.

---

