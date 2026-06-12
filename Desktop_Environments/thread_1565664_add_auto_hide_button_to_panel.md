---
title: "add auto hide button to panel"
date: 2010-09-01
forum: Desktop Environments
---

### Post by taamir on 2010-09-01
Hi, I want to add auto hide button or check-box to a panel.
any way to do it ?

---

### Post by taamir on 2010-09-02
Bump

---

### Post by Frogs Hair on 2010-09-02
Right click the panel and go into properties and you will find the setting there.

---

### Post by Frogs Hair on 2010-09-03
I think I misunderstood your question . I went to the add to panel menu and selected add custom launcher, but was unable to create a command to activate my auto hide launcher. I think it is because auto hide is a setting in properties and not an application like menu applications. 

I also tried to add an location launcher for panel properties and the message returned was "operation not supported."

---

### Post by taamir on 2010-09-04
Is There no way to make a command that changes settings in properties ?

(Maybe I need a new thread for this).

---

### Post by adrianoellero on 2010-11-24
same need
thanks for helping me

---

### Post by Frogs Hair on 2010-11-24
This won't create a button , right click panel go to properties and check show hide buttons, to hide panel select the arrow or line on either side of the panel.

---

### Post by asmoore82 on 2010-11-25
I made this script a while back, it still functions as of 10.04:
```
[COLOR="Blue"]#!/bin/bash
#HidePanels
#  This file is in the Public Domain.[/COLOR]

count=0

while read line
do
    keys[[COLOR="Red"]$((++count))[/COLOR]]=[COLOR="Purple"]"[COLOR="Red"]${line}[/COLOR]/auto_hide"[/COLOR]
done <<EOF
$( gconftool-2 --all-dirs [COLOR="Purple"]"/apps/panel/toplevels"[/COLOR] )
EOF

old=$( gconftool-2 --get [COLOR="Red"]${keys[1]}[/COLOR] )

case [COLOR="Purple"]"[COLOR="Red"]$old[/COLOR]"[/COLOR] in
    [COLOR="Purple"]"0"[/COLOR] | [COLOR="Purple"]"false"[/COLOR] | [COLOR="Purple"]"False"[/COLOR] )
        new=[COLOR="Purple"]"true"[/COLOR]
        ;;
    * )
        new=[COLOR="Purple"]"false"[/COLOR]
        ;;
esac

for key in [COLOR="Purple"]"[COLOR="Red"]${keys[@]}[/COLOR]"[/COLOR]
do
    gconftool-2 --set [COLOR="Purple"]"[COLOR="Red"]$key[/COLOR]"[/COLOR] --type bool [COLOR="Purple"]"[COLOR="Red"]$new[/COLOR]"[/COLOR]
done

[COLOR="Blue"]#End of File[/COLOR]
```

---

### Post by adrianoellero on 2010-11-25
how can I use it in Ubuntu?

sorry but I'm not familiar with Linux yet

---

### Post by asmoore82 on 2010-11-26
You would have to save this in a text file and grant it executable permissions.
You could then create a custom launcher with it as the target.

---

