---
title: "Ubuntu Unity"
date: 2011-11-28
forum: Desktop Environments
---

### Post by aishsarathy on 2011-11-28
Hi All,

The unity --replace command  that i give to get my application's icon on  the system tray under Ubuntu Unity 11.04, the screen blanks out for  couple of seconds before it takes effect.
This happens when the command is given on pressing Alt+F2 .

When given in the command prompt , the screen shakes for a second before it takes effect

Is this the consistent behaviour?
Is there a way out to this problem?

---

### Post by crazy bird on 2011-11-28
I can't provide you with the correct answer since i'm not using Ubuntu with Unity (i really dislike that cheap tablet desktop look) but i want to give you 1 tip:
 
Do not mutlipost the same question: [http://ubuntuforums.org/showthread.php?t=1887861](http://ubuntuforums.org/showthread.php?t=1887861). It is very confusing to everyone where to post and where to look for the correct answer.

---

### Post by aishsarathy on 2011-11-28
Yea shall not repost

---

### Post by Copper Bezel on 2011-11-28
What application is asking you to run unity --replace in the first place? *That's* not a normal behavior. It's normal that there's a pause and some jitter when you run the command, because it's restarting the compositor and reapplying all your window manager settings, etc. But you shouldn't have to run that command at all in ordinary use.

---

### Post by aishsarathy on 2011-11-28
To be more clear.

I am developing an application using wxwidgets and under Ubuntu Classic, the icon of my application in the tray.
But under Unity , it neither comes in the launcher nor in the tray.
To make it come to the tray , I need to use 
gsettings set com.canonical.Unity.Panel systray-whitelist “['all']“ 
along with unity --replace for it to take effect.

But unity --replace is not consistent , it at times crashes.

Is there a way to get outta this?

---

