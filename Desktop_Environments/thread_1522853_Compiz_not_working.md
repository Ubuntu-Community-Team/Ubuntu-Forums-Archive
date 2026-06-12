---
title: "Compiz not working"
date: 2010-07-02
forum: Desktop Environments
---

### Post by uncle_frank on 2010-07-02
I hope this is the correct section. I have recently updated to 10.04 and now Compiz/desktop effects wont work. When I try to turn visual effects on I get a message saying they could not be enabled. I'm a bit new to all this so not sure if I'm doing something wrong.

I've looked at many threads regarding this problem and nothing they say has worked. iv tried using Hardware Drivers (in systems --> administration) but this says "no proprietary drivers are in use on this system".

Also I don't know whether this effects anything but when I open NVIDIA X Server Settings (in systems --> administration) i get a message saying "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

Does anyone know how I can get Compiz/desktop effects working? thanks.

---

### Post by yossell on 2010-07-02
I'm not sure, but it sounds as though you haven't got the right driver installed. I take it it's an nvidia card? When, from the panel, you choose system -> Administration -> Hardware drivers what shows up?

To answer another part of your question, I think when it says `run nvidia-xconfig as root' you can do this by typing

sudo nvidia-xconfig

into a terminal and then enter your password - 

but I might be cautious about doing this until you know what you're doing!

---

### Post by uncle_frank on 2010-07-03
When i go system -> Administration -> Hardware drivers, the full window comes up but then theres nothing in any boxes and it just says "no proprietary drivers are in use on this system" at the very top. 

I've tried "sudo nvidia-xconfig" and nothing happened and restarted X Server. although when I logged on this morning I got an error message about the configuration.

How do I find out if I have a NVIDIA card?

---

### Post by yossell on 2010-07-03
If you've not got an nvidia card then I'm not sure the nvidia server settings are relevant to your case.

I think whether you can run compiz depends on your computer's hardware. I think compiz requires some kind of 3-d acceleration and if you haven't got the right hardware, it may not run on your computer. Even if you have integrated graphics or an ATI card that supports it, I believe it can sometimes be a bit tricky on Linux, since Linux support for these cards is not quite as good as nvidia support - though the situation is changing.

Try going to, from the menu, 
applications -> system tools -> Sysinfo

Is there an nvidia option on the left? If not, click on hardware and choose graphic card on the right and see what it says.

Someone else may chime in and know the right terminal commands for this information.

---

### Post by uncle_frank on 2010-07-03
In graphics card is says "Intel Corporation 82945G Intergrated Graphics Controller (rev 02)" so does this mean that the NVIDIA problem doesn't matter?

Compiz worked just fine before I updated to 10.04 and now nothing works. I cant even change Visual Effects to Normal it says "Desktop effects could not be enabled"

---

### Post by yossell on 2010-07-03
Both my computers have Nvidia so if your graphics is I can't say for sure what the deal is with the nvidia utility is there. My guess, though, is that it shouldn't do anything for your graphics and that, as you lack an nvidia card, it's a red herring.

The fact that it says that even normal affects can't be enabled does suggest to me some kind of driver problem - once, when I was unable to install the proprietary nvidia driver, I had the same symptoms.

So, if I was in your shoes, I would be trying to find out if there's a linux driver you need to install to get the graphics card working. I'm not really an expert so, if nobody else jumps in here, it may be worth starting a new thread about your inability to run compiz on your computer - post its specifications and your difficulties - in the general help section and asking others with integrated intel cards for advice.

---

### Post by andrea000 on 2010-07-03
Try running compiz in the terminal and post the output.Because
if you have a intel integrated card to some how compiz picks
up on it and if it's a blacklisted card it will have to be
unblacklisted before compiz will work.

also you have proprietary drivers installed?

---

