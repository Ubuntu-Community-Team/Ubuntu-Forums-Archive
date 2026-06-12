---
title: "Gourmet Recipe Manager"
date: 2009-04-09
forum: General Help
---

### Post by tonyh6243 on 2009-04-09
I was looking for some specifics on installing Gourmet Recipe Manager. I downloaded the .tar file (version 0.13.8) and unpacked it on my desktop but do not know what to do from there or how to install it. Any help would be appreciated.

---

### Post by chriskin on 2009-04-09
> **tonyh6243 said:**
> I was looking for some specifics on installing Gourmet Recipe Manager. I downloaded the .tar file (version 0.13.8) and unpacked it on my desktop but do not know what to do from there or how to install it. Any help would be appreciated.


most probable way of installation would be in a terminal

./configure
make
sudo make install

try these commands, they work on almost all apps

---

### Post by chriskin on 2009-04-09
searched it and this is not the case

as written in the readme file
"As root, issue a python setup.py install."



gourmet is in the repositories as well, why don't you take it from there? easy one-click installation :)

---

### Post by Therion on 2009-04-09
Gourmet is a neat little app!  It's in Synaptic though, just use Add/Remove or install it from SPM.

---

### Post by tonyh6243 on 2009-04-09
Since I have not done this for other programs, can you provide me an example of what the commands are for a program? I should also not that I am running Hardy 32 bit.

---

### Post by chriskin on 2009-04-09
no command needed, open synaptic package manager and write "gourmet" at the search thingie

it should be there

i don't know for hardy, but intrepid and jaunty have it

---

### Post by N_Nick on 2009-04-09
If you mean installing from Synaptic head to System > Administration > Synaptic Package Manager and install it from there.  Synaptic takes care of everything - including any dependencies

---

### Post by chriskin on 2009-04-09
> **N_Nick said:**
> If you mean installing from Synaptic head to System > Administration > Synaptic Package Manager and install it from there.  Synaptic takes care of everything - including any dependencies


while the tarred package would need you to take care of the dependencies as well, a really boring and frustrating (some times) job :)

---

### Post by tonyh6243 on 2009-04-09
I did not see it in the package manager but I will check again.

---

### Post by N_Nick on 2009-04-09
> **tonyh6243 said:**
> I did not see it in the package manager but I will check again.

I can confirm its in the Interpid repos, named "gourmet".

---

### Post by Therion on 2009-04-09
> **chriskin said:**
> i don't know for hardy, but intrepid and jaunty have it
Hardy repos have it as well.  I went from Hardy straight to Jaunty and I've never had to install Gourmet from source to get it.  

I really *should* get more comfortable installing from source.  Synaptic has made me lazy...  Soft...  *Democratic.... <cough>






/*I kid, I kid!

---

### Post by tonyh6243 on 2009-04-09
Thank you for the responses. I will check the repos as soon as I get home from work.

---

### Post by chriskin on 2009-04-09
a strange thing happens while i try to install gourmet though, it asks me to remove exaile :O

i'll most probably install from source a later version than the on on synaptic

---

### Post by hfw on 2009-04-20
I've been running Gourmet on my two Intrepid boxes, but have not been able to get it working in my Jaunty 32 bit.  I installed it from the repos, and can not get it to launch.  Is anybody else having difficulties?

-hal

---

### Post by Peneus on 2009-04-30
I can get it to launch but cannot get it to import files I exported from previous versions.


> **hfw said:**
> I've been running Gourmet on my two Intrepid boxes, but have not been able to get it working in my Jaunty 32 bit.  I installed it from the repos, and can not get it to launch.  Is anybody else having difficulties?

-hal

---

### Post by gareththered on 2009-05-02
> **hfw said:**
> I've been running Gourmet on my two Intrepid boxes, but have not been able to get it working in my Jaunty 32 bit.  I installed it from the repos, and can not get it to launch.  Is anybody else having difficulties?

-hal

You need to run it with python 2.5 instead of version 2.6 supplied with Jaunty.

Either type ```
python2.5 /usr/bin/gourmet
``` to start it every time, or edit your menu entry with System->Preferences->Main Menu

---

### Post by tinge on 2009-08-03
Can someone help me clarify this?

> **gareththered said:**
> You need to run it with python 2.5 instead of version 2.6 supplied with Jaunty.

Either type ```
python2.5 /usr/bin/gourmet
``` to start it every time, or edit your menu entry with System->Preferences->Main Menu

I'm having the same problem (GRM wants to delete Exaile due to python 2.5 dependencies).  Can someone break this solution down a little more step-by-step? (ie where/how to install GRM without removing Exaile, where/how to install python 2.5 without removing 2.6.).  Unfortunately, the only thing I'm clear about is how to launch GRM once all this is already accomplished.

thanks in advance!

---

### Post by gareththered on 2009-08-03
A far better way to resolve this, as I found out, is to install the latest version of Gourmet.  It's not in the repositories, but if you download it from [the Gourmet Sourceforge site]("http://downloads.sourceforge.net/project/grecipe-manager/grecipe-manager-unstable/0.14.10/gourmet_0.14.10-1_all.deb?use_mirror=heanet") and install it (save the .deb file to e.g. your desktop then double-click it to install) then you will have the latest version, which works with Python 2.6 and has the export facilities fixed.

Hope this helps...

---

### Post by tinge on 2009-08-03
Thanks so much gareththered,

Worked like a charm. For simplicity's sake I try to stick the repos (or add new ones that meet my needs), but doing as you suggest seems to be the best option by far.

Cheers!

---

