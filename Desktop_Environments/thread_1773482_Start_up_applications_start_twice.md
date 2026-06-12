---
title: "Start up applications start twice"
date: 2011-06-02
forum: Desktop Environments
---

### Post by zakchambers01 on 2011-06-02
I have ubuntu 9.04 and I have used the startup applications feature.  I have 2 apps I am trying to start at startup, both of which I have in the panel and run fine when clicked.  If I copy the exact commands and then add them to the startup applications list they seem to start twice.  These apps are transmission and skype.

Now before it was only transmission and I didn't mind cause it only threw up an error but transmission started anyway in the background.  But now skype starting twice is an issue cause it cant login.

I have treid clearing the session and played around with the ~/.config/autostart folder to no avail.  Something is starting the apps twice and I need help figuring out what.

I have search google and this forum and cant find anything to fix this issue.

Any help would be apprciated and i will post the results.

Cheers

---

### Post by Copper Bezel on 2011-06-02
Well, let's narrow down the possible problems. Passing strange if your startup applications are *all* trying to start twice. (I don't trust Startup Applications. = P) 

Does that seem to be the case - if, say, you add gedit to startup applications, log out and come back?

If you untick Skype and Transmission, do they stop launching at startup?

---

### Post by 23dornot23d on 2011-06-02
Which desktop are you using ...... 

I have noticed this happens in KDE ..... with cairo-dock.

I just usually kill off the last one ..... 

but not tracked down why it does it yet.

---

### Post by zakchambers01 on 2011-06-03
if i take skype or transmission out of start apps they dont load at startup.  I agree I dont trust this start app stuff either.  I think there is a clever way to this with the terminal and update.d something cant remeber, if anyone knows about this maybe I could try it this way.  

Also i am not on KDE and dont have cario installed, I'm on GNOME, ubuntu 9.04.

Thanks again for the help

---

