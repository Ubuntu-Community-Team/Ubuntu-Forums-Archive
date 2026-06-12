---
title: "Disabling one screen in Feisty"
date: 2007-04-23
forum: Desktop Environments
---

### Post by Armanzo on 2007-04-23
Hi, I just got Feisty set up with Beryl. I have 2 monitors hooked up but they run at different resolutions. Since Beryl doesn't do too well with that, I was wondering if there was a way to disable one of the outputs so only my 20" display will get a signal. 

I'd rather not unplug the other screen since this computer is dual booting vista, and I prefer having both screens available for that. 

Related specs are:
ATI X800XL AGP
Samsung 730B 17"LCD (1024x768 native resolution)
Benq FP202W 20" LCD (1680x1050 native resolution)

Or could I just go with setting the resolution to 1680x1050 with the 17" turned off?  

When I installed and set it all up, I only had the 17" hooked up so xorg.conf only has the settings for it entered. Do I just go and add the following to have the option to switch to the higher resolution?

        SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection

Thanks.

---

