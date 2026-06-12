---
title: "Exiting a virtual terminal and getting back to it breaks X (I guess)"
date: 2009-02-14
forum: General Help
---

### Post by Smjork on 2009-02-14
So let's just say I work in a GNOME session, in my default virtual terminal, which is equivalent to Ctrl-Alt-F7
Then I need to do something in a different terminal so I press Ctrl-Alt-F1 (...F6), get into that virtual terminal, do whatever I have to do. At the end I type "exit" and return to my default virtual terminal using Ctrl-Alt-F7
Well, starting that point, the virtual terminal corresponding to Ctrl-Alt-F1 is no longer accessible. Ctrl-Alt-F1 leads to a completely black screen, no login, no nothing. And worse, trying to get back to the default (F7) leads to exactly the same, there fore the imposibility to use the PC anymore. The only solution I found so far is press the computer reset button.

So having that in mind, I always need to remember if I ever used any virtual terminal and choose the next "unused-before" one.
So the next choice would be virtual terminal 2 (Ctrl-Alt-F2), do the job and return to default using Ctrl-Alt-F7
The 3rd choice would be Ctrl-Alt-F3 and return to default
... and so on , upto virtual terminal 6
An always remember that the "previous-used" one is no more accessible starting the moment I exit from it. And that if by mistake I switch to any of these and try to get back to the default I will totaly screw up my session, as even the default turns out totally black and unresponsive.

Any clues on why is this happening ?
In my opinion this has to be related to X, but I just don't know why or how to fix it.

---

### Post by detroit/zero on 2009-02-14
> **Smjork said:**
> So let's just say I work in a GNOME session, in my default virtual terminal, which is equivalent to Ctrl-Alt-F7
Then I need to do something in a different terminal so I press Ctrl-Alt-F1 (...F6), get into that virtual terminal, do whatever I have to do. At the end I type "exit" and return to my default virtual terminal using Ctrl-Alt-F7
Well, starting that point, the virtual terminal corresponding to Ctrl-Alt-F1 is no longer accessible. Ctrl-Alt-F1 leads to a completely black screen, no login, no nothing. And worse, trying to get back to the default (F7) leads to exactly the same, there fore the imposibility to use the PC anymore. The only solution I found so far is press the computer reset button.

So having that in mind, I always need to remember if I ever used any virtual terminal and choose the next "unused-before" one.
So the next choice would be virtual terminal 2 (Ctrl-Alt-F2), do the job and return to default using Ctrl-Alt-F7
The 3rd choice would be Ctrl-Alt-F3 and return to default
... and so on , upto virtual terminal 6
An always remember that the "previous-used" one is no more accessible starting the moment I exit from it. And that if by mistake I switch to any of these and try to get back to the default I will totaly screw up my session, as even the default turns out totally black and unresponsive.

Any clues on why is this happening ?
In my opinion this has to be related to X, but I just don't know why or how to fix it.
I could be wrong, but don't type 'exit' when leaving your virtual terminal. Just ctrl-alt-f7 back into your gui.

---

### Post by Dr Small on 2009-02-14
> **detroit/zero said:**
> I could be wrong, but don't type 'exit' when leaving your virtual terminal. Just ctrl-alt-f7 back into your gui.
Just the same, this shouldn't be happening.

---

