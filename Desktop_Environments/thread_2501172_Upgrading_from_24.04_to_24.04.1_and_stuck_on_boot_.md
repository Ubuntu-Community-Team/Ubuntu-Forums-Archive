---
title: "Upgrading from 24.04 to 24.04.1 and stuck on boot with docker on eth errors."
date: 2024-09-25
forum: Desktop Environments
---

### Post by daring-t on 2024-09-25
Hello all, I recently got a popup asking to upgrade from 24.04 to 24.04.1 and I went and  installed it. I saw the it upgraded KDE Plasma to v6 and then restarted. When I restarted I was getting the errors below. I went into recovery mode and ran the dpkg option and disabled docker using systemctl disable docker command. After a reboot I am now looking at a bash prompt, I tried that's where I am now.  Has anyone ran into this issue before and if so what needs to do be done to fix my Kubuntu install?

Thanks,
daring-t


14.903612] docker0: port 1(vetha22bc76) entered disabled state
14.904163] vetha2abc76 (unregistering): left allmulticast mode
14.904260] vetha22bc76 (unregistering): left promiscuous mode
14.904365] docker0: port 1(vetha22bc76) entered disabled state
16.428353] docker0: port 1(vethda726ef) entered blocking state
16.428527] docker0: port 1(vethda726ef) entered disabled state
16.428732] vethda726ef: entered allmulticast mode
16.429078] vethda726ef: entered promiscuous mode
16.557959] etho: renamed from vethe695cd4
16.571239] docker0: port 1(vethda726ef) entered blocking state
16.571389] docker0: port 1(vethda726ef) entered forwarding stat
17.830342] vethe695cd4: renamed from etho
17.838802] docker0: port 1(vethda726ef) entered disabled state
17.850469] docker0: port 1(vethda726ef) entered disabled state
17.851115] vethda726ef (unregistering): left allmulticast mode
17.851202] vethda726ef (unregistering): left promiscuous mode
17.851286] docker0: port 1(vethda726ef) entered disabled state
20.996119] docker0: port 1(vethezebeb7) entered blocking state
20.996219] docker0: port 1(vethezebeb7) entered disabled state
20.996312] vethezebeb7: entered allmulticast mode
20.996413] vethe2ebeb?: entered promiscuous mode
21.138971] eth0: renamed from vetha438326
21.148254] dockerø: port 1(vethezebeb7) entered blocking state
21.148353] docker0: port 1(vethezebeb7) entered forwarding state
22.411046] vetha438326: renamed from etho
22.424807] docker0: port 1(vethe2ebeb7) entered disabled state
22.437810] docker0: port 1(vethezebeb?) entered disabled state
2.438231] vethezebeb? (unregistering): left allmulticast mode
22.438333] vethezebeb7 (unregistering): left promiscuous mode
22.438420] docker0: port 1(vethezebeb7) entered disabled state
28.771188] docker0: port 1(vethd679960) entered blocking state
28.771357] dockerø: port 1(vethd679960) entered disabled state
28.771516] vethd679960: entered allmulticast mode
28.774072] vethd679960: entered promiscuous mode
28.928924] eth0: renamed from veth41f378f
28.939150] docker0: port 1(vethd679960) entered blocking state
28.940017] docker0: port 1(vethd679960) entered forwarding state
30.206879] docker0: port 1(vethd679960) entered disabled state
30.207922] veth41f378f: renamed from ethe
30.234850] dockerø: port 1(vethd679960) entered disabled state
30.236297] vethd679960 (unregistering): left allmulticast mode
30.237331] vethd679960 (unregister ing): left promiscuous mode
30.238625] docker0: port 1(vethd679960) entered disabled state
12.9646441]  docker0: port 1(veth91047eb) entered blocking state
12.9673441]  docker0: port 1(veth91047eb) entered disabled state
42.969358] veth91047eb: entered allmulticast mode
42.970729] veth91047eb: entered promiscuous mode
43.1117971] eth0: renamed from veth121edbe
13,1240721]  docker0: port 1(veth91047eb) entered blocking state
13,1249311]  docker0: port 1(veth91047eb) entered forwarding state
44,.3876361]  veth121edbe: renamed from etho
44.407873] docker0: port 1(veth91047eb) entered disabled state
44,4158281] docker0: port 1(veth$1047eb) entered disabled state
44,4172171] veth91047eb (unreg!ster lng): left allmult icast mode
44,4182511] veth91047eb (unregistering): left promiscuous mode
44.419228] docker0: port 1(veth91047eb) entered disabled state

---

### Post by guiverc on 2024-09-26
I suggest checking and clarifying/correcting your question.

Ubuntu 24.04 LTS is out, as is most recently the [24.04.1 install media]("https://fridge.ubuntu.com/2024/08/30/ubuntu-24-04-1-lts-released/") but 24.04.5 media isn't scheduled for release until August-2026.

KDE Plasma 6.1 has been added to Ubuntu *oracular* or what will be 24.10 (2024-October) in October when released ([https://wiki.ubuntu.com/OracularOriole/Beta/Kubuntu](https://wiki.ubuntu.com/OracularOriole/Beta/Kubuntu)) with 24.04 only having KDE Plasma 5.27 ([https://kubuntu.org/news/kubuntu-24-04-lts-noble-numbat-released/](https://kubuntu.org/news/kubuntu-24-04-lts-noble-numbat-released/))

---

### Post by daring-t on 2024-09-26
Sorry guiverc, I have corrected my post title, the new version I tried to install was 24.04.1.

---

