---
title: "how to disable powersave"
date: 2010-11-25
forum: Desktop Environments
---

### Post by vsespb on 2010-11-25
hi.

i've stopped/killed/uninstalled all power related stuff
like powernow, powerd, upowerd, acpid, gnome powermanager

also turned off APM and ACPI support in bios.

and after that I still have a problem:

my display's backlight turned off after a long period of inactivity and there is no way turn it on.
(sometimes kill of Xorg helps, sometimes alt-ctrl-f1/atl-control-f7 however I need about half hour to get my backligh back)

question is what I missing ? - how to check I indeed removed all power related stuff.

---

### Post by vsespb on 2010-11-26
1. This night i tried the following:

"xset -dpms" + make sure "xset q" prints DPMS disabled.

with that disabled DPMS it slept again !

2. seems series of commands over ssh like

xset +dpms
xset dpms force off
xset dpms force on

woke it up

any ideas ?

---

