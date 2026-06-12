---
title: "Wacom tablet press | offset problem"
date: 2020-03-10
forum: Desktop Environments
---

### Post by 0+-. on 2020-03-10
I've recently installed Kubuntu 19.10 and sometimes, when using a Wacom tablet, there is a problem where unless the top-left corner of the window is positioned at the top left corner of the screen, tablet presses register at the wrong location, offset from the cursor position. The tablet press offset seems equal to the window position offset. This happens 100% of the time in LibreOffice programs and KNotes, and occasionally elsewhere in Kubuntu (like System Settings, Konsole and Dolphin). None of the options in Tablet Settings seems to fix it. I would really appreciate if anyone could help. :)

(Possibly related to above problem): The Application Launcher menu's scrollbars cannot be dragged with a Wacom tablet, only with a mouse. Other scrollbars work though.

---

### Post by mörgæs on 2020-03-11
With the tablet connected please run ```
lsusb
``` and post the output in CODE tags.

---

### Post by 0+-. on 2020-03-13
Here's the output:
```
Bus 002 Device 003: ID 056a:0065 Wacom Co., Ltd MTE-450 [Bamboo]
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by 0+-. on 2020-03-17
I have just tested out the latest KDE Neon (user edition) and the problem doesn't seem to exist there when testing LibreOffice Calc and other programs, so it must've been fixed (although the Application Launcher scroll bars still have a problem; I needed to drag slightly to the side of them for them to work). I guess I'll wait until 20.04 and just do an upgrade. :-\"

---

### Post by mörgæs on 2020-03-18
Good, if you are happy with the results then please mark the thread solved.

If you in the future need to dig deeper into the matter then googling the ID number marked below might help.

```
Bus 002 Device 003: ID [COLOR=#ff0000]056a:0065[/COLOR] Wacom Co., Ltd MTE-450 [Bamboo]
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

