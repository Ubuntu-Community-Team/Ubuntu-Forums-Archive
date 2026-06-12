---
title: "Cairo won't change themes."
date: 2009-03-26
forum: Desktop Environments
---

### Post by cereal killer on 2009-03-26
Hello there. I just installed Cairo-dock, and was given an opportunity to choose a theme. I did so, but when it launched, it was a generic 2D theme with some snowflakes in the back ground. 

I right click and choose to manage themes, but it simply won't change. I googled, but I cannot find any help with this.

Anyone have an idea?

Thanks.

---

### Post by nebileix on 2009-03-27
What version are u using? If i'm not wrong, the version provide by Ubuntu respository is abit outdated. Download from this link [http://developer.berlios.de/project/showfiles.php?group_id=8724]("http://developer.berlios.de/project/showfiles.php?group_id=8724"). Try the 1.6.3.1 version as 2.0.0 is still under testing. Just use the *i686.deb should work for most computer.

Have fun.

---

### Post by fabounet on 2009-03-27
it's probably in auto-hide mode, behind your gnome-panel.

---

### Post by cereal killer on 2009-03-28
Ahh, I installed it wrong. I uninstalled and and used a different set of instructions. I think the plugins were the reason, since I don't think I hade them the 1st time.

Thanks guys.

---

### Post by e1luca on 2009-05-01
I have the same problem in Ubuntu 9.04 with cairo 1.6.3.1. Any idea?

---

### Post by fabounet on 2009-05-01
check that ~/.config/cairo-dock is writable
or try CD2

---

### Post by e1luca on 2009-05-01
@ fabounet:
Tnx for the hit but no luck:
- Actualy the owner of cairo-dock.conf is root but I chmod 777 and no change.
- About CD2: I downloaded from berilos cairo-dock-plug-ins_v2.0.0-rc5_x86_64.deb (I'm on 64b) but get error when gdebi ~/cairo-dock-plug-ins_v2.0.0-rc5_x86_64.deb despite chmod 777 also.

I'm open to any ideas

---

### Post by e1luca on 2009-05-01
maybe this heps: I run cairo 1.6 as sudo and I get this when I try to change theme
```
HTTP request sent, awaiting response... 200 OK
Length: 19 [text/plain]
Saving to: `/tmp/cairo-dock-net-readme.nJxEGj'

100%[========================================================================>] 19          --.-K/s   in 0s      

2009-05-02 01:18:24 (1.03 MB/s) - `/tmp/cairo-dock-net-readme.nJxEGj' saved [19/19]

fichier preview distant (http://themes.cairo-dock.org/Cobalt/preview)
--2009-05-02 01:18:24--  http://themes.cairo-dock.org/Cobalt/preview
Resolving themes.cairo-dock.org... 87.98.128.158
Connecting to themes.cairo-dock.org|87.98.128.158|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 191890 (187K) [text/plain]
Saving to: `/tmp/cairo-dock-net-preview.zWLHN9'

100%[========================================================================>] 191,890      138K/s   in 1.4s    

2009-05-02 01:18:26 (138 KB/s) - `/tmp/cairo-dock-net-preview.zWLHN9' saved [191890/191890]

plus de panneaux de config
downloading theme from http://themes.cairo-dock.org/Cobalt ...
--2009-05-02 01:18:30--  http://themes.cairo-dock.org/Cobalt/Cobalt.tar.gz
Resolving themes.cairo-dock.org... 87.98.128.158
Connecting to themes.cairo-dock.org|87.98.128.158|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-05-02 01:18:30 ERROR 404: Not Found.

uncompressing theme Cobalt ...

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error exit delayed from previous errors
warning :  (cairo-dock-themes-manager.c:cairo_dock_manage_themes:476)  
  Attention : directory /tmp/cairo-dock-net-theme.NJxuFd-data is empty or unreadable


```

---

### Post by e1luca on 2009-05-01
Here I find a thread that seems to deal with the same issue:
[http://www.cairo-dock.org/bg_topic.php?t=2644](http://www.cairo-dock.org/bg_topic.php?t=2644)

---

### Post by levicivita on 2009-05-03
Following the instructions in the cairo-dock thread, I can now manually download themes and have them show up in the cairo theme manager (with an @ before their name).  However actually changing to the downloaded theme still doesn't do anything at all.

---

### Post by e1luca on 2009-05-03
I just spent the last hour with somebody named coz_ on #cairo-dock chanel. He walked me through compiling cairo-dock v2.0 from sources. Or this is what I think :D - he might as well instructed me how to set my house on fire from command line for all I know. Anyway the end result is that I have now a beautiful working cairo-dock. If anybody is brave enough I can send the conversation I had there and you can follow along. (send me PM coz' it's a long conv...)

---

