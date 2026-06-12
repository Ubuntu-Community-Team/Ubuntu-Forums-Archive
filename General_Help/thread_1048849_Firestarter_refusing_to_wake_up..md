---
title: "Firestarter refusing to wake up."
date: 2009-01-23
forum: General Help
---

### Post by yanom on 2009-01-23
When I boot my system, i get this message:

[code]
Starting the Firestarter firewall...        [failed]

so now I have to start firestarter when I login. I'm tired of Firestarter sleeping late, so how do i get it to start at bootup?

---

### Post by oldos2er on 2009-01-23
Why do you need to start it at bootup?

---

### Post by 2hot6ft2 on 2009-01-23
> **yanom said:**
> When I boot my system, i get this message:

[code]
Starting the Firestarter firewall...        [failed]

so now I have to start firestarter when I login. I'm tired of Firestarter sleeping late, so how do i get it to start at bootup?
It shows that while booting up but it should be running once the desktop is up and running without you manually starting it. I get the same message but it's running fine once the desktop is up.

---

### Post by mcduck on 2009-01-24
> **oldos2er said:**
> Why do you need to start it at bootup?

Because he wants a firewall?

The Firestarter service has to be running, the GUI doesn't.

Anyway, just like 2hot6ft2 suggested, you should check if the service starts after you have logged it. Frestarter can fail to start if your network connection isn't started during boot, for example if you are using Network manager to connect to wireless network. THe service should still start as soon as your network starts. You can check firestarter's status with the following command:

```
sudo /etc/init.d/firestarter status
```

---

### Post by oldos2er on 2009-01-24
I thought Firestarter was a configuration tool that was used once, and no longer required. Do its changes not persist across shutdwn and boot?

---

### Post by yanom on 2009-01-24
It's changes stay, does that mean I don't have to start it every time I login?

---

### Post by mcduck on 2009-01-25
> **oldos2er said:**
> I thought Firestarter was a configuration tool that was used once, and no longer required. Do its changes not persist across shutdwn and boot?

Actually Firestarter has to parts, the GUI tool for changing firewall configuration & monitoring traffic, and Firestarter script (running as a service) that loads firewall rules at boot.

All iptables rules clear on reboot so some script or other way to restore them after boot is needed. That's how iptables/netfilter works, it's not a firewall, only collection of all the tools needed to create one. Pretty much every Linux firewall is actually just a script that loads your iptables rules at startup. (more advanced scripts might also monitor traffic and change the rules on-the-fly for better protection against different kinds of attacks).

---

