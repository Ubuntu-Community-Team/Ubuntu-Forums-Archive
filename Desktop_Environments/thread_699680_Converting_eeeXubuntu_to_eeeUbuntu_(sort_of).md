---
title: "Converting eeeXubuntu to eeeUbuntu (sort of???)"
date: 2008-02-17
forum: Desktop Environments
---

### Post by tinny on 2008-02-17
Hi

Just got an ASUS eee PC, GREAT!

Now im wanting to get ubuntu installed on it. Heres my plan, will it work? Any suggestions?

First I plan on installing eeeXubuntu by following these instructions [http://wiki.eeeuser.com/ubuntu:eeexubuntu:home#installation_instructions]("http://wiki.eeeuser.com/ubuntu:eeexubuntu:home#installation_instructions")

I want to install eeeXubuntu to get the hardware support and config straight out of the box. But I like Gnome, so next I plan on removing Xfce and then installing Gnome.

Remove Xfce

```
sudo apt-get remove --purge xubuntu-desktop xubuntu-artwork-usplash
```

Install Gnome

```
sudo apt-get install ubuntu-desktop
```

Is this a good idea?

---

### Post by patrickfromspain on 2008-02-17
nops... xubuntu-desktop is just a metapackage and it won't remove xfce or any of its programs.

---

### Post by tinny on 2008-02-18
Oh ok.

So how can I remove xfce and replace it with gnome? (with out breaking my eee pc eeeXubuntu install).

Thanks :)

---

### Post by liniaal on 2008-02-18
wrong order ;)
before removing xfce, i would in any way recommend to first run gnome after the apt-get install ubuntu-desktop. then, if it runs smoothly, you can consider removing parts of xfce etc.
to remove most of xfce, i think you should remove:
* xfce- packages, ie packages with names that start with xfce
* xfdesktop, xfwm4, xfprint, etc
* mousepad
* orage
* exo (libexo?)
* thunar (of which i won't believe that you would want to remove :P)
after that you will have the greater part removed, i believe.

but have you tried it? as soon as i can get my hands on a eeePC i'll definitely settle with this eeexubuntu.. or maybe something a bit more tuned but the freshly installed xubuntu+compiz on my current laptop means satisfaction to me. :P

what i forgot: to get to your gnome environment, after installing *ubuntu-desktop*, you can click the *sessions* button at the login screen. here, you can opt for the gnome session.

---

### Post by tinny on 2008-02-18
> **liniaal said:**
> wrong order ;)
before removing xfce, i would in any way recommend to first run gnome after the apt-get install ubuntu-desktop. then, if it runs smoothly, you can consider removing parts of xfce etc.
to remove most of xfce, i think you should remove:
* xfce- packages, ie packages with names that start with xfce
* xfdesktop, xfwm4, xfprint, etc
* mousepad
* orage
* exo (libexo?)
* thunar (of which i won't believe that you would want to remove :P)
after that you will have the greater part removed, i believe.

but have you tried it? as soon as i can get my hands on a eeePC i'll definitely settle with this eeexubuntu.. or maybe something a bit more tuned but the freshly installed xubuntu+compiz on my current laptop means satisfaction to me. :P

what i forgot: to get to your gnome environment, after installing *ubuntu-desktop*, you can click the *sessions* button at the login screen. here, you can opt for the gnome session.

Thanks for a great reply.

Sounds like a lot of work.

I think ill try this eeeUbuntu Tutorial first 

[http://ubuntu-eee.tuxfamily.org/index.php5?title=Quick_Start](http://ubuntu-eee.tuxfamily.org/index.php5?title=Quick_Start)

If im not happy with that I think ill just stick with eeeXubuntu.

---

### Post by tedrampart on 2008-02-25
hey, did the above tutorial work for you?  I'm in the same boat as you.. I want the hardware support of the eeexubuntu, but would rather just have eee-ubuntu.. 

I would like to try it, but would like some follow up feedback before reinstalling :)

thanks

---

### Post by fdimmling on 2008-02-25
> ... as soon as i can get my hands on a eeePC i'll definitely settle with this eeexubuntu.. ...
I am owning an eeePC for 2 weeks now and I am perfectly happy with eeeXubuntu as it is. I use it mostly as a Chinese dictionary with stardict and my own CDict and besides that for writing down ideas in OpenOffice, the labyrinth mindmap program and the zim desktop wiki. Not to forget, Skype on the eeePC is a charme, camera, micro an speakers perfect, no interference, excellent sound quality. System is 1.8GB total space, leaving around 1.7GB for the user. 
I am running Gnome on the rest of my computers, e.g. the Acer travelmate 4650 I'm using for writing now, and I like it very much. But for the eePC I definitly prefer Xubuntu, less disk space, starting faster, less load to the slower CPU.

eeePC and eeeXubuntu are just great artwork

Friedrich :)

---

### Post by tinny on 2008-02-25
> **tedrampart said:**
> hey, did the above tutorial work for you?  I'm in the same boat as you.. I want the hardware support of the eeexubuntu, but would rather just have eee-ubuntu.. 

I would like to try it, but would like some follow up feedback before reinstalling :)

thanks

Hi

I have now got my system to a stage where im happy.

Heres what I did...

I followed the eeeUbuntu tutorial and I was not happy with it. My installation broke after I ran a system update.

