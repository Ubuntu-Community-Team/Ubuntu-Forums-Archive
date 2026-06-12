---
title: "Need some help with what can be done with desktop effects"
date: 2007-11-03
forum: Desktop Effects &amp; Customization
---

### Post by thenetduck on 2007-11-03
Hi

I want to be able to push a F9 and view all of my windows and also be able to push a button or click on my workspaces and view all of them (4 quads etc) Is there a way to do this? If so, how can I accomplish such a feat? 

The Net Duck

---

### Post by Locutus_of_Borg on 2007-11-03
ring switcher plugin (alt+super+tab) will let you view all windows
also shift switcher will do this.

and unfold cube (ctrl+alt+down) will show all workspaces


is that what you meant?

---

### Post by psyopper on 2007-11-04
Are you using 7.10 or 7.04. Are you using Desktop Effects or have you installed Compiz Fusion on top of it?

---

### Post by thenetduck on 2007-11-04
> **psyopper said:**
> Are you using 7.10 or 7.04. Are you using Desktop Effects or have you installed Compiz Fusion on top of it?

Hi I am using 7.10 and have not installed Compiz Fusion on top of it. Do I need to?

The Net Duck

---

### Post by thenetduck on 2007-11-04
> **Locutus_of_Borg said:**
> ring switcher plugin (alt+super+tab) will let you view all windows
also shift switcher will do this.

and unfold cube (ctrl+alt+down) will show all workspaces


is that what you meant?

What button is the super button and when I do ctrl+alt+down it just sends me to the desktop below it. 

Thanks 

The Net Duck

---

### Post by Forlong on 2007-11-04
Install ccsm: ```
sudo apt-get install compizconfig-settings-manager
```

Launch it and go to the **Scale** plugin and there to *Actions &#8594; General*
Then, next to **Initiate Window Picker For All Windows** click on **Disabled** under **Key** - there should be a message with "New Accelerator" - then hit [F9]

---

### Post by psyopper on 2007-11-04
> **Forlong said:**
> Install ccsm: ```
sudo apt-get install compizconfig-settings-manager
```

Launch it and go to the **Scale** plugin and there to *Actions &#8594; General*
Then, next to **Initiate Window Picker For All Windows** click on **Disabled** under **Key** - there should be a message with "New Accelerator" - then hit [F9]

Thanks Forlong, you beat me to it!!  :)

The "Super" key is the "Windows" key on a PC keyboard. It generally sits between the Left-Ctrl and Left-Alt keys and usually looks like the Windows "flag".  Linux enthusiasts cant stand calling it the Windows key so we refer to it as the Super key instead...

---

