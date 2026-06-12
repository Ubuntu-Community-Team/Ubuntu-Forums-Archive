---
title: "Networking problems"
date: 2006-04-30
forum: Desktop Environments
---

### Post by OMJD on 2006-04-30
Right, I installed Kbuntu and eth0 is disabled. I want to enable it won't let me login with su root through the gui. It says incorrect password. However, in terminal, it lets me su to root fine without any problems. Does anyone know how to start eth0 through terminal?

Thanks.

---

### Post by dauchuot on 2006-04-30
Don't type su's passwd ! You login Kubuntu with user's passwd, therefore use this passwd to login  through the gui. Lucky!

---

### Post by [S|G] on 2006-05-01
First, you shouldn't try to login as root, as it is as SERIOUS securty risk ;) Use "sudo <command>" instead to do something as root.

Now, as for your problem: Login normally and open up a terminal window (usually kterm on kubuntu). Now, to just bring up eth0, type:
```

sudo ifup eth0

```

Now if you need to configure your network device, I'd suggest reading the manpages for ifconfig:
```

man ifconfig

```

Also, for an easier way out, click on your K menu -> system settings -> network settings. You should now be at the network configuration page. You just need to click on the "Administrator Mode" at the bottom in order to make any chages :)

---

