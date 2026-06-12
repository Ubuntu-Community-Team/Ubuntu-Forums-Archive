---
title: "Modelsim &amp; Xilinx Webpack"
date: 2006-05-06
forum: Desktop Environments
---

### Post by t.rain on 2006-05-06
Hi !

I tried Ubuntu and i think it is a very nice Linux os. For the "everyday ubuntu usage" i must use the following programs:

**Xilinx Webpack**
[http://www.xilinx.com/ise/logic_design_prod/webpack.htm](http://www.xilinx.com/ise/logic_design_prod/webpack.htm)

**Modelsim from Mentor Graphics**
[http://www.model.com/products/60/default.asp](http://www.model.com/products/60/default.asp)

But for both programms there is only a Red Hat Linux Version avialable. Is there a chance to make it run under ubuntu?

Does anybody still use this programms under ubuntu.

Thank you very much for your answers

Greetings from austria
rain

---

### Post by Ramses de Norre on 2006-05-06
Do they come in rpm? You can use alien to convert rpm to deb.
```
sudo apt-get install alien
```
Then do ```
sudo alien package.rpm
``` and it will create a deb in the same directory which you can install with ```
sudo dpkg -i package.deb
```

---

### Post by DAharon on 2006-05-07
I just installed Ubuntu on my new laptop.  Been a Gentoo user for years.  I am about to install Xilinx's WebPack on the lappy tommorrow.
On my desktop I used this guide:  [http://gentoo-wiki.com/HOWTO_Xilinx]("http://gentoo-wiki.com/HOWTO_Xilinx")
It seems pretty generic, so I am sure it will work out alright.

BTW, I am pretty sure that WebPack 8.1i has a simulator built in, so you might be able to do without ModelSim.

---

### Post by hecato on 2006-10-16
(delete, wrong thread)

---

