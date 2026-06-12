---
title: "Lightning Add-on for Thunderbird on Intrepid"
date: 2009-03-05
forum: General Help
---

### Post by cfree220 on 2009-03-05
Hi all,
I'm trying to install the Lightning calendar add-on for Mozilla Thunderbird. The add-on version is 0.9, I'm using TB 2.0.0.19 on Ubuntu 8.10. I've tried to install it twice; the first time did not work at all.... would not display calendar. I looked up how to fix this... apparently Lightning has a dependency on libstdc++5. I installed this using sudo apt-get, and then re-installed the addon. Although it now displays the calendar and allows me to switch between views, I am not able to add new tasks and events... buttons do not seem to work (nor do the equivalent keyboard shortcuts).

apparently the libstdc++5 workaround works for TB2.0.0.17. Does anyone have any ideas on how to get it working on 2.0.0.19?

---

### Post by cfree220 on 2009-03-05
Nevermind. I solved it by disabling my theme, creating a task, and then re-enabling my theme.

---

### Post by cuby on 2009-03-05
Thanks. Your post was usefull to me.

---

### Post by Stretsh on 2009-03-07
Thanks man, this really helped. Been fighting with this for about 2 hours, until I found your post. Installed libstdc++5 and everything started working as expected.

Thanks

---

### Post by 8oluf7 on 2009-03-08
I'm using Intrepid with Thunderbird 2.0.0.19. Lightning 0.8 stopped displaying the calendar properly and didn't display either my calendar entries or my tasks. libstdc++5 was already installed (as well as libstdc++6). 

I found this thread about Sunbird 0.9:

[http://ubuntuforums.org/showthread.php?t=929681](http://ubuntuforums.org/showthread.php?t=929681)

which lead me to here:

[http://forums.linuxmint.com/viewtopic.php?f=32&t=17333&p=104482#p104482](http://forums.linuxmint.com/viewtopic.php?f=32&t=17333&p=104482#p104482)

where there is also a DEB for Lightning 0.9. Downloaded, double clicked, agreed to overwrite supported version, activated Lightning 0.9 in Thunderbird, re-started Thunderbird, problem solved - at least for now.

---

