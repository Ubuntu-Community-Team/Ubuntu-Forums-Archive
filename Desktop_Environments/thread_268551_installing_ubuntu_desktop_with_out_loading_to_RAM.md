---
title: "installing ubuntu desktop with out loading to RAM"
date: 2006-09-30
forum: Desktop Environments
---

### Post by Matt_BLah on 2006-09-30
Hi guys.

Ok I am trying to install ubuntu desktop onto my laptop, BUT I dont want to load it up then install, I want to tell it to install to my HD before it loads up. other wise my old as poo laptop will sit here for 3 days loading it.... I want to avoid that.


thanks,
Matt_BLah

---

### Post by djRobbieF on 2006-09-30
Download the alternate installer iso.

---

### Post by Markkreuzz on 2006-09-30
Okay you might be reffering to an alternate install... ive also had this before when Dapper would't install and kept freezing...
you could try using the alternate install CD using text only setup which you can find [HERE]("http://ubuntu-releases.cs.umn.edu//6.06/"). This one does not load the whole mumbo jumbo on your PC... Hope you are experienced enough to go through the alternate install and answer the questions properly (it's very dangerous to randomly select options especially when it comes to the partitioning part) .... if you have any more troubles just post back. Good Luck

 i would also suggest trying to use the [THIS]("http://ubuntuforums.org/search.php") page more to resolve this problem. I believe this question might have been answered a couple of times before.

---

### Post by Matt_BLah on 2006-09-30
ya I tryed doing the search thing but it wasnt working so I posted... sorry.


thanks for the help tho,
Matt_BLah

---

### Post by Markkreuzz on 2006-09-30
That's okay... By the way i have just now noticed you said *"other wise my old as poo laptop will sit here for 3 days loading it"*... if that is the case i don't think the "Ubuntu Heavyweight Desktop" is for your laptop. if it crawls on the regular Ubuntu CD... your laptop will crawl even more or even croak if you try to install Ubuntu on your laptop. I would recommend using [Xubuntu.org]("http://xubuntu.org/") if you feel your laptop could not take it any much longer... Good Luck...

---

### Post by Ocxic on 2006-09-30
you could connect it by ethernet/usb copy your current partiton over, and use chroot, to make the neessaccery changes to the orginal install on your laptop so it will run correctly. (in theory, but i beleive it is possible.)

---

### Post by lawina on 2006-09-30
What kind of laptop hardware you are using? CPU, memory, make, model.?

---

### Post by Matt_BLah on 2006-09-30
hey I am installing ubuntu now on my laptop.... it seems to be doing fine. It just couldnt handle loading it all to RAM (the way the CD thing works, loading all apps from CD to RAM so you can have a peek before installing it to HD), but now it seems to be doing ok.. and if it has trouble I will check out the lighter edition of ubuntu...

and the laptop is from '98 it is made by a company called microPC (was a compnay that made cheep PC's for schools) with a P3 and about 128 of ram.... I have been runing XP on it to host a few TeamSpeak servers and Apache, I am installing ubuntu desktop then loading the apache,php,mySQL stuff from the server edition of ubuntu (I suck at using command lines...) a friend said ubuntu would help my laptop run a little faster. well it is linux and I have never played around with linux so why not try now?



ok there is my life story, lol.

ttfn,
Matt_BLah

P.S.- up to 92% on install from typing this.

---

### Post by Markkreuzz on 2006-10-03
*" a friend said ubuntu would help my laptop run a little faster."* ROFLMAO --- a usual common misconception of Linux in General... Well as-far-as-i-know, upgrading/overclocking your CPU and adding ram will make your machine go faster. Not Running X will make things go faster etc... Just wait and see until you fire up firefox... well there is always swiftfox for you... Just saying this not to thrash but to set your expectation and not be totally disappointed.... Good Luck. [-X

---

### Post by Ocxic on 2006-10-03
> 
 a friend said ubuntu would help my laptop run a little faster." ROFLMAO --- a usual common misconception of Linux in General... Well as-far-as-i-know, upgrading/overclocking your CPU and adding ram will make your machine go faster. Not Running X will make things go faster etc... Just wait and see until you fire up firefox... well there is always swiftfox for you... Just saying this not to thrash but to set your expectation and not be totally disappointed.... Good Luck.

not really, I find after switching form XP my computer loads up programs/applications much faster, not to mention i dont have to wait the extra 1.5 min just so everything in the task bar can load, MSN esspecially. 
Also i find I can run an almost ulimited number of program at the same time without bogging my machien down, you try encoding a DVD, while browsing the net, playing music, and installing the newest ATI drivers at the same time on a windows machien, then watch it slow to a crawl, i lost count the amount of time I've had to wait for XP to become responive again while it was doin something CPU intensive, ubuntu/linux in general my not be on a whole faster, but does have better memory and CPU mangament. not to mention, that when an app crashs it doesn't take the rest of the OS with it.

---

### Post by Markkreuzz on 2006-10-06
(okay i can't help it....) which apps are you talking about? GNU/Linux and windoze don't have exactly the same apps. i run most appz in CLI and its quick, but try using a GTK front-end and see. *"you try encoding a DVD, while browsing the net, playing music, and installing the newest ATI drivers at the same time on a windows machien"*. ok... Try installing ATI drivers while youre playing music, browsing the net, encoding a DVD in your linuz machine and let's see what happens... well i'm not sure about ATI drivers. 
     when i first run ubuntu(hoary i think) in my machine i had an nvidia 6100 integrated video and it was borked. CLI just staring at me. had to use vesa and had to do dpkg-reconfigure xserver-xorg and select vesa,after that i am unable to compile nvidia drivers due to the kernel was compiled with a differrent version of GCC, i almost snapped the CD in two :) maybe i did. also had a pc with s3TrioDX card ran dapper 6.06.1 on it, no joy. not even a CLI. tried selecting s3 for drivers, no joy only vesa worked for me again... Take note this is an ancient VGA card... Well I don't know if it's just me and my bad luck...  
        and about win XP booting. I can't say anything about that. i ran a tweaked win2k most services stopped. boot time is kind of ok for me and i had long uptimes like several days without reboot and no penalty in CPU usage I have an athlon64 3000+ 1 gig of RAM.... it will now have lesser uptime since i just have finished my super minimal linuz machine which is connected to a speedtouch modem wich works beautifully in dapper, it's powered by a passive pII cpu to handle all my torrents and internet filtering/routing, hoping to lower my electric bill and noise polution...

---

