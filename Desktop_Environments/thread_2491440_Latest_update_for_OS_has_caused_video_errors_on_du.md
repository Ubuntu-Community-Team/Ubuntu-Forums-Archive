---
title: "Latest update for OS has caused video errors on dual screens"
date: 2023-10-09
forum: Desktop Environments
---

### Post by makem2 on 2023-10-09
I installed the latest Ubuntu update to my Ubuntu 23.04 today and now the default screen is blank. At first both screens were blank even though the computer was running. I rebooted the machine and all I got was a black left screen and the Ubuntu default background. Another reboot saw the sign-on box appear and disappear. Another reboot and I was able to sign in but the left screen remains blank. If I open a web page it opens on the left screen but is not visible.

I have had this happen in the past and it is cured by re-setting the Nvidia drivers but this time the usual nvidia-settings page does not open. On that page I can choose which screen is default but now those options are missing. This is the output from the Nvidia settings command:

```
makem@makem-22:~$ sudo nvidia-settings
[sudo] password for makem: 

ERROR: An internal driver error occurred


(nvidia-settings:10255): GLib-GObject-CRITICAL **: 10:16:02.156: g_object_unref: assertion 'G_IS_OBJECT (object)' failed

** (nvidia-settings:10255): CRITICAL **: 10:16:02.157: ctk_powermode_new: assertion '(ctrl_target != NULL) && (ctrl_target->h != NULL)' failed

ERROR: nvidia-settings could not find the registry key file or the X server is not
       accessible. This file should have been installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The application
       profiles will continue to work, but values cannot be prepopulated or validated,
       and will not be listed in the help text. Please see the README for possible values
       and descriptions.

** Message: 10:16:02.178: PRIME: No offloading required. Abort
** Message: 10:16:02.178: PRIME: is it supported? no


```

Can I get any assistance please?

Edit: I keep having the sign in box appear at random intervals.

---

### Post by makem2 on 2023-10-09
Fixed.

Incomplete dpkg install.

Unplugged second monitor and opened synaptic. Synaptic showed the error and gave the command needed to fix the installation.

---

