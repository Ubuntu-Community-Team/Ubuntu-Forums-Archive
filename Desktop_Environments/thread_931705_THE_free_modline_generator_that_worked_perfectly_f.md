---
title: "THE free modline generator that worked perfectly for me."
date: 2008-09-27
forum: Desktop Environments
---

### Post by zorglups on 2008-09-27
I configured a Mythbuntu server connected to my 42" LG Plasma Screen. I could make a 'modeline' to get the 1360x768 resolution work but I wasn't satisfied my the image quality.

The colors were fade out and a few 'bands' were darker than other parts of the screen. This was easy to see when displaying a blank screen or my google calendar.

I then tried a few other modline using a few online modline generators but couldn't get any good results.

I finally found the 'moninfo' tool on my laptop running Windows.
This tool (400KB) can be downloaded from [http://www.entechtaiwan.com/util/moninfo.shtm]("http://www.entechtaiwan.com/util/moninfo.shtm")

It will give you a lot of details concerning the screen (received from the screen itself) and will even give you THE modline.

In my case, it gave me a modline 'recommended by the constructor' and a 'maximum' modline.

I just copy and pasted the line into my xorg.conf and that was it. The image was perfect !!!

I hope you will enjoy the tip...

Best regards,

Pierre

---

### Post by jpeddicord on 2008-09-27
Moved to Desktop Environments.

---

