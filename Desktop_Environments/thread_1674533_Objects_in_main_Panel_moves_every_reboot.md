---
title: "Objects in main Panel moves every reboot"
date: 2011-01-24
forum: Desktop Environments
---

### Post by hoveman on 2011-01-24
Hello,

as the title says, after every reboot every object on the panel expect "Application", "Places" and "System" has different position. 
So i have to reorder them and after that i select "Lock to Panel" for every object but this didn't help.
I am very new at ubuntu and its very cool i think. But this is a little confusing. 
I hope somebody can help me....

More Information: Ubuntu 10.10 64 Bit with Gnome, Latitude E6400

---

### Post by Krytarik on 2011-01-24
Check out this thread: [http://ubuntuforums.org/showthread.php?t=1626529](http://ubuntuforums.org/showthread.php?t=1626529)

Does your screen resize after login?

---

### Post by hoveman on 2011-01-25
thanks for reply... 

[QUOTE=Krytarik]Does your screen resize after login?[/QUOTE]

i don't think so. i have to look carefully when i am back home. but i didn't notice this behavior.

but i have a dockingstation. so sometimes i work with my laptops display (latitude e6400 1440x900) and somtimes i dock my laptop to the station and there i have a resolution of 1920x1200.
Could this be the problem?

---

### Post by Krytarik on 2011-01-25
Obviously. I've just yet tested the behaviour when I switch from 1152x864 to 1024x768 and back again, each time restarting the panels by "killall gnome-panel". After the first change, the items stuck to their positions, but after switching back, some item have moved, although of course locked, as in your case. Great, then I have to re-arrange them now!;)

---

### Post by hoveman on 2011-01-26
thanks for your help... i thin this is the problem

---

### Post by Boondoklife on 2011-01-26
GDM might be running in a different resolution than your desktop. I have seen this happen and it causes the jumpy menu items you are talking about.

---

### Post by Krytarik on 2011-01-26
> **Boondoklife said:**
> GDM might be running in a different resolution than your desktop. I have seen this happen and it causes the jumpy menu items you are talking about.
We did already check that, posts #2+3.

---

### Post by Boondoklife on 2011-01-26
Didn't see a mention of GDM there, but thought I would mention it. Most people don't notice the diff if resolution when it comes to GDM vs. Desktop. In my case it was just a split second thing that was almost impossible to catch or see.

---

### Post by Krytarik on 2011-01-26
> **Boondoklife said:**
> Didn't see a mention of GDM there, but thought I would mention it. Most people don't notice the diff if resolution when it comes to GDM vs. Desktop. In my case it was just a split second thing that was almost impossible to catch or see.
Yeah, thanks for mentioning it.

@hoveman: Do you autologin, or do you have to enter your password to login, or least have enabled timed autologin, so that you can see the login screen (GDM) before you get to your desktop? If the first case is true, then please logout from your session to really see the login screen.

EDIT: Do the panel items really move *everytime* you re-login/boot, or only after you switched between dockingstation and laptop display? The latter won't be fixable, but the other is, at least for a resolution of your choice.

---

