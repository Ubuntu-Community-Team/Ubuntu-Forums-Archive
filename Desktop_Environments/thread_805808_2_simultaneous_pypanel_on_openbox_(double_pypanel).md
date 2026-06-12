---
title: "2 simultaneous pypanel on openbox (double pypanel)"
date: 2008-05-24
forum: Desktop Environments
---

### Post by thebloggu on 2008-05-24
is it possible to execute two instances of pypanel at the same time in openbox? something like gnome panel? please help

thank you

---

### Post by jviscosi on 2008-05-25
It looks like pypanel is explicitly coded to prevent this:

```

            if name == "PyPanel":
                hide = 1
                count += 1
                **if count == 2:**
                    sys.stderr.write("\nPyPanel is already running! Terminating ...\n\n")
                    **sys.exit()    **          

```If you really want to, you could either change the **count == 2** to **count == 3** (or however many you want to run), or comment out **sys.exit()** and then you could run it multiple times, but it doesn't look like there's any way to have them be configured differently.  (But maybe that's what you're after.)

If you're looking for a panel that's designed to run multiple instances with different configurations, you might want to check out fbpanel instead.

---

### Post by thebloggu on 2008-05-25
thank you for replying :)

i would like to have 2 separate configurations so..

i tried fbpanel and works just the way i want ;)

---

