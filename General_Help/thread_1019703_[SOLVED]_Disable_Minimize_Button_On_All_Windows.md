---
title: "[SOLVED] Disable Minimize Button On All Windows"
date: 2008-12-23
forum: General Help
---

### Post by deltaromeo on 2008-12-23
Hi, I have a bad habit of minimizing windows which I need to stop.  Is there a way to disable the minimize button that is at the top right of windows?

Thanks

---

### Post by redilyn on 2008-12-23
Are you using Compiz w/Emerald?

If so you can remove the button using emerald theme manager

```

sudo apt-get install emerald

```

Then launch emerald theme manager, select the theme you are using, click the edit theme tab, then the titlebar tab.

Look for Title-Bar object layout. Remove "N" from that line.

If you are not using emerald....I don't know

---

### Post by deltaromeo on 2008-12-23
I am now installing Emerald and will give it a go, thank you :)

---

### Post by redilyn on 2008-12-23
I should mention, since you are just installing emerald it is possible your current theme will be changed when you try to follow these directions.

But, on the bright side they have some very nice emerald themes here:
[http://themes.beryl-project.org/](http://themes.beryl-project.org/)

:)

---

### Post by deltaromeo on 2008-12-23
Do I need to change the command in compiz settings manager under the Window Decoration plugin?  At the moment it's set to "/usr/bin/compiz-decorator".  I assume I need to change this to Emerald?  If so what's the path?

Thanks.

---

### Post by redilyn on 2008-12-23
I don't think so. I have used emerald and didn't even know that setting existed :)

---

### Post by deltaromeo on 2008-12-23
Ok, I removed the titlebar N and did ```
/usr/bin/emerald --replace 
``` and now it's working just how I want it.  Now I can use Scale / window picker without fear of having any minimized windows not appearing!  Great :)

I never even knew about Emerald.  Now I have prettier decorated windows and a new toy to play with. :P

---

### Post by redilyn on 2008-12-23
Glad I could help! :)

Don't forget to put /usr/bin/emerald --replace in startup programs under sessions (least thats what i did).

System -> Preferances -> Sessions

Merry Christmas :)

---

### Post by deltaromeo on 2008-12-24
> Don't forget to put /usr/bin/emerald --replace in startup programs under sessions (least thats what i did).

I put it in the **command** section of the Window Decoration plugin of Compiz Settings Manager.  I think that's where it's supposed to go, although probably makes no difference to put it in Sessions.

---

### Post by redilyn on 2008-12-24
Excellant. I didn't know you could put it there.

Thanks for the tip!

---

### Post by landtuna on 2011-02-02
Using Compiz (without emerald), you can remove the minimize button by using gconf-editor to remove minimize from /apps/metacity/general/button_layout.

You can prevent minimize from being enabled in the window manager by using CompizConfig Settings Manager / Window Rules to set Non minimizable windows to type=any.

---

