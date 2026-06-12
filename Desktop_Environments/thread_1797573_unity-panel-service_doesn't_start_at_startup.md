---
title: "unity-panel-service doesn't start at startup"
date: 2011-07-05
forum: Desktop Environments
---

### Post by osced on 2011-07-05
Hi

When I started ubuntu unity today, I didn't got dash or a panel, I have been using it for a month without any problem before today .I tried to reset Unity which made the panel and dashboard appear, but when I restart my computer and tried to log in again the panel and dashboard was missing again. So I tried to start unity in the terminal and that made the dash and panel appear again. I looked through the output I got when I typed 'unity' in the terminal, I found in that 'unity-panel-service:' are not running, I suppose that might be what causes my problem. I found a command that should start unity-panel service but it didn't start the panels.

Any one know how to fix my problem? It would be nice to not need to start unity through the terminal everytime I start ubuntu get it to work

//Osced

---

### Post by silvavlis on 2011-10-18
I'm having a similar problem after playing a bit with the compiz configuration tool. The problem now is that I cannot start anything at all! It doesn't even let me start a command using Ctrl+F2!

---

### Post by zico_newbie on 2011-10-18
> **osced said:**
> Hi

When I started ubuntu unity today, I didn't got dash or a panel, I have been using it for a month without any problem before today .I tried to reset Unity which made the panel and dashboard appear, but when I restart my computer and tried to log in again the panel and dashboard was missing again. So I tried to start unity in the terminal and that made the dash and panel appear again. I looked through the output I got when I typed 'unity' in the terminal, I found in that 'unity-panel-service:' are not running, I suppose that might be what causes my problem. I found a command that should start unity-panel service but it didn't start the panels.

Any one know how to fix my problem? It would be nice to not need to start unity through the terminal everytime I start ubuntu get it to work

//Osced

Maybe try re-enable Unity Plugin in CCSM and also
$ try unity --reset

:)

---

