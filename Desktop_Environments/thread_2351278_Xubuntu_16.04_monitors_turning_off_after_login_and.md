---
title: "Xubuntu 16.04 monitors turning off after login and on shutdown"
date: 2017-02-01
forum: Desktop Environments
---

### Post by Sathed on 2017-02-01
Monday morning, I did a clean install of Xubuntu 16.04. Everything worked well. However, I started noticing something goofy when I would login. I put in my password, and immediately after logging in, I would see the prompt for my password again, then my monitors would quickly go to sleep. After about a minute or two, they would come back and I'd be good to go. I also noticed that shutting down/restarting was a nightmare. If I attempt to shutdown the computer, it won't shutdown. The screens turn off, but the computer never shuts down. Same thing if I try to restart. I have to hold the power button to get it to shutdown. 

I ran: ```
$ systemd-analyze plot
```
But everything there looked okay. 

I also verified that my uuid's to make sure there wasn't something missing, but that looked okay too.

At this point, I'm stumped. Any thoughts?

---

