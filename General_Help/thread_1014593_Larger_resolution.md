---
title: "Larger resolution?"
date: 2008-12-18
forum: General Help
---

### Post by asheq on 2008-12-18
So, i'm on 800x600
Or something like that, and theres that and 600xsomething.

Is there any way to get normal size?
I don't like it being so magnified :(
It's not an option, but is there anyway to make it one?

---

### Post by jerome1232 on 2008-12-18
Do you know what video card your using? This depends on your video card/driver/monitor. So knowing what monitor your using can be helpful as well.

If you don't know what the video card is then posting this will clue us in.

```
sudo lshw -C video
```

---

### Post by roopeshshenoy on 2008-12-22
Hi Jerome,

I am also facing the same problem. In windows the resolution is much better so the hardware supports it but with Ubuntu I am not getting an option to choose more than 800X600 - 

This is the output of the above command -

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: KM400/KN400/P4M800 [S3 UniChrome]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 bus_master cap_list
       configuration: latency=32 mingnt=2


Would you be able to help me with this information?


Thanks.


Best Regards,

Roopesh

---

### Post by Usufruct on 2008-12-22
> **roopeshshenoy said:**
> Hi Jerome,

I am also facing the same problem. In windows the resolution is much better so the hardware supports it but with Ubuntu I am not getting an option to choose more than 800X600 - 

This is the output of the above command -

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: KM400/KN400/P4M800 [S3 UniChrome]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 bus_master cap_list
       configuration: latency=32 mingnt=2


Would you be able to help me with this information?


Thanks.


Best Regards,

Roopesh

Looks like your graphics hardware is one of the good old VIA Unichrome series chipsets.  Check out [http://www.openchrome.org/]("http://www.openchrome.org/"), and take a look at the documentation section if you need help compiling the drivers.

---

### Post by roopeshshenoy on 2008-12-23
> **Usufruct said:**
> Looks like your graphics hardware is one of the good old VIA Unichrome series chipsets.  Check out [http://www.openchrome.org/]("http://www.openchrome.org/"), and take a look at the documentation section if you need help compiling the drivers.

Hi,

Thanks.

However, this driver is already installed. I reinstalled it but it does not help much - the screen resolution is still not recognized. :(


Best Regards,

Roopesh

---

