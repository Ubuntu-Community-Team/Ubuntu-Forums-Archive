---
title: "Stuck in limited user! HELP!"
date: 2009-03-09
forum: General Help
---

### Post by red_dreamer on 2009-03-09
I am new to Ubuntu and have made a horrible mistake...
While on my adminstrator account, the one I created with the installation, I changed the location of the account to something other than its name. Now everytime I go onto my admin user all I see is a plain background, no Gnome panel or anything. The only thing I can do now is log onto my other limited user. Is there a way to repair the damage I`ve done through terminal? What do I do? I can log on to my administrator user but all the commands and keys I`ve pressed don`t seem to have worked. I can`t open a terminal window or anything. My only hope is to try do something from the guest account.

Can I give my limited user administrative priveledges while on the limited user? Because then I can change what I did...

Thank-you so much for your help!

---

### Post by The Cog on 2009-03-09
If you boot into recovery mode, this puts you in a root prompt. From there you can use the command line to undo the damage, or if you're not that happy with the command line hten just this one command should make your limited user able to do the admin stuff.
> adduser *username* admin
and replace *username* with the user name of the limited user. This adds the user to the admin group so that he is allowed ot use sudo. Then reboot (command **init 6**)

---

