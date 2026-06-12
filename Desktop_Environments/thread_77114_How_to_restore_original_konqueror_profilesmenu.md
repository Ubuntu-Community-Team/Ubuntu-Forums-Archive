---
title: "How to restore original konqueror profiles/menu"
date: 2005-10-16
forum: Desktop Environments
---

### Post by Jens7677 on 2005-10-16
Hello,

I spend some time to find out how to restore the original konqueror menu/profiles since I really don't like the kubuntu konqueror light version (without breaking something).

This is what I did (as user, not as root):
cp /usr/share/apps/konqueror/konqueror-orig.rc ~/.kde/share/apps/konqueror/konqueror.rc

cp /usr/share/apps/konqueror/profiles/* ~/.kde/share/apps/konqueror/profiles/

I hope this will help someone how missed "Open Terminal" like me :) .

Regards,
Jens

---

### Post by berserker on 2005-10-16
Jens,

Thank you!  I've been trying to figure out how to do this since I upgraded to Breezy several days ago.

However, I'm still missing the right-click context menu "Copy to..." and "Move to...".

Do you know how to get those back?

TIA

---

### Post by Jens7677 on 2005-10-16
[QUOTE=berserker]Jens,
However, I'm still missing the right-click context menu "Copy to..." and "Move to...".
TIA[/QUOTE]

mmh, I have these menus if I do a right click on a folder. I don't remember if I had these before or not... May be you have to play a little bit more with the profiles and/or the rc files. I had copied the second rc-file (konq-websimple.rc or something like this) as well. I didn't noticed any difference, but may be that did the trick...

---

### Post by berserker on 2005-10-16
Could you send me your konq-simplebrowser.rc and konqueror.rc files?

I still can't get "Copy to" and "Move to".

My email address is [email]ejwahl@NOSPAMcox.net[/email] (remove NOSPAM).

Thank you!

---

### Post by Jens7677 on 2005-10-16
surely, but I haven't changed anything inside of them. Did you restarted your kde session?

---

### Post by manubreizh on 2005-10-16
hi,
maybe this can help some of you : [http://wiki.kdenews.org/tiki-print.php?page=Secret+Config+Settings#id478438]("http://wiki.kdenews.org/tiki-print.php?page=Secret+Config+Settings#id478438")
there's lots of actions for hiding or reappearing menu, bars and so on

---

### Post by arcanistherogue on 2005-10-16
Jens, you are amazing!  Thanks ALOT!

:D

---

### Post by mo_x on 2005-10-17
Thanks a lot. I really like the "Open Terminal" also. I happen to know that F4 is "Open Terminal" and F9 is "Navigation Panel" but how are new users ever going to find out.
Stripping functionality from the menu doesn't seen a good idea to me. You need to organize them well.

---

