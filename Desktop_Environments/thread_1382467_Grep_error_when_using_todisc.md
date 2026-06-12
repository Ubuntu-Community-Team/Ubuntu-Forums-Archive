---
title: "Grep error when using todisc"
date: 2010-01-16
forum: Desktop Environments
---

### Post by Mia1990 on 2010-01-16
i have been fighting this for a long time now but i found the error that todiscgui/tovid is giving me when i try to make switched menus here is the error message.I checked and grep is installed.Could someone tell me how to fix this error.I thank it in /usr/local/bin and needs to be in usr/bin/tovid or something like that but i am not sure and i do not know how to fix it.Help
> grep: /usr/bin/tovid-init: No such file or directory

---

### Post by grepster on 2010-01-20
It looks like tovid was not installed correctly, as tovid-init is missing or not in the PATH that executables are searched for.  How did you install ?

---

### Post by Mia1990 on 2010-01-20
We have tovid/todiscgui working now we installed tovid from svn the only thing wwe are having problems with now is how to add chapters in the repo version there was a line to add them in but in the new svn there is no place to do this.So my new question is there a Place to make chapters that we are missing or would that be a tovid custom command and if so there are two tovid custom command places one under behavior and one under encoding so were do i add the command at and is the command  -chapters 10 for 10 chapters Thanks

---

### Post by grepster on 2010-01-20
Go to the "Playback" tab, then select the "Chapters" subtab.  A readonly copy of the videos you have loaded should be there (load those first).  Click on a video and add the # of chapters for that video in the pane below the video list in the "Text" field. If you don't have a different value for each video you can just enter one number for the 1st video to use for all videos. You can alternatively use your own custom chapters in HH:MM:SS format (man todisc has an example): for this you would need a chapter list for each video.  There are mouseover tooltips that explain this as well.

---

### Post by Mia1990 on 2010-01-22
Thank you tovid/tovid fancy works great.

---

