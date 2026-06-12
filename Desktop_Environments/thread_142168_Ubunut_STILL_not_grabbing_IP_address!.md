---
title: "Ubunut STILL not grabbing IP address!"
date: 2006-03-09
forum: Desktop Environments
---

### Post by nmastae on 2006-03-09
I am at my wits end! I have installed Ubuntu as a dual boot system with Windows 2000 on a separate hard drive. After I power down from Windows and reboot into Ubuntu, I can almost never get online -- Ubuntu recognizes an active ethernet connection, but doesn't seem to be grabbing an IP address. 

I changed the Ubuntu host name to match that used by Windows, but that didn't help.

It's unclear to me why the Ubuntu connection *occasionally* works, though. For instance, last night I booted into Ubunutu using the live CD and was able to get online, no problem. Then I booted into the hard-drive installed Ubuntu and was able to get online then, as well.

After that I rebooted into Windows (where I'm always online), powered down, rebooted into the hard-drive installed Ubuntu -- and zip.  No DSL.

Any suggestions? 

PS Ubuntu *says* it recognizes the DHCP protocol, but it still doesn't connect.

---

### Post by gerbman on 2006-03-10
I'm not quite sure what you mean by "recoginizes the DHCP protocol". Does ```
sudo dhclient
``` complete successfully? Any error messages? If dhclient works, what is the output of ```
ifconfig
```

---

### Post by Djartklom on 2006-03-10
A lot of people seem to be having this problem with Linux and certain ISP's.  I have Qwest DSL and one day my domain name access basically just dried up with occasional sporadic web connectivity.  It really sucks.  Here's the advice I got from somebody over at the excellent [http://linuxforums.org]("http://linuxforums.org"):

"Check your DNS settings in Linux.. if the server IP's are right try DNS servers from someone other than qwest. I see a lot of posts over at broadband reports about Qwest DNS problems preventing people from accessing the net..."

If you check your network settings, you should see that the OS recognizes your DSL modem's IP address.  Indeed, rare is the Linux distro nowadays that doesn't configure that stuff automatically.  The problem is likely your domain name server, which is addressed in the same menu.

---

