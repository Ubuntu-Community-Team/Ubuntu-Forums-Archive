---
title: "Installing XFCE and KDE and Gnome and Gnome 3 and Unity"
date: 2011-04-18
forum: Desktop Environments
---

### Post by erbey on 2011-04-18
Hi everyone, been using ubuntu for pretty much exactly a year (downloaded Lucid the day it came out and never looked back) but now i'm getting unsure of what Desktop Environment i want to use...i've always felt really comfortable with gnome, but i don't know if i like the look of unity or even gnome 3 (not having played with them BTW). So the plan is to download and install 11.04 the day it comes out and install it on my spare laptop, this will have unity and classic gnome on it already but i would like to add XFCE KDE, Gnome 3 and maby even others to see what suits me best. I would also like to be able to choose the DE at the log in screen every time i start up.

spare computer is a pretty old dell inspiron 6000 1.5gb RAM 60Gb HDD about 1.5Ghz CPU, i dont know if the system will even be able too handle it? but with no media or anything there should be enough hard drive space.

as i understand it i should just be able to put in a terminal:

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell

and that should get me gnome shell

sudo apt-get install kubuntu-desktop

should get KDE but will remove any of the other desktop environments?

sudo apt-get install xfce4

should get me XFCE and i know it may require some other stuff like: xfwm4 xfce4-panel xfdesktop thunar xfce4-session xfce4-settings xfce4-appfinder xfce-utils xfconf xfce4-goodies

Also one more question, I'm going to give them all a good try for about a week or so especially unity but if for some reason i don't like any but gnome classic, will i still be able to modify future releases of Ubuntu to use gnome classic?

Anyway a lot of questions but any advice would be appreciated. If anyone sees any problems with what i'm trying to do please let me know, because i don't want to get to installing the last DE and it wipes all the others off.any questions i'm always near my computer studying for exams atm so ill get back pretty soon, any other DE's i should consider? any tips or pointers? i have a feeling i wont be the only one trying this idea because its quite confusing to pick a desktop.

---

