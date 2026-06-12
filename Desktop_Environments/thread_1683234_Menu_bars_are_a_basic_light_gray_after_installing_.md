---
title: "Menu bars are a basic light gray after installing graphics card driver"
date: 2011-02-07
forum: Desktop Environments
---

### Post by JonCox on 2011-02-07
Hi,

I've just installed Ubuntu 10.10 64-bit.

It came up saying I could install 2 proprietary drivers, one for my WiFi adapter (which works perfectly) and one for my graphics card - a Sapphire AIT Radeon HD 5770 1024MB GDDR5 PCI-Express Graphics Card. The driver is called ATI/AMD proprietary FGLRX graphics driver.
Before installing this driver I was unable to have Extra Visual Effects in Appearances. However after installing (and restarting) the menu bars are now in a basic light gray mode, rather than the sleek Ubuntu black. - Although Extra Visual Effects does now work.
I've tried rebooting, and I've had a look around in ATI "Catalyst Control Center" but nothing has worked so far.


**Does anybody know what this windows mode is, how to change it back to normal and why it's doing it in the first place?**


Below is a screenshot of my computer:
[http://dl.dropbox.com/u/6920023/Screenshot.png](http://dl.dropbox.com/u/6920023/Screenshot.png)


This is also the first time I've installed Ubuntu on my computer, and am keen for it to work.
Thank you very much for your help, it is really appreciated :-)

---

### Post by Kirboosy on 2011-02-07
Are you sure the theme somehow didn't change? (System --> Preferences --> Appearance)

---

### Post by JonCox on 2011-02-07
Solution to this was found in the following answer to another question on askubuntu.com:
  
[http://askubuntu.com/questions/21305/desktop-forgets-theme/21901#21901](http://askubuntu.com/questions/21305/desktop-forgets-theme/21901#21901)

  I simply used a terminal and sudo nano'd the file in question. Simples.

---

