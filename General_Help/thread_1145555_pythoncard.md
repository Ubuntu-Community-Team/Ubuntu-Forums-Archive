---
title: "pythoncard"
date: 2009-05-01
forum: General Help
---

### Post by okhi on 2009-05-01
hi everyone,

after recently making the switch from Windows,I needed to get PythonCard (Development Tool).
The problem is that in both cases, after installing it from Synaptic or running the sudo apt-get install pythoncard command,i couldn't find the programme under Applications->Development
Does anyone have an idea what the problem is?
Thanks in advance

---

### Post by afrodeity on 2009-06-24
I guess PythonCard is badly documented. I downloaded the item from the repo, and same problem as yours. Typing PythonCard in a terminal did absolutely nothing. Then I found a [thread]("http://ubuntuforums.org/showthread.php?t=535314") explaining how to compile it, and saw that the person who was requesting assistance, was speaking about codeEditor and resourceEditor, which are two PythonCard utilities. I am still not sure if this is the sum total of the PythonCard "suite" or I am missing something, but you can either call them up with a terminal, or put them into your menu by right-clicking edit menu and browsing for them in /usr/bin

BTW I was expecting something a lot more zen-inspired, like Apple Hypercard.

---

### Post by The Cog on 2009-06-24
The pythoncard documentation is truly apalling. The two programs you need are indeed codeEditor and resourceEditor. I prefer geany for doing the code editing, so resourceEditor is really all you need. 

/usr/share/doc/pythoncard-doc contains the documentation such as it is.

---

### Post by Lordthoron on 2011-01-21
> **afrodeity said:**
> I guess PythonCard is badly documented. I downloaded the item from the repo, and same problem as yours. Typing PythonCard in a terminal did absolutely nothing. Then I found a [thread]("http://ubuntuforums.org/showthread.php?t=535314") explaining how to compile it, and saw that the person who was requesting assistance, was speaking about codeEditor and resourceEditor, which are two PythonCard utilities. I am still not sure if this is the sum total of the PythonCard "suite" or I am missing something, but you can either call them up with a terminal, or put them into your menu by right-clicking edit menu and browsing for them in /usr/bin

BTW I was expecting something a lot more zen-inspired, like Apple Hypercard.

ok now that I'm bald from pulling my hair out looking for this answer, thank you much.
indeed all you need is the resourceEditor and it seems to work fine 
I set up a desktop launcher to it with this as the command for anyone else needing it  /usr/bin/resourceEditor  again thanks again for the save

---

