---
title: "Composite Manager Errors!"
date: 2006-05-15
forum: Desktop Environments
---

### Post by CybaCowboy on 2006-05-15
When I boot-up Kubuntu, I given two errors immediately after logging in:
[i]Compostie Manager Failure - Kdialog <2>

The Compostie Manager crashed twice within a minute and is therefore disabled for this session.[/i]


And:
[i]Composite Manager Failure - Kdialog

Composite extension not found
You MUST use XOrg > 6.8 for translucency and shadows to work.
Additionally, you need to add a new section to your X config file:
Section "Extensions"
Option "Composite" "Enable"
EndSection[/i]


Firstly, what does this mean and secondly, how do I fix this without disabling KDE's translucency and shadows effects?

---

### Post by ComplexNumber on 2006-05-15
[I]> Composite extension not foundthis means that, after installing libxdamage-devel, libxrender-devel, libxcomposite-devel, add the lines that i've given below(highlighted in bold)  to your xorg.conf file.



[/I][I]
>  Composite extension not found
You MUST use XOrg > 6.8 for translucency and shadows to work. wait until you've installed dapper drake. that uses xorg 7.0.
[/I][I]

>  Additionally, you need to add a new section to your X config file:
[B] Section "Extensions"
Option "Composite" "Enable"
EndSection[/B] go to the /etc/X11/xorg.conf file, make a backup of it, then add the files above to the bottom of the file.
[/I]

---

