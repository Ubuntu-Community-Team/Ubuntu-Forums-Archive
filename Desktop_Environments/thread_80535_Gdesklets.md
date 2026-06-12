---
title: "Gdesklets"
date: 2005-10-22
forum: Desktop Environments
---

### Post by microo on 2005-10-22
Can someone help me with this annoying thing.

I've intalled Gdesklets and download some email checker the side candy one and the gmail one.

But when i try to install them there is a message appearing:

The element image does not have the cursor property !

How can i fix that ?

Thanks for all the help i can get

---

### Post by aysiu on 2005-10-22
Ordinarily, I Google errors when I get them, but if that's really the error you get, [it's not looking good for you](http://www.google.com/search?hl=en&q=%22The+element+image+does+not+have+the+cursor+property%22&btnG=Google+Search).

---

### Post by microo on 2005-10-22
[QUOTE=aysiu]Ordinarily, I Google errors when I get them, but if that's really the error you get, [it's not looking good for you](http://www.google.com/search?hl=en&q=%22The+element+image+does+not+have+the+cursor+property%22&btnG=Google+Search).[/QUOTE]


I'm on Hoary and i can tell that everything is working fine except the problem above.

Maybe that it would have better to post my thing in the Hoary part of the forums ?

Waiting for help 

Thanks anyway Aysiu

---

### Post by aysiu on 2005-10-22
[QUOTE=microo]I'm on Hoary and i can tell that everything is working fine except the problem above.[/quote] I just wanted to let you know that if you don't get a response, it's not because people don't want to help you. Generally if an error is common, people have solutions for it, and if it's common, it shows up many times in a Google search.

> 
Maybe that it would have better to post my thing in the Hoary part of the forums ?

Waiting for help 

Thanks anyway Aysiu Maybe. It's always a good idea to post to the most appropriate forum. I've moved you there now.

---

### Post by bluebyt on 2005-10-22
I have the same problem, but unfortunately I don't know what to do either!

I now it is related to the mail desklet , because I remove it and I dont have the error message.

For now I running Gdesklets with the weather and disk info desklet and it work good.

For the email I use mail notification in Synaptic.

The forum seem to be close at [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/)
so it is hard to ask for help.

---

### Post by microo on 2005-10-22
I know there is an answer for this problem and i'm sure it will be resolved.

Thanks Aysiu and Bluebyt.


If it was only for me i would have only Ubuntu Hoary on my PC even if it needs some learning ...but we always have things to learn.

---

### Post by TristanMike on 2005-10-23
By chance, did you install gdesklets-data? I know that in Hoary, it breaks gdesklets...if by chance you did a ```
sudo apt-get remove --purge gdesklets-data
```will remove the problematic package, then try again. Do other things work? Are you sure that the "desklet" is compatible with your version of "gdesklets"? Just a few questions to get the noodle cooking :P

---

### Post by microo on 2005-10-23
[QUOTE=TristanMike]By chance, did you install gdesklets-data? I know that in Hoary, it breaks gdesklets...if by chance you did a ```
sudo apt-get remove --purge gdesklets-data
```will remove the problematic package, then try again. Do other things work? Are you sure that the "desklet" is compatible with your version of "gdesklets"? Just a few questions to get the noodle cooking :P[/QUOTE]

Thanks i will follow your advice anyway i have nothing to lose. But i'm sure that i did'nt install Gdesklets Data. I was searching for an email notifier like the Gmail one and the sidecandy notifier. 

So i'll give it a try 

Thanks

---

### Post by rlange on 2005-10-25
I did have gdesklets data installed and that pins my cpu at about 97% . It shows up in "top" command as python. Removing gdesklets data took away the pinned cpu but also most of the available desklets leaving me with a choice of 2 to install. So I guess desklets are out for me, however I do use the rss news feeder to keep up with what is going on in the forums.

---

### Post by TristanMike on 2005-10-25
[QUOTE=rlange]I did have gdesklets data installed and that pins my cpu at about 97% . It shows up in "top" command as python. Removing gdesklets data took away the pinned cpu but also most of the available desklets leaving me with a choice of 2 to install. So I guess desklets are out for me, however I do use the rss news feeder to keep up with what is going on in the forums.[/QUOTE]Not at all, just use the ones from the site. From what I understand, the "-data" was just a pack of desklets from the site that ended up not working. If you go to [here, the homepage,](http://gdesklets.gnomedesktop.org/) you should be able to install the gdesklets from there.

---

### Post by rlange on 2005-10-25
[QUOTE=TristanMike]Not at all, just use the ones from the site. From what I understand, the "-data" was just a pack of desklets from the site that ended up not working. If you go to [here, the homepage,](http://gdesklets.gnomedesktop.org/) you should be able to install the gdesklets from there.[/QUOTE]


Thanks I will give it a shot when I get home.

Here is a question. When I list desklets I have 4 or 5 listed even through none are running or at least I can't see them. If there is any way to kill these. "gdesklets slay" has no effect on the ones that are running when gdesklets is restarted. 
          Is there any way to kill the running desklets that start when it is launched again?

---

