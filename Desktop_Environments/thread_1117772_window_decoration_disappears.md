---
title: "window decoration disappears"
date: 2009-04-06
forum: Desktop Environments
---

### Post by grikdog on 2009-04-06
Does anyone know what causes window decoration (underscore, box, X in the top right corner of the bar) to continually vanish?  Usually, but not exclusively, this happens in Firefox.

I have to run Applications -> System -> Compiz Fusion Icon, then select Emerald, then re-select Gtk+ window decoration to get the tops of my windows back.

Why are they called "decoration," anyway?  There's essential functionality embedded in those window tops.

Signs of instability do not encourage me to migrate to Intrepid or Jackalope, when Hardy desktop bugs never get fixed.

---

### Post by gettinoriginal on 2009-04-06
Do F11 twice, then manually minimize window, close window, and then reopen and maximize with max button.  That should fix the problem for you so that it doesn't happen again.  :p

---

### Post by grikdog on 2009-04-30
> **gettinoriginal said:**
> Do F11 twice, then manually minimize window, close window, and then reopen and maximize with max button.  That should fix the problem for you so that it doesn't happen again.  :p

Well, the decoration comes back, yes.  The question is whether it'll STAY back :-\"

Thanks, anyway, one way or tother.

---

### Post by andrea000 on 2009-04-30
did it fix it? if not do you run compiz?

---

### Post by dmuir on 2009-05-11
Thanks, worked for me. What's the cause? I've had it happen in another app too.

---

### Post by davec64 on 2009-05-11
This was a known issue in Intrepid so to stop it happening the next time you boot:> compizconfig settings manager > workarounds plugin > untick legacy fullscreen support

I'm assuming it's the same on Jaunty!

---

