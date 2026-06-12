---
title: "Kubuntu plasma tooltips color"
date: 2021-02-13
forum: Desktop Environments
---

### Post by a2n on 2021-02-13
_[SIZE=5]intro[/SIZE]_

I have installed kubuntu this week-end and i have installed some dark theme with plasma and kvantum. 
All works fine (even the notifications) but the tooltips/right click have not the right color or have bad margin (screnshoot below).

How can i change this?

*I'm pretty ok if the solution consist to edit some config or theme file ^^*


[SIZE=5]_problem screnshoot _[/SIZE]

[IMG]https://i.stack.imgur.com/6Ou3h.png[/IMG]
[IMG]https://i.stack.imgur.com/61Ls4.png[/IMG]
[IMG]https://i.stack.imgur.com/7mtoQ.png[/IMG]

The good color would be
[IMG]https://i.stack.imgur.com/OYWpM.png[/IMG]


_[SIZE=5]system information[/SIZE]_

 - kvantum give me the possibility to have some blur in my windows i have installed the following theme : [SpectrumSpite]("https://store.kde.org/p/1473003/")
 - In plasma I have :[INDENT]- in global theme : [Ant-Dark]("https://store.kde.org/p/1464332/")
   - in plasma style : [Ant-Dark]("https://store.kde.org/p/1464332/")
   - in application style : kvantum-dark
   - gtk2 theme : breeze-dark
   - gtk3 theme : breeze
   - in window decoration : [layan]("https://store.kde.org/p/1325238") w/ no-border
   - in colors : Breeze Dark
   - in icons : [Fluent]("https://store.kde.org/p/1477945")[/INDENT]


