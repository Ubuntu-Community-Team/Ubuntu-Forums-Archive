---
title: "How do I change the colors of libnotify?"
date: 2007-07-24
forum: Desktop Effects &amp; Customization
---

### Post by wersdaluv on 2007-07-24
I am using the nimbus theme, while libnotify pop-ups on my screen with the human color scheme.

How do I change the colors of libnotify?

---

### Post by zanglang on 2007-07-24
I think at its current version libnotify doesn't provide color customization yet, there's a feature discussion which you can follow here if you want:
[http://trac.galago-project.org/ticket/122](http://trac.galago-project.org/ticket/122)

Meanwhile, maybe you can try changing the 'controls' part in your GTK theme, I think it changes the background color. Or, you can toggle between Ubuntu's and GNOME's libnotify themes with the gconf-key '/apps/notification-daemon/theme' - default is 'ubuntu', GNOME is 'standard'.

---

### Post by wersdaluv on 2007-07-24
> **zanglang said:**
> I think at its current version libnotify doesn't provide color customization yet, there's a feature discussion which you can follow here if you want:
[http://trac.galago-project.org/ticket/122](http://trac.galago-project.org/ticket/122)

Meanwhile, maybe you can try changing the 'controls' part in your GTK theme, I think it changes the background color. Or, you can toggle between Ubuntu's and GNOME's libnotify themes with the gconf-key '/apps/notification-daemon/theme' - default is 'ubuntu', GNOME is 'standard'.

Thank you very much!!!!

---

