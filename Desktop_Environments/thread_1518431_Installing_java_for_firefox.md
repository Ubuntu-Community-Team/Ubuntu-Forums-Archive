---
title: "Installing java for firefox"
date: 2010-06-26
forum: Desktop Environments
---

### Post by Tsun on 2010-06-26
Well, i don't know what to write here, other than "How?"

I can't seem to figure how to get java running for firefox, so i would appreciate some help.
Ubuntu always gets me so pissed off because it's so hard to get the most simple things installed. :(

I have 10.04

---

### Post by ajgreeny on 2010-06-26
Search for and install **sun-java6-plugin** with apt-get install or synaptic.

That's all.

---

### Post by Tsun on 2010-06-27
There is no button to install/uninstall it.

When i click for more info, it says "To show more information about this item, the software catalog needs updating."

---

### Post by lovinglinux on 2010-06-27
[http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by krishnandu.sarkar on 2010-06-27
Just run sudo apt-get install sun-java6-plugin from terminal.

---

### Post by 3rdalbum on 2010-06-27
**Java is in the Partner repository as of Ubuntu 10.04.** You may need to activate it by going to System > Administration > Software Sources and the Other Software tab, and put a check next to the one that says "Partner". Close the window and click OK when asked about reloading the package list. Then you can install sun-java6-plugin.

It's not hard at all, it's just different to what you're used to.

---

### Post by Tsun on 2010-06-27
Ok well that partner repository thing solved it :)
Thanks for the help :p


The "hard" thing is, how am i supposed to know things like this this without asking? Why didn't the software center instruct me to do this?
Also it's hard to bother learning all the terminal commands when i'm used to clicking a button in windows.

---

### Post by krishnandu.sarkar on 2010-06-27
Well...You'd just need to be experienced. That's why Linux is little hard for newbies and awesome once you get used to it :)

---

### Post by ajgreeny on 2010-06-27
> Also it's hard to bother learning all the terminal commands when i'm  used to clicking a button in windows
It may seem hard at the moment, but persevere with it and you will possibly find it the most useful thing about linux.

You seldom really "need" it these days but when you get used to it it can do so much, and often much quicker and easier than a GUI application.

---

