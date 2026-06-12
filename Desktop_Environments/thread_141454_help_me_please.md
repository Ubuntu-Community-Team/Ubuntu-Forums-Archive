---
title: "help me please"
date: 2006-03-08
forum: Desktop Environments
---

### Post by Second_Player on 2006-03-08
i just started using ubuntu and i starting downloading and installing updates and during the installation part i had to leave so i set it to shut itslef down and it looked like it was still just going to install them then shut off but now it says there are still updates but it cant get an exclusive lock.  it thinks that there is another application getting program running, i dont know what to do.
thank you for whoever helps.

---

### Post by pbaehr on 2006-03-08
That happened to me once when I was trying to use apt-get while I had synaptic open. If you're quite sure you don't have an instance of synaptic open somewhere the easiest thing to do would probably just be to restart the computer. I'm sure there's a way to do it without restarting by killing the offending application but restarting the computer should start you with a fresh slate and you should be able to run synaptic again from there.

That's what I'd try anyway. Give it a shot.

---

### Post by Second_Player on 2006-03-08
thank you i'll give it a try

---

### Post by Second_Player on 2006-03-08
nope didnt work

---

### Post by pbaehr on 2006-03-08
In that case I'll step aside and let a more experienced person help you out. Sorry to mislead you. Good luck!

---

### Post by az on 2006-03-08
What does 
sudo apt-get -f install
do?

Show the output...

---

