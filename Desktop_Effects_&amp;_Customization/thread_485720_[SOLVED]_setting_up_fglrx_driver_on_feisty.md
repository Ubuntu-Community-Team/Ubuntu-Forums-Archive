---
title: "[SOLVED] setting up fglrx driver on feisty"
date: 2007-06-27
forum: Desktop Effects &amp; Customization
---

### Post by dbbolton on 2007-06-27
i'm using an ATI Radeon Xpress 200M card. i've had beryl working on this computer on dapper and edgy- now i'm running feisty.

first, i got the driver from [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) as suggested on [http://compiz.org/ATI](http://compiz.org/ATI) .  i ran the installer and everything when fine.

however, when i ran "aticonfig --initial" i got a 'core dumped' error, and manually edited my xorg.conf file to include the flgrx driver under the device section. i also added the options suggested on [http://compiz.org/ATI](http://compiz.org/ATI) .

when i run 'fglrxinfo', i still get the Mesa stuff, not ATI. and i'm getting this error:
```
$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(EE) AIGLX: Screen 0 is not DRI capable

```
since i've had beryl working on this computer, i think that error is probably itself erroneous. 

so, would i be better off installing fglrx from the ubuntu repos? if so, how do i uninstall whatever was installed by the ATI installer?

---

### Post by pedrogl on 2007-06-27
I've installed ati driver on my laptop following these howto:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")
It works for me.

---

### Post by dbbolton on 2007-06-27
> **pedrogl said:**
> I've installed ati driver on my laptop following these howto:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")
It works for me.
this link was very helpful. thank you :)

---

