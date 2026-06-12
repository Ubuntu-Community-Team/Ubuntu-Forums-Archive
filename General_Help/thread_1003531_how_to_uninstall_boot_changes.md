---
title: "how to uninstall boot changes"
date: 2008-12-06
forum: General Help
---

### Post by rseeker on 2008-12-06
Hi,  

I'm about to try Wubi for the first time.  It all looks great, and it seems like the only way I might be screwed is if I couldn't boot into Windows any more.  Like, if something went wrong with my boot configuration and it would no longer execute the boot menu.

So, my only question is, if I needed to, how would I remove the boot menu if for some reason it's not working, and get back to the way it was before installing Wubi?  (XP Pro SP3.)

(I hope this question makes sense.  It's just that this is my only computer, and if I can't use this one then I'm stuck schlepping over to the library for net access.  I realize Wubi is a great product with a lot of happy users, but I might screw something up on my end.)

Thanks!

---

### Post by Sealbhach on 2008-12-06
You can uninstall Wubi just like any other Windows program:

[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)


.

---

### Post by rseeker on 2008-12-06
> **Sealbhach said:**
> You can uninstall Wubi just like any other Windows program:

[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)


.

Yeah but I mean if something is wrong/misconfigured with the boot menu and I can't boot into windows.  Would there be a way to take the boot menu back out of the picture so it boots straight into windows again?

---

### Post by ago on 2008-12-06
> **rseeker said:**
> Yeah but I mean if something is wrong/misconfigured with the boot menu and I can't boot into windows.  Would there be a way to take the boot menu back out of the picture so it boots straight into windows again?

If you can't boot into windows at all try to run chkdsk /r from the recovery console. You will have to boot using the windows setup CD.

---

### Post by Jammanuser on 2008-12-06
> **rseeker said:**
> Hi,  

I'm about to try Wubi for the first time.  It all looks great, and it seems like the only way I might be screwed is if I couldn't boot into Windows any more.  Like, if something went wrong with my boot configuration and it would no longer execute the boot menu.


That's not the **only** way u might be screwed! ;) Just a little headsup...if u get the same "crc error, system halted" error message that i got (after about...a WEEK?) than you wont be able to boot anymore into Ubuntu...and the only way to "fix" it then, it appears, is to reinstall wubi! Just wanted to give u something to think over before u try Wubi... ;)
> **rseeker said:**
> 
So, my only question is, if I needed to, how would I remove the boot menu if for some reason it's not working, and get back to the way it was before installing Wubi?  (XP Pro SP3.)


You wont have to remove the boot menu...Wubi simple modifes ur **existing ** menu, when u install it, and it adds Ubuntu 8.10 to it! ;)

Cheers! :)

-jammanuser

:D

---

