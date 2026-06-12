---
title: "Feisty - No composite extension"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by Madley on 2007-04-25
Hi all, 
today i've installed the drivers for my ATI x300 mobile, on my laptop running Ubuntu Feisty Fawn 7.04. All works fine.

Now i want to enable the desktop effects , but when I click on menu link for desktop effects, I get an error like these one:

[img]http://img142.imageshack.us/img142/3684/errorfc9.png[/img]

then I click OK and it exit...

In English I think the error says: No Composite extension (or something similar)...



Can anybody help me?

p.s. Before I enable the drivers for ATI card, desktop effects works...



Thanks All

---

### Post by |ferrari| on 2007-04-25
I got the exactly same problem. even if you enable composite on xorg.

# sudo gedit /etc/X11/xorg.conf

compiz won't work. Maybe proprietary drivers of ATI gives you direct rendering and 3D aceleration but disables compiz.

Waiting some another reply to solve this issue out

---

### Post by chameleonkid on 2007-04-25
Same Problem. Looking for a Solution

---

### Post by Madley on 2007-04-25
The only thing I find, is that if I enable the composite option in xorg.conf, then when I click on "Desktop Effects" i can see the dialog, but if I click on enable, it give me an error...

---

### Post by kbzona on 2007-04-25
for all the ones that are using  ATI cards you need to run Compiz FROM A XGL session

---

### Post by Madley on 2007-04-25
So, I must to install XGL? Can you tell me if there's an HowTo for this?

Or can I do it simply from Synaptic?

---

### Post by kbzona on 2007-04-25
Of course... there are billions of HowTo's  ...  just google :)
or just goto:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

but install only xgl , not beryl.. bcause that guide is for installing both beryl xgl

---

### Post by tanis143 on 2007-04-29
Ok, I too am having this same issue. I found this thread through google :)

I did the steps in the howto posted, but notta. I didn't get a sessions login when I rebooted, so something tells me I didn't do something right (well duh right?). I'm running Fiesty 7.04 with an ATI Radeon 9600XT and restricted driver turned on. I'm still getting the no composite extension msg. Any further help?

---

