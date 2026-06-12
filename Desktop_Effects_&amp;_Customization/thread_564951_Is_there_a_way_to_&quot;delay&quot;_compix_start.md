---
title: "Is there a way to &quot;delay&quot; compix start?"
date: 2007-10-01
forum: Desktop Effects &amp; Customization
---

### Post by maestrobwh1 on 2007-10-01
Currently I have to launch compiz in kde using a desktop shortcut with icon that I created.  Kubuntu Feisty:

[Desktop Entry]
Encoding=UTF-8
Exec=startcompiz
Icon=/home/bwh-feisty/.local/share/icons/compiz-logo.png
Name=Compiz
Name[en_US]=Compiz
StartupNotify=false
Terminal=false
TerminalOptions=
Type=Application
X-KDE-SubstituteUID=false

where the startcompiz script in /usr/bin looks like
#!/bin/bash
compiz --replace &
sleep 3
emerald --replace || kwin --replace

But if I launch it too soon, emerald crashes and then I have to do a kwin --replace then emerald --replace and it all works and is nice and stable.

If I put  this desktop item into kde autostart, or if I put a line in .bashrc to start compiz and emerald, emerald crashes also.   kwin --replace then emerald --replace fixes it.

Obviously, too much is going on at startup.  I have tried to put some of the "startcompiz" script I put in /usr/bin in my /home/myusername/.bashrc and the same thing happens.

Is there any script I can put in to DELAY the emerald command.  I am not sure what the sleep 3 does, but I found it in a post and it does allow for me to launch things with fewer crashes.

I have a gutsy install in a neighboring partition and this never happens.

---

### Post by zero-9376 on 2007-10-01
the sleep command adds the delay you are looking for it tells bash to wait before doing the next command although i think you need to specify the units. so to extend the delay just change it to

sleep 5s

---

### Post by maestrobwh1 on 2007-10-06
I figured, but the confirmation helped me: I change the "sleep number" to 5, and inserted 'sleep 10' before 'compiz --replace &' just to let everything else that was loading to finish doing so.

Peace

---

### Post by zero-9376 on 2007-10-06
just thought id add that if your ussing a nvidia card adding --indirect-rendering to the compiz replace command resulted in MUCH better responsiveness for me

---

