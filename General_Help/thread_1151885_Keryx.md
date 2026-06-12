---
title: "Keryx"
date: 2009-05-07
forum: General Help
---

### Post by hashi856 on 2009-05-07
***Please read the topic to [this thread]("http://ubuntuforums.org/showthread.php?t=1126542") before responding, as it explains my situation

Someone in the above post recommended Keryx to me.

 When trying to start a new project in Keryx, I get the following error: "please create the project on the plugin's supported OS" Do I have to create the project in ubuntu? Is there a way to start it in Windows?

P.S. Debain is the only option in that drop down box.


.

---

### Post by EXCiD3 on 2009-05-07
You have to create the Keryx project on a debian machine. It has to be able to grab the files necessary in order to create the project, those files won't exist on a Windows machine naturally. Go to your offline computer, cd to the Keryx directory and run
[code]python keryx.py --create <projectname> debian" and your project will be created for you. Or alternatively, you can install the Python-wxversion packages for your offline machine and create the project graphically on that machine, the command-line way is just quicker and simpler. 

Debian means that you are running it on a apt based box, which Ubuntu is based off of debian. I will be changing the wording on a lot of things in the near future as well, it gets confusing and I was in a rush to release it before school started for me again.

I'll be rewriting Keryx from scratch this summer and my goal is to make it easier for everyone to use/understand. If you have any ideas please let me know! :) Just got our website and forums back up over at http://keryxproject.org too.

---

### Post by hashi856 on 2009-05-07
Once I create the project, will it work on the public windows computer here so I can download the packages? How does that work?

---

### Post by EXCiD3 on 2009-05-08
Yes, once you create the project, Keryx will have all the information it needs to allow you to download any package and updates you would like on any computer. Keryx just has to gather that information first before it can know which repositories you want to use, which mirrors, which packages are currently installed and what versions so that you can view the list of available packages and updates. It can't really be simplified much more than how it is right now except that I will be shipping Keryx with default projects for those people who have never updated their offline computer, which I can be that a fair amount of people have not. I just have to do it this way so that Keryx will work for anyone who wants to use it and not just those users who have never updated anything.

If you need anything else, you know who to ask. :D

---

### Post by hashi856 on 2009-05-08
Ok thanks. That's a good idea, as I am one of those people who have never updated my offline machine.

---

