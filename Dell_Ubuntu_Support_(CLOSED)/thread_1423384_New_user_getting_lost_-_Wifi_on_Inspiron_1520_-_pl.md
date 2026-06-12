---
title: "New user getting lost - Wifi on Inspiron 1520 - please!!!!"
date: 2010-03-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Shakespeare1 on 2010-03-06
I have been trawling through Google for a few hours it seems now trying to find a fix to get the wifi working on my Dell Inspiron 1520.  I have tried a couple of helps, putting in coding into a terminal, but am not confident that the fixes are right for the version of ubuntu i have or my computer - there seems to be an assumption of knowledge in most cases.   Can anyone help a complete newbie to ubuntu?  I am coming from Vista and need a step-by-step process to follow. 

So: As I say, I have an inspiron 1520 with a Dell wirelss 1390 WLAN mini card.  Broadcom 440x 10/100 intergrated controller. 

I am connected to internet using wired ethernet connection at the moment, so something is working in there.

I have just installed unbuntu 9.10 Karmic Koala as a dual boot.  Apart from this glitch, seems great!

Any help much appreciated.

---

### Post by bobcollard on 2010-03-06
> **Shakespeare1 said:**
> I have been trawling through Google for a few hours it seems now trying to find a fix to get the wifi working on my Dell Inspiron 1520.  I have tried a couple of helps, putting in coding into a terminal, but am not confident that the fixes are right for the version of ubuntu i have or my computer - there seems to be an assumption of knowledge in most cases.   Can anyone help a complete newbie to ubuntu?  I am coming from Vista and need a step-by-step process to follow. 

So: As I say, I have an inspiron 1520 with a Dell wirelss 1390 WLAN mini card.  Broadcom 440x 10/100 intergrated controller. 

I am connected to internet using wired ethernet connection at the moment, so something is working in there.

I have just installed unbuntu 9.10 Karmic Koala as a dual boot.  Apart from this glitch, seems great!

Any help much appreciated.
In your Menu under Administration find "Hardware Drivers" and open that.  Most Dells have Broadcom cards as yours does.  There should be two choices, the second one Broadcom STA is the one you want.  To "Activate" it you need your Ethernet plugged in.  Afterwards reboot as it tells you.  Next find the Icon in your Task bar for the Internet, probably looks like two Monitors diagonally connected.  Open that with a click and under the Wireless Tab. "Add" your ISP Information.  Don't overdo it. Just basic Info.  Make sure two things are checked (Autostartup) and (For All Users).  Then get back to me with the good news.

---

### Post by Shakespeare1 on 2010-03-06
Thanks.  Problem is that nothing comes up when I go into Hardware Drivers.

Not sure if relevant, but wifi works fine from within Vista

---

### Post by bobcollard on 2010-03-06
> **Shakespeare1 said:**
> Thanks.  Problem is that nothing comes up when I go into Hardware Drivers.

Not sure if relevant, but wifi works fine from within Vista
Open Terminal and use the Following Command:
                                 ```
sudo apt-get install b43-fwcutter
``` Then reboot and follow the rest of the earlier post.

---

### Post by Shakespeare1 on 2010-03-06
Fantastic.  Thank you very much!
Sent from a wifi connection!

---

### Post by bobcollard on 2010-03-06
> **Shakespeare1 said:**
> Fantastic.  Thank you very much!
Sent from a wifi connection!
You are Welcome.  Please go to your first post and "Edit" the Title by adding [Solved] so others may benefit.

---

