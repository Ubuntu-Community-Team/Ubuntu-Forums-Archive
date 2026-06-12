---
title: "Help with IP Tables to get Evolution client around a firewall"
date: 2006-08-07
forum: Desktop Environments
---

### Post by greymoose58 on 2006-08-07
Our family computer is connected to the internet through a proxy server running tinyproxy and DansGuardian. (The parents love DansGuardain.) Unfortunately the machine behind the proxy is unable to connect to the ISP to collect e-mail.

We are using Evolution. As soon as the machine is allowed access to the Internet through the router the e-mail works perfectly. (No proxy settings are touched to make this work.) After much Googling and rumaging throught these forums I find that I am not alone with this problem. 

I have done the following:

[LIST=1]
[*]Make sure the System/Preferences/Network Proxy setting is correct. That is, all of the settings are pointing to the same port - I gather this is correct.
[*]Check the proxy settings in Firefox. (I can't see this being the issue but I'll try anything...)
[*]Run [HTML]Export http_proxy=http://proxy.address.com:portnumber[/HTML]
[/LIST]

I found this discussion [http://www.ubuntuforums.org/showthread.php?t=179080&highlight=proxy+evolution]("http://www.ubuntuforums.org/showthread.php?t=179080&highlight=proxy+evolution")
and would like to try the IPTABLE Rules mentioned in it. I have no idea how to do so. Can anyone explain to me how to add them?

Thanks.

---

