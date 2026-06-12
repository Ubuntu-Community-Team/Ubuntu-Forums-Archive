---
title: "so I tried kubuntu and ..."
date: 2005-08-10
forum: Desktop Environments
---

### Post by luvdemheels on 2005-08-10
After I rebooted, I cannot enable either network interface under Control Center - Network settings.

When I click Administer mode, it asks for password that I do enter correctly and then after it goes to a loading page it returns to a Welcome to kde control center page and never gives and messages or reason why,

Thanks to that I cannot enable my interface that I need and I am having to post this from windoze.  ](*,)  Does anyone know the solution??????

---

### Post by tonysathre on 2005-08-10
i've had the same problem before too... my solution was to enable it through Gnome then it worked fine

---

### Post by luvdemheels on 2005-08-10
I logged off and do not see an option to log into gnome. I tied ifup ath0 and I am getting an error with my /etc/network/interfaces files.

---

### Post by Takis on 2005-08-10
[QUOTE=luvdemheels]After I rebooted, I cannot enable either network interface under Control Center - Network settings.

When I click Administer mode, it asks for password that I do enter correctly and then after it goes to a loading page it returns to a Welcome to kde control center page and never gives and messages or reason why,
[/QUOTE]
This is a bug that has popped up many a time on these forums. Run
```
sudo kcontrol
```and Control Centre will open up with full administrative priviledges. For a more permanent solution, edit your kmenu and make a copy of the Control Centre shortcut. Rename it to something that will remind you that you'll be running with root priviledges. In the options pane on the right (where you specify name, parameters, etc), where it has the option to run as a different user, enable that but don't specify any user. This implies running as the root user.

---

