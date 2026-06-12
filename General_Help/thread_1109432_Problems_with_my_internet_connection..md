---
title: "Problems with my internet connection."
date: 2009-03-28
forum: General Help
---

### Post by ConBon on 2009-03-28
I recently replaced vista with ubuntu, to keep my computer from crashing. Well it worked but my internet won't connect. I tried 'dhclient' but it won't work. It sees the router but it won't connect, and when it does want to connect it kicks itself off after about 5 mins. it did't do this on vista, but it was slow.could it be the wirless card in my laptop, or could it be ubuntu? After I installed Ubuntu it worked for the first 12 or so hours but after that.... nothing.

---

### Post by mikewhatever on 2009-03-28
Well, not all wireless cards are supported. Could you post the outputs of the following commands to help evaluate the situation.
sudo lshw -C network
ifconfig
iwconfig

---

