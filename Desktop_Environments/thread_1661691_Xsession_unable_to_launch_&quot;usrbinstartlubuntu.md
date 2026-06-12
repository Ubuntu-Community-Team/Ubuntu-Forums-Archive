---
title: "Xsession: unable to launch &quot;/usr/bin/startlubuntu&quot; X session"
date: 2011-01-07
forum: Desktop Environments
---

### Post by tranduyhung on 2011-01-07
Hello,

I'm building my own lightweight desktop with LXDE. After installing minimal Ubuntu (command line mode) from alternative CD, I installed xorg, x11 and lxde-core. After restarting I got this error when starting graphical interface:

> Xsession: unable to launch "/usr/bin/startlubuntu" X session ---
"/usr/bin/startlubuntu" not found; falling back to default session.

After clicking "Okay" button I could see LXDE interface as normal.

This is my /etc/lxdm/lxdm.conf:
```
[base]
# autologin=dgod
# session=/usr/bin/startlxde
# numlock=0
greeter=/usr/lib/lxdm/lxdm-greeter-gtk

[server]
# arg=/usr/bin/X -nr vt1

[display]
gtk_theme=Clearlooks
bg=/usr/share/backgrounds/default.png
bottom_pane=1
lang=1
theme=Industrial

[input]

```

I don't know why there was something about Lubuntu here.

How could I fix this problem?

Regard.

---

### Post by Brandon Williams on 2011-01-08
I don't run lxdm, so I'm not sure where it gets its session information from. The rest of my response assumes that it uses the same xsession configuration that gdm and kdm use. If I'm wrong about that, then the rest of this post won't make any sense.

Take a look in /usr/share/xsessions. Does one of the .desktop files there reference lubuntu? If so, this is probably the selection that you're picking for session type. When it doesn't work, Xsession is falling back to the default session, which will run your .xsession file, if it exists. I'm guess that you have a .xsession file that works correctly for initializing your lxde session, and that's why things are starting up for you as expected. gdm installs a file that represents a customer user session: xsession.desktop```
[Desktop Entry]
Name=User Defined Session
Comment=Custom ~/.xsession script
Exec=default
X-Ubuntu-Gettext-Domain=gdm
``` If lxdm uses the files in this directory and this file is not present in /usr/share/xsessions, then create it and select "User Defined Session" as your session type so that your .xsession file will be used instead of the missing startlubuntu script.

---

### Post by fahryrozy on 2011-04-09
> **Brandon Williams said:**
> I don't run lxdm, so I'm not sure where it gets its session information from. The rest of my response assumes that it uses the same xsession configuration that gdm and kdm use. If I'm wrong about that, then the rest of this post won't make any sense.

Take a look in /usr/share/xsessions. Does one of the .desktop files there reference lubuntu? If so, this is probably the selection that you're picking for session type. When it doesn't work, Xsession is falling back to the default session, which will run your .xsession file, if it exists. I'm guess that you have a .xsession file that works correctly for initializing your lxde session, and that's why things are starting up for you as expected. gdm installs a file that represents a customer user session: xsession.desktop```
[Desktop Entry]
Name=User Defined Session
Comment=Custom ~/.xsession script
Exec=default
X-Ubuntu-Gettext-Domain=gdm
``` If lxdm uses the files in this directory and this file is not present in /usr/share/xsessions, then create it and select "User Defined Session" as your session type so that your .xsession file will be used instead of the missing startlubuntu script.
Where can i found this .xsession script ?

---

### Post by sucksatcompiling on 2012-10-29
> **fahryrozy said:**
> Where can i found this .xsession script ?

In his example:
Comment=Custom ~/.xsession script

Where ~/ is your home directory (e.g. /home/user == ~/)

I had the same problem as the original poster.  It was very frustrating because I was using ubuntu-builder to build a custom Ubuntu-mini remix 12.04 distro.  It worked great, I tested the build with Ubuntu-builder Desktop mode and built the iso.  Cool.  I boot the live CD for the first time and I get the same problem as the OP.  Weird.  I looked at the /etc/lxdm/lxdm.conf file and it has /etc/startlubuntu.  

Since I only plan to use this for CD's (no persistence mode use), I returned to ubuntu-builder to change the lxdm.conf to startlxde, but to my surprise, it was set to startlxde in the iso.  wtf

I even took the paranoid route and did the manual process of mounting the iso, unsquashing the filesystem and verify the lxdm.conf file was correct in the iso.  It was.

After a while of scratching my head, I decided to take the easy way out...
ln -s /etc/bin/startlxde /etc/bin/startlubuntu

It's not very elegant and I still don't understand why when I boot the live CD it changes the lxdm.conf file to look for startlubuntu instead of startlxde, but either way, creating a symbolic link works like a charm.

If anyone has insight as to why this is the case (lxdm.conf being changed on boot), I'd sure be interested to hear it.

---

### Post by wildmanne39 on 2012-10-30
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

