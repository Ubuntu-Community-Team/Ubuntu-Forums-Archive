---
title: "Graphics Card"
date: 2009-05-16
forum: General Help
---

### Post by megamouthbolt on 2009-05-16
Can somebody take the time to find me the graphics driver for my card? 

It's Nvidia, and I'm running x32 bit.

```
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6150SE nForce 430 (rev a2)

```

---

### Post by taurus on 2009-05-16
Your card doesn't show up in System -> Administration -> Hardware Drivers?

---

### Post by megamouthbolt on 2009-05-16
Reading a little more, I found out I could do that.

However, I get this:

   SystemError: Failed to lock /var/cache/apt/archives/lock

Other people fixed it by closing synaptic, but I dont have synaptic open, unfortunately.

Can you help?

---

### Post by paradigm2 on 2009-05-16
> **megamouthbolt said:**
> Reading a little more, I found out I could do that.

However, I get this:

   SystemError: Failed to lock /var/cache/apt/archives/lock

Other people fixed it by closing synaptic, but I dont have synaptic open, unfortunately.

Can you help?

do you have anything else open like the update manager?  apt-get going in another terminal?

If not, Its probably easiest to just simply reboot.

---

### Post by megamouthbolt on 2009-05-16
Sure. I'll try that

---

### Post by megamouthbolt on 2009-05-16
Guess what?

It worked!

Thank you so much

---

### Post by megamouthbolt on 2009-05-16
Sorry to bother you guys again, but now I'm getting this error:

SystemError: E:I wasn't able to locate a file for the googleearth package. This might mean you need to manually fix this package. (due to missing arch)

This whole thing was based on trying to get googleearth to work better, BTW

---

### Post by taurus on 2009-05-16
Just add Medibuntu repo and install GoogleEarth from there.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by megamouthbolt on 2009-05-16
That isn't the problem. I already have google earth installed, it's just that is says that google earth isn't compatible with my driver.

I'll just uninstall it, I guess

---

### Post by taurus on 2009-05-16
Did you install an nVidia driver for your graphic card?

---

### Post by megamouthbolt on 2009-05-16
I just fixed it by uninstalling it, the reinstalling it after updating my drivers.

Thx!

---

