---
title: "wget won't close"
date: 2009-02-12
forum: General Help
---

### Post by shak3800 on 2009-02-12
Hi !

I have this problem , i use flashgot + wget to download files and when i want to close wget i get the message SIGHUP received and it doesn't close . The window of wget just stays there , are there any commands that i can write to close it ? Also , how do i pause the downloads with wget and then resume them ?

Thanks for your time !

---

### Post by 2hot6ft2 on 2009-02-12
```
sudo killall wget
```
will kill it. As for the rest I don't know since I don't use it. You can also use force quit...right click on the taskbar and select Add to Panel then select Force Quit and add it to the panel. Then just click on it then put the cross hairs in the title bar of the app you want to force to quit and left click.

Sometimes it wont work and you still have to use killall.

---

### Post by shak3800 on 2009-02-12
Didn't know that it was that simple ! Thanks :)

---

