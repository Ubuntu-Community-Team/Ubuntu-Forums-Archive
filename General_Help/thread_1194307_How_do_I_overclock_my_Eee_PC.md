---
title: "How do I overclock my Eee PC?"
date: 2009-06-22
forum: General Help
---

### Post by t0p on 2009-06-22
My Eee PC 701 has, I believe, a 900 MHz CPU that is underclocked to 600 MHz (or something similar). My previous installation of Ubuntu on the netbook was run with [the RiceeeyTweak script]("http://eee.ricey.co.uk/") - this made it possible for the CPU speed to be dynamically changed "on demand".

Now I'm running the Jaunty netbook remix, and it doesn't seem to include this feature.  Can someone tell me how I can get my CPU clocking up again?

---

### Post by munky99999 on 2009-06-22
Overclocking is done in the bios.

Though that likely wont be possible. So you'll need a newer bios.

---

### Post by t0p on 2009-06-22
I think I may have found the answer myself - a utility called [eee-control]("http://greg.geekmind.org/eee-control").  I'm about to install it now: I'll post my findings here.

---

### Post by t0p on 2009-06-22
Well, I've got eee-control installed now.  It allows me to toggle on-off of wifi, camera and card reader.  But the "performance" control is "not available".  A little perturbing, as the feature list clearly said that CPU clocking could be controlled with this utility.  I'm going to do some more reading [on the eee-control site]("http://greg.geekmind.org/eee-control"). I want to know why the one feature I installed it for is "not available", dammit! :(

**EDIT:** Thanks for the tip, **munky99999**.  I shall also investigate the bios settings.

---

### Post by hibliss on 2009-06-22
eeepc-acpi allows you to overclock. You will not find a new bios that allows for overclocking in the traditional manner.

I use Eeebuntu --[http://eeebuntu.org/]("http://eeebuntu.org/")

They have a forum where you can search for overclocking your model through acpi settings. 

Are you using the Array kernel now? Your model is listed as fully compatible -- [http://array.org/ubuntu/]("http://array.org/ubuntu/")

With the array kernel, which has custom drivers just for your machine, and eee-acpi, you should be able to overclock your machine through eee-control.

Another thread here - [http://crunchbanglinux.org/forums/topic/1493/installing-elmurato-acpi-scripts-on-the-eeepc-701/]("http://crunchbanglinux.org/forums/topic/1493/installing-elmurato-acpi-scripts-on-the-eeepc-701/")

There are custom scripts for your machine to use if the default acpi scripts are not working.

---

### Post by t0p on 2009-06-22
Thank you for the info hibliss.

I'm currently running the Ubuntu Netbook Remix (Jaunty), but I'm not very happy with it. It takes up so much room! and it isn't very fast. I downloaded the eeebuntu base .iso the other day, and I plan to install it to my 701 when I've got some time. I understand it comes with the array kernel.  And from what you said, it seems I'll be able to overclock my silly little CPU again once I've installed eeebuntu.  Lovely!

I really can't work out why Asus thought it was a good idea to stick a Celeron 900 MHz CPU in the 701 and then underclock it to 600 MHz.  It just doesn't make any sense to me.  It will be nice to have this little machine working to its full potential again.  So what if it will run a bit hot?

While I'm on the subject of nice customized Ubuntu installs for the Eee: what on earth has happened to the RiceeeyTweak script?  When I was running vanilla Intrepid Ubuntu as modified by Riceeey, I was very happy with my netbook's performance.  On his site, Ricey says some stuff about getting "hacked"... Okay, I can see that might have disadvantaged him for a short while, but *why oh why hasn't he written RiceeeyTweak.sh v3???*  It ain't right, man!

This bloody eeebuntu better be good, that's all I've got to say on the matter... *grumble*...*moan*...

---

### Post by hibliss on 2009-06-22
I like it, but I am using Eeebuntu 3.0 Standard, based on the Jaunty array kernel.

I also have a much more powerful EeePC, the 1000he, so your mileage will vary. I do however know that there are a ton of custom scripts out there that do exactly what you want. My performance settings over/underclock right out of the box with no scripts based on power consumption mode. Eee-control is awesome.

---

### Post by Bachstelze on 2009-06-22
```
sudo modprobe p4-clockmod
```

As simple as that. :D No need to install Eeebuntu or anything like that.

---

### Post by t0p on 2009-06-22
> **HymnToLife said:**
> ```
sudo modprobe p4-clockmod
```

As simple as that. :D No need to install Eeebuntu or anything like that.

Thanks for the tip!  Now, can you explain the workings a little?  When I check out eee-control, I find I can switch Performance between "normal" and "performance".  I assume "normal" setting is plain old 900 MHz processor under-clocked to 600 MHz, am I right?  And when I switch it to "performance", I can hear the fan pick up speed - so I take it the "performance" setting is over-clocking?  So what's it clocking up to?  Is it being taken up to 900 MHz?  Less?  Or more?

Also, when I right-click on eee-control and select Preferences, one of the options is "Set performance to powersave on battery".  If I select this option, what's the "performance" setting doing then?  I'm a little confused, cos it isn't very self-explanatory.

---

### Post by Bachstelze on 2009-06-22
I don't use that "eee-control" tool so I can't tell you for sure. Usually, the "performance" setting just makes your CPU run at its max speed (here, 900 MHz) all the time. I guess the "Set performance to powersave on battery" seting makes the system switch from the "performance" to "powersave" governor when running on battery (the "powersave" setting just makes the CPU always ru it its minimum speed)

---

