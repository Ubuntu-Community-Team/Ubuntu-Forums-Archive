---
title: "Real-time ~/Desktop -or- user homedir.d system?"
date: 2007-10-01
forum: Desktop Environments
---

### Post by lns on 2007-10-01
Hi all,

I'm facing the support issue of creating specific mandatory Gnome desktop icons for a school with ~200 student user accounts. The teachers want certain mandatory desktop icons for everyone such as FF, OOo, etc etc... There are many already existing users, as well as more that will be added at a future date.

How can this be accomplished? I've searched around and it doesn't look like gconf is a good answer for custom and/or mandatory desktop icons, a 'for /home/*' script won't work very smoothly for newly created users (or the fact that the icons must change at a later date), etc... 

Is there any way to incorporate similar functionality of the C:\Documents and Settings\All Users concept in the M$ world in Gnome (or even user homedirs in general)? I was thinking something like 'include /home/allusers.d' would be really nifty.

Ideas? Thanks, all! :KS

---

### Post by KyleRaynor on 2007-10-04
I'm not too aquainted with bash script yet.
but if you add a script or piece of code to /etc/bash.bashrc that checks for those icons and adds them if missing, it will automatically run whenever they login.
just make sure the icons are readable to all and are in something like /usr/share/pixmaps
the seudo would be
<code>
if ! ff then
cp /usr/icons/ff $HOMEIR/Desktop/ff
fi

if ! OOo then
cp /usr/icons/OOo $HOMEDIR/Desktop/OOo
fi
</code>
then just make sure the files are read/execute only, and that the kids can't delete or modify them. or if that's a major problem, leave out the if's and the links will automatically be created whenever they login.

---

