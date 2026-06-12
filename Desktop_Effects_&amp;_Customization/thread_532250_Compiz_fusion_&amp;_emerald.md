---
title: "Compiz fusion &amp; emerald"
date: 2007-08-22
forum: Desktop Effects &amp; Customization
---

### Post by orange2k on 2007-08-22
Ok Ive followed the official guides. They stop where it comes to making compiz-fusion and emerald start on startup. Ive read further and added "compiz --replace" to startup programs and also added "emerald --replace" to it.
Compiz starts fine, but emerald doesnt - I still have to alt+F2 and type emerald --replace.
Then it works. But why must I do it everytime I start the computer?

Oh, and one more thing: since Ive installed compiz-fusion, it gives me an update of compiz-core to update - Ive updated, but the update message keeps comming back... WTF?

---

### Post by orange2k on 2007-08-22
Nevermind - Ive uninstalled compiz-fusion and emerald for now...
It does not provide much more than eyecandy anyways...
Gonna try it in a few months, when Gutsy comes out...:guitar:

---

### Post by Netsurfer on 2007-08-22
I'm waiting for the same problem for update manager.

To solve the problem of **emerald theme manager**  you have to install "desktop-effects" also.

>sudo apt-get install desktop-effects         (or use synaptic)

Next select **System > Preferences > Desktop Effects** and activate them.

Alternatively you can activate it using [COLOR="Red"]gconf[/COLOR] > **desktop/gnome/applications/window_manager** setting default as **/usr/bin/compiz**.

Next, logout and login to check configuration. If all is OK, open System > Preferences > Sessions

and add just "**emerald --replace &**" (remove "compiz --replace" if present)

Logout and login again.
All done!

---

