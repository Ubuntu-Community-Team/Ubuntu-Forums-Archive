---
title: "Beryl works in gnome but not kde!"
date: 2006-12-13
forum: Desktop Environments
---

### Post by tmilam on 2006-12-13
I've been trying really hard to get beryl working in Kubuntu Edgy Eft. My drivers are all set up and I've followed instructions on setting up Beryl. However, I can only get beryl to work correctly in gnome. If I try it in kde I lose my window borders and am unable to resize/move my windows unless I switch back to kwin! :confused:

---

### Post by tmilam on 2006-12-14
**BUMP**

Nobody can help with this? I've been trying to solve this problem for a week. ](*,)

---

### Post by Jonathan2007 on 2006-12-14
Do you have Aquamarine installed? That is the KDE counterpart to Emerald. It will use your window decorations from Kwin. I think I had the problem your describing but I forget how I solved it. Eventually I did something and now it works great. Good luck and sorry I couldn't help more.

---

### Post by tmilam on 2006-12-14
Thanks for your reply! Yes, I have aquamarine installed. 

```
vitriol@solstice:~$ apt-cache policy aquamarine
aquamarine:
  Installed: 0.1.3~0beryl1
  Candidate: 0.1.3~0beryl1
  Version table:
 *** 0.1.3~0beryl1 0
        500 http://ubuntu.beryl-project.org edgy/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by Jonathan2007 on 2006-12-14
Have you told Beryl to use Aquamarine? I am pretty sure it defaults to Emerald. Sorry if this seems dumb I just want to make sure it isn't something obvious.

---

### Post by tmilam on 2006-12-14
How do I tell beryl to use aquamarine? 

```
aquamarine --replace
```

Like that? This didn't work for me :(

---

### Post by Jonathan2007 on 2006-12-14
I just opened mine to check and guess what... no window borders. I got them by right clicking on the Beryl icon in the taskbar and going to select window manager and then aquamarine. It then gave me my window borders. Hope it works.

---

### Post by tmilam on 2006-12-14
That's strange. I have aquamarine installed, but it's not an option! I have kwin, metacity, and beryl. 

:-k

---

### Post by Jonathan2007 on 2006-12-14
Dang it. I meant to say use Kwin instead of Aquamarine even though it really is using Aquamarine.

You should of tried that option. Haha :p

---

### Post by tmilam on 2006-12-14
ohhhh i understand. Yes, that is helpful and is what I've been doing when I try to use beryl and it robs me of window borders. Only problem is that if I'm using kwin I don't have all the nifty effects that go with beryl!

---

### Post by Jonathan2007 on 2006-12-14
Ahhhh. I see now what you mean. Sorry.

And as a side note. I am using someone's SVN Ubuntu dapper repository and today I just upgraded the packages after not having done that for a few weeks and now my effects don't seem to show. I have window borders using Kwin but no effects. I tried enabling some but they don't seem to work. At least some were working by default last time.

---

### Post by tmilam on 2006-12-14
Cool...I'll try using svn beryl because I've asked countless times on irc in #ubuntu-xgl and still have no idea why it works effortlessly in gnome but not kde. I even deleted my .kde directory!

---

### Post by tmilam on 2006-12-14
It works now! I removed .beryl* .emerald* and .kde* and now it works just fine :D

---

