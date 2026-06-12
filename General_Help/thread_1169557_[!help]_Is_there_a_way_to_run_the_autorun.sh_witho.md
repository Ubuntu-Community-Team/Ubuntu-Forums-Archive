---
title: "[!help] Is there a way to run the autorun.sh without the autorun prompt?"
date: 2009-05-25
forum: General Help
---

### Post by LunaLuan on 2009-05-25
Hello guys,here's my problem:
 
i wrote a small application and burned it into a removable device,and i also wrote a script named "autorun.sh" in order to autorun the application when insert the device to PC. but each time i insert the device it give me the autorun prompt first, and i have to confirm by clicking the "run" button before running my application.
 
is there a way to run the application automaticaly when insert the device without any prompt?
 
and pls notice that i wanna do that in not only one PC and linux distributions. 
 
i really need ur help...
Thanks a lot in advance!!!!!!!!!!!!!

---

### Post by mc4man on 2009-05-27
LunaLuan
I forgot to mention that if you insert something else (cd or flash drive) that has an autorun file and you **Don't** want it to run then hold down the shift button while inserting the media  and you'll get the prompt. (hold down till the prompt appears

Click cancel

---

### Post by LunaLuan on 2009-05-27
Thank u dear upstairs! i tried,it's interesting.:)
 
but since u're so nice can i ask one more question?
 
what if i want do this (run the autorun application without autorun prompt) only for my device,i mean when inserted other device,i'd like the PC work as usual,u know,give the autorun prompt.
 
i tried rename the "autorun.sh" to "autorun.a" or something else, but then the computer can not recogise it as a autorun application, is it should only be named "autorun.sh"?
 
in the mimeapps.list,i add "x-content/software=auto.desktop;nautilus-autorun-software.desktop",it worked,then i tried to add only the first half,that is "x-content/software=auto.desktop;",it still worked,that means i needn't specify the autorun application's name which really puzzled me,can u tell me why?:(
 
 
Thanks a lot!!!

---

### Post by LunaLuan on 2009-05-27
ah,i know the "auto.desktop" and "nautilus-autorun-software.desktop" thing,they are the first choice and the second
 
but my puzzle is that i haven't specify my autorun application's name, what does "x-content" mean,does it valid for all autorun applications????

---

