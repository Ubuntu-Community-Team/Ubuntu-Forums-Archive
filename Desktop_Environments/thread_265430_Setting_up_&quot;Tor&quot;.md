---
title: "Setting up &quot;Tor&quot;"
date: 2006-09-25
forum: Desktop Environments
---

### Post by uph0ria on 2006-09-25
Does anyone know how to set-up Tor in combination with Privoxy so that you can browse the web anonymously? I'm on an Ethernet LAN with IP:10.0.0.4 and am having trouble using Tor and Privoxy in Firefox. Tor wants to set my HTTP Proxy to localhost:8118 to use Privoxy, yet to be able to connect to the Internet I have to use the HTTP Proxy address 10.0.0.1:808.

---

### Post by davebgimp on 2006-10-08
> **uph0ria said:**
> Does anyone know how to set-up Tor in combination with Privoxy so that you can browse the web anonymously? I'm on an Ethernet LAN with IP:10.0.0.4 and am having trouble using Tor and Privoxy in Firefox. Tor wants to set my HTTP Proxy to localhost:8118 to use Privoxy, yet to be able to connect to the Internet I have to use the HTTP Proxy address 10.0.0.1:808.

Install both through the repositories if you haven't already. Then follow the instrctions on this page:

[http://tor.eff.org/docs/tor-doc-unix.html.en](http://tor.eff.org/docs/tor-doc-unix.html.en)

Pay attention to the part about editing your Privoxy config file. It's only a few steps. The whole thing will be working in about five minutes.

---

### Post by matthew on 2006-10-08
This is getting a little old as it was written for Breezy, but it still works for me on Dapper.

[http://ubuntuforums.org/showthread.php?p=523021#post523021](http://ubuntuforums.org/showthread.php?p=523021#post523021)

---

