---
title: "NVIDIA X Server Settings"
date: 2009-07-30
forum: Desktop Environments
---

### Post by Menyus on 2009-07-30
My system is running Ubuntu 9.04 64-bit, nvidia driver 180.44, After configuring nvidia for dual screen (twin view) in the NVIDIA X Server Settings application and clicking the "Save to X Configuration File" button, I get the following error message:

"Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'."

Because I am unable to save the changes, after every reboot I have to redo configuration for the second screen. Is there a way work around this?

Thanks,

---

### Post by manlypain on 2009-07-30
run the nvidia-settings with sudo
so
sudo nvidia-settings

it worked for me

---

### Post by Menyus on 2009-07-30
Ah, magic! It worked for me too :) Thanks for the advice.

---

