---
title: "Dual monitor - keep positions after suspend"
date: 2010-03-30
forum: Desktop Environments
---

### Post by ElSorro on 2010-03-30
Hi all,

I'm running Ubuntu 9.10 on a Dell Inspiron 6000 laptop (intel Mobile 915 video card), with an external 19" HP monitor.

I "preferences/screen" I set the HP monitor to be on the left side. When I restart my computer, this setting is kept ok and the HP monitor works as intended (on the left side). But when I suspend the laptop and resume back, the HP monitor is moved to the right side and have to repeat the process os moving it in the preferences menu. What am I doing wrong/how can I fix it?

Thanks for your help!

---

### Post by ElSorro on 2010-04-06
Anyone?

---

### Post by alberto fanjul on 2010-11-07
sounds strange, couse I have and old graphic card and using dual screen, suspend works like a charm on ubuntu jaunty.

Anyway, as an ubuntu 10.10 users, I found a problem with suspend and dual screen, so I added his hook on /etc/pm/sleep.d/

```

#!/bin/bash

# 
# El uso de dos pantallas impide el resume. Ahora se apagarán y encenderan solas
#

function apagar {
 xrandr --output VGA-0 --off
}

function encender {
 xrandr --output VGA-0 --auto --right-of LVDS
}

case $1 in
    hibernate)
                # Suspension al disco
                        apagar
                        ;;
    suspend)
                # Suspension a la memoria RAM
                        apagar
                        ;;
    thaw)
                # recuperación desde disco
                        encender
                        ;;
    resume)
                # recuperación desde memoria
                        encender
                        ;;
    *)  echo "somebody is calling me totally wrong."
                # Llamada erronea
        ;;
esac

```I have some hooks starting with 10_* at this directory, so I called this hook 09_dual-screen couse I want this to be the very first hook executed, and gave it the same permissions as other files there: 755

See man pm-utils for config hooks at suspend/resume and man xrandr for more information about screens.

You can try the xrandr commands without suspend, until it fits your needs.

---

