---
title: "Khotkeys not working?"
date: 2005-12-31
forum: Desktop Environments
---

### Post by JamesNorris on 2005-12-31
Is it just me, or is it impossible to bing "print screen" to KSnapshot in Breezy? I have always used this shortcut for ksnapshot and have never ever had it not work. It works in gnome (with gnome's equivalent of kss) but not in kde. Since I rarely ever use gnome it would be nice to get this working. I have tried binding the button to both the kmenu command and the terminal command for ksnapshot, but when I press print screen, nothing happens. 

Anyone any idea what I need to do?

---

### Post by daller on 2005-12-31
According to the manpage, I don't see any trigger arguments...

I have the "print screen"-button open ksnapshot, but what you want is to save the print when clicking, right?

---

### Post by JamesNorris on 2005-12-31
All I want it to do is launch ksnapshot. But it doesn't even do that.

---

### Post by GeneralZod on 2005-12-31
Very odd - I just tried binding Print Screen to ksnapshot in the kmenu, and it works fine.  I've no idea why it's not working for you; sorry :/

---

### Post by daller on 2005-12-31
Does khotkeys recognize the button? (You are using it through system settings, or kcontrol, right?)

Did you type in "ksnapshot" in the command field?

I did this:

Enter khotkeys in system settings!

Press "New action", and enter a name for it! ("Print Screen")

And choose action type: "Keyboard Shortcut -> Command/URL (simple)"

Go to "Keyboard Shortcut", press the "none"-button, and press "Print Screen" - the label "Print" should now appear!, Press "OK"

Go to "Command/URL settings".

Enter "ksnapshot", and press "OK" (If it fails with ksnapshot, try "/usr/bin/ksnapshot")

What does the button do now?

---

### Post by JamesNorris on 2005-12-31
Seems to work fine now. Thanks. Dunno why it never worked before, but it's nice to have this back!!

---

