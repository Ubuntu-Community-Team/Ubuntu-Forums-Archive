---
title: "[SOLVED] Problem with graphics I guess? Text displays funny. Help?"
date: 2012-11-01
forum: Desktop Environments
---

### Post by CWIDE on 2012-11-01
EDIT: The problem has been fixed. Thank you all who helped. I installed nvidia-current and that fixed it.

Hello everyone I've been wanting to switch to Xubuntu for awhile now but everytime I try I keep getting this bug and I decided I would finally ask for some help. Below I have posted 2 pictures displaying my problem. Over the text there is like a fuzzy bar I guess. I'm not quite sure how to describe it but I can to move my mouse over it for it to go away and It's quite annoying. Does anyone know how to fix this? 

Thank you in advance,

Picture 1:
[IMG]http://i.imgur.com/Qu2Rn.png[/IMG]

Picture 2:
[IMG]http://i.imgur.com/iml0g.png[/IMG]

EDIT: The problem has been fixed. Thank you all who helped.

---

### Post by vasa1 on 2012-11-01
Are both pictures of the Ubuntu Software Center?
Do you see this elsewhere?

---

### Post by CWIDE on 2012-11-01
Yes it happens everywhere. It happens in multiple programs and the actual Xfce menu when you right click or click the little mouse in the upper left hand corner.

EDIT: The problem has been fixed. Thank you all who helped.

---

### Post by Sparrow40k on 2012-11-01
I had this same problem when I first installed Ubuntu 12.10. I fixed it by going into additional drivers and going from:

"Using X.org X server - ..." (open source)
  To 
"Using NVIDIA binary Xorg driver kernel module and ..." (propriety, tested)

Obviously if you aren't using a NVIDIA card it wont be the one for you, but look for the "propriety, tested". Install and reset.

---

