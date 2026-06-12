---
title: "Brand new Dell studio 15 boots to white screen, any help appreciated"
date: 2008-10-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jyper on 2008-10-20
Got a Dell studio 15, it boots but gdm doesn't work(white screen). Switching Virtual terminals brings up text based login,ctrl alt backspace seems to restart X. Anybody with similar problems, how did you fix them?

---

### Post by superm1 on 2008-10-20
Sounds like you have one with AMD graphics perhaps?  If so, try to switch to a VT and kill compiz.real.  Then make sure your AMD graphics driver is properly setup.

---

### Post by jyper on 2008-10-20
How  do i reconfigure the driver

---

### Post by jyper on 2008-10-20
Compiz isn't running I can't get to GDM

---

### Post by superm1 on 2008-10-20
Well if compiz.real isn't running, then this might be a bigger problem.  Was this a preloaded system?  If so, i'd recommend just reinstalling from the grub menu.

Can you confirm what graphics card came with it though?

---

### Post by jyper on 2008-10-20
preloaded

Reinstalled from ubuntu/Dell disk text based install and it still does it( basic graphics(BIOS/Command line. etc. working and the Dell recovery Boot-graphics check which has normal graphics(Windows program like box that can be moved with mouse worked so I wouldn't think it was a Hardware issue).

---

### Post by superm1 on 2008-10-20
> **jyper said:**
> preloaded

Reinstalled from ubuntu/Dell disk text based install and it still does it( basic graphics(BIOS/Command line. etc. working and the Dell recovery Boot-graphics check which has normal graphics(Windows program like box that can be moved with mouse worked so I wouldn't think it was a Hardware issue).
Interesting.  Well did oem-config come up properly the first time?

---

### Post by jyper on 2008-10-20
Intel Graphics Media Accelerator X3100 
ubuntu studio 15 dell  all parts standard I think

---

### Post by jyper on 2008-10-20
oem-config? Do you mean the reinstall in the grub menu option?


i reinstalled from DVD

---

### Post by jyper on 2008-10-20
Still doesn't work.

---

### Post by superm1 on 2008-10-20
I mean on the first boot, did you get a wizard asking you for your user name and password, or is that where the white screen is?

---

### Post by suncoolsu on 2008-10-22
I am having similar problems. A white screen appears after the bootscreen. My config is same Graphics Media accelerator X3100 and Intel Core 2 Duo Processor on a dell studio 1535.

If I try booting in safe mode (after using the install under windows option) then the desktop shows - but after checking certain errors it says - Root not set up .. and then it wont go further. 

Please help, I am new to linux.

Is it a graphics card problem?

Thanks

---

### Post by Ubugreen on 2008-10-22
I just recieved the same system, and the same problem-except that the white screen turns to 3 vertical partitions/color lines-black-and white.
I downloaded and burned a new cd ubuntu 8.04 for 64 bit and installed from that disc. Same problem, but then I did it in graphics safe mode and it worked. I got the "root not set up message" as well. I went back and did the guided partition, but changed the size of the first one to 4 gigs, and I was able to install.
Now I just need to work out the screen size issue-I'm stuck at 800 x 600
hope this helps,I'm as new as you...

---

### Post by suncoolsu on 2008-10-22
Ditto - I have the same problems :(. Think I received replies from other posts which point to the fact that the developers need to fix this problem :-(. I dont know as I am a no0b

---

### Post by bearbigears on 2008-10-23
I have a precision M4300 which i dual boot with windows( for the wife). I install compiz and got the same problem. I fixed the problem, when the grub menu came up i entered the recovery mode and it gave me a text based start up. At the end a screen came up and one of the choses was to fix x server. i chose that one and it booted correctly and fixed the problem. I tried to install compiz  again and the same problem occurred again. did the same ting again and viola it fixed it. I have never reinstalled compiz again.
hope this gives you a  start.
B

---

### Post by romandas on 2008-11-10
Well, given that I've read posts of people with the same problem I have (White screen of death on a Studio 1535 with Intel Graphics 965 and the X3100 preloaded with Ubuntu) and I have also read others who have reported no problem at all, I decided to let Dell send me a new one and see if it works.

I mean, they can't all be broken, right? :) Nice thing is, I get to hold onto the first one until the new one arrives, so any ideas on a fix.. let me know, I can test them.

And to me, using the vesa driver isn't a "fix". It's a bandaid. I'd like to know why the intel driver doesn't seem to work, yet the hardware test (Fn + Power on) shows no errors.

---

### Post by wonderbriefs on 2008-11-12
I let Dell send me a new one.
Now I have two that boot up to the White Screen of Death.
I've installed in safe mode with Vesa drivers which gets me 800x600. Then I installed KDE which gets me 1024x768.
Any attempt at using the Intel driver gives me the White Screen of Death again.
I've emailed Dell about this and apparently will be hearing back from their "Escalation Team."
I've compiled a list of at least 10 other users who have had the exact same problem. Dell should not be able to say that they sell Ubuntu Preinstalled when they don't even test to make sure the laptops are running.
In the meantime I'm also emailing Canonical about this. Since they certified Dell in selling Ubuntu Preinstalled, it looks like they've dropped the ball as well. I've managed to locate email addresses for Mark Shuttleworth: Founder of Ubuntu, Jane Silber: Director of Operations, Matt Zimmerman: CTO, and Chris Kenyon: Director of Operations.
The way I see it, Dell and Canonical are both making money off of a product that is being sold without testing and are in effect gaming the users out of their cash. Whether this is intentional or not, I can't determine. I just can't justify spending the over $200 for Canonical support to fix a problem that Dell sold me out of the box. So I'm going all the way to the top with this. Should they fail to fix the problem, I will do my best to turn this into a news story. People should be warned that Dell isn't even attempting to test their software before shipping.

---

### Post by suncoolsu on 2008-11-12
Thanks a lot - we needed a brave and determined person like you :D .. I think this will fix the problem pretty soon. :) 

Thanks a lot .. Thanks a lot ..

Hope that it doesnt disappoint the developers out here :).

---

