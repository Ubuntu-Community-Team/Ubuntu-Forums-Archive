---
title: "Ubuntu 13.04 and .run issue"
date: 2013-02-19
forum: Gaming &amp; Leisure
---

### Post by TheMixtureMedia on 2013-02-19
Hey there I am running Ubuntu 13.04 with all updates and I am trying to run a .run install for a game. The game says I have permission to install. The only thing is that there is no programs I can find to start the .run when I try to double click the file. Can someone help me with that please.

---

### Post by The Cog on 2013-02-19
I would guess that you have to run it from the command line. 
First, make the file executable, then run it: 
```
chmod +x whatever.run
./whatever.run
```

---

### Post by TheMixtureMedia on 2013-02-19
Ok I am aware of doing that way but what about doing it on the desktop?

---

### Post by pietrvanhelsing on 2013-04-27
Yeah what about the desktop?

---

### Post by myromance123 on 2013-04-27
I'm not entirely sure this will do what you guys want, but it's worth a try anyway. The new Nautilus has set executable files to open in a text editor, instead of being runnable like in the past.

To fix this, in any Nautilus window (say Home for example), open File Preferences and go&#65279; to the Behaviour tab. Then under the Executable Text Files section, set it to the first option which is "Run executable text files when they are opened". 

Now try double clicking the .run file again (make sure you've ticked 'Allow executing file as program' first, for that .run file).

---

