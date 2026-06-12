---
title: "Can't access the net with proxy in firefox"
date: 2005-11-12
forum: Desktop Environments
---

### Post by mfyahya on 2005-11-12
I configured firefox to use a proxy so I can bypass my country's censors. This works fine in firefox on Windows, but not in ubuntu although I have the exact same proxy settings. What could be wrong?

---

### Post by spizkapa on 2005-11-12
Perhaps you need to set up a global proxy for gnome by going to System -> Preferences -> Network Proxy. I do that at work and it works fine.

---

### Post by Dr. Nick on 2005-11-12
It works for me without a global proxy in FF
Is it a proxy you got online somewhere, or a local proxy like privoxy+tor?

You try it in epiphany? if you do use it in epiphany you must set the global under system-prefrences-network proxy dialog

---

### Post by mfyahya on 2005-11-13
It's an apache proxy on a US server.
I set the global proxy in Preferences->Network Proxy, and now I can access blocked sites in epiphany, but it still doesn't work in firefox.
What is this global proxy? Will all applications eg wget, bittorrent use it? I just need the proxy for basic browsing, and don't want to use a lot of its bandwidth.
And I'd rather make the proxy work with firefox, I'm using the SwitchProxy extension which makes it easy to turn the proxy on or off as needed.
This is the error that Firefox pops up:

"The proxy server you have configured could not be found. Please check the settings and try again"

Thanks for any help

---

### Post by Dr. Nick on 2005-11-13
The global proxy is what some applications will use, mainly gnome ones that dont have their own proxy options. I know firefox doesnt use it , not sure on BT. If you dont mind maybe posting the address here or are you trying several proxies? I have no trouble using them in FF so its hard to troubleshoot. Are they http or socks proxies?

My only guess which may/maynot work is disabling ipv6 or changing socks types in the connection settings. To disable ipv6 type ```
about:config
``` into the FF address bar, filetr ipv6 and set the result to true

---

### Post by mfyahya on 2005-11-14
I already had ipv6 disabled, someone told me that speeds up firefox.
The proxy I'm using is one I set up myself on a server I rent in the US. I had to do that because my ISP actively monitors and blocks most open proxies and anonymizing services. I have apache's mod_proxy configured so that it only allows a few IP addresses belonging to me and some friends to connect. I know it's bad for the net in general to leave a proxy completey open, but I could do it for sometime if you want to take a look.
I do think however that the problem is with firefox in ubuntu, because it works fine in epiphany and also in firefox on my winxp box.

---

### Post by Dr. Nick on 2005-11-14
yeah if it works in other browsers I would bet the server side is set up correctly and that FF is the problem. I dont know what would interfere with it though. 

Hope you figure it out or that someone else can help some as I dont know what it could be

---

