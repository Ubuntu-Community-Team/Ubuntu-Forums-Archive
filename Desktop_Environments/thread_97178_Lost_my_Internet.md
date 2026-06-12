---
title: "Lost my Internet"
date: 2005-11-30
forum: Desktop Environments
---

### Post by ewtesterman@cox.net on 2005-11-30
Okay I have been using Ubuntu for about 3 months. The internet has been working fine after I used ndiswrapper to for my wifi card on my notebook. I closed out of windows with the button for the wifi turned off and then started Ubuntu and turned it back on. Now I cannot get onto the net, I have tried to reinstall ndiswrapper and reconfigure my wifi setting with no luck. please Help.

---

### Post by quietglow on 2005-11-30
Is your card being recognized? What interfaces show up when you "ifconfig"? Or, if you open System>Administration>Networking does your card show up?

Have you checked if ndiswrapper is properly loaded? 

```
lsmod
```

and see if it shows up.

---

### Post by ewtesterman@cox.net on 2005-11-30
I have checked all of that and it seems to be in order. I think that this problem lies in the use of the hard buttons on my laptop. I had a simular problem with the sound after I used the hard mute button so then I had to run gst-register8.0 command to make the sound work again. Do you know of anyway to do something simular with the wifi card. (One of these days I will remmeber to not use the hard buttons)

---

### Post by quietglow on 2005-11-30
I understand fully--my wife has a hp dv1000 that has the same problem. Fortunately, it has a light in the button, so you can see if its running or not. My n610c also has a light.

Have you tried pressing the button once and then trying again?

---

### Post by ewtesterman@cox.net on 2005-11-30
Yes I have tried pressing the button and the light comes on. Everything throught the system says that it should work, but if I launch Fire Fox or Evolution I get the error right away saying that it could not connect. When I reboot into Windows it works and the same with Linux XP. I am hopping that someone knows of a command to recalibrate the software controling the hard buttons. This is on an HP Pavillion zv5330us.

---

### Post by quietglow on 2005-11-30
Sorry, the trick is actually getting a light going on mine. I've never had any trouble once its on--usually that indicates the card has power. You need to know what exactly is happening when the card is initialized. You might try turning it off and back on and and checking your system log (dmesg) to see what exactly the machine is doing with it.

---

### Post by ewtesterman@cox.net on 2005-12-01
I just gave up and did a re-install after I tried reinstalling the hot key software several times and tring different combinations of reboting with the button on or off. I did run the lsmod command like you had asked and I did see the ndiswrapper, when I ran iwconfig I did see that it was not connecting, the strange thing was that using the wifi managers I have all of them would find the available networks, It just would not connect to any of them. Again in the iwconfig it would say that ssid and key did not match, I assure they were correct. So I came to the conclusion that what ever the problem was that I could not fix it my self so I just reinstalled Ubuntu. Now everything is working fine. Seeing how this is about the 3rd time I have had to reinstall it to fix someting, I do believe that I will devote some time this weekend to finding a backup utility and using it :)

---

