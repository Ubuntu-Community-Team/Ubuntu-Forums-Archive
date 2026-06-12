---
title: "No Graphics"
date: 2009-06-23
forum: General Help
---

### Post by naharper on 2009-06-23
When I boot up Ubuntu (Heron) I can't get any graphics to show up. I can log in through the terminal, but that's all I get. So far I've tried these suggested fixes:

sudo /etc/init.d/gdm start (with the result that GNOME display manager fails to start)

sudo X --configure (results unrecognized option error: --configure)

sudo dpkg-reconfigure xserver-xorg (walks you through a configuration process, but ultimately still doesn't work when I try to start the display manager)

I'm getting pretty desperate. Any ideas?

---

### Post by clonne4crw on 2009-09-28
```

# xinit

```

Anything?

---

