---
title: "Intel chipset compatability"
date: 2012-06-30
forum: Desktop Environments
---

### Post by AVHATION on 2012-06-30
My system is a Compaq EVO D510 with an Intel i845 chipset, 1gb RAM, 2.4GHz Intel processor and Ubuntu 12.4. It appears from forums that the Intel i845 chipset is not well suited to running Ubuntu. While the system is now at last stable enough  with Ubuntu 12.4, it is running very slowly; I believe this is to accommodate the i345 chipset.

I have found an affordable system with an Intel 865GV chipset.  Would this bring the lightning speed of Ubuntu that I used to enjoy with my previous lower spec machine? Or should I avoid Intel altogether?

---

### Post by 3Miro on 2012-06-30
You problem doesn't come from the Chipset itself, but rather the integrated video card (which is integrated in the chipset). Such an old card is incapable of supporting the Ubuntu Unity 3D interface and the Unity 2D interface will run slowly on such an old CPU.

To gain better performance, you should consider a desktop environment with low GPU and CPU requirements. Look into LXDE, XFCE and Gnome Classic. Here is a link about how to install different DE under Ubuntu:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by AVHATION on 2012-06-30
Thanks 3Miro.  Would the integrated video card on the Intel 865Gv chipset be as slow as that on the i845 do you think?

---

### Post by 3Miro on 2012-06-30
> **AVHATION said:**
> Thanks 3Miro.  Would the integrated video card on the Intel 865Gv chipset be as slow as that on the i845 do you think?

I think it would be. I think you need at least Intel GMA4500.

Give LXDE and XFCE a try, they should work fine on your hardware.

---

### Post by sudodus on 2012-06-30
> **3Miro said:**
> You problem doesn't come from the Chipset itself, but rather the integrated video card (which is integrated in the chipset). Such an old card is incapable of supporting the Ubuntu Unity 3D interface and the Unity 2D interface will run slowly on such an old CPU.

To gain better performance, you should consider a desktop environment with low GPU and CPU requirements. Look into LXDE, XFCE and Gnome Classic. Here is a link about how to install different DE under Ubuntu:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
+1

Try Lubuntu, Xubuntu and Knoppix running live sessions from a CD or USB drive. Don't install anything, only try. And decide when you can compare the performance from the live sessions.

---

### Post by AVHATION on 2012-06-30
Thanks again for the swift responses.  I have got used to Ubuntu and my son uses it too so I will look out for a machine with the Intel GMA 4500 or higher/bigger/better. If nothing turns up I'll take up the Lubuntu suggestion next.

---

### Post by AVHATION on 2012-07-10
Would this set up suit Ubuntu please: ATI X1300 graphics, Intel’s Q965 chipset?

---

### Post by 3Miro on 2012-07-10
> **AVHATION said:**
> Would this set up suit Ubuntu please: ATI X1300 graphics, Intel’s Q965 chipset?

No! Using X1300 with Ubuntu (or any Linux) is a bad idea.

Old ATI graphics cards had virtually no support for Linux. Since AMD took over, there has been huge improvement and new AMD video cards work great, however, old cards still come with bad drivers.

There was a bad AMD driver for the X1300 cards that worked, however, recently AMD dropped the support for it. The default driver for X1300 will not let you use any kind of 3D effects. Ultimately this card may work better than the old one, but not by much.

---

### Post by AVHATION on 2012-08-01
As an alternative to a better chipset than Intel i845, would either of these graphics cards suit Ubuntu please?

EN210 HD GS SILENT 512MB GRAPHICS CARD

Graphics Card: Nvidia 7900GS 256MB

---

### Post by 3Miro on 2012-08-01
> **AVHATION said:**
> 
EN210 HD GS SILENT 512MB GRAPHICS CARD


I had a card very similar to this one and it works with Ubuntu and Unity just fine. Just make sure it is compatible with your motherboard.

I don't know about 7900.

---

### Post by Sylslay on 2012-08-01
Unity,
I think intel i915 is bare min for ubuntu 12.04.

You can try Xubuntu.

I am using ubuntu 10.04 LTS on old laptop,
Siemens with celeron 2500 and intel 845GV.

PS. Latest Fedora wtih Xface and Lubuntu working fine with this spec.

---

### Post by AVHATION on 2012-08-08
Would this be any good please?
 Integrated graphics using nVidia GeForce 6150SE
Regards,
avhation

---

