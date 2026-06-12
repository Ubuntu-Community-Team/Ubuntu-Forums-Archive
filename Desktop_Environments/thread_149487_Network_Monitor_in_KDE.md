---
title: "Network Monitor in KDE"
date: 2006-03-24
forum: Desktop Environments
---

### Post by krypto_wizard on 2006-03-24
is there any Network Monitor in KDE like in gnome ?

How to setup weather in KDE.

Please help the new KDE user.

---

### Post by Jucato on 2006-03-24
Can you please give a link to the GNOME screenshot you mentioned in your other thread?
There are two ways to add weather/network monitors.
One is to add them in the panel/task bar. Another is to add them on the desktop itself, but requires you to install a widget app similar to gDesklets. Which one are you asking for?

Next time, please be a bit more patient and wait for an answer before creating a new thread with exactly the same topic in the same place? :D

---

### Post by krypto_wizard on 2006-03-24
I want to learn both i.e create on panel as well as on desktop.

could u give some pointers for that



[QUOTE=Fenyx]Can you please give a link to the GNOME screenshot you mentioned in your other thread?
There are two ways to add weather/network monitors.
One is to add them in the panel/task bar. Another is to add them on the desktop itself, but requires you to install a widget app similar to gDesklets. Which one are you asking for?

Next time, please be a bit more patient and wait for an answer before creating a new thread with exactly the same topic in the same place? :D[/QUOTE]

---

### Post by Jucato on 2006-03-24
On the Panel - you basically have to enable/install some panel applets for this to work.
1. Network Monitor is already installed by default, as far as I know.
2. Weather monitor - you have to install the kweather package (use Synaptic, Adept, or apt-get)
Then, right click on an empty space in the Panel, choose Add Applet to Panel, and add the Network Monitor and Weather applets.

On the desktop: you have to install something called Superkaramba. It's found in the repositories (Universe section I think). Once it's installed, you have to download themes for it, similar I guess to gDesklets. Lots of Superkaramba themes can be found in [http://www.kde-look.org](http://www.kde-look.org) under the Karamba section.

---

### Post by krypto_wizard on 2006-03-24
I could not find Network-Monitor in the panel. I searched it a lot.

I installed Superkaramba. Now how to install theme. I got few themes on that website kde-look.org


I wanted to customize my desktop something like these images found in the image section gallery of KDE.





[QUOTE=Fenyx]On the Panel - you basically have to enable/install some panel applets for this to work.
1. Network Monitor is already installed by default, as far as I know.
2. Weather monitor - you have to install the kweather package (use Synaptic, Adept, or apt-get)
Then, right click on an empty space in the Panel, choose Add Applet to Panel, and add the Network Monitor and Weather applets.

On the desktop: you have to install something called Superkaramba. It's found in the repositories (Universe section I think). Once it's installed, you have to download themes for it, similar I guess to gDesklets. Lots of Superkaramba themes can be found in [http://www.kde-look.org](http://www.kde-look.org) under the Karamba section.[/QUOTE]

---

### Post by Jucato on 2006-03-24
There's only one Superkaramba theme that's being used there. It's name is Liquid Weather. You can find that in KDE-Look.org. There are instructions on how to install these themes (on the same page where you got the theme from) but usually it just involves these steps:
1. Untar the .tar.gz file you downloaded
2. Inside that there will be a .theme file. Click on that and it will launch the Superkaramba theme.

Take note that some Superkaramba themes have special install instructions that you must follow. Just check the KDE-look page. They usually have those kinds of instructions.

Have you successfully installed the KWeather plugin for the KDE Panel? I'll check whether the Network Monitor needs to be installed too.

---

### Post by krypto_wizard on 2006-03-24
I couldn't find Kweather. I have installled SuperKaramba and I think I should be able to install.

I have always heard that KDE is better than Gnome from my friends and I was always struggling to configure it.



[QUOTE=Fenyx]There's only one Superkaramba theme that's being used there. It's name is Liquid Weather. You can find that in KDE-Look.org. There are instructions on how to install these themes (on the same page where you got the theme from) but usually it just involves these steps:
1. Untar the .tar.gz file you downloaded
2. Inside that there will be a .theme file. Click on that and it will launch the Superkaramba theme.

Take note that some Superkaramba themes have special install instructions that you must follow. Just check the KDE-look page. They usually have those kinds of instructions.

Have you successfully installed the KWeather plugin for the KDE Panel? I'll check whether the Network Monitor needs to be installed too.[/QUOTE]

---

### Post by Jucato on 2006-03-24
It's not that hard to configure. It just works differently from GNOME. And Kubuntu has not installed some features by default that could be found in other KDE distros (MEPIS has the network monitor) or in Ubuntu.

You can't find KWeather? it's in the main repositories. it's name is kweather. you can install it like this:
```
sudo apt-get install kweather
```

The network monitor is a bit more complicated. You have to enable your universe repositories first. (But since you were able to install superkaramba, I guess it's already enabled). The package name is knetload
```
sudo apt-get install knetload
```
It's not added to the panel like KWeather (sorry, I presumed it was), you have to run it as a separate app, but it gets added to your panel. that is, run
```
knetload
```

---

### Post by krypto_wizard on 2006-03-25
KNetDockApp is a better network monitor than knetload..thats what I thought.

[QUOTE=Fenyx]It's not that hard to configure. It just works differently from GNOME. And Kubuntu has not installed some features by default that could be found in other KDE distros (MEPIS has the network monitor) or in Ubuntu.

You can't find KWeather? it's in the main repositories. it's name is kweather. you can install it like this:
```
sudo apt-get install kweather
```

The network monitor is a bit more complicated. You have to enable your universe repositories first. (But since you were able to install superkaramba, I guess it's already enabled). The package name is knetload
```
sudo apt-get install knetload
```
It's not added to the panel like KWeather (sorry, I presumed it was), you have to run it as a separate app, but it gets added to your panel. that is, run
```
knetload
```[/QUOTE]

---

