---
title: "Adding additional desktop environments messes up the bootup and shutdown screens"
date: 2018-06-05
forum: Desktop Environments
---

### Post by smjork2 on 2018-06-05
So I have a fresh install of Ubuntu 18.04.
Then I add, let's say, MATE ( see, for example [https://linuxconfig.org/how-to-install-mate-desktop-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-mate-desktop-on-ubuntu-18-04-bionic-beaver-linux) )
... suddenly the startup and shutdown screens are MATE's screens. And "Ubuntu MATE" text replaces the default "Ubuntu"
Then I add, let's say, LXDE
... and the bootup and shutdown screens and text labels are the ones specific to LUbuntu

... and this "bootup+shutdown+text labels" replacement occurs each time I add another desktop environment.

Now, according to this thread ( [https://ubuntuforums.org/showthread.php?t=2149520](https://ubuntuforums.org/showthread.php?t=2149520) ) one can "easily fix" this with:
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u

... but it simply does not work. I choose the "default Ubuntu" but I still see "Ubuntu MATE"(+green images) or "LUbuntu"(+blue images) at startup/shutdown,
 or whatever, depending on the last desktop environment that I've installed.

So, is there another way, fully valid no matter how many desktop environments I add, to display the initial "Ubuntu 18.04" text label and images ?

---

### Post by monkeybrain20122 on 2018-06-05
> 
So, is there another way, fully valid no matter how many desktop  environments I add, to display the initial "Ubuntu 18.04" text label and  images ?                         

No. Why do you want many desktop environments? It is almost always a bad idea to add DEs despite all these half baked tutorials ( I suspect some of these people didn't even test it themselves, just cut and paste from somewhere else assuming that it would work) Unless you are extremely careful (and depending on how compatible the DE in the mix maybe) there is a good chance that you will break something.

---

### Post by smjork2 on 2018-06-07
Well, let's just say I'm a dreamer ;-)  I have two particular reasons to look for a proper solution to this: a. Either due to a new "improvement" offered by a Windows update or simply because the weather outside is just too hot, I sometimes bump into a "Linux-clueless" friend who decides to start a revolution and learn Linux :-)     So he/she takes advantage of me :-) I always end up trying to explain that "we have multiple choices when it comes to desktop environments". Their eyes glitter, confused and curious about this new world :-)))))    Shortly after their first contact with some Linux distro in a VirtualBox machine, they start looking for the "tutorials" you mention. And they become even more confused, seeing just "how easy and fool-proof" this is (claimed to be)    Mea culpa, on my side, I'm just afraid to scare them away if I tell them that it's much safer to test each DE in a separate VM.  b. This one is a bit more serious :-) I'd love to have a fully shiny wobbly etc desktop environment for my "normal" work (able to lure the above mentioned friends into my world) BUT I'd also love to have some "very-games-friendly" DE on the same machine, just in case. I'm sure you all get my point. Therefore the need to keep those nasty bootup/shutdown text labels and images as I like.

---

### Post by Frogs Hair on 2018-06-07
You can install various sessions without affecting the boot-up image which is what happens when you install  full desktop environments .

 You'll still end up with lots of clutter including different file managers and duplicate applications , but it's your machine. I have installed many DE sessions in the past, but ended up reinstalling just get rid of the clutter.    

Example: ```
sudo apt install lxde
``` ```
sudo apt install xfce4
``` 

Edit: Installing Budgie will change the boot animation as of 18.04.

---

