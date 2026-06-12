---
title: "Why Thunar hangs before opening"
date: 2013-12-12
forum: Desktop Environments
---

### Post by geovino on 2013-12-12
I'm using Xubuntu 13.10 

I've noticed every time I use Xfce and opening Thunar file manager most of the time it opens quickly, but sometimes it stalls and won't open for a while. Why is this? How can I fix this issue?

---

### Post by dentaku65 on 2013-12-13
Silly question: did you try to remove saved session?
```
rm -rf ~/.cache/sessions
```
and reboot

---

### Post by vasa1 on 2013-12-13
> **dentaku65 said:**
> Silly question: did you try to remove saved session?
```
rm -rf ~/.cache/sessions
```
and reboot
Note that to do so, you will need to 
[LIST]
[*]log out first 
[*]open a console with Ctrl+Alt+F1 
[*]log in from the keyboard
[*]delete the contents or move the files elsewhere
[*]close the console using Ctrl+Alt+F7
[*]log in again
[/LIST]

I'm not sure that a reboot is needed.

If the problem persists, please try to look for some sort of pattern of activity that makes Thunar hang. Thunar hanging when *first* opened in a session used to be an issue about a year ago but isn't now, AFAIK.

---

### Post by geovino on 2013-12-13
That was the wrong advice. After running that command it removed all my files!! Now I have to transfer most of them from my backup. 

Maybe someone else knows how to fix thunar. for now I'll live with it or go back to another OS!

---

### Post by Morbius1 on 2013-12-13
I haven't noticed this problem in a while but a few releases ago it was caused by the default way Thunar will search for Samba shares on the network - regardless if you even have samba shares on the network.

[1] Make a backup copy of a file:
```
sudo cp -a /usr/share/gvfs/mounts/network.mount /usr/share/gvfs/mounts/network.mount.bak
```
[2] Then edit the original network.mount file and set AutoMount to false:
> [Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
[COLOR=#0000cd]**AutoMount=false**[/COLOR]

The downside to this is if you do have samba shares on the network then when you access "Browse Network" it will take a while to find them.

---

### Post by dentaku65 on 2013-12-14
Hi,

> **geovino said:**
> That was the wrong advice. After running that command it removed all my files!! Now I have to transfer most of them from my backup. 

Maybe someone else knows how to fix thunar. for now I'll live with it or go back to another OS!

Which command you enter in order to remove all your files? :confused:

Removing cache sessions as I indicated in post #2 do not delete any personal data though

---

