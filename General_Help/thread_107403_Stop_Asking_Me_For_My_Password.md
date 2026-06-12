---
title: "Stop Asking Me For My Password"
date: 2005-12-22
forum: General Help
---

### Post by pedwards on 2005-12-22
Does anybody know of a way to have ubuntu stop asking me for my password everytime i want to enter symantic, or any sort of admin gui?
i mean seriously my keys are starting to wear out!

---

### Post by towsonu2003 on 2005-12-22
Its asking for passwords is good. You needing to give password too many times is bad :)

You'll get used to it. Basically, if it asks you the pass, it means you are doing something that needs privileges, which can be very badly used by malicious code  / malintended local users. 

Be good to keys ;)

---

### Post by manicka on 2005-12-22
[QUOTE=pedwards]Does anybody know of a way to have ubuntu stop asking me for my password everytime i want to enter symantic, or any sort of admin gui?
i mean seriously my keys are starting to wear out![/QUOTE]

This is just part of the added security that Linux brings to your new environment. Unlike windows, system changes can't be made unless you allow it to happen.

---

### Post by Game_Ender on 2005-12-23
[QUOTE=pedwards]Does anybody know of a way to have ubuntu stop asking me for my password everytime i want to enter symantic, or any sort of admin gui?
i mean seriously my keys are starting to wear out![/QUOTE]

Use windows?  No seriously, the point of a true multiuser system, which linux is, is that the actions of one user cannot destroy the machine for the rest users.  Anything that affects system wide preferences or settings are password protected so your little brother, or your young child, or you malicious coworker can't screw up the entire computer.

Also like towsonu2003 said, it also means unauthorized programs (like viruses) can't screw with system files and do nasty things like on windows.

---

### Post by pedwards on 2005-12-23
hey i thought the whole idea of linux was to have a completly customizable operating system.

so why should i get used to something that i think is annoying like typing my password a billion times per session?

---

### Post by kosmic on 2005-12-23
ok if you want you can configure SUDO so it won't ask you the admin password anymore...but later don't come where cryng that your box is compromissed or is unbootable

---

### Post by codejunkie on 2005-12-23
[http://ubuntuguide.org/#usesudowithoutpasswordprompt](http://ubuntuguide.org/#usesudowithoutpasswordprompt) this guide shows how to do what your asking but use it at your own risk.

---

### Post by nocturn on 2005-12-23
[QUOTE=pedwards]hey i thought the whole idea of linux was to have a completly customizable operating system.

so why should i get used to something that i think is annoying like typing my password a billion times per session?[/QUOTE]

Because, if you didn't have to type your password to do admin stuff, any automated system (like a virus) could also do those actions and we would have Linux viruses and malware in no time.

There are ways to disable it, but I most strongly recommend against it.

---

### Post by Perfect Storm on 2005-12-23
If you're using sudo commands in the terminal the default time before it wears out is 15 min. So if you're doing something in the terminal and uses sudo you only need to type password once.

---

