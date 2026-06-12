---
title: "nvidia screenlet"
date: 2009-02-19
forum: Desktop Environments
---

### Post by andrea000 on 2009-02-19
can anyone tell me how to install the nvidia screenlet or sidebar just
like what's in the picture here   
[http://www.screenlets.org/images/f/fc/Nvidiascreenlet.jpg](http://www.screenlets.org/images/f/fc/Nvidiascreenlet.jpg)  

thanks all

---

### Post by konqueror7 on 2009-02-19
here's the [link]("http://screenlets.org/index.php/Nvidia_screenlet"), donwload it...then open screenlets manager, click 'Install' button and explore the donwload directory of the screenlet...

---

### Post by andrea000 on 2009-02-20
konqueror7 

Thank you i have it installed but as it doesn't do 
anything i uninstalled it but thank you very much.

XOXOXO

---

### Post by mpsii on 2009-02-20
What did yours do?

Do you have the proprietary nVidia drivers installed along with nvidia-settings package?

---

### Post by andrea000 on 2009-02-20
> **mpsii said:**
> What did yours do?

Do you have the proprietary nVidia drivers installed along with nvidia-settings package?

no i can't use the proprietary nVidia drivers i can't get my screen resolution to do right it only will do 800x600 nothing else.That is fine it makes my system run slower not much but a little just testing out some stuff and that look cool.

Thank you all

XOXOXO

---

### Post by mpsii on 2009-02-20
Just out of morbid curiosity... what nVidia card do you have?

```
$ lspci -v|grep "VGA"
```

---

### Post by konqueror7 on 2009-02-20
the requirements for the screenlet is a proprietary driver and the nvidia-settings...

---

### Post by andrea000 on 2009-02-21
> **mpsii said:**
> Just out of morbid curiosity... what nVidia card do you have?

```
$ lspci -v|grep "VGA"
```

FX 5500 I know now that the proprietary driver and the nvidia-settings
are required it still looked looked cool but i couldn't see keeping it 
for looks only i may check out google gadgets and see if that slows me 
down a lot.

Thank you all very much for all your help

xoxoxo

---

### Post by renetwist on 2009-05-19
Hello to you all,

I would like to let you know that the Nvidia screenlet is more up to date at the following [link]("http://gnome-look.org/content/show.php/Nvidia+screenlet?content=81694")

Like konqueror7 said, nvidia proprietary driver and nvidia-settings are dependencies.

Users can also get automatic updates if they subscribe to the 3rd party screenlets repository. (see the link above).

I'm sorry Andrea that it doesn't work for you. I would like to take the opportunity to tell all of you that development is still being done and that I am currently working on a X driver approach of the Nvidia drivers.

Sincerely yours,

René Jansen
Author of Nvidia screenlet

---

