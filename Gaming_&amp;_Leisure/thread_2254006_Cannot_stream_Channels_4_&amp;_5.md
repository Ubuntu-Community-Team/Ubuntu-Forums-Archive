---
title: "Cannot stream Channels 4 &amp; 5"
date: 2014-11-24
forum: Gaming &amp; Leisure
---

### Post by draigcoch2 on 2014-11-24
I have installed Ubuntu 14 (64 bit) on my machine and tried to watch catch-up last night.  BBC iplayer and ITV gave no problem but Channels 4 & 5 just stick immediately before playing a video.  

Chrome shows that Flash Player v1.0 is installed and active.
Firefox says that Shockflash is installed.

I downloaded Pepperflash and installed it (but cannot find it).  

Channel 5 kept asking for an updated version of Flash Player but when I tried to download the APT file it came to a dead end.  Alternatively there are tar.gz and .rpm options available but I don't know which to try!

Can anybody help here please?

---

### Post by Daveski17 on 2014-11-24
It may be that the site itself doesn't recognise Linux properly. I can't stream video on Demand 5 in Firefox or Chromium (with Pepper Flash) on my Ubuntu laptop, yet I can with Win 7 on my other computer. I appear to have exactly the same issue you have had, I can see the video but it just sticks. Like you, BBC iPlayer and ITV run perfectly for me as well.

---

### Post by robbie 348 on 2014-11-24
You need to install hal. (hardware abstraction layer or something like it)
Open a terminal and enter the following 
sudo apt-add-repository/ ppa:mjblenner/ ppa-hal
sudo apt-get update
sudo apt-get install hal
With that it should work, Rob.

---

### Post by draigcoch2 on 2014-11-24
robbie 348 - hal-info has replaced hal.  Installed the former and re-started the computer - no difference.  If Daveski17 has the same problem maybe this is a general fault?

---

### Post by Daveski17 on 2014-11-24
I have sent the Demand 5 link to a number of people online I know who run varying flavours of Linux/Ubuntu, including Elementary, Mint and Zorin and none of them could run the flash player either.

[http://www.channel5.com/demand5](http://www.channel5.com/demand5)

---

### Post by oldrocker99 on 2014-11-25
I tried and it didn't work for me; of course, I live in the US and probably couldn't view it with Windows, either.

---

### Post by Daveski17 on 2014-11-26
> **oldrocker99 said:**
> I tried and it didn't work for me; of course, I live in the US and probably couldn't view it with Windows, either.


Yeah, it could be. I sent the link to a bloke I know in California who runs Zorin and he couldn't run it, but suspected it was because he was outside of the UK. He also reckons it is most likely lazy coding by the Demand 5 webmasters. They obviously need an Ubuntu refresher course lol.

---

### Post by draigcoch2 on 2014-11-30
Managed to solve the problem on Firefox (but not Chromium/Chrome).  

(1)  installed "hal"
(2) installed "pipelight" - [http://pipelight.net/cms/installation.html](http://pipelight.net/cms/installation.html)

Working at the moment.

---

### Post by Daveski17 on 2014-12-02
> **draigcoch2 said:**
> Managed to solve the problem on Firefox (but not Chromium/Chrome).  

(1)  installed "hal"
(2) installed "pipelight" - [http://pipelight.net/cms/installation.html](http://pipelight.net/cms/installation.html)

Working at the moment.

Thanks, I'll have to look into this. I'm a bit of a noob running Ubuntu lol.

---

