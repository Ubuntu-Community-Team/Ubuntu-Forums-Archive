---
title: "Ubuntu or Gnome being the slow one?"
date: 2005-09-07
forum: Desktop Environments
---

### Post by aussieskin on 2005-09-07
Okay, I hope I have posted this in the right forum!

Pretty much everything is slow...all applications are slow to open up, Open office, Firefox, Thunderbird and pretty much all programs I use...I have a broadband connection but pages are taking a lot longer to load than they used to.

Now I have had a squizz through the forums here and notice a lot of people saying Gnome is the slow one...I am fairly new still to linux...so bear with me!

Is there things I can do to speed up my computer? I am getting a bit irritatied with it because it is heaps slower than what windows was...which is not good...

Any pointing in the right direction or advice would be hugely appreciated.

Thanks!

---

### Post by Perfect Storm on 2005-09-07
Hmmm...

1. Get the i686 kernel if you are using P4
2. Make sure that Nvidia/ATI driver is installed
3. Look for howto tweak Firefox
4. Look for howto tweak OpenOffice

---

### Post by lol on 2005-09-07
Open Office is slow to start, no matter what you do (compared to MS Office). ooqstart applet and prelink help to make things better, but not much.

Firefox is slow as well. There are howto on how to tweak it, but I would rather suggest to install and use Opera: IMH, it has a much better UI and is faster without having to spend hours trying to tweak it.

Gnome isn't specially slow, but it requires quite a lot of memory. If you don't have enough, you will make extensive use of the swap, which is going to slow down everything. With less than 512Mb of mem, you should consider using XFCE or another lightweight window manager...

If you have an overall performance problem, you may want to check that:
- you're using the correct kernel
- DMA is enabled for your drives
- you're using the correct video drivers
- no useless services are running
- and much more (you will find tons of tips on the subject, just search the forums)

Finally, you said you have the feeling that windows was faster. The question is which version? You cannot really compare the current Ubuntu with win95... On the other hand, if windows XP is really faster than your linux (again, don't try to compare with a fresh XP install, do it with a windows with all your apps installed and after a month of use...), you probably have something not correctly setup on your linux.

---

### Post by Perfect Storm on 2005-09-07
epiphany are also a good choice to fast browsing and are GTK supported (which means it got the looks after the gnome theme your are using)

sudo apt-get install epiphany-browser
sudo apt-get install epiphany-extensions

---

### Post by Hairy_Palms on 2005-09-07
opera is a lot faster browser for browsing, but epiphany is the fastest to startup ive found, also opera doesnt work with media player plugins 
ooqstart does help open office a lot, and openoffice2 loads faster i find  than 1.13 aswell
[http://ooqstart.sourceforge.net/](http://ooqstart.sourceforge.net/)

P.S. artificial intelligence i just saw your desktop screenshot and there was an nvidia X control panel, how do u get that up? i have the latest official drivers but i cant see that anywhere.
thx

---

### Post by Lord Illidan on 2005-09-07
Open Office is a real hog to startup.. it should be fixed...

However Gnome is in my opinion slower than KDE...though metacity is much slower than Enlightenment, once I installed the latter, I was "breezing" along..

---

### Post by John.Michael.Kane on 2005-09-07
Heres some others things you can try 

replace gnome with fluxbox or xfce4
replace openoffice with abiword
tweak firefox
and look into pre-linking
you can also remove programs and services you do not need..

hope that helps

---

### Post by Perfect Storm on 2005-09-07
[QUOTE=Hairy_Palms]
P.S. artificial intelligence i just saw your desktop screenshot and there was an nvidia X control panel, how do u get that up? i have the latest official drivers but i cant see that anywhere.
thx[/QUOTE]

sudo apt-get install nvidia-settings

To start it just write nvidia-settings in the terminal or make a shortcut :)

---

