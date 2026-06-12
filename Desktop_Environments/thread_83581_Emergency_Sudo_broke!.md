---
title: "Emergency: Sudo broke!"
date: 2005-10-29
forum: Desktop Environments
---

### Post by MistaED on 2005-10-29
Hello, I've been setting up ubuntu boxes recently, and decided to partimage a complete ubuntu install + customization, etc. to make it easier & fast to get ubuntu PC's up and running. The problem I have now is I created a new user because I couldn't rename the default user, (I created it in Users & Groups in Gnome) and I made sure the new user can do administration, then I removed the old user. Now this new user can't do any sudo functions and the root account is disabled (ubuntu default).

So I'm asking, how can I get sudo back?? I looked in knoppix in the /etc/sudoers file (chrooted the ubuntu install) but I'm not sure what to put in there.

Thank you.

---

### Post by Trab on 2005-10-29
ubuntuguide.org has some ideas how to recover sudo funtions if lost (mostly from live cd i think) hope that helps

---

### Post by stuporglue on 2005-10-29
I did the same thing as you about a year ago. :-) I ended up just enabling the root account...not the best option, but it worked. 


[QUOTE=MistaED]So I'm asking, how can I get sudo back?? I looked in knoppix in the /etc/sudoers file (chrooted the ubuntu install) but I'm not sure what to put in there.[/QUOTE]

You're on the right track. Here's something that will work, so that you don't get discouraged. It's not the "right way", but it'll get you back in. :-) 

Chroot back in, then run 

passwd root

It'll make you able to log in as root in the Ubuntu boot, at least on the console. Might not let you log in graphicly as root, but at least you'll be in, and won't need Knoppix.

---

### Post by Remmelas on 2005-10-29
make sure your new user is part of the adm group, required for sudo functionality

---

### Post by MistaED on 2005-10-29
> make sure your new user is part of the adm group, required for sudo functionality

Yeah, I made sure I checked that, but oddly it didn't go through (possibly a bug?). I managed to fix it by adding the user to /etc/sudoers manually under knoppix/chroot, copying the admin entry but naming it the user, so all is well with the world again :) Thank you all!

---

