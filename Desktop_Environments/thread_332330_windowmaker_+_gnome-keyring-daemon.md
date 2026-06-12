---
title: "windowmaker + gnome-keyring-daemon"
date: 2007-01-05
forum: Desktop Environments
---

### Post by SamuelDr on 2007-01-05
Hi!

I'm having a hard time searching for this. I tried with google and with the search function here.
Found nothing of interest.

I want to be able to use the gnome-keyring as I was under gnome, but with windowmaker (which I really like).

On google, I found this : [http://ddaa.net/blog/trying-xubuntu](http://ddaa.net/blog/trying-xubuntu)
> You can get gnome-gpg to work in non-GNOME setups by manually starting gnome-keyring-daemon in your X startup script.  Something like this:

  eval `gnome-keyring-daemon`
  export GNOME_KEYRING_SOCKET
  export GNOME_KEYRING_PID

If those environment variables are inherited by gnome-gpg, it should be able to talk to the keyring.

This was a solution to use gnome-keyring-daemon under xfce. I want to do something similar, but can't find how. The idea would be to start it (and export the vars) before or just after windowmaker starts. But, I don't know how to do it. the .xsession doesn't work, neither .xinitrc does.

tried: GNUstep/Library/WindowMaker/autostart 
but the environment variables doesn't work (but the daemon **is** started).

Thanks for anything useful :)

---

### Post by SamuelDr on 2007-01-11
I'm sorry, but I have to bump.

Any windowmaker wiz around?
or gnome-keyring wiz?

---

### Post by SamuelDr on 2007-01-13
Okay, if you can't help me, can you at least tell me where I can get help?
Another forum?

---

### Post by Hub-1 on 2007-01-13
I can't help you with with the keyring itself, but have you tried it with disabling gdm (or kdm) and start your Xsession manually? By starting your session with "*startx*" it should read the .xinitrc file.

---

### Post by SamuelDr on 2007-01-13
It's a good idea, but would I lose the ability to auto-connect my session when my computer boots? I think it's a gdm-wise feature.

---

### Post by Hub-1 on 2007-01-13
> **SamuelDr said:**
> It's a good idea, but would I lose the ability to auto-connect my session when my computer boots? I think it's a gdm-wise feature.
I don't know exactly what you mean with autoconnect to your session, do you mean reload your previous working state?

---

### Post by AgenT on 2007-01-13
> **SamuelDr said:**
> It's a good idea, but would I lose the ability to auto-connect my session when my computer boots? I think it's a gdm-wise feature.If by auto-connect you mean start the session automatically then no, you will not lose the ability to autostart your session. Starting it automatically is very much possible and was done even before GNOME existed. You just need to read up on how to do it (there are multiple ways).

Your best bet is the Gentoo documentation, Gentoo wiki (gentoo-wiki.org) or Debian documentation. Ubuntu is very lacking in this type of documentation.

---

### Post by Hub-1 on 2007-01-13
Hmm something else. In /etc/X11/gdm/gdm.conf there is a section with the following config options:```
# Note that a post login script is run before a PreSession script.  It is run
# after the login is successful and before any setup is run on behalf of the
# user.
PostLoginScriptDir=/etc/gdm/PostLogin/
PreSessionScriptDir=/etc/gdm/PreSession/
PostSessionScriptDir=/etc/gdm/PostSession/
```

I haven't tried this, maybe you can put your script in one of those folders?

---

### Post by SamuelDr on 2007-01-14
> **Hub-1 said:**
> I don't know exactly what you mean with autoconnect to your session, do you mean reload your previous working state?
I mean, that when I boot my computer, I don't have to manually login, I'm automatically logged-in. (it is a single-user machine and the harddrive is passworded, no need to have a second password)

> **AgenT said:**
> If by auto-connect you mean start the session automatically then no, you will not lose the ability to autostart your session. Starting it automatically is very much possible and was done even before GNOME existed. You just need to read up on how to do it (there are multiple ways).

Your best bet is the Gentoo documentation, Gentoo wiki (gentoo-wiki.org) or Debian documentation. Ubuntu is very lacking in this type of documentation.
This would be an idea, so you say you can start a console session automatically?
Nice.
If any other way doesn't work, I'm going to try this one.

> **Hub-1 said:**
> Hmm something else. In /etc/X11/gdm/gdm.conf there is a section with the following config options:```
# Note that a post login script is run before a PreSession script.  It is run
# after the login is successful and before any setup is run on behalf of the
# user.
PostLoginScriptDir=/etc/gdm/PostLogin/
PreSessionScriptDir=/etc/gdm/PreSession/
PostSessionScriptDir=/etc/gdm/PostSession/
```

I haven't tried this, maybe you can put your script in one of those folders?
```

> cat /etc/X11/gdm/PostLogin/Default.sample 
#!/bin/sh
#
# Note: this is a sample and will not be run as is.  Change the name of this
# file to <gdmconfdir>/PostLogin/Default for this script to be run.  This
# script will be run before any setup is run on behalf of the user and is
# useful if you for example need to do some setup to create a home directory
# for the user or something like that.  $HOME, $LOGIN and such will all be
# set appropriately and this script is run as root.
```

Almost it, we'd need something like it, but ran as the user who's logging in... and preferably stored in the home folder. I do not want to mess with the system files, as I have a separate home partition. If break my installation, I don't want to lose many changes like this one.

I'm currently searching on the internet, and will maybe try it even if it is run as root.

oh, I'm not a native english speaker, but would "This script will be run [...] on behalf of the user" mean that anything like gnome-keyring-deamon would work?

anyway, I'll try it, and I'll edit or reply accordingly to the result.

**EDIT:**
Doesn't seem to work by inputting what I said earlier, sadly.
I think it may be because it is run as root, as I pointed out.

---

### Post by SamuelDr on 2007-01-14
I think this merits a new post, for the better visibility possible.

I did it!

It was so simple, I created a new session file, wmaker-sdr.desktop, in /usr/share/xsession/ which led to a sh script somewhere in my homedir (system wipe safe ;)).

Here is my script:
```

#!/bin/bash

eval `gnome-keyring-daemon`
export GNOME_KEYRING_SOCKET
export GNOME_KEYRING_PID

WindowMaker

```

And it works :)

BUT!, there's a but. It is acceptably great on a single-user machine, but on a multi-user machine, this could be considered as dirty. I'm still open to cleaner solutions, but I have newly regained my lovely keyring!

And I don't know why I didn't think of it before.

Thanks to anyone who helped me :)

---

