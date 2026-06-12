---
title: "Where is Bootloader Administration Tool ?"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Vilius on 2006-06-02
I noticed now that new gui installer(6.06) gives no options about configuring bootloader.
So I decided to configure it after installation. 
Found some gui tool 'Bootloader Administration Too'l, but I can't fing a way to lounch it. Manual states that:

Applications menu
    Choose System Tools &#8594; Boot.
Command line
   Execute the following command: boot-admin

there in no such menu 'system tools', command line can't recognize boot-admin command.

How can I configure boot loader ???

thanks
Vilius

---

### Post by Ramses de Norre on 2006-06-02
```
sudo updatedb && locate boot-admin
``` should show you the location of the binary.
Search for just boot if it doesn't find something, maybe the name changed without the manual being updated..

---

### Post by az on 2006-06-02
Boot-admin is part of the source but is dissabled (not built) because it is buggy.

---

### Post by dolson on 2006-06-09
The documentation should not list such things. This is confusing to users.

---

