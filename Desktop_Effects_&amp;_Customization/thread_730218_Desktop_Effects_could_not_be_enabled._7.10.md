---
title: "Desktop Effects could not be enabled. 7.10"
date: 2008-03-20
forum: Desktop Effects &amp; Customization
---

### Post by stroudle on 2008-03-20
Well...its about the same story that everyone else has. Desktop effects could not be enabled. I have looked for three days for what i need to do, and I cant find anything that got it to work...When i go to the restricted drives manager, it says I dont need them. So, this being said, what do I need to do and what do I need to tell you so you can tell me what to do?

---

### Post by fela on 2008-03-20
are you sure your graphics card supports it? tell me the name of your graphics card and specs.

not needing restricted drivers sounds a bit fishy to me...

---

### Post by stroudle on 2008-03-20
I dont know, I have ben looking for it, but not much luck. Is there a command i can use? When i had linux on my laptop i could figure it out...but with this desktop...I dont think I even have anything :lolflag:

---

### Post by theparticle010 on 2008-03-20
THIS IS NOT AN EXACT GUIDE. PLEASE LOOK OVER THIS IF YOU ARE AN EXPERT ON THIS TOPIC


Allright, I don't know about the rest of you, but it sounds like you computer was not connected to the internet when you installed Ubuntu, my Drivers manager did almost the same thing, some drivers showed up, and the modem did not, and so, I just cheked out the apt sources list file and uncommented the lines and I was set so here is what you need to do:

open a terminal ( Apps> Accessories> Terminal )

type:   sudo su
and enter your password. YOU ARE NOW ROOT DON'T DO ANY THING OTHER THAN WHAT I TELL YOU TO.

type:

gedit /etc/apt/sources.list

Now gedit should pop up, and what you want to do is take a look and read some of the comments, see if it says something like:

" This line has been commented out because if failed to verify..." bla bla bla

uncomment the ones that look like:

# deb http://archive.{ url }
and 
# deb-src http://{url }

Now this is not an exact guide, I would not advise doing this to your computer 'till someone looks at what I have said, I have crashed ubuntu over 15 times messing with the system, and I don't want you to have the same fate I have had. ^_^

---

### Post by stroudle on 2008-03-20
The source list is completely blank when it popped up. Nothing at all. 


When I Had it on my laptop i had no problem with anything...Other than the fact that it wasnt enough computer to really do what i wanted it to do...now i moved it to a slave harddisk on my parents desktop and its just not working right. I really dont know much about their computer other than it is an emachnies.

---

### Post by theparticle010 on 2008-03-22
Allright, If you want to do stuff with linux, and you want to keep your settings, back up your home folder, and make a list of the programs that you installed, then reinstall Ubuntu, and put your home dir right back in it's place, install the programs that you had, and you're good to go.


If however you don't want to do that, just copy my sources list, and we can see what we can get to work.

( I'm using windows right now, give me a day maximum to post the list )

---

