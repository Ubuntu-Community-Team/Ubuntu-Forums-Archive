---
title: "gksudo nvidia-settings"
date: 2008-04-06
forum: Desktop Effects &amp; Customization
---

### Post by parablood on 2008-04-06
This command that allows you to customize your monitor displays with nvidia geforce cards worked in gutsy appears to no longer work with hardy.

The command is: 

```
gksudo nvidia-settings
```

Does anyone know what the command is to get into hardy beta's nvidia-settings is?

thanks,

Parablood

---

### Post by tamoneya on 2008-04-06
it is because nvidia-settings is not installed```
sudo apt-get install nvidia-settings
```

---

### Post by FuturePilot on 2008-04-06
Yes in Hardy they moved the nvidia-settings to a separate package. Before it was included with the driver itself.

---

### Post by parablood on 2008-04-06
ahh I see thanks a lot appreciate you guys.

---

