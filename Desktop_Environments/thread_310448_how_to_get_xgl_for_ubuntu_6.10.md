---
title: "how to get xgl for ubuntu 6.10"
date: 2006-12-01
forum: Desktop Environments
---

### Post by mjolinr on 2006-12-01
hi,
  i have a friend who got me started with ubuntu and he has this thing called xgl :confused: .  i am not really sure what it is, but it looks like a desktop environment, am i correct, like gnome? how can i get this on my computer and does it overwrite ubuntu or can i have a dual-boot thing. i think thats what my friend has.
thanks

---

### Post by Dr. Nick on 2006-12-01
Thier is a varition of xgl called aiglx that is built into edgy 6.10. The effects you probably speak of is called beryl and is just a accelerated interface that can be used with any desktop really, gnome included.
 
Here is a link that may help
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

---

### Post by mjolinr on 2006-12-02
thanks, dr.nick, i'll try that.

---

### Post by mjolinr on 2006-12-03
Just one other thing Dr. Nick, how do I turn it off and why is there no minimize/close bar on top? can you switch the settings?

>edit<

ok i found the settings but i still can't figure out exactly why there is no bar on top of some and not others... and when i try to rotate the cube it doesn't work anymore...

---

### Post by praxis22 on 2006-12-03
It's a known bug. Beryl is still very much a "work in progress" 0.1.2 or so. I'm running it at present too and it screws up firefox, that has no top or sidebars. You could try compiz that's at 0.3.4 (unstable) or 0.2.2 (current)

---

### Post by Dr. Nick on 2006-12-03
> **mjolinr said:**
> Just one other thing Dr. Nick, how do I turn it off and why is there no minimize/close bar on top? can you switch the settings?

>edit<

ok i found the settings but i still can't figure out exactly why there is no bar on top of some and not others... and when i try to rotate the cube it doesn't work anymore...


If you see no bars at the top try running this from a termianl

metacity --replace.

Sometimes I have a bar at the top but it is hidden under the panle, in that case right click the tasbar icon and "move" it.

---

### Post by mjolinr on 2006-12-03
ok, i found out how. all i have to do is maximize it from the taskbar on bottom.  

a few other things: how do you kill beryl? and why can't i listen to music while i'm running it?  it used to work fine, i could listen to music and stuff but now i cant.  And can i bind it to a session so i can pick whether or not i am running beryl? i currently have it set so that when i log in it starts automatically, but can i make a new session so i can switch?

---

### Post by Dr. Nick on 2006-12-03
I think you can make a new session, but I am not sure how.

To stop using beryl just right click teh icon and swith window manager back to metacity.

Or open a termial and type

metacity --replace
killall beryl-manager

Music playback shouldnt be afftected, not sure what would be going on their.

---

### Post by mjolinr on 2007-03-15
I found the beryl webpage that has instructions on making a new session.

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

under configuring Beryl

---

