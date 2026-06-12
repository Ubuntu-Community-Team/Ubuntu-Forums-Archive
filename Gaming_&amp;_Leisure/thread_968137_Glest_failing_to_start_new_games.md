---
title: "Glest failing to start new games"
date: 2008-11-02
forum: Gaming &amp; Leisure
---

### Post by Jagash on 2008-11-02
Hi there, been using Ubuntu since feisty and just upgraded to Ibex which I have heard finally uses my shiny new video card.  Asus GeForce 9600  video card and using Nvidia driver version 177:80

Anyways, prior to both the hardware upgrade and the Ibex upgrade, I had been able to play Glest.  Now it permits me to get to the menu but does nothing when I click on any of start game options.  I can choose the scenario for example, but the start game button clicks and does nothing.  

Anyone run into this problem and/or have a solution?:confused:

---

### Post by xethm55 on 2008-11-15
I am having the same problem. Running from the terminal results in 
```

Couldn't process event: Error accessing value: FogOfWar in: glest.ini
Value not found in propertyMap: FogOfWar, loaded from: glest.ini

```

I then added FogOfWar to the glest.ini file and it worked just fine.
```

gedit ~/.glest/glest.ini

```
Then put 
```

FogOfWar=1

```
on it's own line anywhere in the file (I placed it right above "FogOfWarSmoothing=1" on line 19)

The game should work fine now.

---

### Post by darkazurka on 2008-11-23
Thanks! It worked for me. Before I had the same error as you 2 people.

(I checked also in terminal, and by copying part of the error message I got, I found this thread. Thanks for you people also who recommend running in terminal mode, for more clues! :) )

---

### Post by EdSquareCat on 2009-03-16
Thanks, this worked for me too. What causes this?

---

