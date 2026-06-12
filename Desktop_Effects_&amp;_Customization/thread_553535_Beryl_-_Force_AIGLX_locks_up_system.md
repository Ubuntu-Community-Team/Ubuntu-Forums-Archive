---
title: "Beryl - Force AIGLX locks up system"
date: 2007-09-17
forum: Desktop Effects &amp; Customization
---

### Post by tenjin1 on 2007-09-17
Hi, I hope someone could help me with this...

I had installed Beryl and everything was working fine until I changed a setting in advanced options (forget exactly which one) in Beryl-manager by right-clicking icon. I changed a setting to "Force AIGLX" from "auto". It was working fine on "auto". Now everytime I start Beryl it locks up my system. Basically everything on my desktop is blank, can't ctrl-alt-del or anything..have to press power button to restart. I have tried uninstalling beryl and installing again, deleting ~/.beryl and ~/.emerald folder and still same thing...its still using "Force AIGLX". 

Is there another settings file somewhere (root folder?) that beryl uses that I can change back to "auto" from "force AIGLX"? Everytime I uninstall or delete ~/.beryl folder it locks up my system and upon restart the ~/.beryl folder is back. I have used ```
sudo aptitude remove beryl beryl-manager
``` and searched "beryl" in Synaptic and completely removed everything pertaining to beryl with no luck :confused:

Good thing I didn't add beryl to startup because then I wouldn't know what to do.

PLEASE HELP, thank u

---

### Post by joshuachad on 2007-09-17
i dont know if you tried this but youve got to delete it all. do a find for beryl. There should be like 4 folders. one in /usr/local /usr/share etc. Basically its config is probably still visisble if you do gconf-editor then go to apps >>>Beryl. I bet you may be able to change that setting. No offense but you should use CompizFusion anyhow. But some ppl like beryl.

---

### Post by joshuachad on 2007-09-17
btw i assume you know how to do a find if not open a terminal and run "sudo find / -name beryl" without quotes. The rm -rf each of the beryl folders.

---

### Post by tenjin1 on 2007-09-18
> **joshuachad said:**
> No offense but you should use CompizFusion anyhow. .

Well josh I took your advice and installed Compiz Fusion and ..WoW! I love it. everything seemed to work right from the beginning. Installed using this [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/")

I wonder how many ppl that use Compiz Fusion also use emerald window manager (because of the random missing window title bars)?

---

