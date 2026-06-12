---
title: "[SOLVED] Changing Colour After Login"
date: 2007-11-23
forum: Desktop Effects &amp; Customization
---

### Post by AlistairH on 2007-11-23
This is a minor issue, yet I haven't been able to resolve it, despite the fact that it's probably staring me in the face - so I apologise in advance if it is.

I've changed my login background to match the wallpaper of my desktop and set the login window to show a plain login dialog rather than a themed one (I havn't downloaded any login themes that I like). My problem is this...

Once I am authenticated the my chosen login background wallpaper disappears and the screen turns  the all too familiar mucky light orangery/brown of the default human theme. It is like this for a few seconds until my desktop appears and my wallpaper comes back.

I don't mind it changing to a solid colour whilst it loads my desktop, but how can I change it to something a little more fitting with my chosen colour scheme?

---

### Post by jimerickso on 2007-11-23
you could go to /etc/gdm/PreSession/Default open it with an editor of your choice and where it say Background=dab013 or something like that change it to the number of the color you want.

---

### Post by AlistairH on 2007-11-24
Thanks Jim, that's much better. I wonder though if, since I use the same wallpaper for both the login screen and my desktop, there is a way to keep that wallpaper visible during that interim stage.

---

