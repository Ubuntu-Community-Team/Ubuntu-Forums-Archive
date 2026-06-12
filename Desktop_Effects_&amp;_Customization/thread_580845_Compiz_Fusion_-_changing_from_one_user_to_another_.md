---
title: "Compiz Fusion - changing from one user to another then back crashes system"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by proxess on 2007-10-19
I have two user accounts both with compiz fusion enabled. I'm on my first account and I use the new menu thing to change user. All goes well.
When I use it on the other account, or when I simply ctrl+alt+f7 (or whichever terminal X is on) the whole system completely hangs. Anyone know what this is and how to fix it?

---

### Post by superyounan1 on 2007-10-19
theres an option somewhere (sorry, i tried to find it) that lets you specify whether X is restarted when you log out or not. Dig around or search the forum for that option then toggle it, see if it helps. Sorry, thats all i can think of.

---

### Post by proxess on 2007-10-19
Ahh sorry I didn't say things properly. I don't log out, I simply change user. When I change back to the first user, the system hangs.

I want to be able to use graphics rendering seeing that my cpu is rather old and slow and i only use gpu for video. I want to keep my user account up and running while someone else uses the other account, but still with gpu rendering. 

Any way about this?

---

### Post by sdowney717 on 2007-10-19
you have ATI video card?
means lots of trouble for you.
I cant do that either, neither can I do any 3D apps.
Then I read that the only ATI linux developer was fired, so now more and more delays for better drivers.
Only solution is for me to dump bad ATI card and get Nvidia.

---

### Post by jsully1 on 2007-10-19
This is a known bug with Xorg - it happens with both ATI and nVidia, and I'm not aware of any fix in progress :(
[https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/112518](https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/112518)

---

### Post by sdowney717 on 2007-10-19
supposedly, the lone linux ATI programer, pre released the upcoming driver and got canned.

ATI only has 1 linux programmer ?

---

### Post by proxess on 2007-10-19
Good to know ATI is being worked on... or sometimes... but I have an MSI Geforce 4 Ti4800 SE 128mb

---

### Post by proxess on 2007-10-20
Well I got a temporary work-around for this. The problem seems to be when you log back into an account with compiz fusion.

simply log into a tty, kill compiz through its pid, and change into the account. Then you can run compiz again or run metacity. If you don't understand what I said, I can make a step-by-step guide.

---

