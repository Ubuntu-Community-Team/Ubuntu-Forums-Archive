---
title: "After upgrade, unable to run effects or Unity (fglrx, ATI)"
date: 2011-05-02
forum: Desktop Environments
---

### Post by morrisjones on 2011-05-02
When I first did the upgrade to Natty, no desktop at all would start. I could only get a text terminal login prompt. Log showed a segfault in fglrx module: "firegl_SetSuspendResumeState"

I found instructions to remove the fglrx module and install the default ATI driver.

Now I get a graphical login screen. But I must only login with "Ubuntu Classic (No effects)" in order to get a desktop. If I select Unity or Ubuntu Classic, I never get taskbars or menus and can't run any apps.

So Natty Narwahl is a big step backwards for me.  :(

What is the relevant information to provide?  The display driver is listed as RV710 [Radeon HD 4550] from ATI Technologies Inc.

Mojo

---

### Post by morrisjones on 2011-05-02
If this is relevant, glxgears brings up only a black box.

Mojo

---

### Post by morrisjones on 2011-05-02
If I select "Ubuntu" as my desktop environment, I get a black screen with a working mouse cursor, nothing else. Escape requires a hard reboot of the computer. :(

Is there a log somewhere that might have a relevant error message?

Mojo

---

### Post by morrisjones on 2011-05-02
I can add that my architecture is amd64, VGA hardware is RV710 Radeon HD 4550

---

