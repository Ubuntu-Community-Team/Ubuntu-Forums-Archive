---
title: "Question about using compoz-fusion on gutsy"
date: 2007-10-13
forum: Desktop Effects &amp; Customization
---

### Post by ehdtkqorl123 on 2007-10-13
Hi, I just got the compiz-fusion working on my gutsy.
I am wondering where I can find the setting page for compiz-fusion..
Lke I mean where I can find some setting manger to specify visual effects?
Thanks

---

### Post by techno-mole on 2007-10-13
system - preferences - and there should be an icon for the compiz settings manager somewhere, it may say desktop effects of something similar.
hope this helps
cheers

---

### Post by ehdtkqorl123 on 2007-10-13
Thanks for help...
Actualyl i am using gnome, and when I go to preferences, there is nothing like that... :( weird..

---

### Post by techno-mole on 2007-10-13
im using gnome, thats how i get to it, have you tried running ccsm in terminal ?

---

### Post by ehdtkqorl123 on 2007-10-13
I was just trying that... it says

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily navailable)
E: Unable to lick the administrion directory(/var/lib/dpkg/), is process using it?

---

### Post by ehdtkqorl123 on 2007-10-13
also it seems it is not detected by synaptic package manager...
do i have to add something to /etc/apt/source.list?

---

### Post by mmcmonster on 2007-10-13
Same problem as the original poster.  I got a bit better output from trying ccsm at the terminal, however. :-)

```
$ ccsm
The program 'ccsm' is currently not installed.  You can install it by typing:
sudo apt-get install compizconfig-settings-manager
bash: ccsm: command not found
$ 

```

After the package is installed, it shows up as*** System -> Preferences -> Advanced Desktop Effects Settings***.

That being said, there probably should be a bug filed that compizconfig-settings-manager is not installed by default when compiz is active.

---

### Post by ehdtkqorl123 on 2007-10-13
But I don't have
** System -> Preferences -> Advanced Desktop Effects Settings.**
even though compiz-fusion is working..
When I try to isntall that manager, it says it couldn;t find package..
What package should i add and use?

---

### Post by techno-mole on 2007-10-13
what repo's are you using ?
go into synaptic and then click on settings and then click on repositories, then click third party software sources and tell us what you have
how did you get compiz to run ?

---

### Post by ehdtkqorl123 on 2007-10-13
I am using Gutsy unstable version.
Since it contains compiz-fusion by default I could use it after I enabled Visual Effect. 
In third party, I have 

archieve.canonical.com/ubuntu gutsy partner
archieve.canonical.com/ubuntu gutsy partner (Source code)

both are unchecked.

---

### Post by techno-mole on 2007-10-13
thats interesting because ive been having an issue with compiz on gutsy, ive installed gutsy from sratch and when i loaded it up although compiz was running i only got title bars on firefox and nothing else, and as yet i have been unable to solve the problem using what came with gutsy.
what i did was basically to go into synaptic and search for compiz, and mark everything thats installed for complete removal then you can do this in terminal - 
```

sudo apt-get remove --purge compiz-fusion-plugins-unsupported compizconfig-settings-manager libcompizconfig-backend-gconf 
```

then i installed it again using the method that can be found here - [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion) and it should work, well it worked for me, and the settings manager works aswell.
MAKE SURE you use the method thats right for you, as in dont use the install method for nvidia cards if you have an ati card and vice versa, you should be able to find the right method on that site.
cheers.

---

### Post by screaminj3sus on 2007-10-13
It's just not installed by default in gutsy, just open synaptic and search for compiz settings manager and install it, after you install it it will be in preferences>advanced desktop effects settings.

---

### Post by techno-mole on 2007-10-13
seems a tad strange not to install the settings manager by default if you ask me, seeing as anybody who uses it will no doubt want to alter things ?i had to install it on a fresh install of gutsy, but it gave me the code to use, which is - ```
 sudo apt-get install compizconfig-settings-manager 
``` and that did it for me, after that i had an option in system - preferences, which was advanced desktop effects settings, but as ive found out this isnt working for some people (see the first page of posts in this thread)

---

### Post by ehdtkqorl123 on 2007-10-13
okay.. I will try again...
Is there a repository I have to add to sources.list in order for that to work? (for Gutsy)
also, does anything bad happen if I use Fiesty's repository for Gutsy?.. or can I?

---

### Post by techno-mole on 2007-10-13
ive just re-installed gutsy and i had to run that command in terminal and it worked for me and i havent had to add any repo's.
curiosly it is now working perfectly ? and i have no idea whats different now to the last time i install gutsy from scratch ?

i installed fusion using this method - [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)  and it worked fine, i didnt see any adverse affects from using that repo, although technically youre meant to use the repos for the version your using - eg - fiesty = use fiesty repos and not gutsy repos, although i could be wrong.
if you do try the method found in the link i posted you have to remove compiz first, to do that i would go to synaptic and search for compiz and remove anything thats installed.
cheers.
or you could do what ive just done and do ma complete fresh install of gutsy.

for the method to work you have to add some repos (as you will see) its easy enough to do, i usually go to synaptic and then click settings and then on repositories, then click third party software sources and then click on add and copy and paste the repos, but the link gives another link to a how to for adding repos

---

### Post by lincolnlad on 2007-10-13
sudo apt-get install compizconfig-settings-manager

It's not installed by default.

After you've installed it, reboot (log out might just work) and then go to Appearance preferences and Custom visual effects will have a preferences button where you can set things how you want.

---

### Post by mc4man on 2007-10-14
if your getting this
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lick the administrion directory(/var/lib/dpkg/), is process using it?
```
it's probably because you have restricted drivers enabled for your video card

question ; can you run compiz-fusion (Advanced Desktop Effects Settings) with restricted drivers enabled? (after installing compizconfig-settings-manager)

---

### Post by techno-mole on 2007-10-14
im using restricted drivers and i dont get that error, maybe its just some small bugs that will be sorted with the final release of 7.10.
cheers

---

