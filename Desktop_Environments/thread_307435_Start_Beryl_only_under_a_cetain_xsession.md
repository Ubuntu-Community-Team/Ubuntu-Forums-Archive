---
title: "Start Beryl only under a cetain xsession?"
date: 2006-11-26
forum: Desktop Environments
---

### Post by Jessehk on 2006-11-26
I recently set up Xgl by having its own xsession.

I have a session file located in
/usr/share/xsessions that looks like the following:

```

[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application

```

And /usr/bin/startxgl.sh looks like this:
```

#!/bin/sh 
Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
DISPLAY=:1
exec gnome-session

```

As a result of that setup, I can choose if I want a normal, or Xgl session in GDM.

Now, the problem.
I want beryl-manager to only start when I am in the xgl xsession, not in the normal one. When I put beryl-manager as a startup program in the gnome sessions menu, it starts for both xsessions (and crahses my X when I'm not in the correct one).

How can I get beryl to start only when I'm in the xgl xsession?

Thanks in advance. :)

---

### Post by Jessehk on 2006-11-26
Bump :)

---

### Post by dmartinsca on 2006-11-26
I'd log in to the XGL session first and remove beryl from your gnome session. Then edit the startxgl.sh file so it's something like this:

```
#!/bin/sh 
Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
DISPLAY=:1
beryl-manager
sleep 4
exec gnome-session
```

You might find that sometimes the gnome loading screen thing gets stuck on for a while saying that it's starting the window manager. It disappears after a while and doesn't seem to really affect anything. I'm not sure why this happens.. Other than that it works great.

---

### Post by Jessehk on 2006-11-26
Thanks for the tip. :)

 It worked just as you said, but I don't like the stalling splash-screen.
I decided to just add beryl-manager to start-up programs and change it when necessary (as I really, really like beryl :p).

---

