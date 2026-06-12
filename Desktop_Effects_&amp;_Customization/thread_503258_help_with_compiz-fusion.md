---
title: "help with compiz-fusion"
date: 2007-07-17
forum: Desktop Effects &amp; Customization
---

### Post by ITdrummer on 2007-07-17
Hey everyone.  

Ive been looking at different desktop customization options and i think ive decided on compiz-fusion.  Can anyone tell me what i should do to get started?
I found a "step-by-step" guide here in the forums for installing it but it was no help.  The instructions were vague and didnt go into much detail.  \

Has anyone found a decent walkthrough on how to install compiz-fusion?

ps. is 768 MB ram enough to run compiz-fusion?

thanks in advance.

---

### Post by skymera on 2007-07-17
im not sure on the RAM. sure its plenty.
the Graphics Card is the main component.

i cant run it, since mines so poop

---

### Post by ITdrummer on 2007-07-17
well i think i have 64 MB of ram.  Is this enough?

Im running a P4 - 2.2 ghz  also

---

### Post by mikewhatever on 2007-07-17
This guide looks straight forward [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)
Ask if you have questions.

---

### Post by ITdrummer on 2007-07-17
before i get started, lets say i go through all of those steps.....and i decide that compiz-fusion is not right for me....it looks extremely complicated to install....what would i have to do to uninstall?

i just dont want to get into a situation where i spent a lot of time in the terminal, downloading and installing several packages, and then if it doesnt work.....being stuck with a bunch of crap that thoroughly screwed my computer up.

---

### Post by rickycodie on 2007-07-17
the uninstall is a little difficult, in addition to the sudo you need to remove the repositories before you do anything else, like beryl. and i don't think 64mb is enough to even run the desktop effects from just compiz.

edit: i'm confused, your sig line says 768 mb of ram, which is plenty, but you 64, which is not.

---

### Post by mikewhatever on 2007-07-17
If that looks complicated, do not go for it. If you must, make sure to read the guide several time. Now, to your question, the following command installs the specified packages > sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
Substituting remove for apt-get and issuing it again will remove the packages installed.
You can also always reinstall Ubuntu and get back to where you'd started.

---

### Post by ITdrummer on 2007-07-17
I apologize, 64MB VIDEO memory, 768MB SYSTEM memory

---

### Post by Deco_21 on 2007-07-17
You should try to unninstal compiz from Synaptics 
System > Adm > Synaptics 
Firts plugins , and the last thing the core.

---

### Post by Deco_21 on 2007-07-17
> **ITdrummer said:**
> well i think i have 64 MB of ram.  Is this enough?

Im running a P4 - 2.2 ghz  also


You will have a compiz fusion session too slow , but it should works.

---

### Post by ITdrummer on 2007-07-18
> **Deco_21 said:**
> You should try to unninstal compiz from Synaptics 
System > Adm > Synaptics 
Firts plugins , and the last thing the core.

So what your saying is that i should remove the part of compiz that comes with the package manager before i manually install compiz-fusion?

---

### Post by Vorian on 2007-07-18
If you want to install compiz fusion, you will need to follow each step of the how-to you choose to follow.

The first step is removing Compiz, which comes default in feisty.  If you are concerned about the install, then wait until October when Gutsy comes out.  Compiz Fusion will be available in Gutsy.

---

### Post by SlCKB0Y on 2007-07-18
> **Deco_21 said:**
> You should try to unninstal compiz from Synaptics 
System > Adm > Synaptics 
Firts plugins , and the last thing the core.

Why not just remove the core? you'd think it would remove the rest.

---

### Post by ITdrummer on 2007-07-18
> **Vorian said:**
> If you want to install compiz fusion, you will need to follow each step of the how-to you choose to follow.

The first step is removing Compiz, which comes default in feisty.  If you are concerned about the install, then wait until October when Gutsy comes out.  Compiz Fusion will be available in Gutsy.

I think thats what im going to do.  By then i might also have built my new computer with PLENTY of system memory and video memory!  I can wait...

---

### Post by jbradhurst on 2007-07-18
I just installed compiz fusion on my machine and it runs just fine.

Here is a website that I stumbled onto and used the instructions from it.

[http://osnovice.blogspot.com/2007/07/how-to-install-compiz-fusion.html](http://osnovice.blogspot.com/2007/07/how-to-install-compiz-fusion.html)

---

