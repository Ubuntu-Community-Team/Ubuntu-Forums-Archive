---
title: "desktop effects error ati radeon"
date: 2008-03-06
forum: Desktop Effects &amp; Customization
---

### Post by thischarmingman on 2008-03-06
Hi

Just done a fresh install of ubuntu and can no longer enable desktop effects. My system configuration is exactly the same as before and I was able to apply desktop effects. I've followed just about every bit of advice in the forums, still no joy! Any suggestions?

---

### Post by overdrank on 2008-03-06
> **thischarmingman said:**
> Hi

Just done a fresh install of ubuntu and can no longer enable desktop effects. My system configuration is exactly the same as before and I was able to apply desktop effects. I've followed just about every bit of advice in the forums, still no joy! Any suggestions?

HI and could you tell us the model of the graphics card and some system specs?

---

### Post by {BzF}~JOKesTER on 2008-03-06
Suggest Enabling The Restricted ATI Driver In Control Center ---Restricted Drivers Management                -It Worked For Me

Hope This Helps

---

### Post by thischarmingman on 2008-03-06
> **overdrank said:**
> HI and could you tell us the model of the graphics card and some system specs?

*-display
                description: VGA compatible controller
                product: Radeon Mobility M7 LW [Radeon Mobility 7500]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga bus_master cap_list
                configuration: latency=66 mingnt=8

Its an IBM T40 thinkpad, 1 gig RAM, intel chip 1500mhz. I'm at a complete loss as the driver isn't showing up in the restricted drivers list and I have also downloaded the ati open source driver following instructions on another thread. If you can shed any more light on this it would be greatly appreciated!

---

### Post by averageidiot on 2008-03-07
i'm having the same issue, IBM thinkpad A31, ATI 7500 and the driver doesn't show up in resistricted driver manager.

---

### Post by {BzF}~JOKesTER on 2008-03-07
Ok Heres How To Get It Too. {The Restricted Driver}

Go To The Synaptic Package Manager.

Click The "Settings" Tab And Than Click "Repositories" ...

Under The "Ubuntu Software" Tab - Check All The Boxes...

And Under The "Updates" Tab Check All The Boxes...

Now Click "Close"

Now In Synaptic Package Manager - Click The "Reload" Button...

Now Run "Update Manager" And Hit "Check" And Install Any Updates...

Restart Your Computer And Now The ATI Driver Should Show In The Restricted Drivers Managment.

Hope This Helps!!!:)

---

### Post by averageidiot on 2008-03-07
cool, ill try this when I get home. Has anyone had any luck with this method yet?

---

### Post by thischarmingman on 2008-03-07
> **{BzF}~JOKesTER said:**
> Ok Heres How To Get It Too. {The Restricted Driver}

Go To The Synaptic Package Manager.

Click The "Settings" Tab And Than Click "Repositories" ...

Under The "Ubuntu Software" Tab - Check All The Boxes...

And Under The "Updates" Tab Check All The Boxes...

Now Click "Close"

Now In Synaptic Package Manager - Click The "Reload" Button...

Now Run "Update Manager" And Hit "Check" And Install Any Updates...

Restart Your Computer And Now The ATI Driver Should Show In The Restricted Drivers Managment.

Hope This Helps!!!:)

I was so hopeful that would work but alas, if anything I think my graphics appear worse. Typing this as I speak the cursor is very twitchy and theres are delay on the letters appearing on the screen! I need a drink or several! Thankyou anyway

---

### Post by averageidiot on 2008-03-08
tried that, still no driver displaying in restricted driver manager

---

### Post by bwang on 2008-03-08
If it's a Radeon 7500 there shouldn't be any restricted drivers.

---

### Post by Matsuri on 2008-03-08
I'm having the exact same issue. I'm running a Radeon x850 Pro. When I did a fresh install I managed to get the desktop effects to work however, I didn't get any of the screen resolutions I wanted, that was with the restricted ATI drivers.

I changed the drivers over to something else to get the screen resolution I wanted and now I can't run the desktop effects. Any help?... I'm quite fond of my screen res =]P

---

### Post by Matsuri on 2008-03-08
If your still having trouble with the ATI graphics card try this:

Enable the ATI restricted drivers.
If the desktop effects don't work install xserver-xgl

```

sudo apt-get update
sudo apt-get install xserver-xgl
 
```

Restrart your computer and like magic it should work.. at least worked for me.

---

### Post by thischarmingman on 2008-03-08
> **Matsuri said:**
> If your still having trouble with the ATI graphics card try this:

Enable the ATI restricted drivers.
If the desktop effects don't work install xserver-xgl

```

sudo apt-get update
sudo apt-get install xserver-xgl
 
```

Restrart your computer and like magic it should work.. at least worked for me.

Tried this, again, no luck! I feel like completely giving up with this.

---

### Post by thischarmingman on 2008-03-08
Hoorah! I managed to fix my problem.

If anyone is interested heres what I did.

In synaptic package manager I searched for 'radeon'. Any results with the name "fglrx", i uninstall ed, then installed the package named gatos and xserver-xorg-video-ati. Done a reboot, went into the appearance menu and hey presto it worked. Let me know if anyone else finds this works for them

---

### Post by averageidiot on 2008-03-11
trying this now, removed fglx stuff and installed gatos, gonna reboot now. i already had xserver-xorg installed though so i wonder if that will make a difference.

---

### Post by averageidiot on 2008-03-12
worked great, no troubles.


thanks!!

---

### Post by Cpuboye11 on 2008-04-27
Hey when you guys got yours working, did you have slow-ness.. Was your windows slow... Scrowllilng slow?? 

All the effects are slow.. And i can't fix it.. :(

---

