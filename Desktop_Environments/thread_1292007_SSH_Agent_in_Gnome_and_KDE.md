---
title: "SSH Agent in Gnome and KDE"
date: 2009-10-15
forum: Desktop Environments
---

### Post by hbj on 2009-10-15
I'm currently running Ubuntu 9.04.  After KDE started the 4.x series I switched to Gnome but have recently been trying KDE again.  One thing I found nice about the Gnome setup was that the first time I used ssh after logging in, a dialog box would pop up asking for my ssh passphrase.  I guess this somehow interfaced with ssh-agent to remember it.

In KDE, I just get a prompt in my terminal window asking for my passphrase, and I have to run ssh-agent myself if I want the passphrase to be remembered.

I really like how Gnome has things set up to do this - it's so simple, and I want something similar when I use KDE.  In the past, I've put different scripts in the KDE autostart folder, hacked some files, etc.  It seems like I must be missing an easy way to do this, but I can't figure it out.  Can somebody help?

---

### Post by Lars Noodén on 2009-10-27
I have KDE set up and using ssh-agent.  Looking at the files related to Xorg, I see three that have ssh-agent in them:

/etc/alternatives/x-session-manager
/etc/X11/Xsession.options
/etc/X11/Xsession.d/90x11-common_ssh-agent

The last one seems to set the environment variables you need, SSH_AGENT_PID and SSH_AUTH_SOCK

---

### Post by Lars Noodén on 2009-10-27
If it's any help, the script startkde is what launches the agent:

```

1032 ?        Ss     0:00 kdm
 1295 tty7     Ss+   17:18  \_ /usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-hIMEoU
 1678 ?        S      0:00  \_ -:0
 2371 ?        Ss     0:00      \_ /bin/sh /usr/bin/startkde
 2416 ?        Ss     0:00          \_ /usr/bin/ssh-agent /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/lars/.gnupg/gpg-agent-info-mini /usr/bin/dbus-launch --exit-with-session /usr/bin/startkde
 2417 ?        Ss     0:01          \_ /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/lars/.gnupg/gpg-agent-info-mini /usr/bin/dbus-launch --exit-with-session /usr/bin/startkde
 2506 ?        S      0:00          \_ kwrapper4 ksmserver

```

---

