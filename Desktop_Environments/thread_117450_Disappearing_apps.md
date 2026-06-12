---
title: "Disappearing apps"
date: 2006-01-14
forum: Desktop Environments
---

### Post by Almighty on 2006-01-14
Hello all.

I recently installed Ubuntu 5.10 and I am running into a problem I first encountered when I installed 4.10. When I first installed the OS, I made sure to run the update so everything is fresh and running well. After I have done that I started to install some apps that I normally use with windows. After installing a few different apps, I try to use them. when I go to start the app, I find that, for example fire fox will not start.

What am I doing wrong? How would I revert to when things were working properly?

Thanks in advance everyone.

---

### Post by aysiu on 2006-01-14
Have you tried adding a new user and using that user to see if it encounters the same problems as your current user?

---

### Post by Almighty on 2006-01-15
I have created a new user and it seems the change is universal.

---

### Post by Almighty on 2006-01-15
No one has an answer to this problem?

---

### Post by borisattva on 2006-01-16
thats the first i heard.

how do the applications not start, the popups go away as you click and nothing happens?
if you try to run it again doe sit by chance tell you that youre running it with root privilegies?
have you added some other repositories taht maybe cross messing up your system?
how soon after you start installing applications does this start to happen?
have you noticed anykind of a pattern for this to start happen after you install a particular set?

---

### Post by cwaldbieser on 2006-01-16
[QUOTE=Almighty]No one has an answer to this problem?[/QUOTE]
If you open a terminal and try to start it that way, does anything happen?

---

### Post by Almighty on 2006-01-16
[QUOTE=borisattva]thats the first i heard.

how do the applications not start, the popups go away as you click and nothing happens?
if you try to run it again doe sit by chance tell you that youre running it with root privilegies?
have you added some other repositories taht maybe cross messing up your system?
how soon after you start installing applications does this start to happen?
have you noticed anykind of a pattern for this to start happen after you install a particular set?[/QUOTE]

Yes, the apps will appear in the task bar saying they are about to start. Then the window disappear.

When I try to restart the program, it goes through the same pattern again. There is no mention of root priviledges.

Im not sure if any new repositories have been added. Sorry but I am a knoob with all of this.

I have noticed the changes almost instantly after all the updates and what not.

Is there any way to revert to a previous configuration?

---

### Post by Almighty on 2006-01-16
Oh and one last thing. When I try to launch fire fox in terminal I get this error message:

libstdc++.so.5: cannot open shared object file: No such file or directory.

---

### Post by GeneralZod on 2006-01-16
[QUOTE=Almighty]Oh and one last thing. When I try to launch fire fox in terminal I get this error message:

libstdc++.so.5: cannot open shared object file: No such file or directory.[/QUOTE]

Ding ding ding! :)

```

sudo apt-get install libstdc++5

```

---

### Post by Almighty on 2006-01-16
Wow, I feel like a complete idiot. I thought it was a directory, so I made one and didnt work. 

Thank you so much for helping a knoob like me out. One day I can be a bigger help to the forum.

---

