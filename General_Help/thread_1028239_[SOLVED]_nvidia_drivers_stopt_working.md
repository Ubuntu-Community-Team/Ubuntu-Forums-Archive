---
title: "[SOLVED] nvidia drivers stopt working"
date: 2009-01-02
forum: General Help
---

### Post by vocifer on 2009-01-02
hi

i googled for a solution for my problem but i can't seem to find one. the only solution i can think of is reinstall, but that doesn't seem like the most productive option, anyway .

i wanted to installed the ubuntu restricted extra's in add/remove. it told me that there were conflicting packages installed and that i had to go to synaptics so it could resolved the issues. so i did. i looked for the package marked it, and applied the changes. however it never warned me of any conflicting packages, and never uninstalled anything. it then told me to reboot. before i get the login screen again, i get an error telling me there is something wrong with my grafics.

it gave me the option to generate a new configuration, but i lost all 3d acceliration. my drivers don't work anymore. seems like i'm unable to activate them. 

i unstinstalled the ubuntu restricted extra's but that didn't change anything. the drivers seem to be in here, but i just can't activate them with the system->administration->hardware drivers. if i go to synaptic all the relevant packages are installed. 

i remember i had a similar problem once when i installed something along the lines of nvidia settings. a front end for changing settings for my nvidia grafic card. that was just after i switched to 8.10. back then i did actually reinstall. solved my problem too :d. 

tried some other things i read on the net so far, nothing seems to work, messed up more then i solved so ... . rebooting doesn't seem to help either, other than reinstalling my operating system i'm out of options.


now i've been an ubuntu user for some time now. with that i mean. i USE ubuntu, i don't know that much about it. all i can do is mess around a bit and hope things won't crah on me.

i don't know if it's relevant but 
ubuntu 8.10
kernel 2.6.27-9-server (why does it say server there :s, hope that's not my doing)
nvidia GeForce 8600xm


things that didn't solve my problem :d
[http://ubuntuforums.org/showthread.php?t=1004660](http://ubuntuforums.org/showthread.php?t=1004660)
most post i read about this involve upgrading from 8.04 to 8.10. so i think it's seperate.




any help would be greatly appriciated.
greetz

---

### Post by Thura on 2009-01-02
Once, I have this kind of problem ...
I solved like this ...
First, removed all nvidia-realted packages from synaptic ( search >> nvidia >> name )
Then, downloaded the [official package]("http://www.nvidia.com/Download/index.aspx?lang=en-us") and installed it ...

---

### Post by linux_tech on 2009-01-02
To install and run nvidia-settings-
```
sudo apt-get install nvidia-settings
```
```
nvidia-settings
```

---

### Post by Tomatz on 2009-01-02
Try using envyng:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by vocifer on 2009-01-02
this may be a retarded question. but how do i find out if i'm using 32 bit or 64 bit system? (seems like there are seperate drivers for the two). 4

@linux_tech
the problem was then when i installed it last time my drivers stoped working, more or less like they stopped working just now.

@Tomatz
i went to the website, the list of supported Operating Systems stops at 8.04. don't know if that's a big problem. However i don't like the idea of installing other software to manage drivers. 
my drivers have always worked, everything was just fine untill i messed it up. trying to figure out a decent way to fix what i broke. :) i don't really see the need to install something else. if nothing else works i'm sure going to give it a try.



i removed all my drivers and nvidia related software. rebooted my pc and nothing much changes witch is a good thing i suppose. I went to hardware drivers, but noting is listed there. 
when you install ubunut, it will automaticaly search for drivers. so i suppose there is some way to make it do that again. problem is i don't know how. 

i donwloaded the drivers official drivers, apparently it's still beta. (i hope it's the 32 bit version i need :p) if things go terrebly wrong i can always still reinstall the whole system.



ps : @Tomatz
i did install that envy thing. everything seems to work just fine. thanks. and thanks to the rest of you as well didn't expect such a quick response. i still don't like the idea of installing envy to install the drivers. but hey what the hell, it's not like i know enough about it to ever notice the difference. 

anyway thanks again.

pps: maybe someone has any idea what went wrong. it seemed like it had something to do with installing the restricted extra's, as add/remove complained about conflicting packages. but i don't know why. perhaps a can learn something from this :)

---

