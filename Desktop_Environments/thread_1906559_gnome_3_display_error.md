---
title: "gnome 3 display error"
date: 2012-01-09
forum: Desktop Environments
---

### Post by satyapramodh on 2012-01-09
i recently installed gnome3.. it worked well on the first run but after that the top toolbar is replaced by a bar with multipixilated colors like this ["click here"]("http://www.freeimageslive.co.uk/files/images003/multipexles.jpg") .
over this i am able to identify broken text.. ie.. say i am on firefox.. it says F r f x W b Br w   r(boxes in between the spaces with colors)..
i tried to take a screenshot to show you guys exactly what my problem is but when i take a snapshot it is only showing me my wallpaper and nothing else.. btw my Ubuntu untiy desktop is working fine..
i also tried _re-installing_(i dont know how to completely remove gnome 3 files and download n install them again) gnome 3 a few times..

---

### Post by jerrrys on 2012-01-11
Gnome3 is part of the default install.  Unity and gnome-shell are built on gnome3.  Im guessing that its g-Shell your talking about and you need to shut down compiz.  G-shell will not run under compiz and needs to be stopped.  On the other side you have Unity 3d which will not run without compiz, and I suspect thats why unity works and gnome will not.  So fire up that multi colored screen of yours and...

Press **Ctrl Alt F6**  that should give you a readable terminal (tty) and enter:

killall compiz

Then press **Ctrl Alt F7  **this will return you to your desktop and hopefully a usable desktop.

Option #2 - remove compiz in terminal:

sudo apt-get remove compiz

This will also remove Unity 3d and replace it with Unity 2d and both will now work.

If not happy with this setup you can reinstall compiz.

---

### Post by satyapramodh on 2012-01-14
i have tried both the options you mentioned sir.. but no use.. its still the same..

---

### Post by BlinkinCat on 2012-01-14
Are you referring to Gnome Shell? and if so what is your graphics card?

---

### Post by Adam.Pixelite on 2012-02-16
Yeah; I'm having the same issues sadly, despite having uninstalled Compiz.. Sorry to bump this oldish thread but it saves creating a new one unless nobody replies.. The least I can do is try and display a picture taken of the display seeing as though I also have the screenshot error.. Any help would be appreciated and thanks in advance :)

---

### Post by 23dornot23d on 2012-02-16
What graphics card do you have ....  and will the system boot into safe graphics mode  ....

---

### Post by Adam.Pixelite on 2012-02-16
Running 1gb ATI Radeon HD 4800, I'll try the safe graphics mode in the meantime..

*Edit* Safe graphics mode works~

---

### Post by 23dornot23d on 2012-02-16
ATI Graphics are not my topic - I always stick with Nvidia ....

but I did a quick search ... nothing is jumping out and saying this is a definite fix

[https://www.google.com/search?client=ubuntu&channel=fs&q=Radeon+HD+Radeon+HD+4800&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&channel=fs&sclient=psy-ab&q=ubuntu+HD+4800+solved+11.10&pbx=1&oq=ubuntu+HD+4800+solved+11.10&aq=f&aqi=&aql=&gs_sm=3&gs_upl=34616l38847l5l39377l9l6l3l0l0l0l207l695l0.4.1l9l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75&biw=976&bih=499](https://www.google.com/search?client=ubuntu&channel=fs&q=Radeon+HD+Radeon+HD+4800&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&channel=fs&sclient=psy-ab&q=ubuntu+HD+4800+solved+11.10&pbx=1&oq=ubuntu+HD+4800+solved+11.10&aq=f&aqi=&aql=&gs_sm=3&gs_upl=34616l38847l5l39377l9l6l3l0l0l0l207l695l0.4.1l9l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75&biw=976&bih=499)

and I do know with Gnome-Shell in particular there were some display problems

you may be better waiting for a reply from a ATI person ... with a similar card ....

but at least you can get in now and install drivers etc .... there may be some later ones

for ATI on there website or in the repos ..... additional hardware may give you some

options .... thats the best I can do at the moment .....

---

### Post by Adam.Pixelite on 2012-02-16
Ahh it's alright ^-^' Thanks for replying anyway, so far I've managed to get the application bar to stop being pixelated and there's no blocks between the text (Just gaps without any odd colours) so I'd say the text is the only thing left to fix.. Hopefully shouldn't be too hard :)

---

### Post by 23dornot23d on 2012-02-16
Ok .... I did a quick search for later drivers ... 

[https://www.google.com/search?client=ubuntu&channel=fs&q=Radeon+HD+4800+drivers&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=VeZ&channel=fs&sclient=psy-ab&q=Radeon+HD+4800+drivers+linux+2012&pbx=1&oq=Radeon+HD+4800+drivers+linux+2012&aq=f&aqi=&aql=&gs_sm=3&gs_upl=8286l11336l1l12032l9l8l1l0l0l0l448l1489l0.5.0.1.1l9l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75&biw=976&bih=499](https://www.google.com/search?client=ubuntu&channel=fs&q=Radeon+HD+4800+drivers&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=VeZ&channel=fs&sclient=psy-ab&q=Radeon+HD+4800+drivers+linux+2012&pbx=1&oq=Radeon+HD+4800+drivers+linux+2012&aq=f&aqi=&aql=&gs_sm=3&gs_upl=8286l11336l1l12032l9l8l1l0l0l0l448l1489l0.5.0.1.1l9l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75&biw=976&bih=499)

but without trying them or knowing someone has had a success ..... its hard to say whether they will make the situation better or worse .... 

Sometimes updated drivers are the solution .... also xorg edgers are sometimes good ... for things
there is a ppa ..... for them .... but as I say my main dealings are with Nvidia but I did a search
for ATI 4800

[https://www.google.com/search?client=ubuntu&channel=fs&q=Radeon+HD+4800+drivers+xorg+edgers&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=Radeon+HD+4800+drivers+xorg+edgers&ie=utf-8&oe=utf-8)

ok best of luck and hope something is of use here ....  if not another user may have a solution

---

