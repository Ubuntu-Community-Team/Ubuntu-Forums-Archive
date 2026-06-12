---
title: "set proxy globally"
date: 2006-03-31
forum: Desktop Environments
---

### Post by Zelut on 2006-03-31
I understand how to set the proxy settings in Firefox but where/how can I set this globally for the entire machine?  I also need things like ssh, lynx, etc.

Appreciate it.

---

### Post by rwestgeest on 2006-04-01
that is one my big issues with linux. There is not one place to set proxy settings. I have been struggling with this recently. 
For gnome: 'System|Preferences|Network proxy'
For kde: something similar in kcontrol
For commandline: environment variable http_proxy and / or ftp_proxy
For ssh use a progam like corkscrew to get past a proxy. Here's an examble ssh config entry:
   Host myhost
   HostName bla.bloh.com
   User rwestgeest
   ProxyCommand  corkscrew <proxyhost> <proxyport> %h %p

Then 'ssh myhost' should get you past <proxyhost> <proxyport> to blah.bloh.com

There are more application specific ways to get past aproxy like firefox and others.

cheers

---

