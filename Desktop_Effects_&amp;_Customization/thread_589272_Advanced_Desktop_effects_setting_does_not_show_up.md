---
title: "Advanced Desktop effects setting does not show up"
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by cnfnr9 on 2007-10-24
I have had major problems with installing and setting up compiz.  I have tried entering sudo apt-get install compizconfig-settings-manager in the terminal but nothing happens and the Advanced desktop effects tab in pref. is not there. Can anyone help me please.

---

### Post by realvz on 2007-10-24
can you try 
alt+f2
and type
ccsm

if this doesnt work...how did you install compiz/...are you doing it from the official repos or are you using any other repository?

---

### Post by Maestro23 on 2007-10-24
Are you running Feisty of Gutsy?

---

### Post by Rabindranath on 2007-10-24
Try installing via "Add or remove Programs". I tried only yesterday and it worked. :guitar:

---

### Post by Bakon Jarser on 2007-10-24
> **Rabindranath said:**
> Try installing via "Add or remove Programs". I tried only yesterday and it worked. :guitar:

seems easier to search for in the synaptic package manager.

---

### Post by cnfnr9 on 2007-10-24
I tried the alt+f2 and searched ccsm its not there.  and ccsm is not in the synaptic package manager is not there at all.
Im running Gusty

---

### Post by atam_kapoor on 2007-10-25
I have the same problem...

I had fiesty 7.04 and I upgraded it to 7.10 (gusty)...

When I type ccsm in Alt+F2 .. an error message pops up saying "could not open file:///ccsm"

and when I type "sudo apt-get install compizconfig-settings-manager" I get the error message in terminal saying 

"could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable) ....   unable to lock the administration directory '/var/lib/dpkg' , is another process using it ? "


What should I do now.. I tried going to synaptic package manager and it seems the required compiz applications are installed ...

Please help me in getting the "Desktop Effects" link in the main menu ...

Thanks in advance..

Atam

---

### Post by bertlacy on 2007-10-25
Here is what you need to do, make sure that you have the respostories added and then run these commands...

sudo aptitude update

sudo apt-get remove compiz-core desktop-effects

sudo apt-get install compiz  # compiz-gnome AND/OR compiz-kde

sudo apt-get install compizconfig-settings-manager # compizconfig-backends-* ?!

sudo apt-get install compiz-fusion-*

---

### Post by Brindled on 2007-10-25
> **bertlacy said:**
> Here is what you need to do, make sure that you have the respostories added and then run these commands...

sudo aptitude update

sudo apt-get remove compiz-core desktop-effects

sudo apt-get install compiz  # compiz-gnome AND/OR compiz-kde

sudo apt-get install compizconfig-settings-manager # compizconfig-backends-* ?!

sudo apt-get install compiz-fusion-*


Thank You! Thank you for your input, bertlacy!

i'd been having this problem lately also. i knew the answer would pop up sooner or later.

Great Community

---

### Post by atam_kapoor on 2007-10-26
Thanks for your reply.. 

It worked on my laptop but my PC on which I also installed Ubuntu gives an error.. 

I was successful while removing compiz core and while installing compiz but when I tried to install compizconfig-settings-manager.. it gave the error " Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable) ... Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? "

What can I do now.. I even tried uninstalling the compiz that I succeeded to install but again the same error message comes.. Even when I write sudo aptitude update, it gives the same message... 

What does this message actually mean ? Could you help me through this ?

Thanks for your tip though, 

Atam

---

### Post by atam_kapoor on 2007-10-26
I tried it after 10 minutes and this worked now.. 


Thanks for your help.. 

but still do you know why this bug was there before ?

---

### Post by Six_Digits on 2007-11-01
Did you have synaptic open? Something else may have been using the repositories.

---

