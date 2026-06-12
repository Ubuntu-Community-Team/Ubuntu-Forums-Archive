---
title: "installing gnome on 10.04"
date: 2010-08-23
forum: Desktop Environments
---

### Post by needhelp0815 on 2010-08-23
hi

I have ubuntu 10.04 running on my server. I want to install gnome there so that I can do remote desktop with vnc. however, if I type in the following command:

```
apt-get install gnome
```

then it returns the following:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome: Depends: swfdec-mozilla but it is not going to be installed
E: Broken packages
```

Thank you for your help =)

---

### Post by utnubuuser on 2010-08-24
sudo apt-get install ubuntu-desktop

---

### Post by needhelp0815 on 2010-08-24
I have installed "ubuntu-desktop" now. Then I started tightvncserver and connected to VNC. However I only got a command line there. Then I typed in startx and it returned this:

```
exec: 3: /usr/bin/X: not found
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
```

---

### Post by needhelp0815 on 2010-08-24
*push*

I know it's seen as rude to push a thread after just some hours are gone, but I need the server really urgently at the moment, so it would be good to get help from someone.

---

