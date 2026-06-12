---
title: "Rhythmbox Searching for Plugins"
date: 2009-05-05
forum: General Help
---

### Post by vahnx on 2009-05-05
Continuing from [my old thread]("http://ubuntuforums.org/showthread.php?t=1115254"), this is still happening in the final version to this date. My import errors are a corrupt MP3, two WPL (Windows Playlists), and about 33 RealMedia Audio (RAM) files. The error is popping up about 3-4 times every Rhythmbox launch. This did not used to happen on 8.10 I believe (or 7.10/8.04). 

Anyone come up with a solution yet? I've Googled for a bit and no avail.

---

### Post by vahnx on 2009-05-08
*bump*

---

### Post by hansdown on 2009-05-08
Hi vahnx.

It's likely another thing for the devs to look at if someone files a

bug report.

---

### Post by pastalavista on 2009-05-08
Try this... worked for me
```
sudo aptitude remove rhythmbox --purge && sudo aptitude install rhythmbox
```

---

### Post by vahnx on 2009-05-08
Thanks, I think the above post did it. :)

---

### Post by vahnx on 2009-05-10
Didn't work actually =(

I figured out though it's caused from the import errors. Is there a way I can get it to ignore all "Import Errors", eg: disable that feature? I can remove from the Import Error list but they just come back next time I start the program.

---

### Post by hansdown on 2009-05-10
vahnx, there is a solved thread that may help.

[http://ubuntuforums.org/showthread.php?t=942166](http://ubuntuforums.org/showthread.php?t=942166)

Scroll down to this post.

Try reinstalling the gstreamer plugins.

---

### Post by vahnx on 2009-05-12
Seems to have worked, just launched Rhythmbox and no errors. If I do not reply within a week, re-installing those plugins like that thread mentioned may have solved it. For those Google bots:

```

gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps

```

---

### Post by hansdown on 2009-05-12
Glad you fixed it vahnx. ( I hope.)

---

### Post by vahnx on 2009-05-12
Nope =(
Still getting like 35 import errors and "search for plugins".
There's gotta be an option buried somewhere to "ignore all import errors and repercussions"

---

### Post by pastalavista on 2009-05-12
> **vahnx said:**
> Nope =(
Still getting like 35 import errors and "search for plugins".
There's gotta be an option buried somewhere to "ignore all import errors and repercussions"It's likely one of your folders it's trying to import from has the wrong permissions or belongs to root. And I believe the search for plugins can be disabled in the Rythmbox Plugins settings. Uncheck the ones you don't need maybe. Are you connected to the network while doing this?

---

### Post by vahnx on 2009-05-12
I am connected to the network (files are local though), and permissions for the directory containing the music (and sub dirs) are belonging to root. I checked plugins and none of them seem conflicting and there are none to disable this Import Error checking. 

How would I set permission for that Music dir and all sub-dirs within to just the user and not root? chmod 777 while logged on the current user? And setting permissions would not affect the files in Leopard or 7 right?

---

