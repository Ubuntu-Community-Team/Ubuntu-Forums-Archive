---
title: "&lt;Turbo&gt;e Shortcut?"
date: 2007-11-20
forum: Desktop Effects &amp; Customization
---

### Post by Githlar on 2007-11-20
I went to enable Desktop Effects using the default menu, but I had some problems. It would not let me use the workspace on a cube option, so I started looking around more. I found gnome-compiz-manager and uninstalled the default tool. I am very surprised at how much more it has than the default - and it let me use Workspaces on a Cube (with a lot of X restarting). So, I'm pretty happy now.

My question, in toying around with some of the effects, I assigned the water cursor effect to <Turbo>w. While I was pressing it, I accidentally slipped and pressed <Turbo>e. It took me forever to figure out exactly what I did, but I finally replicated it. But, it shows all of the workspaces lined up in a horizontal row and a nice reflection of them on a floor.You can even grab the windows on their title bars and move them across the workspaces.  I saw nothing about this in the gnome-compiz-manager application. Where is this documented? I can't seem to find it anywhere.

---

### Post by Forlong on 2007-11-20
That's the Expo plugin - you can configure it in ccsm:
```
sudo apt-get install compizconfig-settings-manager
```

(and please remove gnome-compiz-manager again - the two will interfere with one another)

---

