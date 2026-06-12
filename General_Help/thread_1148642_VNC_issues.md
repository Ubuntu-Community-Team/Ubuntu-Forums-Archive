---
title: "VNC issues"
date: 2009-05-04
forum: General Help
---

### Post by ashcarr on 2009-05-04
I can connect to the VNC server perfectly, with one huge issue. No actions on the screen 'show up' on the viewer. Effectively, a screenshot has been taken and thats all you get aside from the mouse being tracked.

This screenshot should help explain this:
[IMG]http://farm4.static.flickr.com/3385/3501868850_bf95e43463_b.jpg[/IMG]

The laptop is the client, the monitor is the server. I LOCALLY minimized firefox, which didn't show on the laptop's screen, all clocks are frozen on the time of connection, and as you can see, the menubar at the top is displayed locally, but not shown to the client. The server behaves perfectly normally.

Has anyone ever seen this before?

---

### Post by slimx3m on 2009-05-04
i haven't seen this before, but i would recommend you to make sure that you are allowing port 5900 on the server in order to run propertly.

---

### Post by ashcarr on 2009-05-04
With regards to port forwarding, that is active. Both external (dyndns domain) and internal IP result in the same strange effect.

Thanks for the reply though!

Oh, this same effect happens with Windows' ultra VNC, Mac OS X's built-in VNC as well as Chicken of the VNC (OS X)

---

### Post by cybergalvez on 2009-05-04
there is a problem with vnc and compiz and januty.  if you can compiz turned on vnc is basically useless, try turning compiz off to see if that fixes it

---

### Post by ashcarr on 2009-05-04
Aha! I can't say for sure as I don't have access to the box. However, I think you may have just solved the problem.


Thank you!

EDIT:
Yup, that was the issue.
Is there a workaround or is this being looked into? I hate to just ask without giving, but I wouldn't be of any help to anybody.

---

### Post by Darkade on 2009-05-04
If you are tunneling your connection trough SSH, and you should, and that being the case you are using publickeys, and again you should. You can do the Compiz workaround by adding this before the public key in your ~/.ssh/authorized_keys file
```
command="metacity --replace" <your key>
```

This will start replace Compiz with Metacity as soon as you SSH into the host.

EDIT: here's a useful link in the whole SSH/VNC thing
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

