---
title: "Beryl and my laptop help"
date: 2007-05-14
forum: Desktop Effects &amp; Customization
---

### Post by acompdude on 2007-05-14
I am trying to get Beryl to work on my Acer Aspire 5670. It has an ATI x1400 and I am having the hardest time getting Beryl to install and work. I managed to mess up so bad the last time that I cant even get into the GUI now. I tried to reconfigure xorg and still couldnt get back to my GUI. I am reinstalling tonight. I was hoping someone here could give me a step by step tutorial from a base install of Ubuntu Feisty Fawn with my grapics card and all. Any and all help is greatly appreciated.

---

### Post by mssever on 2007-05-14
> **acompdude said:**
> I am trying to get Beryl to work on my Acer Aspire 5670. It has an ATI x1400 and I am having the hardest time getting Beryl to install and work. I managed to mess up so bad the last time that I cant even get into the GUI now. I tried to reconfigure xorg and still couldnt get back to my GUI. I am reinstalling tonight. I was hoping someone here could give me a step by step tutorial from a base install of Ubuntu Feisty Fawn with my grapics card and all. Any and all help is greatly appreciated.

I found this on the Beryl website: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

Before messing with your xorg.conf, it's a good idea to make a copy of it, so that if you mess it up, you can simply restore your copy. That way you don't have to reinstall.

Also, in order to use beryl, you need direct rendering. Type this to make sure you hardware supports direct rendering (and has it enabled): ```
glxinfo | grep 'direct rendering'
```

---

### Post by acompdude on 2007-05-15
The only problem is that the site that it directs me to does not have my card on the supported list. I guess I can try to do it again but I dont know if it will turn out any better this time. I also need to know how to make a copy of my xorg.conf file.

---

### Post by mssever on 2007-05-15
> **acompdude said:**
> The only problem is that the site that it directs me to does not have my card on the supported list. I guess I can try to do it again but I dont know if it will turn out any better this time. I also need to know how to make a copy of my xorg.conf file.

I don't have your card, so I don't know whether it will work. If you have direct rendering, I think that should be sufficient--though I'm not positive about that.

To make a copy of xorg.conf:
```
cd /etc/X11
sudo cp xorg.conf xorg.conf.bak
```The cd command changes directories and the cp command copies files from the first name listed to the second. sudo is to give you sufficient privileges. I mention this because if you hose your xorg.conf, you'll likely have to restore it from the command line--so you need to know what to type.

---

### Post by acompdude on 2007-05-15
Ok, I followed this guide [http://ubuntuforums.org/showpost.php?p=2564461&postcount=13](http://ubuntuforums.org/showpost.php?p=2564461&postcount=13) and I still couldnt get it to work. After I finished and rebooted it went to a white screen and all I could was enter a console. I tried reconfiguring xorg but had no luck. I reinstalled again and I am now waiting for another idea. I really need another approach because I just cant figure it out.

---

### Post by mssever on 2007-05-16
> **acompdude said:**
> Ok, I followed this guide [http://ubuntuforums.org/showpost.php?p=2564461&postcount=13](http://ubuntuforums.org/showpost.php?p=2564461&postcount=13) and I still couldnt get it to work. After I finished and rebooted it went to a white screen and all I could was enter a console. I tried reconfiguring xorg but had no luck. I reinstalled again and I am now waiting for another idea. I really need another approach because I just cant figure it out.

You should really use AIGLX over XGL if at all possible. It just works better. The thread you mentioned uses XGL, and also disables the version of beryl that's in the universe repository. I'd recommend the universe version over some other version if you're having problems because it's probably more stable. That said, my machine that has beryl-capable hardware is down at the moment, so I can't do an actual test.

In the absence of a guide for my specific hardware, I would also strongly favor guides on the beryl website or on the Ubuntu wiki on the grounds that they're probably more general.

---

### Post by bsleys on 2007-05-16
I have the same laptop and followed these instructions and have it working fine the first time.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Eye_Candy](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Eye_Candy)

Two notes on my install and the above instructions.

1. I skipped the open source drivers and skipped down to the "Alternate method: Using closed source FGLRX drivers from ATI." instructions.

2. at the step "If you are missing your shutdown and restart buttons, use this instead:" well I was missing the shutdown and restart buttons so I had to go back and reedit the file making the changes as noted.

---

