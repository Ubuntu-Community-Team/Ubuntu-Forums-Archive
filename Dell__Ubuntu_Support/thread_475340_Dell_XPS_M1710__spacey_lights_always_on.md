---
title: "Dell XPS M1710  spacey lights always on"
date: 2007-06-16
forum: Dell  Ubuntu Support
---

### Post by showgun22 on 2007-06-16
When you turn on the XPS M1710 there is those lights all around the case that stays on all the time now as well as the XPS finger pad.
Dell had a program to set up those lights change color or even turn them off which is nice they get to be annoying after a while and I am also eat some battery life. So is there something for us Ubuntu user to at least turn them off <BG> Or is there something in the plan by Dell ? or the Ubuntu people?

Ps will there be software support by Dell?

Thanks

---

### Post by mike999999 on 2007-06-18
> **showgun22 said:**
> When you turn on the XPS M1710 there is those lights all around the case that stays on all the time now as well as the XPS finger pad.
Dell had a program to set up those lights change color or even turn them off which is nice they get to be annoying after a while and I am also eat some battery life. So is there something for us Ubuntu user to at least turn them off <BG> Or is there something in the plan by Dell ? or the Ubuntu people?

Ps will there be software support by Dell?

Thanks

You can turn off the lights in the bios.

---

### Post by dmarsh on 2007-06-18
There actually exists a utility to set these lights, although I don't think it currently works for the touchpad.  Google for 'libsmbios'- it includes a utility called dellLEDCtl that can set the color and intensity of the lights...

You have to compile it yourself, though- I didn't find any Ubuntu packages for it.

Update: Here's the URL [http://linux.dell.com/libsmbios/main/index.html]("http://linux.dell.com/libsmbios/main/index.html")

Update2: I lied- a not-quite-up-to-date package is available for feisty through synaptic/apt-get.  Try either 'apt-get install libsmbios-bin', or search in synaptic for libsmbios.  Not sure if the LED utility is included, but if not, manually install the newer package available at the previous URL...

---

### Post by trinity.treize on 2008-05-14
And if you don't like to meddle with the shell [there's a gui]("http://xpsledchanger.sourceforge.net/").

---

