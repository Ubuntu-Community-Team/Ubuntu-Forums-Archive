---
title: "Java environment user session"
date: 2011-03-10
forum: Desktop Environments
---

### Post by venturax on 2011-03-10
The situation is that I often need to change my Java environment, which I do by using the ```
sudo update-java-alternatives --set somejavaversion
``` This has worked like a charm, BUT..

I have installed an Ubuntu server (10.04 LTS), since there are more persons working on tha same thing as me. However the update-java-alternatives command is not a feasible approach on the server, since it sets the environment globally, which is not what i want. :(

I only want the change to be user specific or even better; session based.

Is this doable?

Thanks!

---

