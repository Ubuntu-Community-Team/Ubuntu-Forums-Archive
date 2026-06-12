---
title: "Customizing view menu from folders"
date: 2015-08-12
forum: Desktop Environments
---

### Post by rob141 on 2015-08-12
Hello everyone,

I would like to know if there is any way to actually customize the standard menu from within a folder. What i mean is that for example, if i would like to edit the file or the view menu, can that be done !

The thing i really want to do is to hide the option ( show hidden files ) from the view menu and only use the keyboard shurtcut  ctrl + h to show or hide my files and folders. 

How may i remove or hide the option ( show hidden files ) from the view menu please ?

I am using ubuntu version 14.04 with xfce4

Thank you very much.

---

### Post by workshopsystems on 2015-08-13
install xdotool

```

sudo apt-get install xdotool

```

create a custom thunar action and enter the below command and select all the boxes 
```

xdotool key "ctrl+h"

```

and you can create scripts or use commands to achieve what ever else you want with thunar actions

---

### Post by rob141 on 2015-08-13
Thanks, this may help but will i be able to remove the option:  show hidden files   ?  from the view menu ?

---

