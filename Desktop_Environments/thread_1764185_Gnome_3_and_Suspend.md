---
title: "Gnome 3 and Suspend"
date: 2011-05-21
forum: Desktop Environments
---

### Post by irv on 2011-05-21
Is anyone else having the same problem I am having?
I am running 11.04 and Gnome 3 on a Dell Inspiron 1521 laptop and I can't get out of suspend mode. I am forced to power off and then restart my system. Is this a bug?

---

### Post by trevelyan on 2011-05-21
for me suspend will suspend the computer but if i leave it for a while and then wake it up then the screen looks all messed up. I'm still looking for a solution.

Anyone?

---

### Post by irv on 2011-05-22
I got tired of fighting with 11.04, Unity and Gnome 3 and I went back to 10.10 and Gnome 2.32. I am almost back to normal. What is normal?:confused:

---

### Post by brent.of.all.people on 2011-05-28
I just upgraded to 11.04 and I'm having similar problems with suspend. When I try to wake up my computer, The picture is screwed up -- but I can see the mouse pointer clearly, and it responds when I use the trackpad.

I'm using an HP Pavilion dv6000.

---

### Post by brent.of.all.people on 2011-05-28
However, if I just type in my password and hit enter, the screen will go back to normal and I can use the computer without having to reboot. Annoyance downgraded from major to minor.

---

### Post by rvchari on 2011-05-28
i am using 10.10 and had downloaded gnome3 from the ppa a couple of days back. havent found such problem (or may be i havent put my thinkpad to suspend)...
it was my testing mood to try out gnome3.... lets see how things go

---

### Post by irv on 2011-05-29
> **irv said:**
> I got tired of fighting with 11.04, Unity and Gnome 3 and I went back to 10.10 and Gnome 2.32. I am almost back to normal. What is normal?:confused:

To set the record straight I am back to 11.04 but this time I am just using Unity and am back to having problems with suspend. The bug or problem is with 11.04 and not with Gnome 3 because i haven't even installed it. Maybe it is with Unity if it handles the suspend mode.

Just thought I would update this post because the title is now wrong.

---

### Post by moTaro on 2011-05-29
Suspend is f**ed up in gnome 3. Tested in Fedora 15 same story Lenovo R61 Thinkpad model here.

Will consider using gnome after 3.1 maybe, there is a reason why canonical went for unity. Gnome 3 has too many issues and it's premature.

You should stick with unity 4now, until 11.10. Suspend works flawlesly in unity natty

---

### Post by Durden on 2011-05-29
> **trevelyan said:**
> for me suspend will suspend the computer but if i leave it for a while and then wake it up then the screen looks all messed up. I'm still looking for a solution.

Anyone?

try alt+f2 then type in the letter 'r' and press enter. Will reload gnome 3. Every so often I lose my background when resuming, this usually fixes it

---

### Post by irv on 2011-05-29
> **moTaro said:**
> Suspend is f**ed up in gnome 3. Tested in Fedora 15 same story Lenovo R61 Thinkpad model here.

Will consider using gnome after 3.1 maybe, there is a reason why canonical went for unity. Gnome 3 has too many issues and it's premature.

You should stick with unity 4now, until 11.10. Suspend works flawlesly in unity natty

Like I said in my last post, I am using Unity and 11.04 and there is still an issue with suspend. If I select suspend from the menu and let it go into suspend before I close the lid it will works find, If I set the option to suspend when the lid is closed it will not come out of suspend when the lid is open. I tried ever button on the keyboard plus the off button and nothing bring it back to life. Now I found a work around. After a couple of power off's I found if I close the lid again and then open it, it will come out of suspend mode.

I believe this problem can be fixed with a small change in the code.

---

### Post by T0NYisME on 2011-05-30
Hi folks ;-) I to have also had some suspend/hibernate issues(dual boot win7/Ubuntu 11, acer aspire 5735, Intel dual core T5800 processor, 4gb ram), basically from 10.04 upwards. Pretty much the same, suspend is ok but hibernate is a bit tricky-I can hibernate but when I leave it overnight (and as with the last kernel) I had to take the battery out of my laptop, leave for 10sec's, re-insert and reboot, so I had too shut it down to save taking out my battery :-)--however I found that updating the kernel from 2.38 to 2.39 helped somewhat. I still have the overnight issue which I've not tried to sort as of yet(I just shut it down) but hopefully the kernel update will help you guy's go in the right direction ;-)

---

### Post by irv on 2011-05-30
> **T0NYisME said:**
> Hi folks ;-) I to have also had some suspend/hibernate issues(dual boot win7/Ubuntu 11, acer aspire 5735, Intel dual core T5800 processor, 4gb ram), basically from 10.04 upwards. Pretty much the same, suspend is ok but hibernate is a bit tricky-I can hibernate but when I leave it overnight (and as with the last kernel) I had to take the battery out of my laptop, leave for 10sec's, re-insert and reboot, so I had too shut it down to save taking out my battery :-)--however I found that updating the kernel from 2.38 to 2.39 helped somewhat. I still have the overnight issue which I've not tried to sort as of yet(I just shut it down) but hopefully the kernel update will help you guy's go in the right direction ;-)

