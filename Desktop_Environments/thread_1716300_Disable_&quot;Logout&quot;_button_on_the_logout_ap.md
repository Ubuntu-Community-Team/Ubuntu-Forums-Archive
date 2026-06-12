---
title: "Disable &quot;Logout&quot; button on the logout applet under XFCE"
date: 2011-03-28
forum: Desktop Environments
---

### Post by cccc on 2011-03-28
Hi

I try to create a very simple thin client with XUBUNTU.
Howto disable "Logout" button in the logout applet under XFCE?
I mean "Logout" option is not possible, when the user press on Logout menu button, then he gets just "Shutdown", "Restart" etc.

I've already tried:```
  
xfconf-query -c xfce4-session -np '/shutdown/ShowLogout' -t 'bool' -s 'false'
```but it doesn't work.

---

### Post by cccc on 2012-02-26
I still cannot find a solution.

---

