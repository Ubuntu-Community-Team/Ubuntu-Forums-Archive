---
title: "Not able to change to Dvorak keyboard layout through xorg.conf"
date: 2009-02-27
forum: General Help
---

### Post by DeathOnJuice on 2009-02-27
I just upgraded to Intrepid (yeah, I'm lazy), and I'm trying to get Dvorak to work. It works fine the normal way in GNOME, but I use a different window manager. So, I put this is my xorg.conf:

Section "InputDevice" 
        Identifier "Generic Keyboard" 
        Driver "kbd" 
        Option "CoreKeyboard" 
        Option "XkbRules" "xorg" 
        Option "XkbModel" "pc104" 
        Option "XkbLayout" "dvorak,us" 
        Option "XkbOptions" "grp:shift_toggle" 
EndSection 

I should now be able to switch layouts by pressing both shifts. But even though dvorak is first, it's always normal us layout outside of GNOME. I've restarted, of course. What gives?

See the next post for information on the other way I tried to fix this.

---

### Post by DeathOnJuice on 2009-02-27
OK, so I followed this tutorial:

[http://dragonseptarts.com/blog/?p=152](http://dragonseptarts.com/blog/?p=152)

And Dvorak was then the default at the login screen. However, I couldn't toggle between it and normal. Also, I meant for normal to be the default, and when I changed it to be that way... Dvorak is still the default! This is bad, because now games will use Dvorak as the movement control, which screws everything up.

Any help?

---

### Post by DeathOnJuice on 2009-02-28
Bump.

---

### Post by DeathOnJuice on 2009-02-28
Anyone?

---

### Post by DeathOnJuice on 2009-02-28
Someone must know.

---

### Post by DeathOnJuice on 2009-02-28
I'm gonna get this answered.

---

### Post by DeathOnJuice on 2009-03-22
So... Any ideas?

---

