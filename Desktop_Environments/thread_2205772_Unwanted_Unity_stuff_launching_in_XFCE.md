---
title: "Unwanted Unity stuff launching in XFCE"
date: 2014-02-15
forum: Desktop Environments
---

### Post by halfbeing on 2014-02-15
Hello,

I installed UbuntuStudio (which uses XFCE), switched to Unity for a while, and then switched back to XFCE. The trouble is that I still have Unity things launching with my XFCE session, such as Evolution services and a couple of panel applets (Wanda the Fish and a clipboard tool). There were other things as well which I found launchers for in ~/.config/autostart, but for Evolution etc I can't find a launcher anywhere which I can disable. How do I stop these things loading?

---

### Post by deadflowr on 2014-02-15
All three items you listed are gnome thingies, and have nothing to do with unity at all.
But if the evolution one says evolution-data-server, then that's what unity used for it's calendar in the panel.
But it isn't really evolution though.

Anyway, if it is that package, then that's what you should look for if you want to remove it.

---

### Post by vasa1 on 2014-02-15
And while trying to remove anything please be **alert** to what else can be removed. 

If you don't mind the command-line, always run *apt-get purge **-s** package_name* **first** where "-s" means you're just doing a simulation. Examine the proposals. Ask for help if you aren't sure of the output.

BTW, you could use *remove* instead of *purge* but *purge* is more thorough because it deletes system-wide config files. In both cases, you're in charge of keeping your home folder clean. Purge won't delete config files from your home folder.

---

### Post by halfbeing on 2014-02-15
Thanks for the reply.

Is there a way to disable this stuff without uninstalling it? That way I won't get my packages in a mess and the stuff will be available should I want to use Unity again. I mean if the stuff gets started when my XFCE session starts then there must be an instruction somewhere specifying this. If it's not in ~/.config/autostart then it must be somewhere else.

---

### Post by Dennis N on 2014-02-15
> Is there a way to disable this stuff without uninstalling it?
Try:

[B]Settings > Session and Startup > Application Autostart
[/B]
Maybe you will find them in there.

Reference System: Xubuntu 12.10

---

### Post by halfbeing on 2014-02-16
Thank you! You are right. I'd actually looked for session and startup more than once before in the settings manager but I simply didn't see it because it was where I thought it would be. But this time I have found it and it does have all the controls there that I was looking for.

---

### Post by mintfan7200 on 2014-02-18
Make sure XFCE is set as your default windows manager . I think you can remove unity , that is if you do not use it anymore .

---

### Post by buzzingrobot on 2014-02-18
> **mintfan7200 said:**
> Make sure XFCE is set as your default windows manager . I think you can remove unity , that is if you do not use it anymore .

Do some research on removing Unity to see if it is worth the risk of losing the other core components it will take with it.

---

