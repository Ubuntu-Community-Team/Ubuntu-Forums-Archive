---
title: "[xorg] &quot;Plug and Play&quot; Mouse via evdev?"
date: 2005-08-06
forum: Desktop Environments
---

### Post by C38a7r1zvl on 2005-08-06
Good Morning everybody.

I've got a Logitech MX 900 mouse connected via Bluetooth to my Notebook. When using the ExplorerPS/2 Protocol and /dev/input/mice as a device I can connect and disconnect the mouse at any time without the need to restart Xorg but on the downside, I can't use all of its buttons since the protocol apparently is restricted to seven buttons. What really bothers me regarding this restriction is that I can't use the appropriate button to scroll up but I have to use the wheel because if released it is considered a use of button 4 which means going back in the browsing history ](*,)

So I tried the evdev protocol and concerning the buttons it worked like a charme. Unfortunately whenever I reconnect the mouse I have to restart the XServer in order to get it recognized again. Apparantly /dev/input/event3 changes to /dev/input/event4 on reconnect and /dev/input/mice doesn't work for evdev.

Here's a snippet of my config:```

        Driver          "mouse"
        Option          "Protocol"              "evdev"
        Option                 "Dev Name"      "Logitech Bluetooth Mouse"
        Option                 "Dev Phys"      "00:04:0E:XX:XX:XX"
        Option                 "Device"        "/dev/input/event3"
```

While that problem might be solved by fooling around with the udev-configuration, the more severe issue is that the XServer doesn't even start up if the mouse is not connected. NO, it's not my Core Pointer and YES, I have "AllowMouseOpenFail"            "true" as a serverflag.

Well... Any ideas? :)

Have a nice day and happy bringing humanity,
Niels.

---

### Post by mongo on 2005-10-31
i have the exact same issue with my mx518 and evdev. did u find a solution dePOLL? ;)

---

### Post by C38a7r1zvl on 2005-10-31
To cut a long story short: nope :)

---

