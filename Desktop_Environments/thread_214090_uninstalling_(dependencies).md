---
title: "uninstalling (dependencies) ????"
date: 2006-07-12
forum: Desktop Environments
---

### Post by quick on 2006-07-12
hi,


well i like the apt-get system to install things its really easy
but what i dont like is that i always have to install many depedencies for just one single program.

well i dont have a problem with it because i dont care about the files
but whats with uninstalling them 

i mean when i uninstall - say azureus  which had many dependencies - is there a way to remove the dependencies too??

a way to check if some packages are NOT USED ? and purge them? 

if theres something like this please let me know because i think using a linux system without removing unneeded packages for a year the computer will be bloated :)

thanks

---

### Post by quick on 2006-07-12
i found a way - 

apt-get install deborphan

this works i think :)

if someone else has a better way please let me know

---

### Post by Ramses de Norre on 2006-07-12
A more easy way is using aptitude instead of apt-get, aptitude will remember which packages are installed as dependency and will remove them when they're not needed anymore. The syntax is the same as apt-get, just replace the words "apt-get" by "aptitude" ;)

---

### Post by quick on 2006-07-13
thank you for this really good tip :) can i set up synaptic to use aptitude instead of apt

-- why is aptitude not the standart system if it gives u such a good function?

---

### Post by madmetal on 2006-07-13
i dont know if this is what you want but when i want to uninstall something i either use synaptic and choose total remove or aptitute purge.

---

### Post by quick on 2006-07-13
i think this just cleans the config files but not the dependencies

image you install firefox it installs 10 more libs - i want to remove the libs not just firefox :) 

thanks for your help

---

### Post by bluenova on 2006-07-13
> **Ramses de Norre said:**
> A more easy way is using aptitude instead of apt-get, aptitude will remember which packages are installed as dependency and will remove them when they're not needed anymore. The syntax is the same as apt-get, just replace the words "apt-get" by "aptitude" ;)
This works if yoy've used aptitude from the beginning, but not if you've used apt-get and want to purge. I will certainly be using aptitude after the next time I do a format.

[quote=madmetal]...but when i want to uninstall something i either use synaptic and choose total remove...[/quote]Does this really remove all deps? I though it just removes your settings as well as the application.

---

### Post by madmetal on 2006-07-13
i am not an experienced user so my replies contain answers...

---