Before taking the battery out did you ever hold the power button in for 30-40 seconds and just make it completely power off? If I did this I could get it to shutdown completely and then I just hit the power button again to start it up again.

---

### Post by KawaiDon on 2011-05-30
> **Durden said:**
> try alt+f2 then type in the letter 'r' and press enter. Will reload gnome 3. Every so often I lose my background when resuming, this usually fixes it

It&#347; great how we learn new tricks.  I should study up on function key shortcuts - I never new of the ALT+F2 shortcut.

Thanks.

---

### Post by Hnat on 2011-06-03
Alt F2 r does not restart Gnome. It tries to start a program ~/r which usually not exists. But one could make it exist.

Reinhard

---

### Post by The_Underscore on 2011-06-03
Alt+F2 normally starts programs as if you were entering a shell command, but since typing "r" in the Terminal doesn't do anything I assume that Alt+F2 and "r" does not execute a command but simply restarts GNOME Shell. Same goes for typing "restart".

---

### Post by irv on 2011-06-03
> **The_Underscore said:**
> Alt+F2 normally starts programs as if you were entering a shell command, but since typing "r" in the Terminal doesn't do anything I assume that Alt+F2 and "r" does not execute a command but simply restarts GNOME Shell. Same goes for typing "restart".

Since I started this thread I move on to Xfce DE. Does Gnome 3 or Unity have a keyboard shortcut setting somewhere like Xfce: 
[ATTACH]194097[/ATTACH]
Things like this make it so easy to change things around and you can do it your way.

---

### Post by brianrobles204 on 2011-07-26
I'm writing from Natty w/ Gnome3. I believe I have the latest ppa updates, but suspend is still not working. :|

Anyway, I've made a workaround, for those interested.
Copy the following to Gedit:

```
#!/bin/bash
case "$1" in
    thaw|resume)
        gnome-shell --replace
        gnome-shell
        ;;
    *)
        ;;
esac
exit $?
```

Basically, the problem is Gnome3 doesn't start when you resume from a suspend/hibernation. This tells ubuntu to run it again. Save it as: 10_gnome-shell-run

Then open a terminal and cd to the directory you made it. Run the following:
```

sudo cp 10_gnome-shell-run /etc/pm/sleep.d

```
This copies it to /etc/pm/sleep.d
Any executables in this folder will run on wakeup from sleep.
Therefore, Gnome3 will start from waking up :)

Note: I'm not sure, but you might need to change the permissions for it to work. Try this code if it fails:
```

sudo chmod a+rwx 10_gnome-shell-run

```
Then cp your script to the folder again. :D

---

### Post by irv on 2011-07-27
> **brianrobles204 said:**
> I'm writing from Natty w/ Gnome3. I believe I have the latest ppa updates, but suspend is still not working. :|

Anyway, I've made a workaround, for those interested.
Copy the following to Gedit:

```
#!/bin/bash
case "$1" in
    thaw|resume)
        gnome-shell --replace
        gnome-shell
        ;;
    *)
        ;;
esac
exit $?
```

Basically, the problem is Gnome3 doesn't start when you resume from a suspend/hibernation. This tells ubuntu to run it again. Save it as: 10_gnome-shell-run

Then open a terminal and cd to the directory you made it. Run the following:
```

sudo cp 10_gnome-shell-run /etc/pm/sleep.d

```
This copies it to /etc/pm/sleep.d
Any executables in this folder will run on wakeup from sleep.
Therefore, Gnome3 will start from waking up :)

Note: I'm not sure, but you might need to change the permissions for it to work. Try this code if it fails:
```

sudo chmod a+rwx 10_gnome-shell-run

```
Then cp your script to the folder again. :D

Thanks for the tip for the work-around. I followed it but my pc is doing some processing so I have to wait to try the suspend. Thanks again

---

### Post by mtphr on 2011-09-05
> **brianrobles204 said:**
> I'm writing from Natty w/ Gnome3. I believe I have the latest ppa updates, but suspend is still not working. :|

Anyway, I've made a workaround, for those interested.
Copy the following to Gedit:

```
#!/bin/bash
case "$1" in
    thaw|resume)
        gnome-shell --replace
        gnome-shell
        ;;
    *)
        ;;
esac
exit $?
```

Basically, the problem is Gnome3 doesn't start when you resume from a suspend/hibernation. This tells ubuntu to run it again. Save it as: 10_gnome-shell-run

Then open a terminal and cd to the directory you made it. Run the following:
```

sudo cp 10_gnome-shell-run /etc/pm/sleep.d

```
This copies it to /etc/pm/sleep.d
Any executables in this folder will run on wakeup from sleep.
Therefore, Gnome3 will start from waking up :)

Note: I'm not sure, but you might need to change the permissions for it to work. Try this code if it fails:
```

sudo chmod a+rwx 10_gnome-shell-run

```
Then cp your script to the folder again. :D

i have tried this workaround and it failed in my situation. i get an "unlock screen" and can freely move the mouse, but the second i start typing for the password everything freezes, and can't get back. the only solution is a hard-shutdown. running gnome3 on ubuntu 11.04 on an msi windbook netbook.

---

