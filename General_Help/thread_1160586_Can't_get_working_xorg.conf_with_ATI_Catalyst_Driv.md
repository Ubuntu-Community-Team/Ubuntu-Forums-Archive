---
title: "Can't get working xorg.conf with ATI Catalyst Driver"
date: 2009-05-15
forum: General Help
---

### Post by HunterThomson on 2009-05-15
Thankyou for reading this.

I have never set up an xorg.conf file and am having problems.

I have a laptop with a Mobility FireGL 5700 (which is a Redeon HD 3650)
My screen is 1650x1050
HP elitebook 8530w MobileWorkstation

I tried to just coppy otherpeopels xorg.conf with no luck.

[http://scribute.com/2009/03/arch-linux-ati-catalyst-xorgconf/](http://scribute.com/2009/03/arch-linux-ati-catalyst-xorgconf/)

and this one with out the "ImputDevice" sections

[http://www.vinceliu.com/xorg.conf-dual](http://www.vinceliu.com/xorg.conf-dual)

I get the same error for both>>>

```
Data incomplete in file /etc/X11/xorg.conf
Undefined Screen "Screen 1" referenced by ServerLayout "Default Layout"

(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal sever error:
no screens found
```

When I run fglrxinfo I get this>>>
Error: unable to open display (null)

I am using Arch Linux and I do have fglrx in my Modules array.

---

