---
title: "Compiz: Window Manager needs restart upon boot up"
date: 2009-01-09
forum: General Help
---

### Post by Drubie on 2009-01-09
Evening.

I have configured the Compiz-Fusion desktop effects and whatnot to what I want (or close enough) and everything works and is okay.
There is just one hitch: When I boot up, none of the effects work until I reload the windows manager (right click the compiz icon and reload)

It's not really a problem, but more of a nuisance.  Is there a way to not need to restart the window manager or to automatically do that as I boot up?
[color=white]blarg[/color]

---

### Post by Drubie on 2009-01-09
Update:  The window manager does not need a restart when I start up from a suspend.

Has anybody else had this problem?

[color=white]Hidden Message: e^(i*pi)=-1[/color]

---

### Post by Chrisj303 on 2009-01-09
What I do is create an Emeralditem in sessions.

Go SYSTEM>PREFERENCES>SESSIONS

Then "ADD" then call it "Emerald" and in the command box put > emerald --replace

Make sure its tick box is checked.

Now Emerald should startup on every boot.

---

### Post by Drubie on 2009-01-09
I will try that.  I didnt really want to goof with emerald yet, but if it will work, then okey-dokey

Thanks

---

### Post by JECHO on 2009-01-09
> **Drubie said:**
> I will try that.  I didnt really want to goof with emerald yet, but if it will work, then okey-dokey

Thanks



if you dont want to mess with emerald just yet then instead of adding "emerald --replace" to the sessions menu, try adding "compiz --replace". reboot and see if that works for you.

---

