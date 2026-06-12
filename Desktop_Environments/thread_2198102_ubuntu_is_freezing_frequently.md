---
title: "ubuntu is freezing frequently"
date: 2014-01-07
forum: Desktop Environments
---

### Post by 10tigger on 2014-01-07
I'm using ubuntu 12.04 LTS, and the desktop freeze frequently and I don't know why...

I think maybe the graphic driver or steam might be the problem (because the only thing that i change before the freezing started is installing nVIDIA graphic driver and steam client)
Also, when I did the last normal shutdown the desktop(before the freezing ), compiz did not turned off properly. So I think this problem might related to GUI somthing..

because of freezing i cannot use 'Oracle VM virtualBox' (it freeze every time when I run the virturalbox..)

I do not know what information is needed, but my graphic card is geforce GT 640.


p.s. when the computer freezes, I cannot do anything except press reset button because keyboard and mouse turned off

---

### Post by cincibluer6 on 2014-01-09
What driver are you using? Is it the stable one, old (173) one, or testing one?

---

### Post by 10tigger on 2014-01-10
i think i'm using 331.20. or 319

---

### Post by 10tigger on 2014-01-10
> **cincibluer6 said:**
> What driver are you using? Is it the stable one, old (173) one, or testing one?

I think i'm using 331.2 or 319
X server setting said to me it's 331.2, but if i use dpkg -l |grep nvidia, 331 and 319 both are appeared

---

### Post by cincibluer6 on 2014-01-10
Weird. But either way, those are newer versions than 304 which is tested and stable.
I would try using that one, reset your X settings (sudo sh /etc/X11/Xreset) and try that out for a bit.

Worse comes to worse, use the provided X driver.

---

### Post by 10tigger on 2014-01-12
Thanks for your advise.
After severall rebooting, everything goes to normal..... even i didn't do anything....
whatsoever, thanks a lot. I'll try 304 or current one (from the ubuntu software center) if I have the troble again.

---

