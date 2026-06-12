---
title: "New workspace switching in Jaunty--I'm not a fan, can I revert?"
date: 2009-05-04
forum: Desktop Environments
---

### Post by fiddler616 on 2009-05-04
Hello,
I've been using Ubuntu since Hardy, and liked the workspace switching in both Hardy and Intrepid--the entire desktop (wallpaper, panels, windows) slides to the left/right/etc. (as opposed to DEs like Openbox or Xfce, where the next workspace just appears with no transition). But with Jaunty, I've noticed that only the windows move--the wallpaper and panels stay in exactly the same place.
I know it's a small point, and won't be too upset if it doesn't get solved, but is there some way to revert to the previous effect?

Thanks.

---

### Post by Mr.Banana on 2009-05-04
Yeah, I've been wondering that myself, so here's one bump for ya in hope someone will answer...

---

### Post by fiddler616 on 2009-05-12
Nobody?

---

### Post by days_of_ruin on 2009-05-12
Apparently some people have the opposite view [http://ubuntuforums.org/showthread.php?t=784758]("http://ubuntuforums.org/showthread.php?t=784758")

Maybe you can download the old version from the compiz site.

---

### Post by Vostrocity on 2009-05-13
Yes, I dislike the new workspace-switching animation too. But I just disabled multiple workspaces, not because of this, but because I'm a Windows native so I'm not used to using them.

---

### Post by days_of_ruin on 2009-05-13
I found the solution.
First install compiz settings manager:
```
sudo apt-get install compizconfig-settings-manager
```

Open it up in system->preferences.

Select "Desktop Wall", click on the "Viewport Switching" tab and backspace everything in the "Non sliding Windows" entry.

And now everything will slide not just the windows:D

---

### Post by fiddler616 on 2009-05-13
> **days_of_ruin said:**
> <snip>
And now everything will slide not just the windows:D
Brilliant! Thanks! (Too bad the "thanks" button died...)

For those who are interested, I kept the
```
type=Dock | state=Sticky
```
part so that sticky windows (to be seen on all workspaces) and the panels would stay put (I decided the panel part was actually a good call).

---

