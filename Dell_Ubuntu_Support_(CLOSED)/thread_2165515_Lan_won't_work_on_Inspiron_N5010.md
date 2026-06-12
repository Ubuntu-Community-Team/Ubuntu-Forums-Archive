---
title: "Lan won't work on Inspiron N5010"
date: 2013-08-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ThunderMoon99 on 2013-08-05
Using Ubuntu 13.10. I have had my computer for several years now and always had the same problem with lan and not being able to connect to lan games through various versions of Ubuntu and various flavors of it. At first I thought it was just something with a firewall setting but I tried looking for firewall settings with no luck. I know it is not the internet because my younger sibling is able to connect to various lan games with no problem with his friend both of them using Ubuntu. I have looked around and I assume I need to install a missing driver, How I don't know. I am still kind of a noobie so I will need a little help.

---

### Post by dieuwe2 on 2013-08-09
I've got the same problem, just open a terminal and type:

sudo ifconfig eth0 up
sudo dhclient eth0

That should bring it back up, but the applet still won't show anything connected and you do have to do this manually every time you log in (unless you put it in a script)

I suspect this is just a bug that will be fixed eventually. I'll let you know if I find out any more.

---

### Post by dieuwe2 on 2013-08-09
Ah, I found the fix just a few minutes later:[URL="http://askubuntu.com/questions/71159/network-manager-says-device-not-managed"]
http://askubuntu.com/questions/71159/network-manager-says-device-not-managed[/URL]

Do do this in a terminal:


> sudo vi /etc/NetworkManager/NetworkManager.conf

Change the line *managed=false* to *managed=true*


Then stop and start network manager:


> sudo service network-manager restart


---

