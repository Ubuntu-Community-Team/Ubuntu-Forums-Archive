---
title: "[SOLVED] Can't install Cold War demo"
date: 2008-07-02
forum: Gaming &amp; Leisure
---

### Post by Ryozanpaku Tiger on 2008-07-02
Hi all!

I would like to uninstall the Cold War demo. When I run ./uninstall, I get "Could not open product information for -L".

Can anyone help? Thanks!

---

### Post by Ryozanpaku Tiger on 2008-07-02
I'm sorry, there must be "UNinstall" not "install" in the header!!!

Anyway, I changed to root and tried to run uninstall again. Here is the outcome:

Could not find a usable uninstall program. Aborting.

Can anyone help? :(

UPDATE: the problem has been solved without changing to root, by directly running the uninstall program, which is given in the uninstall script.

> 
[email]user@dell-desktop:~/.lgp[/email]/installed/bin/Linux/x86$ ./uninstall coldwar_demo
Product: Cold War Demo
Installed in /home/user/coldwar_demo
Could not remove install directory: Directory not empty
Cold War Demo has been successfully uninstalled.
[email]user@dell-desktop:~/.lgp[/email]/installed/bin/Linux/x86$ 

P.S. Dear Moderator, could you please correct the name of the thread? Thank you!

---

