---
title: "Help with display size on Ubunto 8.10 and nvida 6200"
date: 2008-12-03
forum: General Help
---

### Post by Racer5 on 2008-12-03
Ok, definate noob but I am computer savvy.

My PC has an integraded nvida 6200 video.

I installed Ubuntu 8.10 and it has the nvida (build 177 if memory serves) drivers.  it will let me select up to 1024x768 but that is it.  I have a 19" LCD with a 1280x1024 resolution.  I can not figure out how to change this for the life of me.  I spend 2 days searching and trying different things to no avail.

Any help is appreciated.

---

### Post by overdrank on 2008-12-03
> **Racer5 said:**
> Ok, definate noob but I am computer savvy.

My PC has an integraded nvida 6200 video.

I installed Ubuntu 8.10 and it has the nvida (build 177 if memory serves) drivers.  it will let me select up to 1024x768 but that is it.  I have a 19" LCD with a 1280x1024 resolution.  I can not figure out how to change this for the life of me.  I spend 2 days searching and trying different things to no avail.

Any help is appreciated.

Have you tried using the nvidia-settings 
```
gksu nvidia-settings
```

---

### Post by Racer5 on 2008-12-03
Yes.  It is not showing up in there either.

I am guessing it is not detecting my monitor correctly?  Is that possible?

I know it runs at 1280x1024 at 60hz

---

### Post by mhh91 on 2008-12-03
select "X server Display configuration",then click on "advanced" button,in "panning",type the resolution you want :)

---

### Post by Racer5 on 2008-12-04
> select "X server Display configuration",then click on "advanced" button,in "panning",type the resolution you want 

That just lets me scroll the screen around, it doesnt allow me to change to the proper resolution.

---

### Post by mhh91 on 2008-12-04
there's "resolution",it's set to "auto",try changing it

i have GeForce 6200 as well,and i have 1600X1200 here :)

---

