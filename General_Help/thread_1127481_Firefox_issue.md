---
title: "Firefox issue"
date: 2009-04-16
forum: General Help
---

### Post by sabretooth16 on 2009-04-16
Hello,

I am running Ubuntu 8.04 with firefox 3.0.8. Since around a week ago, firefox is acting really weird. It starts up really slowly and freezes up several other applications ( vlc, terminal..) but cpu/memory don't seem to be used up. Opening google takes around 5-10 minutes. I reinstalled firefox but the problem remained. I am using Opera right now and it works without problems. What could be wrong? Any suggestions would be appreciated.

---

### Post by Daisuke_Aramaki on 2009-04-16
> **sabretooth16 said:**
> Hello,

I am running Ubuntu 8.04 with firefox 3.0.8. Since around a week ago, firefox is acting really weird. It starts up really slowly and freezes up several other applications ( vlc, terminal..) but cpu/memory don't seem to be used up. Opening google takes around 5-10 minutes. I reinstalled firefox but the problem remained. I am using Opera right now and it works without problems. What could be wrong? Any suggestions would be appreciated.

do you use ipv6? if not, can you check if ipv6 is enabled on firefox. it notoriously slows down firefox. typ about:config in the address bar, and look for this option. type ipv6 in the Filter box, and then you will have something like network.diable.ipv6 or something. just set the value as true. let me know how it went.

---

### Post by ddrichardson on 2009-04-16
Try emptying your history, the default is 90 days and I've experienced problems with the sqlite database that stores the history getting enormous.

---

### Post by codeseer on 2009-04-16
You could try another, new, profile to eliminate issues related to configuration and addons:

```

firefox -profilemanager -no-remote

```

---

### Post by sabretooth16 on 2009-04-16
Thanks for the replies fellas,

However the problem is still there. Whenever I start firefox, the tab on the panel shows "Starting Firefox..." then it goes away and nothing happens for a quite a while, everything freezes ( I keep a kill command typed in the terminal and use it to kill the process).

The profilemanager option codeseer suggested didn't do anything ( literally nothing happened)

I don't think it has anything to do with history. I've had slow firefox before, this time it's beyond slow. 

Daisuke_, firefox doesn't even open for me to type about:config :(

---

### Post by codeseer on 2009-04-16
Send your /home/username/.mozilla directory to the trash bin or rename it and then try to run firefox again.

---

### Post by sabretooth16 on 2009-04-17
Started getting other problems ( suddenly all network interfaces stopped working as well as random freezes); did a reinstall of ubuntu. Everything works fine now.

---

