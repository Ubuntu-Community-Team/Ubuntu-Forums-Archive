---
title: "Problems with Keyboard Layouts"
date: 2010-10-29
forum: Desktop Environments
---

### Post by ernsttremel on 2010-10-29
I installed 3 keyboard layouts (German, Hindi, Tamil)
(cf. "Tastatureinstellungen.png")
But they are not displayed at the panel above correctly.
Instead of as "German, Hindi, Tamil" they atre displayed as bullies like "*, *, *".
If I click on "Add" there is not displayed any alternative for choising out of installed languages and their keyboard layouts.
But only cf. "wählen.png".
I guess there is something wrong with the keyboard-layout-feature on my Ubuntu10.10 installation.
Is there any possibility to repair this feature?
If so, which one?
Thanks in advance for tips and helping
Ernst

---

### Post by ernsttremel on 2010-10-29
I'll add some more screen shots to illustrate the problem.
Which keyboards are installed
cf. 1.png
Options are empty
cf. 2.png
So can this - I call it "incorrect" behaviour - bug to be solved any how or is it required to install Ubuntu10.04 and Ubuntu10.10 totally new.

PS:
By the log-In-Procedure before having inputted my password there are 5 choicable keyboard layouts shown:

layout de 
layout in (Variant bolnagari)
layout in (Variant tam)
layout ir (Variant avestan)
layout us
--------------------
Andere ... i.e. Others ....

If I click "Andere ... i.e. Others ...."
it opens a window called "Keyboardlayouts" but this window is empty

---

### Post by ernsttremel on 2010-11-04
I think it is a problem with the 
keyboard layout indicator plugin.
This is defect on my computer.
Is there a possibility to repair or replace it.
And if so, how to manage it?

---

### Post by gesy on 2010-11-04
I found a satisfying solution ! See my next post.

---

### Post by gesy on 2010-11-05
I found an almost perfect solution by upgrading gnome-settings-daemon to version 2.32.0-0ubuntu3.

This is the link:

[https://launchpad.net/ubuntu/+source/gnome-settings-daemon/2.32.0-0ubuntu3/+build/1995395](https://launchpad.net/ubuntu/+source/gnome-settings-daemon/2.32.0-0ubuntu3/+build/1995395)

Rectification: it's not almost and not at all perfect: the applet doesn't show the current layout most of the time. I tried LinuxMint based on Ubuntu 10.10 and the applet works perfectly (but not GCstar which seems incompatible with LinuxMint. That's why I will stay with Unbuntu).

---

### Post by ernsttremel on 2010-11-06
Thank you.
But I don't know;
What have I to do to upgrade?

I'm rather new in using Ubuntu.

Have I tu use the Termial?
If so, which commands have to be used?

---

### Post by gesy on 2010-11-07
You just have to download the deb file:

[https://launchpad.net/ubuntu/+source/gnome-settings-daemon/2.32.0-0ubuntu3/+build/1995395/+files/gnome-settings-daemon_2.32.0-0ubuntu3_amd64.deb](https://launchpad.net/ubuntu/+source/gnome-settings-daemon/2.32.0-0ubuntu3/+build/1995395/+files/gnome-settings-daemon_2.32.0-0ubuntu3_amd64.deb)

and double click on it. That will launch the Ubuntu Software Center and press the "Install" button.

As I said, it is "almost perfect": I have to press once on the key I have assigned to change the layout the first time I type to allign the layout's order as the applet doesn't show the right layout in use. After that, it will run as it should.

---

### Post by ernsttremel on 2010-11-08
Thank you for your instructions.
But I do not have installed a 64 bit system.
My system is 32 bit.
Please have a look at the attached error message.

---

### Post by ernsttremel on 2010-11-27
The only way to resolve this problem was to install Ubuntu 10.10 totally new.
Thanks for all your suggestions and tips.

---

