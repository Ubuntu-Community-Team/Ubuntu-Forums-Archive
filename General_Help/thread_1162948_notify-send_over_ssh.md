---
title: "notify-send over ssh"
date: 2009-05-18
forum: General Help
---

### Post by Error403 on 2009-05-18
Hi, I occasionally ssh to my home pc from a public pc at work, and would like to be able to send some messages to the person in front of the computer.  In past versions I remember I could do it, but now when I use notify-osd it prints out:

libnotify-Message: Unable to get session bus: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


Any ideas?  Thanks!

---

### Post by spacesamurai on 2009-05-18
While I am not exactly sure how to fix it, my guess from your error message is that you are running a Gnome-session as opposed to a Xsession. Is there any way you are able to run notify send with starting the Xsession?

```
dbus-launch /etc/X11/xdm/Xsession
```

---

### Post by marcoc2 on 2009-07-08
Not with notify, but it worked fine for me:

After **ssh** type:

```
xmessage MESSAGE -display :0 &
```

(maybe you will need **sudo**)

from: [http://en.andregondim.eti.br/?p=72](http://en.andregondim.eti.br/?p=72)

---

### Post by jfanaian on 2009-07-13
I had the same issue, and it turned out that X11Forwarding was disabled. Check /etc/ssh/sshd_config and make sure `X11Forwarding` is set to `yes`. Once you do that, restart ssh `sudo /etc/init.d/ssh restart` and connect to ssh with -Y `ssh -Y user@hostname`. Then try `notify-send`. Also, make sure you have libnotify1 and libnotify-bin installed (both may not be necessary).

I've gotten it to work but it's using the old libnotify (pre-jaunty). Please let me know if you figure out how to get it to work with the new libnotify.

---

