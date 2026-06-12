---
title: "Firefox can't install Flash?"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Zdravko on 2006-06-02
When I reached a site, that requires flash, Firefox alerted me to download this plugin. I said OK - but the installation failed. What should I do?

---

### Post by johnc4510 on 2006-06-02
In synaptic, look for this and install it:
flashplugin-nonfree

---

### Post by aysiu on 2006-06-02
[Get extra repositories](http://www.psychocats.net/ubuntu/sources). Paste this command into the terminal: ```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

---

### Post by Zdravko on 2006-06-02
[[COLOR=#5f2d06]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941"), it didn't work. Firefox detects the Flash, then tries to install it. But it sill fails!
But is the list on this site compatible with the current language of Ubuntu I use (German)?

---

### Post by Neobuntu on 2006-06-02
Excuse me if you did but don't forget to restart Firefox and all instances of Firefox must be closed first (to load the new versions and prob plug-ins too.)

---

### Post by Zdravko on 2006-06-02
Yeah, that was the problem! Sorry! :)

---

### Post by Neobuntu on 2006-06-02
No problem friend. That's what the friendly ubnutu forums are for.

God bless

---

### Post by rcarring on 2006-06-02
I installed Flash 7 from Adobe. OK, my ./mozilla/plugins directory had gone root only so I had to hack that but it worked.

---

### Post by jerinjoy on 2006-06-02
I would normally download the plugin from the macromedia site but heres a quick way I accidentally found:
1. go to [http://video.google.com](http://video.google.com)
2. click on a video, it will say plugin missing.
3. click on plugin missing rectangle, it will install the plugin.

I tried it on other flash enabled sites but it didn't work, maybe the google guys keep a copy of the installer or something. Other sites tell me to do a manual install.

weird but worked for me. anyone else seen this?

---

### Post by ZombiekE on 2006-06-03
[QUOTE=jerinjoy]I would normally download the plugin from the macromedia site but heres a quick way I accidentally found:
1. go to [http://video.google.com](http://video.google.com)
2. click on a video, it will say plugin missing.
3. click on plugin missing rectangle, it will install the plugin.

I tried it on other flash enabled sites but it didn't work, maybe the google guys keep a copy of the installer or something. Other sites tell me to do a manual install.

weird but worked for me. anyone else seen this?[/QUOTE]
It didn't work for me.

I've already installed Flash. Thank you aysiu.

---

