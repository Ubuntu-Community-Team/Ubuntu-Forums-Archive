---
title: "Windows maximise themselves, won't move, don't have full titlebar"
date: 2008-12-18
forum: General Help
---

### Post by d-d-d-d-d-d-card on 2008-12-18
I was having problems with Nautilus, so I reinstalled it and gnome..

Only problem is now all my windows maximise themselves on open, which is annoying, I cannot click and drag windows as I could when I first started using ubuntu, and the icons part of the titlebar of each window, where you would usually see the 'x' button and the maximising and minimising buttons is gone.

I've been tweaking ubuntu to my own version of perfection so I can ditch Vista, but this is really annoying me...really really annoying me.

I've heard a few theories about it I thought I'd get an opinion on this board, can anybody offer a guess to whats going on or how to resolve it?

Thanks, D

---

### Post by Izek on 2008-12-18
Are you running compiz?

Have you tried running

metacity --replace

in terminal?

What's your graphics card?

---

### Post by d-d-d-d-d-d-card on 2008-12-18
I'm going to sound like a total idiot here.. but I don't know what My graphics card is... it's a new laptop, Compaq presario that I've had for a few months and is certainly quite up to date so I wouldnt think the card would be too bad.

I am running Compiz though

---

### Post by Izek on 2008-12-18
Install emerald in terminal:

sudo apt-get install emerald

after that, do emerald --replace in terminal.

---

### Post by drs305 on 2008-12-18
It hasn't affected me so I haven't paid close attention, but I think this is one of the bugs that is overcome by hitting F11 twice to restore the window's min/max buttons. You can then adjust the size of the window and close it out. When you restore it I believe it will work again.

---

### Post by d-d-d-d-d-d-card on 2008-12-18
Does installing emerald mean I should get rid of compiz? if so , how?

---

### Post by Izek on 2008-12-18
> **d-d-d-d-d-d-card said:**
> Does installing emerald mean I should get rid of compiz? if so , how?

emerald and compiz work together actually.

---

### Post by Johnkozz on 2008-12-19
i am experiencing almost the same problems, some pre-sized window boxes. I am going to use Evolution Mail as an example, when i click to the icon to run, and the window opens it reads '...click next'. If i wanted to click next its impossible since the box for 'next' is not on the screen; i have the resolution set at 800x600. All thoughts and ideas on how to correct this are welcome.

---

### Post by d-d-d-d-d-d-card on 2008-12-19
As an update, I've started noticing that the maximise, minimise and exit buttons do appear when windows first open, but only for a second, before they disappear and the window maximises.

I've read somewhere that this could be down to a troublesome proccess running, such as devilspie.

Does this sound right to anyone? Or does anyone think maybe Compiz might be causing this?

---

### Post by d-d-d-d-d-d-card on 2008-12-19
Problem solved.... for anyone reading this with the same problem its all down to a crafty process called DevilsPie....

Going to SYstem, Preferences, and then Sessions should allow you to remove it from startup.

It says in the description that it removes window decoration and forces maximumisation (sp?) of screens.. wish I knew that before I spent all day yesterday trying to fix it.

---

