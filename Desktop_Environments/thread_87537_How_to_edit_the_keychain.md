---
title: "How to edit the keychain"
date: 2005-11-08
forum: Desktop Environments
---

### Post by afonit on 2005-11-08
I have searched and cannot see how to edit passwords and locations in the keychains.


I mount a couple servers with ssh, and for one of them I typed in the wrong password,  

and for that one, when i try to mount it again it says 'access denied'  - undobtably due to its having the wrong password.


how can I edit the keychain or even just clear it out and start from scratch again?

I have tried to completely remove openssh and ssh, then reinstall, this did not work.

any ideas?

---

### Post by Ampersand on 2005-11-08
There might be something in .gnome2/keyrings in your home folder. I've not got anything in there to test it on my computer, but removing files from there should help.

---

### Post by afonit on 2005-11-08
[QUOTE=Ampersand]There might be something in .gnome2/keyrings in your home folder. I've not got anything in there to test it on my computer, but removing files from there should help.[/QUOTE]



That did it, thanks.


could not open it with text editor, 

but i was able to delete it, then enter my passwords.

Thank you for your assistance.

---

### Post by kalin on 2005-11-08
FYI you could also use a GUI application called Keyring Manager (the package name is gnome-keyring-manager).

---

### Post by rossellamj on 2005-11-30
I  managed to create another keyring using the keyring manager, but when I open the application it keeps popping up wanting the default keyring password and I cannot remember it... does anybody know how to reset it?
Thanks.
R

---

