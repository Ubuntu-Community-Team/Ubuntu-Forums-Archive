---
title: "apt-get, update manager &amp; synaptic behind proxy"
date: 2012-01-19
forum: Desktop Environments
---

### Post by mstjohn1974 on 2012-01-19
I am having a problem with my Ubuntu desktop 11.04. My Company  implemented a proxy where everything has to go thou and it used AD  integration for user authentication. I added proxy settings to several  locations on my system and apt-get, update manager and synaptic package  manager are not working. Firefox asks every single time when I start it  for User name and password and I have to enter DOMAIN\Username and my  password for it to work. I added the proxy information to the following  configurations:

1. <System><Preferences><Network-Proxy>
2. /etc/bash.bashrc and exported it
3. /etc/apt/apt.conf
4. gconf-editor <system><http_proxy>

and none helped to make it work.

I am wondering if there is a possibility that certain symbols are not allowed to be used for that like a - or and !?

I tried the following syntax for the configuration files:

[http://username:password@ip-address:port](http://username:password@ip-address:port)

anything I forgot or did wrong?

Please let me know if you need more information.

---

### Post by jerrrys on 2012-01-21
Im not behind a proxy so I don't know, but though this may help you.  good luck

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+behind+proxy&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+behind+proxy&sa=Search&cof=FORID:9)

---

