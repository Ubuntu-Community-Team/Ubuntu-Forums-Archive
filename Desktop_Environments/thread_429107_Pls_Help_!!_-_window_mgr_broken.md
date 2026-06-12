---
title: "Pls Help !! - window mgr broken"
date: 2007-04-30
forum: Desktop Environments
---

### Post by goneskiing on 2007-04-30
After using suspend it broke the user manager - windows cannot be moved, resized, or have the manager icons missing.   The workspaces are gone.   Other user accounts on the same machine are okay.  If I try to go to the menu |System|Window Manager => it gives an error - window manager not valid for user "unknown"  - is there a config file that can be fixed ?  thks

---

### Post by Turin Turambar on 2007-04-30
Same thing happened to me. There are no menu borders.

So far I'm very UNhappy with Feisty. Lots of bugs. It even crashed when I tried to copy one archive. :(

---

### Post by llamakc on 2007-04-30
Did you have Desktop Effects enabled?

---

### Post by goneskiing on 2007-05-01
> **llamakc said:**
> Did you have Desktop Effects enabled?

No.  btw I have a Lenovo laptop running the Intel graphics chip.  Some of the other posts discussed the nvidia aglx fixes but I don't think that applies.  Since it is in just one user account, the post about /.gnomerc made sense except there is no .gnomerc file in that user account - maybe it's under something else.   This is really hurting me so any help would be great.

---

### Post by llamakc on 2007-05-01
There's no .gnomerc file, but sometimes wiping clean & deleting ~/.gconf ~/.gconfd ~/.gnome ~/.gnome2 ~/.gnome2_private has helped me in the past.

---

### Post by Turin Turambar on 2007-05-01
I corrected the problem by enabling the desktop effects. Even when you disable it later, it will work.

---

### Post by Sunflower1970 on 2007-05-01
Try adding metacity to the startup menu. That fixed the problem for me.

---

### Post by goneskiing on 2007-05-02
> **Turin Turambar said:**
> I corrected the problem by enabling the desktop effects. Even when you disable it later, it will work.

thank you - this is how I finally fixed it too.   First I typed metacity in the terminal - this restores the windows functionality.  Then I enabled the effects, then disabled them - then logged out.  When I logged back in, everything worked fine again.

---

