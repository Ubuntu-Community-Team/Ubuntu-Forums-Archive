---
title: "Gutsy- Emerald not working with beryl"
date: 2007-10-23
forum: Desktop Environments
---

### Post by Coward on 2007-10-23
Yesterday I upgraded from Ubuntu Feisty to Gutsy. I have managed to get everything working just as before except there are no windows decorations when using beryl. I had emerald working fine in Feisty. The strange thing is that if I switch the windows manager to Compiz then I can see emerald working. I really like beryl better though.

I have tried typing "emerald --replace &" into the terminal with no success, what else is there to try?

O yea, I have nvidia drivers if that is important. I don't know what else could be important for you to know.

---

### Post by Xgen on 2007-10-23
The compiz/emerald files (0.3~git?) borked themes in the beryl/emerald version (0.2). To get around this, I deleted the emerald and libemeraldengine files through synaptic, temporarily unchecked all updates in Software sources (other than the official 3rd party beryl repo) and reloaded/reinstalled the files through synaptic. When updated, I locked the emerald/libemeraldengine files (Package-->LockVersion) and rechecked the Software Sources updates.

---

### Post by Coward on 2007-10-24
Well I typed "emerald --version" I get "emerald: emerald version 0.3.0-svn" so I tried to follow your directions. I completely removed the packages you mentioned through Synaptic. 

Then I was a bit unsure about what your directions meant. I went to settings>repositories, clicked on the updates tab, and unchecked everything there. Then I hit reload.

Ok, well I found "force version" so now when I type "emerald --version" I get "emerald: emerald version 0.2.0." Still no luck. I just checked and see that now emerald isn't working with compiz either now. I don't really care about compiz not working if beryl works, but I thought I'd mention it. When I type in "emerald" I get "Segmentation fault (core dumped)" which sounds bad.

Never mind, I found that my libemeraldversion was still 0.3.  Solved!

---

