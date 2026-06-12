---
title: "Nautilus open-with bash script"
date: 2006-09-27
forum: Desktop Environments
---

### Post by Lemming-by-nature on 2006-09-27
ok well I'm playing around with a bash script to run the par2 program
against a file.. the script is very crude.. all it does is basically run:

par2 r `pwd`$1

to run the command against the file its been handed. I knwo this may not
be a good way to do it... and any help with this would be great.

but my main question is how I can get Nautilus to run this script against
.par2 files when they are double clicked.

I get the whole Open With->Open With Other Application->use custom command

but what is the command?

say to run the script it would be 

~/./par2script file.par2

---

### Post by henriquemaia on 2006-09-27
Install Nautilus-actions, available on synaptic. It's a gui for configuring actions (based on commands) for nautilus to execute on the rigth-click menu.

---

