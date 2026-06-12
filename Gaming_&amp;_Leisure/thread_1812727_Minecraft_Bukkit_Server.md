---
title: "Minecraft Bukkit Server"
date: 2011-07-26
forum: Gaming &amp; Leisure
---

### Post by parkerskouson on 2011-07-26
I need help with making a minecraft bukkit server. i have tried every tutorial i could find and cant figure it out. I have a belkin router. And help appreciated.

Parker

---

### Post by Jepic Phail on 2011-07-26
There are numerous posts in this forums alone regarding this very topic. Also few people have written scripts and auto installers for Minecraft. So, I would first suggest that you take advantage of the search function.

Take a look at this [Bukkit wiki article]("http://wiki.bukkit.org/Setting_up_a_server"). Essentially you need to download CraftBukkit jar and run that in place of Minecraft Serve jar. Bukkit used to be a server side mod, but that is no longer the case. The Bukkit project was split into two projects: 1) A temporary API for the Minecraft Beta and 2) server side mod that runs plugins written with Bukkit API. Unless you are planning on developing plugins/mods only thing you need is CraftBukkit. Note that CraftBukkit itself does nothing. You need to download plugins and configure them to your wants and needs.

If your server is running on a remote machine or you want other people to be able to access your server you need to forward ports. You can do this in your [router firewall settings]("http://en-us-support.belkin.com/app/answers/detail/a_id/60/%7E/configuring-port-forwarding"). By default Minecraft uses port 25565.

---

