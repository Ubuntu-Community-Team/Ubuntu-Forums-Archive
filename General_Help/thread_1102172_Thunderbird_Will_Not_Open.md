---
title: "Thunderbird Will Not Open"
date: 2009-03-21
forum: General Help
---

### Post by WarholsGhost on 2009-03-21
Hello,

So i'v been having the problem on my second laptop for a few months, and i'v tried everything. the error that pops up is:

"Thunderbird is already running, but is not responding. To open a new window, you must first close the existing Thunderbird process, or restart your system"

I'v restarted, i'v uninstalled and reinstalled thunderbird like 3 times. And i doesn't show up in top. 

ug please help!

---

### Post by hyper_ch on 2009-03-21
in the terminal run:

```

killall thunderbird
thunderbird

```

post the output of the commands here

---

### Post by WarholsGhost on 2009-03-21
the killall thunderbird:
"No Processes Killed"

thunderbird makes the same message as above popup

---

### Post by hyper_ch on 2009-03-21
start thunderbird from the temrinal and post the output here.

---

### Post by WarholsGhost on 2009-03-21
the same "thunderbird is already running" pops up when i type "thunderbird" in the terminal

---

### Post by hyper_ch on 2009-03-21
what's the output of
```

ps aux | grep thunderbird

```

---

### Post by WarholsGhost on 2009-03-21
frenzy 14702 0.0 0.1 3236 796 pts/0 S+ 09:98 0:00 grep thunderbird

---

### Post by hyper_ch on 2009-03-21
(1) when posting any output enclose it in [noparse]```

```[/noparse] brackets --> makes it easier to read

(2) it's strange that it doesn't work.

---

### Post by here.david on 2009-06-03
Here is what I see...

# killall thunderbird
thunderbird: no process killed
# thunderbird
Segmentation fault
# ps aux | grep thunderbird
root      8834  0.0  0.0   7524   900 pts/0    R+   09:08   0:00 grep thunderbird
# 

Also sometimes the same non-open of Firefox....reboot and everything works for some time then will no longer open until a full shutdown and re-start...

8GB RAM AMD64 UBUNTU 9.04

# ps aux | grep firefox
david     8718  6.7  1.2 627272 97156 ?        Sl   09:06   0:24 /usr/lib/firefox-3.0.10/firefox
root      9034  0.0  0.0   7524   904 pts/0    S+   09:12   0:00 grep firefox

---

