---
title: "New to Ubuntu 7.10; vissual effects problem"
date: 2007-12-27
forum: Desktop Environments
---

### Post by sherv on 2007-12-27
Hello, I have installed Ubuntu 7.10 (gusty) for three or four days. When I go to Preferences -> Appearance -> visual effects and click on anything other than None ( e.g. Normal or Extra ) after a few seconds I get this message:  " Desktop effects could not be enabled".

I have read all other similar problems for the past 2 days and tried all kinds of suggestions but it still does not work. Could someone kindly help me with this. I appreciate it.

Here is some information about my labtop:

1)  Graphic card:
             ATI Radeon Xpress 1100

       by command lspci:
          VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] 

2) screen resolutions:
  
           max :   1024 x 768   rate:  86hz

3) restricted drivers management:

           ATI accelerated graphics driver                        NOT IN USE
           Atheros Hardware Access Layer(HAL)               IN USE

---

### Post by chewearn on 2007-12-27
Can you enable the ATI restricted driver?  Does it work after that?

---

### Post by sherv on 2007-12-27
Thank you for your response. No it doesn't. When I do that, then I get the other error, something like "composite extension is not found". ???

---

### Post by Gigamo on 2007-12-27
try installing Envy and installing the ATI driver with it.

---

### Post by sherv on 2007-12-27
I searched for Envy in Add/Remove applications. The only application I found was Envy24 control (control Envy24 (ice1712) based soundcards) which I don't think is the right one. Is it? Could you explain more? It's my like 5th day using ubuntu. I am not really good at working with this thing. Thank you.

---

### Post by winter_mute on 2007-12-27
First of all, don't use the ATI driver for this sort of thing.  The one in the repo's (8.37, I believe) doesn't have AIGLX, which is needed for desktop-effects.  If I remember correctly, you should be able to use the open-source 'radeon' driver with your Xpress 1100, though I've never dealt with one of these.  I'm not sure what's supported, but if it is supported with 3D, you'll be better off using that for the time being until the next release of Ubuntu, when the (hopefully) stabilized proprietary driver with AIGLX is included.

The other option is to use xserver-xgl and the ATI driver, 'fglrx'.  I would only use this option if the 'radeon' driver did not work.  The XGL method is a bit of a hack, but it works with all drivers.  You can install the XGL server on 7.10 by running first

```
sudo apt-get update	
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

```

followed by

```
sudo aptitude install xserver-xgl
```

This will automatically change GDM/KDM to using a xgl server and allow you to use the visual effects.

If you want to get more in-depth about the FGLRX driver, there's a newer version out there that may - or may not - work for you at the moment.  Here's the wiki for it:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually)

Hope this helps you.

---

### Post by chewearn on 2007-12-27
Gigamo mentioned envy, but did not provide a link; so here it is:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by sherv on 2007-12-27
Envy worked, thank you. But now when I customize my desktop for example when I choose 'cube', alt-ctrl-arrow keys do not work anymore! I don't think that's a big deal now. If there is a fast solution to that, I appreciate it if you let me know. Other than that, everything else is working. Thank you for your help.

---

### Post by sherv on 2007-12-27
NEver mind , never mind. I got that working too. Thanks everyone.

---

### Post by chewearn on 2007-12-28
Glad to hear it is working.
Please mark this thread as solved, thanks.
:popcorn:

---

### Post by zairol79 on 2008-01-04
Thanks Altalavista.. I'm also manage to enable compiz in my laptop now..but look like to graphic quality especially their text not so good.. :-) I'm new in this forum.. Hi everyone, btw.. one problem... I'm also using dell inspiron 1501 laptop with IG ATI 1100, the problem is when I boot to Ubuntu, ther is no splash screen, My screen turn black until log in windows come up.. Any idea to reconfigure it or just to disable it to text mode? Hope somebody can help

---

### Post by chewearn on 2008-01-04
> **zairol79 said:**
> Thanks Altalavista.. I'm also manage to enable compiz in my laptop now..but look like to graphic quality especially their text not so good.. :-) I'm new in this forum.. Hi everyone, btw.. one problem... I'm also using dell inspiron 1501 laptop with IG ATI 1100, the problem is when I boot to Ubuntu, ther is no splash screen, My screen turn black until log in windows come up.. Any idea to reconfigure it or just to disable it to text mode? Hope somebody can help

Have a look here:
[http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html](http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html)

---

### Post by zairol79 on 2008-01-06
Thanks again... problem solved.. Now my ubuntu boot faster because previously it keep looking the corect resolution..:guitar:

---