Next I tried a eeeXubuntu install by following these instructions [http://wiki.eeeuser.com/ubuntu:eeexubuntu:home#installation_instructions]("http://wiki.eeeuser.com/ubuntu:eeexubuntu:home#installation_instructions")

I found that everything worked straight out of the box!!!

Next I applied a few eee PC related optimizations.

I added the following to the bottom of my /etc/sysctl.conf file (no memory swapping to prolong the life of my flash memory)

```
vm.swappiness=0
vm.vfs_cache_pressure=0
```

Then I did too more recommend optimizations.
[http://wiki.eeeuser.com/ubuntu:eeexubuntu:customization#add_noatime_to_your_fstab]("http://wiki.eeeuser.com/ubuntu:eeexubuntu:customization#add_noatime_to_your_fstab")
[http://wiki.eeeuser.com/ubuntu:eeexubuntu:customization#use_ramdisk_for_temp_files]("http://wiki.eeeuser.com/ubuntu:eeexubuntu:customization#use_ramdisk_for_temp_files")

Now the system config is setup. But because I like Gnome I decided to install the Ubuntu desktop.

```
sudo apt-get install ubuntu-desktop
```

When you reboot you will have to change your session to gnome (you can do this at the login screen).

And thats it!!! Gnome on your eee PC!

---

### Post by tedrampart on 2008-02-25
I might give that a shot.. my regular ubuntu install seems to be working fairly well, but the  battery is still giving me wonky reports back.  

does your report the battery info correctly?  mine says its 1% capacity when fully charged, and only 0.8Wh (but 43.7Wh as the design charge).  I heard eeeXubuntu wasn't the same.. could you verify?

thanks again, I'll be downloading the image tonight and making a bootdrive at work..

---

### Post by tinny on 2008-02-26
> **tedrampart said:**
> I might give that a shot.. my regular ubuntu install seems to be working fairly well, but the  battery is still giving me wonky reports back.  

does your report the battery info correctly?  mine says its 1% capacity when fully charged, and only 0.8Wh (but 43.7Wh as the design charge).  I heard eeeXubuntu wasn't the same.. could you verify?

thanks again, I'll be downloading the image tonight and making a bootdrive at work..

Hi

My battery information is the same. :(

Let us know if you find a solution. (seems to give me the full battery life while running on battery)

---

### Post by tedrampart on 2008-02-26
hmm thats discouraging.  seems everything else is fine except that.  I was hoping you would say its working great haha, oh well..

I might just keep this install on here if eeexubuntu isn't going to fix that problem as well.  I'm stubburn, so I wont give up on finding out a solution.. I might try adding a boot option I saw in the system76 forum I'm about one of their models bad batter reporting, which fixed that.. so it maybe the same thing (blind luck if it works really)..

edit - just tried the suggestions you gave about converting.. are you using a swap or no?  I don't have a swap, so I'm assuming I should do the swappiness=0 and cache pressure=0 as well.. since the link said if you have a swap to do =1....

---

### Post by tedrampart on 2008-02-26
regarding the battery, just saw this on a google search.. 
[http://paste.lisp.org/display/54516](http://paste.lisp.org/display/54516)

not sure how accurate it is.. but somewhere in there it says its an issue with the battery firmware or bios.. which asus needs to fix.. so that may be the be all and end all to that cunundrum...

EDIT - so I added ec_intr=0 to my boot options in grub, and it seems like it made a bit of a difference with the battery icon.  it still reports funny misleading numbers, but the time seems a bit more realistic, and it doesn't go from the nearly dead look, back to the safe look and back again over and over.. so who knows.. might be worth looking into further.. it fixed a battery issue for my friends system76 laptop, so I thought it was worth a shot..not perfect, but seems a step closer...

---

### Post by tinny on 2008-02-26
> **tedrampart said:**
> hmm thats discouraging.  seems everything else is fine except that.  I was hoping you would say its working great haha, oh well..

I might just keep this install on here if eeexubuntu isn't going to fix that problem as well.  I'm stubburn, so I wont give up on finding out a solution.. I might try adding a boot option I saw in the system76 forum I'm about one of their models bad batter reporting, which fixed that.. so it maybe the same thing (blind luck if it works really)..

edit - just tried the suggestions you gave about converting.. are you using a swap or no?  I don't have a swap, so I'm assuming I should do the swappiness=0 and cache pressure=0 as well.. since the link said if you have a swap to do =1....

I have no swap partition.

---

### Post by tinny on 2008-02-26
Also...

I don't trust my wifi signal strength, when im sitting next to my wifi router I only get a signal strength of about 80%. When I had Xandros running I would get 100% in the same situation.

---

### Post by tedrampart on 2008-02-27
I'm using the ndiswrapper driver instead of the madwifi, and I get about 93% about 5 feet away.  you could try using that instead.  and see if it makes a difference.  

Im probably going to throw an intel 3945a/b/g card in it as I have an extra one.  probably do that when I put my touchscreen in.

---

### Post by earlycj5 on 2008-02-27
> **tinny said:**
> Also...

I don't trust my wifi signal strength, when im sitting next to my wifi router I only get a signal strength of about 80%. When I had Xandros running I would get 100% in the same situation.

There's a thread or two in the eee user forums about this.

The Xandros fudges the signal strength from what I was able to gather.

---

