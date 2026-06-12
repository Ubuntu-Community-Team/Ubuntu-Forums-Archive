---
title: "Upgrade to 10.10 from 10.04 Killed X/Gnome. (ATI)"
date: 2010-10-15
forum: Desktop Environments
---

### Post by P90Puma on 2010-10-15
Just (regrettably) upgraded from 10.04 to 10.10 using update-manager, on a HP Elite HPE-110f with an ATI gfx card.

Without knowing about this:
[http://www.redshirtlinux.com/?p=308](http://www.redshirtlinux.com/?p=308)

I am having exactly this issue:
[http://askubuntu.com/questions/5972/upgrade-to-maverick-broke-the-display](http://askubuntu.com/questions/5972/upgrade-to-maverick-broke-the-display)

Purple screen after booting and when I try to drop to terminal via ALT-SHIFT-F1 my monitor shuts off, I am using the HDMI output on the gfx card.

Just grabbed a live-disc and it works fine on the live disc, wondering how to fix X/Gnome to get back to work. As I can access my files from the livedisc. 

Thanks.

---

### Post by P90Puma on 2010-10-15
Fixed by booting to recovery console and running

apt-get install fglrx

---

### Post by onexhundred on 2010-10-15
i had this problem doing the same upgrade and spent hours on google. finally, i found a work-around: put "pci=nocrs" into the kernel line in grub. (found here: [https://bugzilla.redhat.com/show_bug.cgi?id=620313](https://bugzilla.redhat.com/show_bug.cgi?id=620313))

the upgrade saved my old kernel (2.6.32) and the solution below worked with it but not really with the new 2.6.34, if i recall.

so. to test if this works: if you see the grub list when you boot, hit "e" when the kernel you want is selected. go to the line starting with "linux," hit the end button, and add this expression to the end of the line: pci=nocrs. hit ctrl-x to continue booting. (warning: i really don't know what this does but it worked great for me until i just decided to reinstall 10.04 and get working graphics.)

if this works for you and you want to make the change permanent, edit /etc/default/grub. the line you want to change should end up like this:
GRUB_CMDLINE_LINUX_DEFAULT=”*[maybe quiet splash or whatever was already here] pci=nocrs"*

now if you don't see the grub list after booting, i don't know how to make it appear but someone must.

hope this helps. let me know if anything is unclear. i'm a newbie so others should chime in if i'm leading the op astray[I]....
[/I]

---

### Post by onexhundred on 2010-10-15
ha. much more elegant solution!

---

