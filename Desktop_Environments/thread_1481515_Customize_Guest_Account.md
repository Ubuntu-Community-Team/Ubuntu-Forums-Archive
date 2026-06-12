---
title: "Customize Guest Account"
date: 2010-05-12
forum: Desktop Environments
---

### Post by kid1000002000 on 2010-05-12
Hi;

I occasionally let others use my computer and want to be able to use the guest account to protect my data.  Its really annoying, however, to have setup windows pop up at the beginning of every guest session and have to customize it every time I log in.  What I would like is some way to preserve settings that could be made in the guest account.

How can I do this?  I'm not finding anything from search.

Edit: Its ok to scrub the guest account clean, but not *everything!*

---

### Post by kid1000002000 on 2010-05-19
bump

---

### Post by portentum on 2010-05-19
[This]("http://www.linuxquestions.org/questions/ubuntu-63/how-do-i-change-the-default-settings-for-the-guest-account-683503/") pointed me to the /usr/share/gdm/guest-session/guest-session-setup.sh file.

It looks like it copies the /etc/skel directory as a guest /home on each login.

The way I would handle it is to log in as guest, get it set up the way you like, then open a terminal and cp your modified guest /home to something like /etc/skel_guest. Then change the guest-session-setup.sh file so that it copies /etc/skel_guest instead of /etc/skel.

I'm not sure what the actual path for guest's home would be, but as an example of what I'm talking about..
```

sudo cp -r /home/Guest /etc/skel_guest

```

Line 47 in guest-session-setup.sh has the command it executes for the cp that you would alter
```

from this:
cp -rT /etc/skel/ "$HOME"

to this:
cp -rT /etc/skel_guest/ "$HOME"

```

---

### Post by areseapea on 2010-05-19
Note for Lucid Lynx users:

On the fresh install that I have been attempting this on, it puts the generated guest account in:

/tmp/guest-home.XXXXXX

Where XXXXXX is an apparently random string.  Other than that, this appears to work flawlessly.

---

### Post by Matti L on 2010-05-19
If your lazy like me and don't want to do anything so complicated then just make a new unprivileged user, set it up like you want, and use a simple password (or it seems you can use no password on Lucid now).

---

### Post by portentum on 2010-05-19
> **Matti L said:**
> If your lazy like me and don't want to do anything so complicated then just make a new unprivileged user, set it up like you want, and use a simple password (or it seems you can use no password on Lucid now).
This misses the point of a guest account, however. It means each guest doesn't get a blank, clean account to work with.

---

### Post by Gunnar Hjalmarsson on 2010-09-13
I wrote a tutorial, [Customize guest session]("http://ubuntuforums.org/showthread.php?t=1566078"), that provides a few customization examples.

---

### Post by kainalu on 2011-04-08
This Guide was a help to me. Thanks.

---

