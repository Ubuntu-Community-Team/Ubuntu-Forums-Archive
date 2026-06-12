---
title: "[SOLVED] Nautilus going wild when opening files"
date: 2008-02-27
forum: Desktop Environments
---

### Post by LunatikOwl on 2008-02-27
I have a problem that driving me NUTS in the last few months. Every time I open some file with nautilus the CPU usage jumps up to 100% for a good few seconds(I've got Core duo 1.86GHz). When i open task manager at the time i think the process responsible is nautilus although I can't be certain, the task manager's monitoring is not very exact. 
On my other user in this computer the problem don't occur so I guess that the culprit is somewhere in the home directory. 
I've tried deleting the .nautilus directory and reinstalling it with synaptic. Suggestions anyone?
p.s. I have vino-session running all the time although I never configured it on this box, is this normal?(vino is a remote desktop control deamon)

---

### Post by LunatikOwl on 2008-02-27
Well, as it seems nautilus is not the only one choking my cpu. After firing up top -d 0.3 > cpu and reviewing the file i can see that the processes that taking turns on the top list(with almost 100% cpu usage) are Xorg, F-spot(understandable since i opened an image with f-spot viewer), Pyton(:confused:) as well as nautilus. Do I need to start worrying?

---

