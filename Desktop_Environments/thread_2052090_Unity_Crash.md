---
title: "Unity Crash"
date: 2012-09-02
forum: Desktop Environments
---

### Post by Kodeine on 2012-09-02
Salutations!

So I added a PPA that updates the drivers for my mesa graphics. A few minutes ago update manager popped up with some more updates. I installed and a little while later I restarted. I found it on phoronix along with many others and the updates have indeed improved my graphics performance in the past so it's not the PPA maintainers fault. But upon logging in I could see the files on my desktop along with my wallpaper. However no top panel or unity launcher. Running gnome-panel via terminal brings me to a working gnome2 environment, nothings wrong there. However upon running unity from terminal I get some odd happenings.

Certain UI elements flicker. Say if I open the menu via the gear icon in the top right hand corner. The drop down menus background will flicker showing my wallpaper. After clicking off the menu so it should no longer be shown it still continues to flicker on and off. Sometimes opening a drop down menu will result in it not loading. If I move my cursor down along the menu then bits of it will appear.

Is this something to do with the newly installed drivers? I purged the PPA and reinstalled unity and ubuntu-desktop to no affect.

---

### Post by Kodeine on 2012-09-02
I ran unity again and this time took note of it's output. I have all of the output and will put it on pastebin if needed but there's one line in particular that stood out.

```
zack@DesktopPC:~$ unity
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing composite options...done
libGL error: failed to load driver: i965
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
...
```


*** I was using the oibaf PPA that updates my mesa drivers. It seems that the latest updates required a package that wasn't available in 12.04. Also oibaf's PPA didn't support precise which I hadn't known. I reverted back to the stock graphic drivers (via purging the oibaf PPA) and now are using the 'Ubuntu X teams' mesa updates which does support ubuntu precise pangolin. FYI if your having similar issues.

---

