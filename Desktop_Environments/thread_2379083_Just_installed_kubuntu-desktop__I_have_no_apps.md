---
title: "Just installed kubuntu-desktop : I have no apps"
date: 2017-11-30
forum: Desktop Environments
---

### Post by mrjeffmacdonald on 2017-11-30
Hi!

I just did a `sudo apt install kubuntu-desktop`. I logged out. Chose Plasma on login menu, logged in. When I bring up the K menu and click on "Applications" there is nothing there. If I search for "k" for example, I see some things, but not much. I had to install Konqueror separately. Did I miss some package? Oh ! Btw, this is on 16.04

Thanks

---

### Post by vasa1 on 2017-11-30
Have you run```
sudo apt-get update
```and```
sudo apt-get dist-upgrade
```after rebooting? Is the output free of warnings or messages?

And, just for example, what does```
apt policy kate
``` show?

---

### Post by mrjeffmacdonald on 2017-12-01
Thanks for the tips eh! I wasn't aware that dist-updgrade worked like that. I thought it was only for moving from release to release. Everything is fine now.

---

### Post by nibal on 2017-12-01
Could you plz mark thread as solved?

---

### Post by wildmanne39 on 2017-12-01
Go to the top of the page under thread tools to mark your own thread solved, you need to do it yourself please.

---

