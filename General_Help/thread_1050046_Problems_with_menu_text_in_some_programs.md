---
title: "Problems with menu text in some programs"
date: 2009-01-25
forum: General Help
---

### Post by timg1982 on 2009-01-25
Hi,
I'm having problems with some programs not showing up the menus properly. Please see the attachments for examples of the problems in wine configuration and amarock. Does anyone have any ideas what might be causing this?

Thanks,

Tim

---

### Post by gimcrack on 2009-01-25
It's a video card driver problem. 

If you can live without the Linux eye candy do this.

Preferences>>Appearance>>Visual Effects>>None

By turning off the visual effects to none. You should be able to see your font menus now.

If you can't solve this problem with update drivers. Then move on to a upgrade video card that use different drivers on your old video card.

---

### Post by timg1982 on 2009-01-25
Thanks for that. I disabled the nvidia accelerated graphics driver and it seems to be ok now.

Tim

---

### Post by ajgreeny on 2009-01-25
> Thanks for that. I disabled the nvidia accelerated graphics driver and it seems to be ok now.
You don't need to do that, which may lower your graphics generally, just disable compiz with```
 metacity --replace
```

---

