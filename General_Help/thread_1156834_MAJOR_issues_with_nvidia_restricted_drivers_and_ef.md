---
title: "MAJOR issues with nvidia restricted drivers and effects"
date: 2009-05-12
forum: General Help
---

### Post by adamspurgin on 2009-05-12
so, i recently got ubuntu up and running. i tried activating the effects and it prompted me to download the restricted drivers for my card (8400m) in a dell laptop. it let me know it needed to restart and i did.

it was fine up until the splash screen goes away, then it is replaced by a mostly grey screen that slowly turns into a white screen with a black bar going down the middle. i can still log in, but i can't see a thing. any way i can fix this without doing a system restore?

and if it does come down to a system restore, is there any way i can get the effects without having this critical driver error?

oh, i'm running hardy by the way.

---

### Post by adamspurgin on 2009-05-12
bump

---

### Post by Tipped OuT on 2009-05-12
Try setting you Xorg file back to default settings.

Type in terminal: **sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf **

---

### Post by adamspurgin on 2009-05-12
> **Tipped OuT said:**
> Try setting you Xorg file back to default settings.

Type in terminal: **nano /etc/X11/xorg.conf**

is there a way to open the terminal via a keyboard shortcut? i can't exactly do much clicking right now.

---

### Post by chriskin on 2009-05-12
can't see why people install hardy even a year after it got released - especially since most of its bugs are solved by now

anyway, not my job to criticize :)

as for the real problem now
it happened to me as well once when i started effects before installing the drivers 

now, what Can you see or do? anything that can help us help you

---

### Post by Tipped OuT on 2009-05-12
**CTRL + ALT + F1** I believe it is.

---

### Post by jowilkin on 2009-05-12
You should be able to get to a terminal with Control-Alt F1.  However the command posted above will only open the xorg.conf file for editing, it won't revert it back to old settings.

Can't remember how to do that off the top of my head, but I think the new xorg should work with no xorg.conf file.  So you could try renaming xorg.conf to xorg.conf.bk and then restarting X.

Edit: if you are on Hardy then xorg will be older and may not work with no xorg.conf file, it can't get you to a worse state than you are already in however.

---

### Post by zeex on 2009-05-12
> **adamspurgin said:**
> so, i recently got ubuntu up and running. i tried activating the effects and it prompted me to download the restricted drivers for my card (8400m) in a dell laptop. it let me know it needed to restart and i did.

it was fine up until the splash screen goes away, then it is replaced by a mostly grey screen that slowly turns into a white screen with a black bar going down the middle. i can still log in, but i can't see a thing. any way i can fix this without doing a system restore?

and if it does come down to a system restore, is there any way i can get the effects without having this critical driver error?

oh, i'm running hardy by the way.

Hi, 

Boot into single user mode try XFIX option. In the single user mode remove any nvidia drivers you 've installed. Now your system should boot normally without nvidia drivers. 

Take a look at [this link]("http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/"). It uses Dell Laptop with Nvidia card 8400M in Ubuntu Hardy. It's the same configuration you 've. Follow the instructions it should help.

---

### Post by Tipped OuT on 2009-05-12
> **jowilkin said:**
> You should be able to get to a terminal with Control-Alt F1.  However the command posted above will only open the xorg.conf file for editing, it won't revert it back to old settings.

Can't remember how to do that off the top of my head, but I think the new xorg should work with no xorg.conf file.  So you could try renaming xorg.conf to xorg.conf.bk and then restarting X.

Edit: if you are on Hardy then xorg will be older and may not work with no xorg.conf file.

I edited the command, check again.** sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf **

---

### Post by chriskin on 2009-05-12
isn't the problem just with effects on? compiz i mean? 

i would say that i good idea would be to 
1)alt+F2
2)write metacity --replace
then you would have your desktop back, and can reinstall the drivers and all would work ok 


am i too unreasonable? i haven't tried it but it seems easier than those mentioned above. hm...

---

### Post by adamspurgin on 2009-05-12
> **chriskin said:**
> 

now, what Can you see or do? anything that can help us help you

i can see a mostly white screen with a black vertical bar going through it, judging by the sounds, the OS is still running, i just can't see a thing 

> **jowilkin said:**
> You should be able to get to a terminal with Control-Alt F1.  However the command posted above will only open the xorg.conf file for editing, it won't revert it back to old settings.

Can't remember how to do that off the top of my head, but I think the new xorg should work with no xorg.conf file.  So you could try renaming xorg.conf to xorg.conf.bk and then restarting X.

Edit: if you are on Hardy then xorg will be older and may not work with no xorg.conf file.

sorry, but i'm a bit of a newb here, i'm not sure what you mean by "X" or how to rename a file.

---

### Post by Tipped OuT on 2009-05-12
Restart "X", basically, restart your computer.

---

### Post by chriskin on 2009-05-12
> **Tipped OuT said:**
> ..

[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

---

### Post by chriskin on 2009-05-12
> **Tipped OuT said:**
> Restart "X", basically, restart your computer.

read the link on wikipedia above, what you are saying is kind of...strange :)

---

### Post by Tipped OuT on 2009-05-12
To make it simpler for him, just restart his computer, then everything gets restarted, see where my logic is getting at? lol :P 

I hope I'm not sounding like an idiot right now, its 3:05 AM, no sleep.


EDIT: Eh, I'm going to bed now, I need some sleep, continue to help him for me please.

---

### Post by nothingspecial on 2009-05-12
To come at this from a completely different angle.

In your other thread you say you have a big paper due tomorrow and I take it it`s on your Ubuntu box?

You obviously have another computer you`re posting on. 

Is the most pressing issue getting the paper off your Ubuntu box?

If so and you have a pen drive or cd or these computers are on the same network this can be achieved.

---

### Post by adamspurgin on 2009-05-12
> **zeex said:**
> Hi, 

Boot into single user mode try XFIX option. In the single user mode remove any nvidia drivers you 've installed. Now your system should boot normally without nvidia drivers. 

Take a look at [this link]("http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/"). It uses Dell Laptop with Nvidia card 8400M in Ubuntu Hardy. It's the same configuration you 've. Follow the instructions it should help.


ah! that did it! thank you so much. now that i got my UI back up i can finish my paper, and follow the instructions on that link tomorrow. :D:D:D:D:D:D:D:D

thanks to the rest of you as well, this one incident taught me a lot about ubuntu.

---

### Post by adamspurgin on 2009-05-12
> **nothingspecial said:**
> 

You obviously have another computer you`re posting on. 





well, i'm actually posting from a friend's iphone, and typing it all out on a mini-keyboard doesn't sound too appealing at the moment

---

### Post by djuke04 on 2009-05-12
When you install the drivers, try using EnvyNG (get from add//remove software).

I had problems with an Nvidia graphics driver and a bunch of people told me to try that because it's different than just using the hardware drivers manager.

---

