---
title: "Getting a buffer I/O error after Wubi install: 8.10"
date: 2009-01-30
forum: General Help
---

### Post by demoflauchy on 2009-01-30
I ran the wubi install in xp pro sp2, it installed ubuntu, asked me to reboot to finalize the installation. I rebooted, selected Ubuntu from the dual-boot menu (windows being the other option). 

Ubuntu screen comes up with a status bar and an orange line going back and forth across the screen. 

Then it goes into a command line mode and gives me an error repeated over and over again. Here was the error:
"end_request: I/O error, dev sr0, sector 1430968
buffer i/o error on device sr0, logical block 178879"

So I restarted, and pressed "esc" to enter the options screen after choosing "ubuntu" from the dual-boot menu. I selected "select installer verbose mode" 

It went through 30 seconds of command line prompts/text and then hung up on something with the following error:

buffer i/o error on device sr0, logical block 357794

I'm running an old Dell machine, P4 2.4ghz, 80GB, and 512 ram. 

Thanks for any help.

---

### Post by demoflauchy on 2009-01-30
Ok, so I just let it finish with all the "buffer errors" while I was submitting this question ... and it looks like its installed as I'm seeing a "checking the installation" prompt with a brown artsy background. 

I'm still a bit concerned with all of those errors, even though thing appear to be 'working'

---

### Post by demoflauchy on 2009-01-30
Ok, so everything installed just fine, despite the errors. However, when I restart it takes a good 3-5 minutes for ubuntu to startup. All I see is a blank screen, and then a few minutes later ubuntu shows up. Is this typical?

---

