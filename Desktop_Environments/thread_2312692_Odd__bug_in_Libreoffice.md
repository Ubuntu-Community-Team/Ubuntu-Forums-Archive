---
title: "Odd  bug in Libreoffice?"
date: 2016-02-06
forum: Desktop Environments
---

### Post by pete0512 on 2016-02-06
I was using office write today and I tried to select a block of text with the mouse and the machine locked up (Ubuntu 14.14) not just the app the whole caboodle, ok the curser moved but nothing else worked mouse click keyboard shortcuts nix.
The only solution was a hard reboot. So I tried again using ctl-a same result cut and past seems to be impossible anybody else found this? office version  4.2.8.2

---

### Post by grahammechanical on 2016-02-06
I have had that on Ubuntu 15.10 when the OS is running on the open source video driver. It happens if we try to select more than 10 lines of text or there abouts. Is what I have found.

If you Crtl+Alt+F1 you should see a message about GPU lock up. I have an Nvidia GT220. I am now using 16.04 development branch with Libreoffice 5 and you will notice some other discouraging things.

1) Open a Writer document with a large number of pages and it takes a lot longer to load.
2) Find is a lot slower.
3) There is some sort of incompatibility between documents created in Libreoffice version 4 and Libreoffice version 5. Open the document from the earlier version and the Libreoffice menu structure will not appear in the top panel with a mouse-over. This can be solved by opening a new (blank) Libreoffice 5 document and copying & pasting the data from the earlier document and then saving the version 5 document with the same name as the earlier document. Now, that document will have a menu structure which appears in the top panel.

Regards

---

### Post by pete0512 on 2016-02-06
Ah right so if I switch to the propriety driver it should solve the problem?

---

