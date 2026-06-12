---
title: "Beryl &amp; xgl (nvidia)"
date: 2007-01-23
forum: Desktop Environments
---

### Post by rkrizan on 2007-01-23
I did a fresh install of Ubuntu Edgy, then proceeded with installing xgl and beryl. After installing the nvidia-glx drivers of course. But when I start beryl/beryl-manager, its totally unreadable. Any ideas?

---

### Post by tpg on 2007-01-23
If you've got an nVidia card, then you shouldn't need XGL, as the nVidia drivers work with AIGLX. See [here]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA") for a walkthrough. Hopefully this will work better for you!

---

### Post by rkrizan on 2007-01-23
> **tpg said:**
> If you've got an nVidia card, then you shouldn't need XGL, as the nVidia drivers work with AIGLX. See [here]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA") for a walkthrough. Hopefully this will work better for you!


Thanks, but this didn't help either.

---

### Post by tpg on 2007-01-23
OK, well what exactly do you mean by unreadable? Any chance of a screenshot? I'm not sure if I'll be much use though, as I don't have an nVidia card myself!

---

### Post by rkrizan on 2007-01-23
Its all totally scrambled. I can't take a screenshot, because I can't see the menus, let alone see the desktop. You know how it would look if you took a rag soaked in lacker thinner and wiped it across an oil painting? Thats how my screen looks when I run beryl.

---

### Post by tpg on 2007-01-25
> **rkrizan said:**
> You know how it would look if you took a rag soaked in lacker thinner and wiped it across an oil painting? Thats how my screen looks when I run beryl.

I think I get the idea! Do you have proper 3D acceleration if you don't have Beryl running? Check this by running ```
glxinfo | grep direct
``` in a terminal, and make sure the output is something like "direct rendering: Yes". If not, then there's a problem with the drivers.

---

### Post by rkrizan on 2007-01-25
I was able to get everything running properly, it was a problem with my drivers. I used the nvidia-glx instead of the beta drivers.

---

### Post by jual_mahal1 on 2007-01-25
**rkrizan**, if you are using nvidia driver (**nvidia-glx**) provided by Ubuntu repository, you must uninstall it if you want to install Nvidia-provided driver.

To make it easy for you, use **Envy** script (please use google or this forum for more information)

Your **Beryl** setup is ok.

---

