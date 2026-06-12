---
title: "Prevent a specific device from automounting."
date: 2012-09-09
forum: Desktop Environments
---

### Post by bwinfrey on 2012-09-09
Hello, I would like to prevent my android phone from auto-mounting.  Can I do this without affecting other auto mount devices?

When debugging is turned off on my phone it will mount a partition for windows drivers.  It's a pain because the window grabs focus.

I was thinking there may be a file that I can use to blacklist this device/partition.

Thank you.

Regards,
Brian

---

### Post by mcduck on 2012-09-09
Every Android phone/Tablet I've sued has had an option to configure what happens when you connect it to a computer, including an option to default to charging only, or to ask what to do, both of which should prevent your problem.

Another possible option would be to stop Ubuntu from opening a window when you plug in removable devices, just mounting it int the background instead. I'm not at my Ubuntu system at the moment, but if I rember right you should get the option to configure that when you plug in the device. (If not, take a look at the file manager's options, and if it's not there then probably in the Control Center).

Configuring a single drive to nout mount automatically is quite an easy trick to do with permanently conencted drives, you'd just add the drive in /etc/fstab, and use the "noauto" option for it. But I doubt that would work for a removable devices such as your phone, so you'd probably have to edit some udev config file to add a rule for the device. So I'd recommend trying the above options first...

---

### Post by LewisTM on 2012-09-09
To obtain fine control over what the OS does when a user plugs in a given USB device, your will have to familiarize yourself with udev rules.

Cheers!

---

### Post by bwinfrey on 2012-11-03
> **LewisTM said:**
> To obtain fine control over what the OS does when a user plugs in a given USB device, your will have to familiarize yourself with udev rules.

Cheers!

I appologize for some reason I never saw a notification for your response.  Thank you.  I will check out udev.

---

