---
title: "[SOLVED] Will Compiz Fusion work on Gusty with ati x1200"
date: 2007-11-26
forum: Desktop Effects &amp; Customization
---

### Post by kendalw3 on 2007-11-26
Hello All,

I'm a linux noob and I just installed gusty as a dual boot with vista (new laptop came with vista and personally i think it sucks big time!!!) and I am trying to convert over to the light side and go solo linux but one must take baby steps first.  Anyway i have an ATI radeon x1200 card and i can't seem to get CompizFusion to work.... is it possible?  It seemed to work well on the live disk of Mandriva 2008 but perhaps that was just the mandriva desktop.  Any help would be great i think that Compiz Fusion effects look awesome and would like to partake in the all the coolness that linux has to offer!

Thanks in advance!

---

### Post by pieisgood4589 on 2007-11-26
You might want to download the drivers for the ATI x1200 card. That's what I did with my lappy, and Compiz works like a breeze! (Although I disabled it cuz it got annoying to see a spinning cube whenever I wanted to change workspaces!)

---

### Post by kendalw3 on 2007-11-26
which driver did you use and how did you set it up?  I've tried a few things but like i said i'm a big noob and need almost line by line instructions for things like this
 thanks again

---

### Post by erfahren on 2007-11-26
installing new versions of drivers get's a little involved, and not always with great results with the ATI drivers.

Have you enabled the restricted driver for your graphics card? It's not enabled by default.
Go to System > Administration > Restricted Drivers Manager and check it off and reboot. (the driver is called "fglrx" for future reference.)

Anyway, with that driver when you go to enable desktop effects (Visual Effects) - which is Compiz-Fusion - you'll be prompted to install XGL (xserver-xgl). Do that and restart X (Ctrl+Alt+Backspace) and they should work.

---

### Post by kendalw3 on 2007-11-26
when i try to change the visual effects from none to anything else i get a message saying that:

The Composite extension is not available

after that i am unable to close the window or if i click on ok nothing happens... i can still do other things but that window will not go away until i restart the computer

any ideas?

and yes i have enabled the restricted drivers

thanks

---

### Post by kendalw3 on 2007-11-26
i just got it to work.... that was amazingly simple.... i just used synaptic to download xserver and now it works just fine.... but is there an place where i can find a list of all the commands to make it do the different things??

thanks for the help

---

### Post by erfahren on 2007-11-26
hmm, strange you wasn't prompted to install XGL.

Anyway, install the compizconfig-settings-manager package. You can then configure it through the Advanced Desktop Effects Settings

note: you can mark this thread as "Solved" by going to the Thread Tools above the first post.

good luck

---

### Post by zigx on 2008-02-03
i also was not prompted to install xserver-xgl.

Can anyone shed light on how i log a bug or what logs/reports to include???   

i think this is important as many people would love to use compiz and may not know exactly  what to do!

---

### Post by Lackofabox on 2008-03-01
I was not prompted either.  But, this will run the install the xserver

    sudo aptitude install xserver-xgl

Then, make sure you restart X:  ctrl-alt-BACKSPACE

Depending on your graphics card, advanced desktop effects should work at that point.  This worked for me with a Radion X1200 on a Toshiba A215 laptop.

BTW, this command prints your video card:
     lspci | grep VGA

good luck!

---

