---
title: "X Forwarding"
date: 2011-07-19
forum: Desktop Environments
---

### Post by 133 on 2011-07-19
Hi Guys,

Is that possible to ssh to a box and launch a programme, say firefox, have the session disconnet when not using it and then you can reconnect to the same session again?
Its pretty much like using screen... Is that possible?

Thanks

133

---

### Post by enimeizoo on 2011-07-19
Have a look at "ssh -X" .
You might have to change a few settings on the server if you don't have the default settings.

---

### Post by 133 on 2011-07-19
ssh -X enable you to do the X forwarding, yes it will give me the programme on a local screen but once you kill that programme, you have to lauch a new programme.

What I like to do is to launch firefox remotely and then login to a website, disconnect it and then reconnect to the same session whenever I want.

Any clue?

---

