---
title: "KDevelop"
date: 2006-01-10
forum: General Help
---

### Post by wizzkid on 2006-01-10
My KDevelop doesnt work anymore. I click and nothing happens. I dont know what went wrong.. The last time i used its working, last week was the last time i used the program. I tried to re-install the application thru synaptics but doesnt fix the problem. 

What should I do now? :)

Thanks.

---

### Post by Malakim on 2006-01-10
Hi there,

I had some issues with KDevelop not working on Debian (before I moved to Kubuntu) when I updated from KDE 3.4 to 3.5. Have you touched any of the KDE libs or anything else related to KDE that might have broken some dependencies?

Regards,
Markus Svensson

---

### Post by wizzkid on 2006-01-10
I just updated my kde from 3.4 to 3.5, install GNU Emacs.

The icons of KDevelop was gone. its a blank icon. :-( even after I re-install the kdevelope thru synaptic.

---

### Post by Malakim on 2006-01-10
I see, guess we encountered a similar problem. I never got it working again, probably because there wasn't a complete KDE 3.5 set for Debian at the time, and installing some of the KDevelop dependencies would break other applications, or just weren't available. That's why I moved on to Kubuntu, which already had KDE 3.5 when I installed it (IIRC). 

What happens if you try to launch KDevelop from a terminal? Sometimes that will give more information about what's missing.

---

### Post by wizzkid on 2006-01-11
I see, I haven't tried it running on terminal, whats the command to run kdevelop on terminal? When I tried to launch the program by clicking the icon of kdevelop, it nothing happens, even the small icon of kdevelop doesnt appear.

any more suggestions?

---

### Post by Malakim on 2006-01-11
You just open Konsole, and type kdevelop at the prompt. You should be able to type kdev and then press the TAB key, and the rest should be filled in automagically. If you get a "file not found" (or something to that effect), the kdevelop executable hasn't been installed corerctly. If KDevelop launches, your shortcuts probably points to the wrong location.

Hope this helps. :)

---

### Post by Thirsteh on 2006-01-11
**kdevelop3** in your console.

---

### Post by wizzkid on 2006-01-11
Hi!

I type kdevelop3 on terminal and it worked. but i saw this message on terminal:
Qt: Locales not supported on X server
with bunch of codes, i think thats normal as i dont see any error msg.. 

on the properties command of the Kdevelop C++ icon is kdevelop --profile CandCppIDE %u  i tried to change the kdevelop to kdevelop3, but still nothing happens...

---

### Post by Malakim on 2006-01-11
I think I've experienced the same problem. The only short cut I'm able to use is the one labeled something like "KDevelop Multiple Languages" or something similar. The ones with specificf language profiles just won't work. I'm not at my Linux box right now, so I acn't chack if there's any difference between the command executed ny the C++ profile and the "Multiple Languages" profile.

---

### Post by GoldBuggie on 2006-01-11
Not sure what the exact problem for you was but the problem of not gettin kAssistant or KDeveloper to start thrue the kmenu is fixed by doing
```
sudo ln -s /usr/share/apps/kdevelop3 /usr/share/apps/kdevelop
```

---

### Post by Thirsteh on 2006-01-11
If everything goes wrong, I recommend the **Anjuta** C/C++ IDE. Although it's for Gnome, but in my opinion it's far superior to Kdevelop.

---

### Post by wizzkid on 2006-01-11
sudo ln -s /usr/share/apps/kdevelop3 /usr/share/apps/kdevelop doesnt seem to work :(

I will try Anjuta C/C++ IDE

Im also trying Eclipse with CDT what do yo think? :)

---

### Post by Malakim on 2006-01-11
[QUOTE=wizzkid]sudo ln -s /usr/share/apps/kdevelop3 /usr/share/apps/kdevelop doesnt seem to work :(

I will try Anjuta C/C++ IDE

Im also trying Eclipse with CDT what do yo think? :)[/QUOTE]

I don't really like the Eclipse interface, but that's just me I guess. :p 
If yu really want to use KDevelop, why don't you just create a shortcut on the desktop to it, since it worked when you ran it from the terminal?

---

### Post by wizzkid on 2006-01-12
OKay, I can add an icon, its easy :) but how to run these or what command line should i use.

IDE for C/C++
IDE for KDE Developement
IDE for Ruby
IDE for Scripting Langauage

btw, what is the diffrence of those? sorry-- very new and wanna learn programming. Any good software for IDE C/C++ would be fine, just dunno which.  

its just that, im getting nuts that kdev is not working hehe,, i dont want application in my system thats not running, i might as well remove it, but kdev cnt be revome.

Thanks.. any help will be appreciated.

---

### Post by Malakim on 2006-01-12
[QUOTE=wizzkid]

IDE for C/C++
IDE for KDE Developement
IDE for Ruby
IDE for Scripting Langauage

btw, what is the diffrence of those? 
[/QUOTE]

Don't know the differance, really. Probably the IDE starts up settings for the chosen language. But if you just open kdevelop3, you'll still be able to use any of the languages above when you start a new project (at least that's how I remember it ;) ). I'm doing C and C++ development (non-KDE) with the "general" settings, and it's working just fine. KDE projects can be selected when starting a new project, so that shouldn't be a problem either. I don't use the other languages, so I really can't comment on them.

Regards,
Markus Svensson

---

### Post by overcast on 2006-01-13
I dont know almost no developer application is supported under ubuntu,why they have such inert support for ubuntu?
Why not have developer envirement within ubuntu?Python only will not do the job.

---

