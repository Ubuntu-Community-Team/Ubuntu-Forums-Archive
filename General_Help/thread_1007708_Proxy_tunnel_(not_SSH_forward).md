---
title: "Proxy tunnel (not SSH forward)"
date: 2008-12-10
forum: General Help
---

### Post by munwin on 2008-12-10
Disregarding the moral / legal / employee issues for a minute.

I am using a PC with no ability to directly connect to the internet. ALL access must go through the corporate proxy server / filter. I cannot connect over any outbound ports at all. Port 80 and 443 have to go through the corporate proxy/filter.

Is it possible to setup a proxy service on my home PC (or a Virtual Private Server somewhere), that I can access over https, through the corporate proxy ?

I am thinking of a web page running on the remote host. The page has a form field that you can input a web address into, and it displays that page. That way, the only info passing through the filter would be the remote link address and the https content.

I would think some combination of apache with some knocked up PHP "should" work OK. 

Anyone have any suggestions ?

---

### Post by s2156945 on 2009-02-19
[http://proxytunnel.sourceforge.net/]("http://proxytunnel.sourceforge.net/")

works great:

Set up ssh on port 443 at home.

Set up proxytunnel at work as a ProxyCommand in ssh.

Set up PPP to use ssh as transport

Set PPP as default gateway.

---

