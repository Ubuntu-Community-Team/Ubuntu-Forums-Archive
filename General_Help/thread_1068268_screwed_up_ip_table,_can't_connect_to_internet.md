---
title: "screwed up ip table, can't connect to internet"
date: 2009-02-12
forum: General Help
---

### Post by days_of_ruin on 2009-02-12
I ran this script [http://wiki.ekiga.org/index.php/Ekiga_behind_a_NAT_router#What_iptables_rules_could_I_use_for_GNU.2FLinux.3F]("http://wiki.ekiga.org/index.php/Ekiga_behind_a_NAT_router#What_iptables_rules_could_I_use_for_GNU.2FLinux.3F")

hoping it would make ekiga work but it gave some error about certain directories not existing. But now I can't connect to the internet nor 
can I secure shell.What is the default iptables settings?

---

### Post by firsttimeuser on 2009-02-12
run an "iptables -F" to flush all the rules and you should be able to connect

---

### Post by days_of_ruin on 2009-02-12
> **firsttimeuser said:**
> run an "iptables -F" to flush all the rules and you should be able to connect

Yeah I just figured that out before reading your post.I should mention
that it won't work right away; I had to restart the computer (I am sure there is a way to do it without restarting).

---

