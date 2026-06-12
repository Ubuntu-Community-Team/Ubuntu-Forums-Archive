---
title: "LxDoom the right way"
date: 2006-10-05
forum: Desktop Environments
---

### Post by fululian on 2006-10-05
i installed lxdoom from the ubuntu-repositories, alongside the freedoom and the doom-wad-shareware. when i start "lxdoom", a tiny window shows doom running alright, without sound or music and with the mouse locked to this window.

does anyone know how to

1) get the resolution right - perfect would be 1280 x 800 points.

2) get the sound working on this one

3) "un"lock the mouse from that window?

also a nice tutorial/how-to would be great

thanks

---

### Post by DirtDawg on 2006-10-22
> **fululian said:**
> i installed lxdoom from the ubuntu-repositories, alongside the freedoom and the doom-wad-shareware. when i start "lxdoom", a tiny window shows doom running alright, without sound or music and with the mouse locked to this window.

does anyone know how to

1) get the resolution right - perfect would be 1280 x 800 points.

2) get the sound working on this one

3) "un"lock the mouse from that window?

also a nice tutorial/how-to would be great

thanks


1) open /.lxdoom/boom.cfg in your favorite text editor. Look for the lines starting under #Video Settings, and simply change the screen_width property to 1200 and the screen_height to 800. Make sure to save.

2) Apparently, sound is an issue for many people. I have read alot about an engine named Doomsday that's supposed to run better. Being a ppc user, I do not have that option :( But look into it.

3) Not sure what "unlock" refers to. I like using "w" for forwards and "s" for backwards,("a" and "d" for strafe) In the boom.cfg file, under the heading #Mouse Settings, I changed Mouse_sensativity_vert to 0. I'm not sure this solves your particular issue, but it made me happy.

I see it's been a couple weeks since you posted. Who knows if you care anymore. I would've posted sooner, but I just found this game yesterday.

---

