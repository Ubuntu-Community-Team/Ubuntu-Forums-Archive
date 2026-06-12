---
title: "Navigate trough ssh"
date: 2009-02-09
forum: General Help
---

### Post by chuse on 2009-02-09
hi to all!

I'd like to navigate the web through another connection, I mean: I'm doing some work at home, but those office computers have access to some web resources which I cannot access from home. So I've been sshing and using lynx, but obviously in the web 2.0 era this is not enough, I need a browser. Do you any have a clue about **navigating the web with a GUI through ssh?**?

thanks,
jose

---

### Post by Ahadiel on 2009-02-09
You can use an ssh tunnel.
```
ssh -D *port* user@host
```
Then through whatever browser you wish to use, set the proxy setting to socks, server = localhost, and port = *port*.

---

### Post by Dr Small on 2009-02-09
Here is a simple guide on it:
[https://help.ubuntu.com/community/SSHHowto#Breaking%20out%20of%20a%20controlled%20network](https://help.ubuntu.com/community/SSHHowto#Breaking%20out%20of%20a%20controlled%20network)

---

### Post by geirha on 2009-02-09
Make sure you turn on X11 Forwarding. Either by setting ```
ForwardX11 yes
``` in /etc/ssh/ssh_config (on the client side), or by adding the -X option each time you connect:
```
ssh -X user@host
```

After logging in with X forwarding enabled, you should be able to run firefox, epiphany, opera or any other GUI web browser you'd like. Note that in the case of firefox, you might need to close firefox on your local box, or else, running firefox on the remote host will just create a new tab or window in your locally running firefox instance, defeting the effort.

---

