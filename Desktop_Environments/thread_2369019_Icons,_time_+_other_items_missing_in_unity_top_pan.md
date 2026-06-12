---
title: "Icons, time + other items missing in unity top panel"
date: 2017-08-17
forum: Desktop Environments
---

### Post by heisenberg333 on 2017-08-17
Dear all,

I was Kubuntu user for some time but decided to switch back to using Ubuntu. So I installed ubuntu-desktop and ran into few problems.

1. When I log in to Ubuntu, no window borders or unity panels are showing. So I need to manually start unity from terminal.
2. When I have started unity manually I have no icons, time, battery status, volume, notifications etc. showing on top panel. It's just black panel with no info. I have googled quite intensively to find solution but have not found working solution yet. 

I would really appreciate if you could help me with this issue. 

Thank you in advance,

Arto

---

### Post by again? on 2017-08-17
Try to reset and reload unity
```
dconf reset -f /org/compiz/ && setsid unity
```

---

### Post by heisenberg333 on 2017-08-18
Thank you for the reply. Unfortunately resetting and reloading unity did not help the issue.

---

### Post by again? on 2017-08-18
What you can do is determine if it's a user setting or a system problem by creating a 
new user account, login and test that account.

---

### Post by heisenberg333 on 2017-08-18
I created new user and it has the same issue which indicates that this is system problem.

---

