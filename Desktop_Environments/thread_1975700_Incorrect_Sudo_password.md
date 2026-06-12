---
title: "Incorrect Sudo password"
date: 2012-05-07
forum: Desktop Environments
---

### Post by Callumgw on 2012-05-07
Hi,
I recently upgraded (actually complete clean install!) the home server from Kubuntu-Desktop on UbuntuServer 10.04 to Lubuntu-Desktop on UbuntuServer 12.04.  The box it runs on has a inbuilt graphics card with not power so Lubuntu is working better than Kubuntu did. But I have some little issues to work through, the one I can't find anything on is an odd behaviour for the sudo password.

When I use sudo on the command line everything is fine, when I put the sudo password into the desktop synaptic, everything is fine.

However, I got an error mesage and asked if I would like to report it, so I said yes and it started the reporting process and popped up a password box. I entered my password and it return as "incorrect password".  I tried a few more times before quitting out of the error reporting. This has happened half a dozen times since and I have tried "remember for this session" and "save in wallet" but none of these options change things.
I have also found that if I "open this folder as root" in the file manager (pcmanfm) I getthe same password request box and the same error (incorrect password).

This only happens in this windowed box and the sudo password works everywhere else. It even works if I launch pcmanfm from sudo in the commandline.

Any ideas how to fix this?

Cheers,
C

---

### Post by wojox on 2012-05-07
You need a Launchpad Account to file a bug. Try your Launchpad password next time you report a bug.

Also check which "Groups" you belong to.

---

### Post by Callumgw on 2012-05-07
oh, I dont think I have a Launchpad password.....also that wouldn't explain why it wont let me "open as root" in the gui for pcmanfm......
Let me check groups, is there a lubuntu desktop sudo group I need to be in?

Cheers
C

---

### Post by wojox on 2012-05-08
> **Callumgw said:**
> .....also that wouldn't explain why it wont let me "open as root" in the gui for pcmanfm......


:p That's why I didn't give you a definitive answer. :lolflag:

One problem at a time though, what about the Launchpad account?

---

### Post by Callumgw on 2012-05-08
Ok I have one now. Will try it tonight.

C

---

### Post by Callumgw on 2012-05-09
Alright I found the problem, had to do with "gksu" vs "sudo".
I ran this:

Code:
gksu time-admin

in terminal and it proved gksu was the issue because it caused an error, then followed this link to the fix:
[http://ubuntuforums.org/showthread.php?t=1424299](http://ubuntuforums.org/showthread.php?t=1424299)

C

---

