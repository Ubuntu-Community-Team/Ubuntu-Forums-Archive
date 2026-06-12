---
title: "Another noob wants Beryl"
date: 2007-03-16
forum: Desktop Effects &amp; Customization
---

### Post by ajmannen on 2007-03-16
Hi, i have installed Beryl on my Ubuntu (egdy eft). I have the Emerald Theme maneger, Beryl manager and everything. But i can not use it, the themes are in emerald theme manegder and i try to dubbel/tripple click them and it wont help:confused: 
After installing beryl there have bin no changes to my computer/desktop look :(  
What should i do? 

And how do i play Windows media player based internett radio in ubuntu?

---

### Post by louis_nichols on 2007-03-16
Regarding beryl, did you try to start it from the system tray right-menu icon? That has an option "Select window manager" and there you must select beryl in order to activate it. If that doesn't work, try starting it from terminal and paste here the error you get. To start it in terminal, you type the command: ```
 killall metacity && beryl --replace 
``` In case this leaves your windows without borders, just type ```
metacity --replace
``` and that should be solved. As I said, after this you should post here the error from running beryl.

As for your second question, there are actually several alternatives, afaik. I use amarok-xine with libxine-extracodecs installed. Admittedly, I don't know if any of the streams I listen to are wma (I will be able to check when I get home), but I read around that it should work with wma also.

---

### Post by steveneddy on 2007-03-16
> **ajmannen said:**
> Hi, i have installed Beryl on my Ubuntu (egdy eft). I have the Emerald Theme maneger, Beryl manager and everything. But i can not use it, the themes are in emerald theme manegder and i try to dubbel/tripple click them and it wont help:confused: 
After installing beryl there have bin no changes to my computer/desktop look :(  
What should i do? 


Go to Applications ->System Tools and select Beryl Manager

This will put a small red emerald on the top Gnome bar. Right click the red emerald, go down the list to "Select Window Manager" and select Beryl.

A few seconds later you will the wobbly goodness of Beryl. 

Good Luck

---

