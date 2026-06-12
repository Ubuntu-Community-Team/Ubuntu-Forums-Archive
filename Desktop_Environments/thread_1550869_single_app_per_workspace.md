---
title: "single app per workspace"
date: 2010-08-11
forum: Desktop Environments
---

### Post by Lewis Cowles on 2010-08-11
Hello, This is my first post so please be gentle... Is there a way to restrict a single application to each workspace?

I am referring to workspaces as the screen representations shown in the workspace switcher (next to my trash icon)

Also if this is possible, is it possible to have a script or application that re-launches the application if it is shut down, crashes or prevent the application minimizing.

I am also interested in removing the right-click menu and panels from gnome so that this system is the only option.

I got this idea from the gentoo, firefox kiosk live-cd and decided how to make the cd more usable as a public kiosk. Also I prefer debian and ubuntu so I do not fancy tinkering with other distros.

Lastly I do not mind, if this is in gnome, or an alternative as long as the functionality is there.

Thanks in advance, 
Lew:popcorn:

Update:
X :3 -ac &  nvidia-settings --load-config-only & sleep 2 & DISPLAY=:3 gedit seems to launch gedit in screen3 but this is not a workspace :(
also I have tried wmctrl but it only recognises desktop 0 :( so not sure how to use that, ooh poo :(

Update2:
to check if say firefox was running I can use the following script, I have tested it and I was thinking of having something like this for each app
```

if [ "$(pidof -x firefox)" ] 
  then
    echo "firefox is running"
  else
    firefox&
fi

```

---

### Post by Lewis Cowles on 2010-08-15
any insights???

---

