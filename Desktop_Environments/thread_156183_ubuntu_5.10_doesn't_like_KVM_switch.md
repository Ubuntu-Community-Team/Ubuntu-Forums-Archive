---
title: "ubuntu 5.10 doesn't like KVM switch"
date: 2006-04-06
forum: Desktop Environments
---

### Post by bigbear on 2006-04-06
Hi All
I am a new user to Linux, I recently built another pc to run linux using a Belkin kvm switch .
I can load ubuntu and it works fine, if I switch over to windows and then go back to ubuntu and move the mouse eveything goes berserk, multiple applications keeps opening, the only way I can restart is by pulling the power plug.
Is there a workaround this problem? :-k

---

### Post by jeepmanjr on 2006-04-06
Bigbear - I run a "cheapie" 4-port KVM switch made by LinXcel I bought on eBay.  One Ubuntu box, two windows (I use the rack-mounted MS machines to control some communications and telemetry gear).  I don't have a specific answer for you other than I can switch back and forth without any issues.  Someone correct me if I'm wrong, but I believe your KVM switch must emulate a mouse and keyboard when not switched to a particular machine to prevent it from becoming "unplugged".  If this holds true, I would ensure that your switch does just that.  Try a direct connect of your mouse & keyboard, disconnect it and plug it back in.  Does the same thing happen?  If so, you'll know where to start.

This probably doesn't help you a whole lot, but my noobie 2 cents anyway.....

GOOD LUCK!!

---

### Post by qpieus on 2006-04-06
Similar problem with my KVM (2 port, don't remember manufacturer), not as extreme though. When I switch back the my kubuntu machine, the mouse scroll wheel does not work any more. The pointer moves OK and I can click on stuff, just no scroll. The mouse is a PS2 Logitech MX500.

To (temporarily) fix this, I go to terminal and type: sudo modprobe -r psmouse
(this kills the mouse completely.)
Then I type in: sudo modprobe psmouse
Now the mouse AND scroll works again.

It's quite annoying though because every time I switch from and back to the kubuntu machine I lose the scroll. I made a script file and figured out how to run it from a menu item I made for it, so it's a little less painful than actually typing in the commands, but it's still a hassle.

When I run my script to fix my mouse, the terminal box first prompts me for my password. Is there a way to have my script file enter that for me?

The script file I'm using is:

#!/bin/bash

sudo modprobe -r psmouse
sudo modprobe psmouse

I run it via the command "bash /filename"

The KDE Menu Editor for this menu item has an option box by the "Run in terminal" box that says "terminal options" but I don't know if this can help me or not (I don't know what to put in there).
Any help would be appreciated.

---

### Post by poseidon84 on 2006-07-16
My problem with kvm switches is this;

My monitor only shows upper left quarter of the screen.

any ideas?

---

### Post by ihitf13anddied on 2006-08-08
> **qpieus said:**
> Similar problem with my KVM (2 port, don't remember manufacturer), not as extreme though. When I switch back the my kubuntu machine, the mouse scroll wheel does not work any more. The pointer moves OK and I can click on stuff, just no scroll. The mouse is a PS2 Logitech MX500.

To (temporarily) fix this, I go to terminal and type: sudo modprobe -r psmouse
(this kills the mouse completely.)
Then I type in: sudo modprobe psmouse
Now the mouse AND scroll works again.

It's quite annoying though because every time I switch from and back to the kubuntu machine I lose the scroll. I made a script file and figured out how to run it from a menu item I made for it, so it's a little less painful than actually typing in the commands, but it's still a hassle.

When I run my script to fix my mouse, the terminal box first prompts me for my password. Is there a way to have my script file enter that for me?

The script file I'm using is:

#!/bin/bash

sudo modprobe -r psmouse
sudo modprobe psmouse

I run it via the command "bash /filename"

The KDE Menu Editor for this menu item has an option box by the "Run in terminal" box that says "terminal options" but I don't know if this can help me or not (I don't know what to put in there).
Any help would be appreciated.


annoying? yes.....fixes the issue? YES. thank you very much, this will work for now

---

