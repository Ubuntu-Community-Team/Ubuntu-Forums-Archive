---
title: "So much for an easy fix...."
date: 2009-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by AtlantaBob on 2009-05-21
I'm running 9.04 on a Dell Vostro 1500. I'm running into the "laptop killing hard drive bug."

I've followed the instructions @ [https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement) by essentially adding "ENABLE_LAPTOP_MODE=true" in to the (otherwise blank file) /etc/default/laptop-mode, and then running "sudo /etc/init.d/laptop-mode restart"

Yet I still get the increasing load count when I run "sudo smartctl -a /dev/sda|grep Load_Cycle_Count"

Any advice? Thanks....

---

### Post by Gausian on 2009-05-21
this feature is built into your hdd to keep it from being damaged during movement.  it is normal to have an increasing count, as long as it isnt at too fast of a rate.

a couple an hour isnt anything to worry about.  a few a minute, and you may need to implement the fix.

---

### Post by AtlantaBob on 2009-05-21
Right, this is a few a minute. And I've implemented the "fix" but it doesn't appear to work....

---

### Post by anjilslaire on 2009-05-21
have you rebooted?

---

### Post by AtlantaBob on 2009-05-21
Yeah, I have... unfortunately, no difference. Even after running the restart acpi command (I checked it both ways).

Now that I think about this, it's an upgraded 8.10 installation (now 9.04) but from the sites I've googled it still looks like that entry is the only one that is needed.

Can anyone else confirm that the file would otherwise be blank? I was a little surprised to see that there wasn't an existing file of the same name...

---

