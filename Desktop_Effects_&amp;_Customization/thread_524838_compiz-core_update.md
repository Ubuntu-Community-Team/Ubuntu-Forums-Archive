---
title: "compiz-core update"
date: 2007-08-13
forum: Desktop Effects &amp; Customization
---

### Post by skymera on 2007-08-13
update manager says 
compiz-core has an update

i click to update it and it says successful.
but it still says it needs to be updated =S

why?

---

### Post by Hobo Joe on 2007-08-13
You probably have a bad repository, paste your sources.list file.
```

sudo gedit /etc/apt/sources.list

```

---

### Post by Happy_Man on 2007-08-13
Perhaps an error ocurred? Run ```
sudo apt-get upgrade
``` from the terminal.

Of course, it could just be a quirk, and will be gone the next time you log in.... try that first.

---

### Post by skymera on 2007-08-13
yeah was just a dud repo.

all ghone and all sorted :)

---

### Post by luisromangz on 2007-08-13
I had this problem when I used the «official» repositories for ubuntu. Using Treviño's is a better option in my opinion.

---

### Post by michaelramm on 2007-08-13
I also got this message last night. Then I saw that [Compiz went Final (0.5.2)]("http://ubuntuforums.org/showthread.php?t=524872") today and thought maybe it was related to that.

I will have to change to Trevino's repo's tonight when I get home.

Thanks for the help in tracking this down.

---

### Post by meho_r on 2007-08-26
Same problem here.  I'm using amaranth repo:

```
deb http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main restricted universe multiverse
deb-src http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main restricted universe multiverse
```

Any ideas?

---

### Post by Rupertronco on 2007-08-26
meho_r, 

switch to trevino's or vorian's repository.

---

### Post by Vorian on 2007-08-26
I pulled packages from my repository.  _I do not recommend using any 3rd party repository other than Amaranths._  His repository has the same packages used in Gutsy.

As for the update bug, once you install Compiz w/ fusion plugins, uncomment Amaranths repository, until which time there is an update.  It is the stable 0.5.2 version of Compiz w/ fusion plugins.

---

### Post by meho_r on 2007-08-26
Uncomment or comment? Yeah, I did that. I've been using Trevino's repo, but had some issues after updating, so now I want to try Amaranth's. Till now, everything is working just fine :)

---

### Post by smokeslikeapoet on 2007-09-24
Amaranth has said this is a bug with the PPA repo.  Just put the compiz-core on hold for now by following these instructions from another post. This will remove the upgrade nag. Now if you see an upgrade to other compiz packages you'll want to take it off hold to make sure there's  not an upgrade. Only a few short weeks until Gutsy and we'll have Compiz by default.

Here is how to set the compiz-core package on hold (to avoid the update manager bugging you to install it indefinitely).

echo compiz-core hold | sudo dpkg --set-selections


To read the current state:
sudo dpkg --get-selections compiz-core

To change it back:

echo compiz-core install | sudo dpkg --set-selections

---

### Post by benhur99ph on 2007-09-24
For me, I just uncommented the repo that I used. That solved it right away.

---

