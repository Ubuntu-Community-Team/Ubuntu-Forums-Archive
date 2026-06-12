---
title: "k3b lame help"
date: 2005-12-03
forum: Desktop Environments
---

### Post by escobar on 2005-12-03
Not quite sure what I did wrong but I am no longer able to see the mp3 option when ripping CD's. This occured after I was attempting to edit the metadata options for mp3 within K3b. I tried reinstalling lame but this did not help. Anyone think they may know where I went wrong? Also, is there a guide someone can point me to for commands that lame accepts in Linux? I tried a few different methods pulled from Google and this forum and couldn't seem to get it right. I was thinking I could use the same commands as I did within Windows i.e. "lame --alt-preset extreme", then add the tagging prefs. Seems like I made a real mess here. I understand the description may be a little vague so I attached a screen for reference.

Thanks.

---

### Post by escobar on 2005-12-07
[QUOTE=escobar]Not quite sure what I did wrong but I am no longer able to see the mp3 option when ripping CD's. This occured after I was attempting to edit the metadata options for mp3 within K3b. I tried reinstalling lame but this did not help. Anyone think they may know where I went wrong? Also, is there a guide someone can point me to for commands that lame accepts in Linux? I tried a few different methods pulled from Google and this forum and couldn't seem to get it right. I was thinking I could use the same commands as I did within Windows i.e. "lame --alt-preset extreme", then add the tagging prefs. Seems like I made a real mess here. I understand the description may be a little vague so I attached a screen for reference.

Thanks.[/QUOTE]


I managed to get K3b to recognize Lame again. Now I'm running into an issue where it will not encode because of what I believe to be a bad command. The default encoding command worked fine but encoded everything at only 128k. I wanted to change this so I added the command "lame  -V 0 --vbr-new %t%n%a%m %f" this doesn't seem to work. Can anyone post up the command that's there by default? My goal is to get it to encode at 256k VBR. Would be much appreciated. Thanks to any that respond.

---

