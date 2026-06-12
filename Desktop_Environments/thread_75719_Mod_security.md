---
title: "Mod_security"
date: 2005-10-14
forum: Desktop Environments
---

### Post by dbee on 2005-10-14
I've been having some difficulties with mod_security ... namely that it doesn't actually seem to want to work ??

I've been messing around with apache for a few days now, just installing it and uninstalling it in different ways. 
If I take it straight off synaptic - why aren't the config files that go with it free from 

<ifModule mod_security.so>

... there is no way to alter it's setting ... I'm using the mod_sec manual and I can get it installed fine, but I was expecting the httpd.conf file to show some mod_sec modifications ... nothing !!

and when I add them myself, such as 

SecChrootDir

it appears as if it's still running from 

/usr/local/apache 

????

---

