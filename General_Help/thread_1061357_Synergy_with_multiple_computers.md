---
title: "Synergy with multiple computers"
date: 2009-02-05
forum: General Help
---

### Post by Dave_Connor on 2009-02-05
I am trying to run synergy on my ASUS eee with my desktop and laptop. My Desktop and Laptop work but with my eee it will just refuse to connect. With synergyc -f computer it shows its running but it will refuse to work with my mouse/ keyboard. My synergy.conf is here
```
  
  computer1:
  computer2:
  computer3:
end
section: links
  computer1: 
  left = computer2
  right = computer3
  computer2:
  right = computer1
  coomputer3:
  left = computer1
end

```
I have no idea and I can't find examples of synergy.conf files that have more then 2 systems.

---

