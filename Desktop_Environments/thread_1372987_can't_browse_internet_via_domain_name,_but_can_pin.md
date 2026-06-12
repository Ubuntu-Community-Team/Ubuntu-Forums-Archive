---
title: "can't browse internet via domain name, but can ping domain names"
date: 2010-01-05
forum: Desktop Environments
---

### Post by ffoeg on 2010-01-05
I did an install of Ubuntu 9.10 desktop. Updated the install. Then brought the computer to a different location, different internet connection.
When I tried to connect to the internet, no website would come through via Firefox. If I entered the IP of a website, it came through. But not if I entered the domain name.
I could not use update manager. It would run, but it was unable to connect to the repositories.
When I checked the connection from the terminal (ifconfig), I saw a valid address, subnet, and gateway. When I checked resolv.conf, I saw that network manager was entering the correct nameservers.
When I tried to ping domain names, the ping would go through. But I still could not browse via domain name. I couldn't even open the config window of the Linksys router. I entered the correct password, but no config window would open up.
I went through a complete reinstall at this location, the only improvement was that I could access google.com. I could even run a search, but I couldn't click on any search result links.
The Windows computers at this location were having no problems connecting to the internet at this site.
This is actually a dual boot computer. So, when I boot to Windows it connects without a problem.
When I brought that 9.10 workstation back to the first location, after trying all this at the 2nd locaiton, it connected to the internet right away.
Any ideas on why Ubuntu is having problems at this location?

---

### Post by lovinglinux on 2010-01-05
See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

---

### Post by ffoeg on 2010-01-05
Thanks. I'll look into Firefox optimization. But why wouldn't this be necessary at the first location (where the internet worked at all times)?

---

