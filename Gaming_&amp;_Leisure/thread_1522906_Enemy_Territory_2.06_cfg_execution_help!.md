---
title: "Enemy Territory 2.06 cfg execution help!"
date: 2010-07-02
forum: Gaming &amp; Leisure
---

### Post by silentrock on 2010-07-02
Hello guys i just downlaoded and succesfuly installed Enemy Territory 2.06
but every time i go in game my monitor puts a message about Input Out of range and tells me to switch to 1440x900-60hz but i dont know what to do so i saw in another thread
that making a cfg file and placing it in the /Enemy Territory/etmain/  folder and then running it from ET console will change the game resolution by running this command

```
exec or /exec config
```


and heres what it is in the cfg file

```
seta r_mode "-1"
seta r_customwidth  "1440"
seta r_customheight "900"
vid_restart
```

but when i run the command it returns " couldn't execute config"

---

### Post by Cresho on 2010-07-03
You are going to have more questions after you get it running like mic and also improving framerate.

Let me get y ou started.
cd to executable and....
```
./etqw seta r_mode "-1" seta r_customwidth "1024" seta r_customheight "768"

```

see if this works temporarily.  delete the config you did.

---

