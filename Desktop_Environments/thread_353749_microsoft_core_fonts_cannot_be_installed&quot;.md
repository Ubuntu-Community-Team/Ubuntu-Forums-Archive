---
title: "microsoft core fonts cannot be installed&quot;"
date: 2007-02-05
forum: Desktop Environments
---

### Post by cephlon on 2007-02-05
I just did a fresh install of Ubuntu, and I am just going through the normal set up routine. I tried to install the Microsoft Core Fonts, but I get the following error:

Microsoft Core Fonts cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.

Any suggestions?

---

### Post by renzokuken on 2007-02-05
how did you try and install them?

there is a deb about somewhere called msttfcore or something that does it for you. i cant remember if its in the repos or not. have a search in synaptic

---

### Post by bapoumba on 2007-02-05
```
Package: msttcorefonts
State: installed
Automatically installed: no
Version: 1.2ubuntu3
Priority: optional
Section: multiverse/x11

```

You need to add multiverse repositories to your sources.list:

[https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096")

---

### Post by cephlon on 2007-02-05
ahh, i see now. Thanks for that. Maybe there should be a link in the error message or let people know that they need to enable this feature. Just a suggestion...

---

### Post by ShortyMac on 2007-02-19
I just installed 6.10 Edgy and encountered this same error. This OS is slightly different, and I'm not quite sure what to do. Any suggestions?

---

### Post by bapoumba on 2007-02-19
@ ShortyMac: the link in my previous post explains how to enable the multiverse repositories. Let us know if you have any problem.

---

### Post by ShortyMac on 2007-02-19
Yeah, I checked the link and my pc's menu and settings are a little bit different. I got it figured out, and the link did help. Thanks!

---

