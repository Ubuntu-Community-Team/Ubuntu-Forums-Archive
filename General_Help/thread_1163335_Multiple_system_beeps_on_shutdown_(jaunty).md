---
title: "Multiple system beeps on shutdown (jaunty)"
date: 2009-05-18
forum: General Help
---

### Post by Jameshardy88 on 2009-05-18
Hi ever since i have installed Jaunty (fresh install)i get several rapid system beeps everytime i shutdown/restart my computer (not the case on my previous intrepid or hardy installs). I have not noticed any other errors but this is finally starting to annoy me and i wondered how i might go about solving it?

Thanks for any help,

James

---

### Post by Jameshardy88 on 2009-05-19
bump

---

### Post by mike555 on 2009-05-19
I got this from another post , it worked for me ...


OK well to disable the beeps you can try these two commands (one after the other):

Code:

sudo rmmod pcspkr

and then this:

Code:

echo 'blacklist pcspkr' | sudo tee -a /etc/modprobe.d/blacklist

Hopefully you will now be beep-free! If your system fails to shutdown, another way to shut down is to run this command:

Code:

sudo shutdown -h now

---

### Post by JUSTINBEAIRD on 2009-05-20
how i disabled beep was

sudo gedit /etc/modprobe.d/blacklist.conf

then add 

blacklist pcspkr

to that list

---

### Post by Jameshardy88 on 2009-05-20
Why am i getting the beeps in the first place? will doing what either of the previous posts suggest stop system beeps in other instances where they are justified?

---

### Post by VCoolio on 2009-05-20
You will indeed turn off all pc-speaker sounds, which most people are completely happy with. The previous commands let you put pc-speaker on a blacklist (btw with gui-applications like gedit always do 'gksudo gedit' instead of 'sudo gedit', read [here]("http://www.psychocats.net/ubuntu/graphicalsudo") why).

One other solution not mentioned here which works for some people: turn off sound under System -> Preferences > Power Management -> General -> Extras -> Sound notification.

---

### Post by Jameshardy88 on 2009-05-20
Thankyou to all those that posted solutions, i have eventually used the solution suggested by vcoolio, but appreciated all of your input.

---