My config : 
```

[FONT=monospace][COLOR=#5454FF]**           `.:/ossyyyysso/:.               **[/COLOR][COLOR=#5454FF]**hadock**[/COLOR][COLOR=#000000]@[/COLOR][COLOR=#5454FF]**hadock-legion**[/COLOR]
[COLOR=#5454FF]**        .:oyyyyyyyyyyyyyyyyyyo:`**[/COLOR][COLOR=#000000]           --------------------  [/COLOR]
[COLOR=#5454FF]**      -oyyyyyyyo**[/COLOR][COLOR=#000000]**dMMy**[/COLOR][COLOR=#5454FF]**yyyyyyysyyyyo-         **[/COLOR][COLOR=#5454FF]**OS**[/COLOR][COLOR=#000000]:       Kubuntu 20.10 x86_64  [/COLOR]
[COLOR=#5454FF]**    -syyyyyyyyyy**[/COLOR][COLOR=#000000]**dMMy**[/COLOR][COLOR=#5454FF]**oyyyy**[/COLOR][COLOR=#000000]**dmMMy**[/COLOR][COLOR=#5454FF]**yyyys-       **[/COLOR][COLOR=#5454FF]**Host**[/COLOR][COLOR=#000000]: 81FV Lenovo Legion Y530-15ICH  [/COLOR]
[COLOR=#5454FF]**   oyyys**[/COLOR][COLOR=#000000]**dMy**[/COLOR][COLOR=#5454FF]**syyyy**[/COLOR][COLOR=#000000]**dMMMMMMMMMMMMMy**[/COLOR][COLOR=#5454FF]**yyyyyyo     **[/COLOR][COLOR=#5454FF]**Kernel**[/COLOR][COLOR=#000000]: 5.8.0-43-generic  [/COLOR]
[COLOR=#5454FF]** `oyyyy**[/COLOR][COLOR=#000000]**dMMMMy**[/COLOR][COLOR=#5454FF]**syysoooooo**[/COLOR][COLOR=#000000]**dMMMMy**[/COLOR][COLOR=#5454FF]**yyyyyyyyo`    **[/COLOR][COLOR=#5454FF]**Uptime**[/COLOR][COLOR=#000000]: 2 hours, 53 mins  [/COLOR]
[COLOR=#5454FF]** oyyyyyy**[/COLOR][COLOR=#000000]**dMMMMy**[/COLOR][COLOR=#5454FF]**yyyyyyyyyyys**[/COLOR][COLOR=#000000]**dMMy**[/COLOR][COLOR=#5454FF]**sssssyyyo    **[/COLOR][COLOR=#5454FF]**Packages**[/COLOR][COLOR=#000000]: 1932 (dpkg), 15 (snap)  [/COLOR]
[COLOR=#5454FF]**-yyyyyyyy**[/COLOR][COLOR=#000000]**dMy**[/COLOR][COLOR=#5454FF]**syyyyyyyyyyyyyys**[/COLOR][COLOR=#000000]**dMMMMMy**[/COLOR][COLOR=#5454FF]**syyy-  **[/COLOR][COLOR=#5454FF]**Shell**[/COLOR][COLOR=#000000]: zsh 5.8  [/COLOR]
[COLOR=#5454FF]**oyyyysoo**[/COLOR][COLOR=#000000]**dMy**[/COLOR][COLOR=#5454FF]**yyyyyyyyyyyyyyyyyy**[/COLOR][COLOR=#000000]**dMMMMy**[/COLOR][COLOR=#5454FF]**syyyo  **[/COLOR][COLOR=#5454FF]**Resolution**[/COLOR][COLOR=#000000]: 1920x1080  [/COLOR]
[COLOR=#5454FF]**yyys**[/COLOR][COLOR=#000000]**dMMMMMy**[/COLOR][COLOR=#5454FF]**yyyyyyyyyyyyyyyyyysosyyyyyyyy  **[/COLOR][COLOR=#5454FF]**DE**[/COLOR][COLOR=#000000]: Plasma 5.19.5  [/COLOR]
[COLOR=#5454FF]**yyys**[/COLOR][COLOR=#000000]**dMMMMMy**[/COLOR][COLOR=#5454FF]**yyyyyyyyyyyyyyyyyyyyyyyyyyyyy  **[/COLOR][COLOR=#5454FF]**WM**[/COLOR][COLOR=#000000]: KWin  [/COLOR]
[COLOR=#5454FF]**oyyyyysos**[/COLOR][COLOR=#000000]**dy**[/COLOR][COLOR=#5454FF]**yyyyyyyyyyyyyyyyyy**[/COLOR][COLOR=#000000]**dMMMMy**[/COLOR][COLOR=#5454FF]**syyyo  **[/COLOR][COLOR=#5454FF]**WM Theme**[/COLOR][COLOR=#000000]: Layan  [/COLOR]
[COLOR=#5454FF]**-yyyyyyyy**[/COLOR][COLOR=#000000]**dMy**[/COLOR][COLOR=#5454FF]**syyyyyyyyyyyyyys**[/COLOR][COLOR=#000000]**dMMMMMy**[/COLOR][COLOR=#5454FF]**syyy-  **[/COLOR][COLOR=#5454FF]**Theme**[/COLOR][COLOR=#000000]: Breeze Dark [Plasma], Breeze-Dark [GTK2], Breeze [GTK3]  [/COLOR]
[COLOR=#5454FF]** oyyyyyy**[/COLOR][COLOR=#000000]**dMMMy**[/COLOR][COLOR=#5454FF]**syyyyyyyyyyys**[/COLOR][COLOR=#000000]**dMMy**[/COLOR][COLOR=#5454FF]**oyyyoyyyo    **[/COLOR][COLOR=#5454FF]**Icons**[/COLOR][COLOR=#000000]: Fluent [Plasma], Fluent [GTK2/3]  [/COLOR]
[COLOR=#5454FF]** `oyyyy**[/COLOR][COLOR=#000000]**dMMMy**[/COLOR][COLOR=#5454FF]**syyyoooooo**[/COLOR][COLOR=#000000]**dMMMMy**[/COLOR][COLOR=#5454FF]**oyyyyyyyyo     **[/COLOR][COLOR=#5454FF]**Terminal**[/COLOR][COLOR=#000000]: konsole  [/COLOR]
[COLOR=#5454FF]**   oyyysyyoyyyys**[/COLOR][COLOR=#000000]**dMMMMMMMMMMMy**[/COLOR][COLOR=#5454FF]**yyyyyyyo      **[/COLOR][COLOR=#5454FF]**CPU**[/COLOR][COLOR=#000000]: Intel i5-8300H (8) @ 4.000GHz  [/COLOR]
[COLOR=#5454FF]**    -syyyyyyyyy**[/COLOR][COLOR=#000000]**dMMMy**[/COLOR][COLOR=#5454FF]**syyy**[/COLOR][COLOR=#000000]**dMMMy**[/COLOR][COLOR=#5454FF]**syyyys-       **[/COLOR][COLOR=#5454FF]**GPU**[/COLOR][COLOR=#000000]: Intel UHD Graphics 630  [/COLOR]
[COLOR=#5454FF]**      -oyyyyyyy**[/COLOR][COLOR=#000000]**dMMy**[/COLOR][COLOR=#5454FF]**yyyyyysosyyyyo-         **[/COLOR][COLOR=#5454FF]**GPU**[/COLOR][COLOR=#000000]: NVIDIA GeForce GTX 1050 Ti Mobile  [/COLOR]
[COLOR=#5454FF]**        ./oyyyyyyyyyyyyyyyyyyo/.           **[/COLOR][COLOR=#5454FF]**Memory**[/COLOR][COLOR=#000000]: 2381MiB / 15883MiB  [/COLOR]
[COLOR=#5454FF]**           `.:/oosyyyysso/:.`**[/COLOR]
[/FONT]
```

---

