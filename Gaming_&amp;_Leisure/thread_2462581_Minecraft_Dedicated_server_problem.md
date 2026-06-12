---
title: "Minecraft Dedicated server problem ?"
date: 2021-05-23
forum: Gaming &amp; Leisure
---

### Post by wazabiqc on 2021-05-23
Hi ! I am currently trying to host a minecraft server , ran in a docker container on ubuntu. The server does seem to run fine because I can access it locally, but no one else can connect.. My ports are forwarded on the router, I allowed the port through ufw and enabled ufw too.. But still cannot reach it ! Is there anything in ubuntu server 20.04.2 that could prevent this ?

---

### Post by Tadaen_Sylvermane on 2021-05-23
More likely an isp problem. Do you have a static ip / business package with them? With a static ip you get ports unblocked. Just because they are open on your router doesn't mean the isp lets them through. Typically they don't want people hosting servers on home plans regardless of what the server is... At least in my area. Around here I can get a static ip for an additional 10 bucks a month. For that price I chose instead to run it on AWS. Don't play much anymore though so it's gone now.

---

### Post by mastablasta on 2021-05-24
if you can access it locally, but not from outside then the issue is really in one of the ports not being forwarded outside of LAN.

also make sure that server is not set to lan mode or something like that. forgot how it is called. in that case you can really only access it locally or through VPN.  i only ever setup a local server for the kids.

---

