---
title: "Dell Vostro 1500 - 10.04 - WiFi Wicd and networkmanager"
date: 2010-06-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fetuspuppet on 2010-06-29
Is it just me or did anyone else with a Vostro 1500 notice a huge amount of issues with networkmanager and getting the hardware support setup for the wireless cards?

I found so many different solutions, a few of them worked, and a few didn't.

Is there a clear a exact solution instead of the 50 other people who got their WiFi going? I wish there was some other way to do it without fwcutter.

Finally came up with installing wicd which feels really dirty - I can do everything from the command line just fine, but I really really wanted to just have networkmanager and nothing else to get it up and going.

Has anyone found a solution where this is the case?

Thanks!

---

### Post by bobcollard on 2010-06-30
> **fetuspuppet said:**
> Is it just me or did anyone else with a Vostro 1500 notice a huge amount of issues with networkmanager and getting the hardware support setup for the wireless cards?

I found so many different solutions, a few of them worked, and a few didn't.

Is there a clear a exact solution instead of the 50 other people who got their WiFi going? I wish there was some other way to do it without fwcutter.

Finally came up with installing wicd which feels really dirty - I can do everything from the command line just fine, but I really really wanted to just have networkmanager and nothing else to get it up and going.

Has anyone found a solution where this is the case?

Thanks!
You seem to be confusing your networkmanager or wicd with your wifi card driver which may be broadcom or another brand.  To find out your wireless card open terminal and  type ```
lspci
```  Then look under System/Hardware Drivers for the appropriate recommended proprietary driver and install it using a wire hooked into your Ethernet.

---

### Post by fetuspuppet on 2010-06-30
Actually I'm not confusing it... Let me back up a bit.

So I installed the drivers recommended by System -> Administration -> Hardware Drivers 

as the fresh install suggested.

After doing so WiFi did not work. I did do the lspci before you had mentioned it, and figured out the correct driver to use with fwcutter, and set that up.

But the networkmanager applet in the top right corner still would not give me the ability to control the wireless card.

After installing wicd I was able to control the WiFi with the wicd applet and see all the networks visibly present.

I guess what my problem is that I don't want to have to use wicd, I would like to just use networkmanager so I have only one visual control for the card.

Everything was working after this, but I went ahead and tried again from a fresh install on the Vostro.

This time I installed the b43, the other driver suggested, and the nvidia display drivers. (I had done this earlier today on another machine - a HP Mini 311)

When installing in the same order the wireless controls still do not function for the card through the networkmanager applet, but the iwconfig shows the wireless card as "eth1"

So anyhow I can probably install wicd again, but I would really like networkmanager to just see the card so I don't have to fuss with it anymore, I'm suspecting it's a config file somewhere, but I don't know where.

Any ideas?

---

### Post by bobcollard on 2010-06-30
My settings look like this:

---

### Post by fetuspuppet on 2010-07-01
Brilliant! I will try and post my screen captures later today, I took a few photos whilst doing the install.

It's really weird - the HP mini 311 I have has similar drivers and devices, but the Ubuntu install was a breeze and everything worked right off the bat - including being able to see all nearby networks listed.

With your settings are you able to do this with your Vostro?

---

