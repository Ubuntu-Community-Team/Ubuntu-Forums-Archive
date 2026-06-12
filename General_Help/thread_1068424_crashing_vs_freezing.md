---
title: "crashing vs freezing"
date: 2009-02-12
forum: General Help
---

### Post by phirestalker on 2009-02-12
I started ubuntu with 6.10 and loved the crash reporting feature, when I upgraded to feisty it was still there. With gutsy it stopped working and I found that they had disabled it, I re enabled it and all was well again. Now that I have intrepid installed I have not seen it, but I'm not sure if it is disabled again or not as I don't think I have had a single program crash. This sounds good but it actually isn't. There are now 2 classes of program failures on my system, either it just doesn't open with no graphical error message ( I would have to start it from terminal to get an error), or it will freeze. Freezing is the most insidious software disease there is, I have used windows and ubuntu and neither nor I believe ANY OS is able to diagnose a frozen application, which of course makes it difficult to report a bug. I'm not sure what has caused this shift in functionality (right word?) but it is down right annoying. I don't know what really happens when a program freezes. my limited programming in the past would only offer up the endless loop (is that really the only cause of freezes?). I realize debugging is a "hobby" of its own as it takes lots of patience. Anyway let me get to the point.

Is it at all possible for an operating system (since it is still running when the application is frozen) to be able to somehow analyze the program in its frozen state and make a "non crash" report? (like when you force kill an app in gnome by clicking close, maybe before it kills it, it could start the "analyzing" process) Has noone attempted this task. Is it not considered a priority?

This may seem like a rant, but I am very happy with my ubuntu. I am just trying to figure out some things to help me if I ever get time to try and track down these freezes :confused:

---

### Post by Bonsanto on 2009-02-12
MY system crashes too, I can move my mouse bt I can't do anymore. Please watch this.

---

### Post by phirestalker on 2009-02-12
well.. first off videos are not all that helpful in a freezing or crashing situation and second the videos are not at all in a quality that I could make them out if they were useful. Also I probably cannot provide help, I would suggest that you open a new topic.

---

### Post by dcstar on 2009-02-12
> **phirestalker said:**
> 
.........
Is it at all possible for an operating system (since it is still running when the application is frozen) to be able to somehow analyze the program in its frozen state and make a "non crash" report? (like when you force kill an app in gnome by clicking close, maybe before it kills it, it could start the "analyzing" process) Has noone attempted this task. Is it not considered a priority?
.........

As far as I can see killing a "frozen" program in a specific way causes a core dump - which can then be analysed in the usual manner:

[http://wiki.davincidsp.com/index.php?title=Multithreaded_Debugging_Made_Easier_by_Forcing_Core_Dumps#Step_2:__Forcing_your_program_to_core_dump](http://wiki.davincidsp.com/index.php?title=Multithreaded_Debugging_Made_Easier_by_Forcing_Core_Dumps#Step_2:__Forcing_your_program_to_core_dump)

---

### Post by Bonsanto on 2009-02-13
Well my system crashes But My pc is Pentium 4 HT

---

### Post by phirestalker on 2009-02-13
Thanks david that is what I was looking for :) you wouldn't happen to know where these lovely core dumps will end up would ya?

---

### Post by dcstar on 2009-02-13
> **phirestalker said:**
> Thanks david that is what I was looking for :) you wouldn't happen to know where these lovely core dumps will end up would ya?

Not really, but I suspect there is some standard Linux location for them (somewhere).......

---

