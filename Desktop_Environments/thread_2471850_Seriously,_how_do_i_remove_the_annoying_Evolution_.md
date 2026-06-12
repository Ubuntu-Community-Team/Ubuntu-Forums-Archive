---
title: "Seriously, how do i remove the annoying Evolution Alarm Notifications?"
date: 2022-02-11
forum: Desktop Environments
---

### Post by dbee on 2022-02-11
how do i remove the annoying Evolution Alarm Notifications?

I still want to get general slack, gmail, calendar etc... notifications.

---

### Post by ActionParsnip on 2022-02-11
What is the output of:
```

lsb_release -a; uname -a; dpkg -l | grep -i evolution

```
Thanks

Do you use Evolution as an application in any way?

---

### Post by mIk3_08 on 2022-02-11
> **dbee said:**
> how do i remove the annoying Evolution Alarm Notifications? 
I think you can easily remove these messages alert on Thunderbird. Just go to the Thunderbird preferences,
located on the Thunderbird Menu --> then go to Edit --> then go to Preferences then go to -->
General tab at the left side of the preferences window then browse the windows at the bottom and find the "Incoming Emails" tab under
the "General" window then if you find a "Customize..." button Click it. then a window will show you with the radio boxes
Just uncheck the *Message Preview Text *Subject *Sender then Click OK.
Under the "Incoming Emails" tab you should uncheck too the "Show an alert" radio box and the" Use the system notification" radio box and "Play a Sound" radio box too. 
So Good luck and cheers.

---

### Post by Jaxilian on 2022-02-15
> **dbee said:**
> how do i remove the annoying Evolution Alarm Notifications?

I still want to get general slack, gmail, calendar etc... notifications.

It should be under Ubuntu Settings > Notifications > Evolution Alarm Notify

---

### Post by dbee on 2022-04-03
> **Jaxilian said:**
> It should be under Ubuntu Settings > Notifications > Evolution Alarm Notify

I've turned Evolution Alarm Notify off. I still get these really annoying popup notifications.

> **ActionParsnip said:**
> What is the output of:
```

lsb_release -a; uname -a; dpkg -l | grep -i evolution

```
Thanks

Do you use Evolution as an application in any way?

```
dara@laptop-20-04:~$ lsb_release -a; uname -a; dpkg -l | grep -i evolution
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 21.10
Release:	21.10
Codename:	impish
Linux laptop-20-04 5.13.0-39-generic #44-Ubuntu SMP Thu Mar 24 15:35:05 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
ii  evolution-data-server                      3.40.4-1ubuntu1                              amd64        evolution database backend server
ii  evolution-data-server-common               3.40.4-1ubuntu1                              all          architecture independent files for Evolution Data Server
ii  libcamel-1.2-62:amd64                      3.40.4-1ubuntu1                              amd64        Evolution MIME message handling library
ii  libebackend-1.2-10:amd64                   3.40.4-1ubuntu1                              amd64        Utility library for evolution data servers
ii  libebook-1.2-20:amd64                      3.40.4-1ubuntu1                              amd64        Client library for evolution address books
ii  libebook-contacts-1.2-3:amd64              3.40.4-1ubuntu1                              amd64        Client library for evolution contacts books
ii  libecal-2.0-1:amd64                        3.40.4-1ubuntu1                              amd64        Client library for evolution calendars
ii  libedata-book-1.2-26:amd64                 3.40.4-1ubuntu1                              amd64        Backend library for evolution address books
ii  libedata-cal-2.0-1:amd64                   3.40.4-1ubuntu1                              amd64        Backend library for evolution calendars
ii  libedataserver-1.2-26:amd64                3.40.4-1ubuntu1                              amd64        Utility library for evolution data servers
ii  libedataserverui-1.2-3:amd64               3.40.4-1ubuntu1                              amd64        Utility library for evolution data servers

```

No. AFAIK I'm pretty sure I don't use Evolution.

So at the end of the day, I softlink'd the Evolution dataserver .service files to /dev/null as per @PAStheLoD suggestion here...

[https://askubuntu.com/questions/315640/how-do-i-completely-remove-evolution](https://askubuntu.com/questions/315640/how-do-i-completely-remove-evolution)

---

### Post by dbee on 2022-04-06
The above solution doesn't work guys.

Evolution is still triggering notifications :-(

Very annoying. 

Does anyone have a proper solution?

---

### Post by ActionParsnip on 2022-04-08
[https://gitlab.gnome.org/GNOME/gnome-control-center/-/issues/295](https://gitlab.gnome.org/GNOME/gnome-control-center/-/issues/295)

---

### Post by dbee on 2022-04-12
Like a bad dream, just when you think you've gotten rid of this thing. It reappears.


As per gitlab.gnome.org link. Running a

```

rm ~/.local/share/evolution/calendar/system/calendar.ics

```

Removes the offending .ics file. But the file gets replaced on system startup.

The solution I came up with is to delete this file on system start using the crontab ie. 

```

crontab -e

```

```

@reboot rm ~/.local/share/evolution/calendar/system/calendar.ics


```

Just remember to leave the newline at the end at EOF (End Of File). This solution works.

---

### Post by dbee on 2022-04-13
Damn. Damn. Damn.

The .ics file reappears - like a bad case of herpes.

The above solution doesn't work guys. If anyone has any other ideas. I'd love to hear them.

---

