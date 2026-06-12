---
title: "problem with sceenlets. randomly start?"
date: 2007-11-09
forum: Desktop Effects &amp; Customization
---

### Post by pjones0404 on 2007-11-09
i have installed screenlets and they appear to be working. The issue that i am having is that they sometimes start and other times do not. i have selected approx 4 of them to start when i login using the screenlets manager. some of the screenlets start while others do not. It is not always the same ones that do not start,

Do i need to add these to my sessions individually or can i use the screenlets manager to start them? I have tried to save my current session once i have them all running but it does not help the issue at all. 


I also receive this error when i open the screenlets manager " Unable to connect or launch daemon. Some values may be displayed incorrectly." Is this what is causing the problem?

thanks for any help.

---

### Post by itsjustarumour on 2007-11-10
I'm also getting the  "Unable to connect or launch daemon. Some values may be displayed incorrectly" message...

Does anyone know whats causing this?

---

### Post by pjones0404 on 2007-11-10
i have made no progress in this issue.

it seems that screenlets is not very stable as far as i can tell. i see alot of them on screen shots but i cant get them to work reliably for me. sometimes the clock screenelt shows up and other times it does not. 

i have looked in my sessions and all the screenlets are there individually. i go to the screenlets manager when they do not load and i am able to manually start them. i them save the session and when i log back in they are gone. 

i would like to fix this or i will just not use them at all. anyone got any ideas?

---

### Post by yourpalal on 2007-11-10
i have a similar problem, although my screenlets will start without problem, they will randomly create a new instance, so as long as i leave my compy on they just keep adding and adding themselves.

---

### Post by itsjustarumour on 2007-11-18
> **pjones0404 said:**
> i have made no progress in this issue.

it seems that screenlets is not very stable as far as i can tell. i see alot of them on screen shots but i cant get them to work reliably for me. sometimes the clock screenelt shows up and other times it does not. 

i have looked in my sessions and all the screenlets are there individually. i go to the screenlets manager when they do not load and i am able to manually start them. i them save the session and when i log back in they are gone. 

i would like to fix this or i will just not use them at all. anyone got any ideas?


After 2 weeks of "experimentation", I've abandoned them completely.  

The whole program was so unstable it was almost comical, with my screenlets behaving like a badly trained troupe of meerkats - popping up all over the place, disappearing, first there were five and then there were none, not doing what I told them to do, then forgeting about it completely and doing their own thing anyway!  :lolflag: 

They do look good in screenshots and I'll be keeping an eye on the project for later, but right now it does feel like very alpha software.

---

### Post by Dyqik on 2007-11-18
I think I've solved the problem of the calender and some other screenlets not starting on login.

The calender screenlet ( /usr/local/share/screenlets/Calender/CalenderScreenlet.py ) is not set with executable permissions when screenlets is installed.  Some user screenlets also suffer this problem (Wireless definitely does).  The screenlet .py files must be set executable to be started on login, but need not be when started by the screenlets manager

```
sudo chmod a+x /usr/local/share/screenlets/Calender/CalenderScreenlet.py
```

will fix the Calender screenlet.  Equivalent lines for other problem screenlets should fix those.

---

### Post by itsjustarumour on 2007-11-18
> **Dyqik said:**
> I think I've solved the problem of the calender and some other screenlets not starting on login.

The calender screenlet ( /usr/local/share/screenlets/Calender/CalenderScreenlet.py ) is not set with executable permissions when screenlets is installed.  Some user screenlets also suffer this problem (Wireless definitely does).  The screenlet .py files must be set executable to be started on login, but need not be when started by the screenlets manager

```
sudo chmod a+x /usr/local/share/screenlets/Calender/CalenderScreenlet.py
```

will fix the Calender screenlet.  Equivalent lines for other problem screenlets should fix those.


Good work!  :-D

---

### Post by Dyqik on 2007-11-18
Stupidly simple really.

The other default screenlets affected are Pager and Storage.  The Wireless 3rd party screenlet is also affected.  I haven't found any other 3rd party ones with this problem, although I haven't tried many of them.

---

