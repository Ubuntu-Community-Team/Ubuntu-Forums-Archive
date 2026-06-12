---
title: "How to use wine"
date: 2006-06-08
forum: Desktop Environments
---

### Post by sbu on 2006-06-08
Good day all!

I am using 5.10 Breezy bagder and have installed wine from a source(a .deb file released in october 2005).Now all I need to know is how install a windows program.I downloaded the wine file to my desktop and used the following command in the terminal to install:
cd Desktop
sudo dpkg -i <winefilename>.deb

To test if it works,I've tried to install a windows program it by just double clicking on a setup.exe file but I recieve a message that says:'<file> cannot be displayed'
Can anyone help me?,please note my pc is currently not connected to the internet. :(

---

### Post by dmizer on 2006-06-08
what are you trying to get working in wine?

since you said you have no net, is it safe to assume that you are trying to install the driver for your wireless network adapter?

if so, you can't make it work in wine, you'll have to use ndiswrapper.

---

### Post by rado_london on 2006-06-08
Try typing in terminal
```
wine /pathtofile/setup.exe
```

GOOD LUCK

---

### Post by an.echte.trilingue on 2006-06-08
Just to get terms straight, what you did is not installing from source... that would mean you did something like something like [this]("https://wiki.ubuntu.com/BuildingWineFromSource").  Rather, you installed the binary .deb package from a source other than the repositories.

To get wine working, follow the instructions outlined [here]("https://wiki.ubuntu.com/Wine").  For a specific example, [this]("https://wiki.ubuntu.com/DVDShrink?action=show&redirect=HowToRunDVDShrinkWithWine") details how to get DVD Shrink working under wine.

I must stress, though, that wine is not easy to use and that you should try to use Ubuntu native alternatives if you can.  Be sure to read the[Installing Software]("https://wiki.ubuntu.com/InstallingSoftware") page and the [Adding Repositories]("https://wiki.ubuntu.com/AddingRepositoriesHowto") page.

---

