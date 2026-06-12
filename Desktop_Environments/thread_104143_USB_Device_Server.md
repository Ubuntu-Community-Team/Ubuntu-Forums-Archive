---
title: "USB Device Server"
date: 2005-12-15
forum: Desktop Environments
---

### Post by steppenwulf241 on 2005-12-15
Greetings all! I have a question...

I have a Silex USB Device Server that connects to my network via the router. Under WinXP there is a little app you can install that enables you to connect to all the peripherals connected to it (printer, scanner, external USB HD). 

Now, here's my problem... Ubuntu apparently is not WinXP *gasp* *astonishment*

So. I have tried getting the included windows app to run under crossover/wine with no luck. I have the notion of trying to get Ubuntu to connect to the device itself without the aid of the included application... but it seems oblivious.

Is there anyone out there who has experience connecting such peripherals to Ubuntu? Any advice would be much appreciated. Thanks!!

Further Device Info: [http://www.silexamerica.com/us/support/printserver/sx1000u.html](http://www.silexamerica.com/us/support/printserver/sx1000u.html)

---

### Post by s_p_a_r_k_y on 2005-12-15
The problem here is thats its most likely a driver issue. The Windows app may have installed or uses a windows driver to make the device work. Under crossover the app would try to talk to the windows driver, and since Linux!=Windows that shouldn't work. If they don't have a Linux module, or no current module supports the device, then you may be out of luck my friend.

---

### Post by steppenwulf241 on 2005-12-15
[QUOTE=s_p_a_r_k_y]The problem here is thats its most likely a driver issue. The Windows app may have installed or uses a windows driver to make the device work. Under crossover the app would try to talk to the windows driver, and since Linux!=Windows that shouldn't work. If they don't have a Linux module, or no current module supports the device, then you may be out of luck my friend.[/QUOTE]

I was afraid this might be the case... Thanks for your reply! ;)

---

