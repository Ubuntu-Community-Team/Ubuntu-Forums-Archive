---
title: "Can't reinstall my kubuntu desktop"
date: 2017-12-07
forum: Desktop Environments
---

### Post by romzy on 2017-12-07
My desktop was gone: having a black font, no more bar and an only firefox tab, unabling me to use anything

I tried to reinstall kubuntu-desktop by typing : 

              sudo dpkg-reconfigure kubuntu-desktop
              sudo apt-get install --reinstall kubuntu-desktop

But it returned me an error about packages unmeting depencies, and asked me to type something (which I also tried in the root mode after) :

              apt --fix-broken install

Then I even was'nt able to enter my session : it froze after typing my password; I was able before to go in and face a black font. So I tried :

              sudo apt-get purge kubuntu-desktop
              sudo apt-get install kubuntu-desktop

But still the same issue..

---

### Post by SeijiSensei on 2017-12-07
Did you run "sudo apt-get update" first?  You always need to do that before any updating.

---

