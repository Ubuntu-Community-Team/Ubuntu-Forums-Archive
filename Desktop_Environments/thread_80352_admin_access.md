---
title: "admin access?"
date: 2005-10-22
forum: Desktop Environments
---

### Post by Furwolfie on 2005-10-22
im defentally a noob on at this, so hopefully its just me not knowing what to do is the problem.. so here is my problem, i cant access "administrator mode"? well, i could on my first boot after a fresh install "installed several times now on both my computers" and im having the same problem on both of them.. anyhow, after the first reboot, i cant access admin mode at all, so i cant set the time, or put in settings for my wireless ect.. anything admin.. when i do click admin mode, it prompts me for password, i put in password, that box goes away, no errors or anything is displayed, but the box for "time, wireless ect." just goes back to faded out again and i cant adjust the settings.. it doest say incorrect password ect.. i have tried new passwords, rebooting.. im at a total loss at this point. hehe. i wish i knew where i was going wrong, if anyone has any idea on how i can fix this problem, that would be most awsome. thanks  much... oh yeah, im using 5.10 on KDE.

---

### Post by Stereotypical Rage on 2005-10-22
Everything that you need root access for is done using the "sudo" command in the Konsole.

The admin pass while using KDE is the password of your user account.

---

### Post by landotter on 2005-10-22
[quote=Stereotypical Rage]Everything that you need root access for is done using the "sudo" command in the Konsole.

The admin pass while using KDE is the password of your user account.[/quote]

This forum is for Gnome support, not KDE. 

In Gnome, you can use a terminal of your choice, Xterm and Gnome-terminal are installed by default.

The admin password while using Gnome is the password of your user account.

---

### Post by Furwolfie on 2005-10-22
first off, thanks for responding.. yeah, i was guessing it was the same password as i use to login to KDE.. unfortunally that password does not work? but it works fine for logging in to KDE still.  is there anything i can or have to do in "sudo" to get it working properly again?

---

### Post by Furwolfie on 2005-10-22
opps! *Giggles* indeed i am in the wrong section, sorry abouts that, i will post to correct one. thanks

---

### Post by aysiu on 2005-10-22
[QUOTE=Furwolfie]opps! *Giggles* indeed i am in the wrong section, sorry abouts that, i will post to correct one. thanks[/QUOTE] Never mind. I moved it for you.

---

### Post by Matchless on 2005-10-22
[QUOTE=Furwolfie]first off, thanks for responding.. yeah, i was guessing it was the same password as i use to login to KDE.. unfortunally that password does not work? but it works fine for logging in to KDE still.  is there anything i can or have to do in "sudo" to get it working properly again?[/QUOTE]


Try using    sudo kcontrol     in the konsole and see if it helps, you should then be in admin mode after entering your password.

---

### Post by The Keeper on 2005-10-22
This is a KDE 3.4 bug and there's a long thread about this problem in [here]("http://ubuntuforums.org/showthread.php?t=75114"). Several workarounds have been posted in that thread, hopefully KDE developers will fix the problem soon.

---

