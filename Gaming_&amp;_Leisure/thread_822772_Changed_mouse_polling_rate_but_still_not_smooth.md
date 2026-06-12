---
title: "Changed mouse polling rate but still not smooth?"
date: 2008-06-08
forum: Gaming &amp; Leisure
---

### Post by Castlef on 2008-06-08
I have a logitech G5 laser mouse....

i have a problem where it is very unresponsive... as in if i take the cursor and start at the top left.. and move diagonally dwn to the bottom right... it stutters and just is not smooth all the way down like it is in windows. I found out about mouse polling rate... and i changed it to 2... but it is still doing it. It is so bothersome that i will switch back to windows just for this one reason if i can't fix it. any help is appreciated

---

### Post by Vadi on 2008-06-08
I think the recommended is around 10... give that a try?

---

### Post by Cappy on 2008-06-08
2ms (500) is the correct/highest mouse polling for the G5. I have the same mouse.

Run
```
cat /sys/module/usbhid/parameters/mousepoll
```
and make sure it prints out "2"


If not, As a test, use ```
sudo gedit /sys/module/usbhid/parameters/mousepoll
```
and input "2" and save. Then unplug and replug your mouse.


If that solves the problem for you, you can make it permanent by following my guide:
[http://ubuntuforums.org/showthread.php?t=392494](http://ubuntuforums.org/showthread.php?t=392494)

---

### Post by dm3nt0r on 2008-07-12
I tried that but cannot write to the mousepoll file or even open it.
Tried changing permission with chmod and got no error but when I try to go in it still wont let me even see the file.

---

### Post by namaster on 2008-10-20
bump same with me..cant open file.. using hardy 4.1 release

---

### Post by Shaythong on 2008-10-20
You should be able to open the file with "sudo gedit". If it doesn't work you can try going into root user mode "sudo -i". I haven't used the root admin in a while, so I'm not sure if it was "sudo -i". I don't recommend using the root terminal access a lot since it's better to use the normal stuff.

---

### Post by namaster on 2008-10-20
> **Shaythong said:**
> You should be able to open the file with "sudo gedit". If it doesn't work you can try going into root user mode "sudo -i". I haven't used the root admin in a while, so I'm not sure if it was "sudo -i". I don't recommend using the root terminal access a lot since it's better to use the normal stuff.

Nope either it doesn't work. But i got 2 working by this way :P

```

sudo rmmod usbhid && sudo modprobe usbhid mousepoll=2

```

---

### Post by Cappy on 2008-10-21
I wrote a tutorial on this a while back. It may be outdated now.

[http://ubuntuforums.org/showthread.php?t=392494](http://ubuntuforums.org/showthread.php?t=392494)

Nm .. I already linked to it. I guess everyone missed it.

---

### Post by fabzor3 on 2008-12-03
check that the mousing surface is not shiny or reflective.

---

### Post by namaster on 2008-12-03
> **fabzor3 said:**
> check that the mousing surface is not shiny or reflective.

using razer gaming mouse pad :P i am back to windows though..just wasnt able to handle high acceleration and all..:)

---

### Post by crazyfuturamanoob on 2008-12-04
My mouse works perfectly, but I was just curios to see what's my polling rate, and ran the command somebody posted:
```

$ cat /sys/module/usbhid/parameters/mousepoll

```
And it returned me 0! What does that mean? It waits 0ms between each mouse update event?

---

### Post by namaster on 2008-12-04
Use it 2. 2 - 500ms 

I forgot how i changed it. It posted on forums somewhere. To me acceleration is problem. I really cant stop acceleratation and moves keep jumping from pixel to pixel. 

Got to try on 8.10 as soon as i update it.

---

### Post by epitaph on 2008-12-04
I've done a few tweaks to my mouse input in order to get what I consider to be an acceptable feel.

First, changing the mouse polling interval:

Add the following to /etc/modules:

```
-r usbhid
usbhid mousepoll=2
```

After a reboot check it:

```
cat /sys/module/usbhid/parameters/mousepoll
```

It should say "2". 2ms works out to 500hz.

I run a tiny script at login:

```
#!/bin/bash
export SDL_VIDEO_X11_DGAMOUSE=0 &
xset m 0 0
```

I THINK the xset command is supposed to disable acceleration, and it definitely does SOMETHING, you can see it change if you move your mouse as you login when the script activates. After doing this my mouse sensitivity much more closely resembled what I was used to. Disabling DGA mouse solved a strange issue where, if I moved my mouse very quickly, it would slow and become unresponsive. I wouldn't use it unless you're having a similar issue.

When I run games, I launch them from a script similar to the following to disable compiz and the screensaver. The screensaver would try to activate and would actually cause the mouse to stop working for a few seconds. READ: After using the command to disable the screensaver it sometimes does not come back on. At first, this was solved by disabling the "Unredirect Full Screen Windows" option in the CCSM, now I sometimes have to force an activation using "xdg-screensaver activate" and then it runs fine. This is kind of an erratic issue and I'm not sure if it's related. The script looks and kills compiz.real because I was having an issue where sometimes zombie compiz.real processes were cropping up.

```
#!/bin/bash
gconftool-2 --set /apps/gnome-screensaver/idle_activation_enabled --type bool 0 &
metacity --replace &
ut2004
killall -9 compiz.real &
compiz --replace &
gconftool-2 --set /apps/gnome-screensaver/idle_activation_enabled --type bool 1 &
```

---

