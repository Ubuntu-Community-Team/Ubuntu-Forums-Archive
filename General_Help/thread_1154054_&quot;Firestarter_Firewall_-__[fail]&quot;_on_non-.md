---
title: "&quot;Firestarter Firewall -  [fail]&quot; on non-GUI boot - Why?"
date: 2009-05-09
forum: General Help
---

### Post by emarkay on 2009-05-09
I have configured it and tried both to have it autoload, and then to have it automatically start as a process (I then have to enter my password again at boot again.) 

I get the red [COLOR="Red"][fail][/COLOR] at boot.  How do I correct this?

Thanks!

---

### Post by mb_webguy on 2009-05-09
Firestarter is not a firewall.  It is a GUI configuration tool for iptables, the Linux firewall.  It's not necessary to have Firestarter running for iptables to work, and if you're trying to start Firestarter (or any other GUI application) in a non-GUI environment, you're naturally going to get errors.

BTW, Firestarter is rather old, and hasn't been updated in a while.  The official iptables configuration tool for Ubuntu is the CLI-based ufw.  If you want a GUI configuration tool, use gufw.  Most people, however, really don't need to bother with the iptables settings in Ubuntu, especially if you're using a router or behind a network proxy.  All ports are closed on a default installation of Ubuntu, so changing the iptables settings won't make you any safer -- and could very easily cause problems with your network connection.  A router acts as a firewall anyway, so messing with iptables is doubly useless if you have a home network.

---

### Post by emarkay on 2009-05-10
OK, got that, thanks.

I'll unload it  vua Synaptic, - but still, I have always had it in my Ubuntu installs - and never had this "fail" note on boot (I always like to see my booting and shutdowns).

Could this be a bug?

---

