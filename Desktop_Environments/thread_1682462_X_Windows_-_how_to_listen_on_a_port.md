---
title: "X Windows - how to listen on a port"
date: 2011-02-05
forum: Desktop Environments
---

### Post by Skaperen on 2011-02-05
It appears that X Windows under Ubuntu (or Gnome?) is started to listen to a Unix named socket, instead of a TCP port number, for client connections.  That's what SSH is forwarding when it does X forwarding.

I need to start X applications on a remote machine, and then close the SSH connection.  So I need to make the connections directly.  This is within a LAN on private IPs, so security is not an issue.

I searched on help.ubuntu.com, but there appears to be no particular document that covers this.  Anyone know where this is configured to enable it to listen on a TCP port like the usual 6000?

---

### Post by gmargo on 2011-02-06
```

$ grep nolisten /etc/X11/*/*
/etc/X11/xinit/xserverrc:exec /usr/bin/X -nolisten tcp "$@"

```You can try editing that file and take out the "-nolisten tcp".

---

### Post by Skaperen on 2011-02-07
> **gmargo said:**
> ```

$ grep nolisten /etc/X11/*/*
/etc/X11/xinit/xserverrc:exec /usr/bin/X -nolisten tcp "$@"

```You can try editing that file and take out the "-nolisten tcp".
There's no GUI config for that?

---

### Post by Skaperen on 2011-02-07
> **gmargo said:**
> ```

$ grep nolisten /etc/X11/*/*
/etc/X11/xinit/xserverrc:exec /usr/bin/X -nolisten tcp "$@"

```You can try editing that file and take out the "-nolisten tcp".
It did not work.  That option must be coming from somewhere else.

```
lorentz/root /root 6# cat /etc/X11/xinit/xserverrc
#!/bin/sh
exec /usr/bin/X "$@"
lorentz/root /root 7# time find /etc /usr /var -type f -exec egrep -l 'nolisten[[:space:]]*tcp' '{}' ';'
/etc/X11/xinit/xserverrc-original
/usr/share/gnome/help/gdm/C/gdm.xml
/usr/share/gnome/help-langpack/gdm/en_GB/gdm.xml
/usr/share/doc/nvidia-current/html/framelock.html
/usr/bin/x11vnc
[[ 4m55s real 295.434 - user 2.840 - sys 18.220 - 7.12% ]]
lorentz/root /root 8# 
```

---

### Post by krunge on 2011-02-07
Check the gdm desktop manager settings.  gdm starts the X server.

On a squeeze machine I have:

defaults: /usr/share/gdm/defaults.conf
custom:   /etc/gdm/gdm.conf  

```

# If true this will basically append -nolisten tcp to every X command line, a
# good default to have (why is this a "negative" setting? because if it is
# false, you could still not allow it by setting command line of any particular
# server).  It's probably better to ship with this on since most users will not
# need this and it's more of a security risk then anything else.
# Note: Anytime we find a -query or -indirect on the command line we do not add
# a "-nolisten tcp", as then the query just wouldn't work, so this setting only
# affects truly attached sessions.
DisallowTCP=true

```

Your distro's gdm configuration files may be different.

---

### Post by gmargo on 2011-02-08
It is documented in the gdm help, which is a pain to find. (I found it by grepping through /usr and found it in /usr/share/gnome/help-langpack/gdm/en_GB/gdm.xml.)

Add the following to **/etc/gdm/custom.conf**:
```

[security]
DisallowTCP=false

```

---

### Post by Skaperen on 2011-02-09
> **gmargo said:**
> It is documented in the gdm help, which is a pain to find. (I found it by grepping through /usr and found it in /usr/share/gnome/help-langpack/gdm/en_GB/gdm.xml.)

Add the following to **/etc/gdm/custom.conf**:
```

[security]
DisallowTCP=false

```
That worked.  The file did not exist, so I added it with just that content alone.  The name "custom" seems to imply that would be the thing to do.

---

