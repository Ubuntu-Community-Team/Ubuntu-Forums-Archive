---
title: "driving test software for UK"
date: 2005-10-29
forum: Desktop Environments
---

### Post by davidhall on 2005-10-29
Does anyone know of some driving test software available for UK.

I have some windows software but since I only run Ubuntu on my PC I was looking for  a Linux version.

Any help appreciated.

PS I am a Linux newbie

---

### Post by magnusbb on 2005-10-29
My tip is to install the very latest beta of WINE. It's really good!

Add 

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

to your /etc/apt/sources.list

Do a "sudo apt-get update" and a "sudo apt-get install wine". Then run "winecfg" and finally "wine ------.exe".

---

### Post by Hairy_Palms on 2005-10-29
would it happen to be the official DVLA cdroms with the hazard perception test too? ive got that, it worked fine under crossover office so wine should work, just make sure you install flash first as it relys heavily on flash

---

### Post by davidhall on 2005-11-12
Tried wine,
Installs OK but then I just get a small black window which when clicked closes and exits.
fixme:d3d:IWineD3DSwapChainImpl_Present Unhandled present options 0x7fb1f06c/(nil)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock

lots of these.

Are there any software titles under Linux for driving test theory?

---