### Post by 3Miro on 2011-04-18
With kubuntu-desktop and xfce4 (or xubuntu-desktop, xfce4 gets you everything that you need, except the goodies package), you can have Gnome2 (Unity and Classic), KDE and XFCE living together. I am not sure about the right Gnome3 repository and how that may affect your system (i.e. I don't know if Gnome2 and Gnome3 would live together).

In all cases, prepare to spend some time with the new DE and they play around with it. Nothing will work "out of the box" for you, you will have to do some adjustments (panels, shortcuts, transparency ... )

---

### Post by erbey on 2011-04-18
> **3Miro said:**
> With kubuntu-desktop and xfce4 (or xubuntu-desktop, xfce4 gets you everything that you need, except the goodies package), you can have Gnome2 (Unity and Classic), KDE and XFCE living together. I am not sure about the right Gnome3 repository and how that may affect your system (i.e. I don't know if Gnome2 and Gnome3 would live together).

In all cases, prepare to spend some time with the new DE and they play around with it. Nothing will work "out of the box" for you, you will have to do some adjustments (panels, shortcuts, transparency ... )

Hmmmm, good point 3Miro, didn't consider if gnome 2 and gnome 3 would conflict...I might try all the others first and add gnome 3 last or even considering making another partition for Gnome 3.

I understand where your coming from with "nothing will work out of the box", especially since my desktop is a bit different from a "classic" gnome 2... for example i don't have any panels just an AWN dock with everything on it i usually use. I plan to set up each desktop to my liking one after the other and see which one i prefer overall.

Thanks for the advice, when i start setting it all up probably on friday after my exam ill give some feedback on any problems etc...

---

### Post by Copper Bezel on 2011-04-18
Right, Gnome 3 will break Gnome 2, which in turn breaks Unity. You have to decide between the two.

The equivalent to XFCE-as-opposed-to-Xubuntu for Kubuntu is the meta-package kde-standard. I haven't done much with KDE or XFCE, but from what I've seen, you're better off just installing the DES without the Ubuntu branding.

---

### Post by erbey on 2011-04-18
> **Copper Bezel said:**
> Right, Gnome 3 will break Gnome 2, which in turn breaks Unity. You have to decide between the two.

The equivalent to XFCE-as-opposed-to-Xubuntu for Kubuntu is the meta-package kde-standard. I haven't done much with KDE or XFCE, but from what I've seen, you're better off just installing the DES without the Ubuntu branding.

Ok thanks for that info...Ill install kde-standard, without the ubuntu branding, because i was wondering if kubuntu-desktop may delete gnome.
I'll try gnome 3 in another partition with either the fedora-gnome3 iso thats on the gnome website or lucid with gnome 3 installed.

I think im pretty much ready to go then...just need to get these exams out of the way...

---

### Post by stealth. on 2011-04-18
> **Copper Bezel said:**
> Right, Gnome 3 will break Gnome 2, which in turn breaks Unity. You have to decide between the two.

The equivalent to XFCE-as-opposed-to-Xubuntu for Kubuntu is the meta-package kde-standard. I haven't done much with KDE or XFCE, but from what I've seen, you're better off just installing the DES without the Ubuntu branding.


That is pretty much exactly what I did, its not fun. 

](*,)

---

### Post by sanderd17 on 2011-04-18
> **Copper Bezel said:**
> Right, Gnome 3 will break Gnome 2, which in turn breaks Unity. You have to decide between the two.

Hmmm, are you sure? I'm working on gnome-shell now (when I log in, I have to check gnome 3) and I think I installed it via the package manager. The settings are in /usr/share/gnome-shell/... and I still can use gnome 2.

@OP: you can always compile gnome3 yourself with jhbuild. That will certainly not break your system (you don't compile it as root, so it has no rights to affect your gnome installation) but maybe you get a compilation error that you can't resolve.

PS. You forgot LXDE, that's a very fast and light DE. The related *buntu is Lubuntu.

---

### Post by 3Miro on 2011-04-18
> **erbey said:**
> Ok thanks for that info...Ill install kde-standard, without the ubuntu branding, because i was wondering if kubuntu-desktop may delete gnome.


No it will not. Kubuntu-desktop only adds KDE, it will not delete Gnome. Same for xubuntu-desktop.

the DE versions will make a lot of changes to your system (like the splash screen), the standard xfce4 and kde-standard will have a much smaller effect, so those may be a better option.

---

### Post by 3Miro on 2011-04-18
> **sanderd17 said:**
> Hmmm, are you sure? I'm working on gnome-shell now (when I log in, I have to check gnome 3) and I think I installed it via the package manager. The settings are in /usr/share/gnome-shell/... and I still can use gnome 2.

@OP: you can always compile gnome3 yourself with jhbuild. That will certainly not break your system (you don't compile it as root, so it has no rights to affect your gnome installation) but maybe you get a compilation error that you can't resolve.

PS. You forgot LXDE, that's a very fast and light DE. The related *buntu is Lubuntu.

Gnome-shell is not Gnome 3. Gnome-shell is only the top part of Gnome 3. GS does work on Gnome2, but Gnome 3 conflicts with Gnome 2.

Gnome 3 comes with a whole lot of new and different stuff "under-the-hood". Gnome3 will dramatically change the content of .gnome settings (I think), so Gnome3 and Gnome2 don't live together.

---

### Post by sanderd17 on 2011-04-18
> **3Miro said:**
> Gnome-shell is not Gnome 3. Gnome-shell is only the top part of Gnome 3. GS does work on Gnome2, but Gnome 3 conflicts with Gnome 2.

Gnome 3 comes with a whole lot of new and different stuff "under-the-hood". Gnome3 will dramatically change the content of .gnome settings (I think), so Gnome3 and Gnome2 don't live together.

thanks to clear that up.

---

### Post by erbey on 2011-04-18
@sanderd17
Ok ill try LXDE aswell. but compiling it sounds complicated especially just to test it...but maby not as complicated as installing it in a seperate partition?

@3miro
seeing as im really just testing the UI, would it be easier to install gnome-shell on top of gnome 2 rather than gnome 3 or is user experience between gnome 2 with gnome shell very different from gnome 3 with gnome shell.

and also would gnome-shell conflict with unity if they were both  using the same gnome 2 base(as long as not at the same time maby not?). 

i hope thats not too confusing :s

thanks for all the help its greatly appreciated.

---

### Post by 3Miro on 2011-04-18
> **erbey said:**
> @
@3miro
seeing as im really just testing the UI, would it be easier to install gnome-shell on top of gnome 2 rather than gnome 3 or is user experience between gnome 2 with gnome shell very different from gnome 3 with gnome shell.


Gnome-shell on top of Gnome2 will run, however, it may be slower and you may experience more bugs. However, the UI is essentially the same, just keep the above in mind when assessing speed and stability.

---

### Post by erbey on 2011-04-18
> **3Miro said:**
> Gnome-shell on top of Gnome2 will run, however, it may be slower and you may experience more bugs. However, the UI is essentially the same, just keep the above in mind when assessing speed and stability.

ok thanks for that, i think ill just install gnome-shell over gnome 2 just to test it out.

so all ill need to enter into a terminal is:

sudo apt-get install xfce4 kde-standard gnome-shell lxde

and then have about 5 weeks worth of testing each one. its going to be interesting.

---

