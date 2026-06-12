---
title: "amarok and conky help needed please"
date: 2009-05-20
forum: General Help
---

### Post by merlin_ie on 2009-05-20
Hi everyone. I'm sure people are sick and tired of this topic, but I'm trying to get my Amarok to show in Conky but I get the following error : sh: /home/graham/.conky/amarok: Permission denied...I have a .sh file in the .conky/amarok folder but I don't know if this is correct. I also wonder if it has something to do with the mysql as that has been giving me problems for the last 2 days lol. Running Jaunty Jakalope but downgraded amarok to v1.4 as I heard it was better for mysql.

Anyone care to try and help (hand holding needed lol)

---

### Post by squaregoldfish on 2009-05-21
Is the script executable? Try

```
chmod +x /home/graham/.conky/amarok
```

Steve.

---

