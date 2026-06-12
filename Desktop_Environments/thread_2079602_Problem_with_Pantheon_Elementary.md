---
title: "Problem with Pantheon Elementary"
date: 2012-11-02
forum: Desktop Environments
---

### Post by eivhys on 2012-11-02
i Installed Pantheon Elementary OS on my laptop with ubuntu 12.04. suddenly when i tried switching back to the normal Unity theme i got the close button on the left side and the maximize button on the right side, and i do not know where the minimize button went. 

Is there any way to completely remove it from my system? 

Thx in advance :)

---

### Post by nightfellas on 2012-11-03
I have the same problem as yours and I solve it :) thank god

I have a solution and it might works for your case

open **dconf editor**

and go to :
org -> gnome -> desktop -> wm -> preferences

search for **button-layout**

I assume that your button-layout value is ":minimize,maximize,close"

change it into(without quote):
"close,maximize,minimize:"


have a try :)

---

