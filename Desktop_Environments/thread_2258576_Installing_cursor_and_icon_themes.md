---
title: "Installing cursor and icon themes"
date: 2014-12-28
forum: Desktop Environments
---

### Post by DanBender on 2014-12-28
Hello! I have xubuntu installed on my son's laptop, and would like to install a Minecraft cursor theme for him (he loves it).

I downloaded [this theme]("http://gnome-look.org/content/show.php/Minecraft+Cursors+Theme?content=140649"), and extracted it into /user/share/icons. It did not appear in the icons selection page of the Appearance settings.
I created a /home/jason/.icons folder and copied it to there. It did not appear in the icons selection page of the Appearance settings.

I followed the instructions in the readme, and edited the "Inherits" entry in /user/share/icons/default/index.theme to read "minecraft" instead of "DMZ_White". This works!
However, it changes it for all users. Is there a way to do this properly so my "daddy" admin account and the login screen use normal cursors, and the minecraft theme can be selected for him only?

Thanks for any pointers you can provide.

Also, is there any functional difference between and xfce session and an xubuntu session? The only difference I see is that the applications menu in an xfce session is better-populated, making that better for me (admin) and the xubuntu better for him (user). All the launchers and other things seem to be identical between sessions. Any tips on editing and customizing his applications menu would also be welcome. I haven't looked into this at all in the documentation; it's by far the less important question. Thanks!

-dan

---

### Post by Dennis N on 2014-12-29
Putting the cursor folder into the user's ~/.icons would be the correct place. You change the cursor in Xubuntu in **Settings > Mouse and Touchpad > Theme Tab**, not **Appearance > Icons**.  Revert the change you made to the index.theme file first.

Make the choice of the new cursor from the user's account. It will change in certain places, such as in Firefox or Libre Office, and will not change in other places, such as over the panel and certain other applications. Those places probably are still governed by cursor set by the administrator account. This is not really what you want. If you really want a different cursor for another user working in all places, it can be done correctly in Ubuntu Mate instead of Xubuntu. I have tried it out and it does work. If there is a way to do the same in Xubuntu, I haven't seen it.

---

