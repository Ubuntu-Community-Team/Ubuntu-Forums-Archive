---
title: "I've got GRUB and Windows booter- how can I hide GRUB?"
date: 2008-12-20
forum: General Help
---

### Post by d-d-d-d-d-d-card on 2008-12-20
I recently started editing GRUB, under the impression my PC would boot via that at startup (I have dual boot ..Ubuntu and Vista)..

Now, when I boot up my PC.. the usual ista OS selector comes up.. and when I choose ubuntu, a horrible looking GRUB comes up straight after. I realise now that I only wish for the Vista one to be visable at startup, the last thing I want is for Ubuntu to have a slower startup time than it already has...

I've tried selecting 'HIde GRUB' in GrubEd, but to no luck.. any idea on how I can make my PC dual boot just from the Vista dual boot screen as before, eg reverse the proccess of making GRUB visable at startup?

CHeerrss!

---

### Post by TeXtonyx on 2008-12-20
You can remove Ubuntu from Vista boot menu with Easybcd. Or,
you can have it boot Ubuntu and change the menu.lst timing down 
to 1 or 0 seconds and it will automatically boot your default 
Ubuntu setting (the first one usually). That is done in menu.lst 

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5  <---(change that to 1 or 0)

You can install grub to the MBR which replaces the Vista bootloader
and there should be an entry for booting Vista in menu.lst

That will still invoke the Vista bootloader, but again you
can change the timer setting to 1 or 0 and it will quickly
continue to Vista.

The problem with making the timer work so fast is that you
don't have time to pick another boot option on the menu.
So you have to go back and change the timer setting to a
few seconds if you want time to pick a different boot option
than the default. 

When Vista is in the MBR, then you get the Vista bootloader
at startup. That means you needed to install grub to the
/boot partition of Ubuntu, the other choice is the MBR. That 
choice comes up in Step 7, Advanced, with the live cd install.
Or you manually reinstall grub their later.

I wasn't quite sure from your post that Ubuntu was actually
booting from the Vista bootloader or you were getting an error
message after choosing Ubuntu. If you can boot Ubuntu, then
changing the timer setting to 0 should work.

---

