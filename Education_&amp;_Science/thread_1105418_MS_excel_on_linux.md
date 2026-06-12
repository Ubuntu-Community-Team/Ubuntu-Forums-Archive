---
title: "MS excel on linux"
date: 2009-03-24
forum: Education &amp; Science
---

### Post by pnik on 2009-03-24
hi to everybody

I would like to ask if you are able to use efficiently MS excel on linux. I'm finishing financial engineering and I am obliged to use excel along with C++ matlab r-statistic etc. Excel is a standard on this field.

I have installed several versions of crossover office and then I installed MSOffice. I can open the MSExcel but it is not working as good as on windows.

For instance I need to use several add-ins or create some of them with VB, or the spreadsheet shortcuts are not working. Does anybody have relevant experience how to make it work on linux????

It will be a big disappointment if I have to change to windows...

regards

---

### Post by amauk on 2009-03-24
probably best to use a VM, and install Windows & Excel in the VM

check out VirtualBox

---

### Post by pnik on 2009-03-24
I love VBox and I am using it for over two years now, so far using Vbox I was feeling that I have the "perfect" OS because I had linux and some apps from windows that are not working on linux. 

But the thing is that now I have to create a professional environment that I will have everything in front of me. Imagine that you need to integrate C++ code with some toolbox from matlab and some add-ins from MSexcel, and then they need to run on the same system. As a student I wouldn't mind to play around and spent some more time, but now I have to start thinking what is better for the work.

I would appreciate if anybody has some idea..

---

### Post by gunksta on 2009-03-24
Disclaimer: This is an absolute shot in the dark. That being said, I took a similar shot in the dark, and it worked. :p

Wine makes it "easy" to install Windows based software onto Linux. But it's not without it's fair share of problems. Wine is NOT a 100% complete re-implementation. For example, VB stuff can't run on Wine, unless you install something to execute VB. Unfortunately, when you install a Windows program, it doesn't tend to check to first make sure it has access to everything. It "assumes" that it is setting up shop in a normal Windows environment. This causes problems.

For example, Access on Wine is typically an absolute failure? It always crashes when you try to do sometihng, because Wine does not include a version of the jet database, which is part of a normal Windows installation. Your problem may be as simple as "dll" hell. If Excel is failing to function in the manner you expect, it could be an indication that Wine is missing some critical piece of functionality. Thus, we need to implement that piece of functionality, by cheating.

[Winetricks]("http://wiki.winehq.org/winetricks"), is your friend.

Before actually running winetricks, make sure you have cabextract installed (synaptics, apt-get) or things won't work as advertised. I have also had problems getting ie6 to install via winetricks, but I am using fakeie6 with some success.

I also suggest reading [this]("http://www.wine-reviews.net/microsoft/running-ms-office-2003-under-linux-with-wine-0952.html"). It helped me learn more about installing office on Wine in general. But, I did find one bug in the suggestions. The article recommends installing msi onto Wine. This is an update to widows to handle msi installations. When this article was written, that was probably a good idea. But, I'm running Jaunty Alpha 6+, which is a much newer version of Wine. When I installed msi, Office would no longer install cleanly. If I just left wine alone, everything worked fine.

I don't know for sure if this will help you or not. I don't need Excel to run VBA (which is different but related to VB) extensions so I have never worried about it.

Good luck. It's easy to play around too much with winetricks / wine. Here's one last suggestion. I tend to get a basic, stable Office installation running first. I then back up my .wine file, with an attached date, so I have two .wine files.

.wine
.wine-3-24-2009

In fact, I have two or three of these at any given moment as I'm experimenting. This way if I try something and it borks Office, I can just delete my .wine configuration and copy in an older, functional copy. But, I'm sure this violates my EULA from MS.  :popcorn:

---

### Post by pnik on 2009-03-25
thanx a lot gunksta

you've been quite informative :)

I 'll try to have a look on that

---

### Post by s0ultaker12 on 2009-03-25
can you help me guys? i can't access my excel file. the computer said that access was denied. i want to know if their is a chance for me to access the file using ubuntu. the file can not be copied so i cant make any backup. please help me.. thanks

---

### Post by gunksta on 2009-03-26
s0ultaker12:  Technically, this is hijacking the thread, which is generally considered rude. This isn't really what the OP intended to discuss. As a forum member you are very much entitled to start your own thread. However, I would suggest a change of venue, and adding more information to your help request.

The Beginner's forum or general forum are probably more appropriate places for your question than the Education & Science forum.

When you re-post, try to slow down and provide some relevant context. Where is this mysterious file? Is it on a Windows or Ubuntu machine? How are you trying to access the file? Is it a file that you have permission to open? Can you copy the file, rather than opening the file directly? Are you trying to open the file via a wine app? (which is what the rest of the thread is talking about) What have you tried to do, to open the file?

I'm afraid that your current request for help, doesn't help us answer your question. It's a little like looking at a car through a window and trying to figure out why it can't get into gear.

Start a new thread and GOOD LUCK.

---

