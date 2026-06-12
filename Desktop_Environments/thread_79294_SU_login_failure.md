---
title: "SU login failure"
date: 2005-10-19
forum: Desktop Environments
---

### Post by AllanP on 2005-10-19
Just installed Breezy dual boot with XP; went great however when I am asked for the password after the su command; I type it in but the curser doesn't follow. I know that I am typing in the right password but, it says "Authentication failure Sorry." :confused:

---

### Post by amohanty on 2005-10-19
Is this a band new install?
AFAIK you cannot su until the root password is setup. Ubuntu allows you to sudo all su related tasks. When you use sudo you just need to provide your own password.

HTH
AM

---

### Post by AllanP on 2005-10-19
Got it "sudo passwd root" thanks a lot.

---

### Post by Marcos.Rufino on 2005-10-20
[QUOTE=AllanP]Got it "sudo passwd root" thanks a lot.[/QUOTE]

You're enabling the root login with this command. Remember that Ubuntu team doesn't recommend this. If you want to use a lot of commands that requires administrative privileges you can use "sudo -s".

---

### Post by AllanP on 2005-10-20
I am the only one using this computer; are you saying I shouldn't use root login.

Thanks, Allan (LInux newbie)

---

### Post by jamyskis on 2005-10-20
That would be an affirmative. You should only ever use root for as long as it is absolutely necessary - that means using sudo. If you really, really, really want a shell which gives you root access, write a script or create a launcher that calls 'gksudo gnome-terminal' (which strangely disappeared from Breezy, probably a security risk).

It doesn't matter if you're the only one using the computer. Actually people who use the same computer are the least of your problems. You should be more worried about people hacking in through your network connection.

---

