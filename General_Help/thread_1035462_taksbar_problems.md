---
title: "taksbar problems"
date: 2009-01-09
forum: General Help
---

### Post by Jameshardy88 on 2009-01-09
hi iv'e got a problem with all of my "human" themes. Im running intrepid ubuntu with gnome. The problem seems to be localised to all of my human themes. Whenever i let my cursor drift over the taskbar (the 1 with the title of what you are on as well as the close, maximize and minimize buttons it will just grey out all of its contents. This seems to have been a problem since the install however i have not used a human theme until now.

Any and all help appreciated thanks

---

### Post by IceReaver75 on 2009-01-09
I'm guessing you have a nvidia graphics card since there is a problem with the nvidia drivers with some model of cards.  There are a few options you can try:

1) Change the window borders to a different theme under system/apperance then click on the customize tab and change the window border to something like clearlooks doesn't seem to affect that window border.

2) The 96 drivers for nvidia listed in the hardware tab will take care of the problem but cause other problems usually.

3) Install emerald theme manager through synaptic if your using compiz and download a couple compiz themes from gnome-look.org.  Install the compiz-icon through synaptic and change the window manager to emerald.

4) If you want to go this route you can download and use the beta drivers off the nvidia site.  Manually install the driver and it will take care of all problems.  Bad thing with that though is you have to manually install the driver and have to install the driver again after a kernel update.

---

### Post by Jameshardy88 on 2009-01-09
> **IceReaver75 said:**
> I'm guessing you have a nvidia graphics card since there is a problem with the nvidia drivers with some model of cards.  There are a few options you can try:

1) Change the window borders to a different theme under system/apperance then click on the customize tab and change the window border to something like clearlooks doesn't seem to affect that window border.

2) The 96 drivers for nvidia listed in the hardware tab will take care of the problem but cause other problems usually.

3) Install emerald theme manager through synaptic if your using compiz and download a couple compiz themes from gnome-look.org.  Install the compiz-icon through synaptic and change the window manager to emerald.

4) If you want to go this route you can download and use the beta drivers off the nvidia site.  Manually install the driver and it will take care of all problems.  Bad thing with that though is you have to manually install the driver and have to install the driver again after a kernel update.

thanks for your help, this being the case i think ill provisionally tinker around with another boarder theme, just for future reference do you know how to turn emerald on by default when you log in (at the moment im running "emerald --replace" whic gets a little tedious) also how can i switch it off and just use compiz again?

---

### Post by IceReaver75 on 2009-01-09
If you install the fusion icon from synaptic......when you start that it will put a blue box in the panel where when you right click the panel box it will let change between metacity or emerald window managers in just a click.

also metacity --replace will turn emerald off for you

---

### Post by Jameshardy88 on 2009-01-09
> **IceReaver75 said:**
> If you install the fusion icon from synaptic......when you start that it will put a blue box in the panel where when you right click the panel box it will let change between metacity or emerald window managers in just a click.

also metacity --replace will turn emerald off for you

thankyou very much =)

---

