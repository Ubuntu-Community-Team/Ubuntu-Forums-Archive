---
title: "Run Official Minecraft Through Proxy?"
date: 2020-11-30
forum: Gaming &amp; Leisure
---

### Post by Tadaen_Sylvermane on 2020-11-30
I've been hammering things out here to get myself behind squid for both http and https. I've got it all worked out except for Minecraft. It says it can't get online. If I disable the proxy I can log in no problem.

I'm using the official Minecraft.deb from [https://launcher.mojang.com/download/Minecraft.deb](https://launcher.mojang.com/download/Minecraft.deb)
According to the wiki page there is a couple of options that can be passed for proxy but they don't seem to work. Google has endless ideas and I've been hacking at it most of the afternoon.

If anyone has anything that works I'd love to see it. Help?

---

### Post by Tadaen_Sylvermane on 2020-12-02
Marking solved. I worked my way through countless permutations of the squid configuration file. Similar to Windows updates one must bypass. I did this by creating an ACL for bypass, and adding the minecraft domains to the list. Link to git with my working results. Some of the links I sourced at the top of my squid.conf for the Windows updates say it's possible but after reading the squid-cache page on the splice subject I don't see how it can work.

[https://github.com/jmgibson1981/scripts/tree/main/docker/squidssl](https://github.com/jmgibson1981/scripts/tree/main/docker/squidssl)

---

