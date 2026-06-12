---
title: "Light-weight WM recommendations?"
date: 2007-04-23
forum: Desktop Environments
---

### Post by notwen on 2007-04-23
I have a 1.7ghz P4 (1gb ram) machine currently running Xubuntu Feisty that I typically use for a FTP server and nothing else, possibly run a website off it at a later time.  For now I'm wanting to explore my possibilities for a lighter WM than XFCE.  I've looked into Fluxbox, E17, & IceWM, although I'm not familiar w/ any of them.  I'm wanting to run it over a basic Ubuntu/Xubuntu install.   I know my machine can handle a bit more, but I'm wanting the least amount of system resources used, while still keeping a light-weight WM.  XFCE has somewhat out-grown it's boundaries for the small amount that I wanted out of it.  Fluxbox looks to be the most appealing, but I'm posting to get other ppl's opinions from previous experiences w/ each of the other WMs. Thanks in advance. My regards. =]

---

### Post by Sunflower1970 on 2007-04-23
I've been playing around with E17, IceWM and also Fluxbox. My favorite out of the three is IceWM. Very configurable, very light. It starts quite fast, programs open fast, easy to use. 

I also like E17. Minor problem with that is it will crash for me every once in a while, and I'm not too sure why. But for some eye candy on an old box, it's great :)  

Fluxbox. I'm not as familiar with it, and have had a bit of a hard time trying to figure out how to configure it to how I want it. I still need to play around with it more to get the hang of it. But, it really is light, and things do seem to fly on it.

---

### Post by kerry_s on 2007-04-23
Fluxbox is the only thing i waste my time with. Once you learn it you you learn to love it.

sudo apt-get install fluxbox fluxconf

Fluxconf is the gui editor for the menus, keys,etc...that everyones so use to using in other environments. I do mine manually with a text editor.

---

### Post by RedSquirrel on 2007-04-23
I recommend Fluxbox. I use it pretty much all the time and it's very lightweight. It's also rock solid. I was tinkering with E16 for a day and it crashed. That sent me running right back to Fluxbox.

It's easiest to configure Fluxbox by editing the configuration files directly. It takes a bit of time to learn the syntax and where certain configuration items are located, but once you do, changing settings is trivial. The syntax is mostly self-explanatory once you see some examples. Fluxbox looks very plain when you first install it but you can make it look very nice with a little work. :)

The Fluxbox in the repos is very stable. These days, I'm compiling the latest Fluxbox svn revision just to stay on the bleeding edge and report any bugs I find (nothing so far).

---

### Post by Sunflower1970 on 2007-04-23
> **kerry_s said:**
> Fluxbox is the only thing i waste my time with. Once you learn it you you learn to love it.

sudo apt-get install fluxbox fluxconf

Fluxconf is the gui editor for the menus, keys,etc...that everyones so use to using in other environments. I do mine manually with a text editor.


Ah. That's probably what I'm looking for: fluxconf. Will have to try that tonight when I get home :)

---

### Post by notwen on 2007-04-23
Does Flux run better on Edgy or Feisty, or would I even notice a difference?  Keep in mind, this box will just about be FTP services only and maybe eventually a web server.

---

### Post by aanderse on 2007-04-23
> **notwen said:**
> ... I typically use for a FTP server and nothing else, possibly run a website off it at a later time.

no window manager? just do a server install if you really only use it for that.  if you really need a window manager you can use screen for a text based system :-)  when i was running a box at my house for hosting files etc i found a pretty good difference in speed between gui and no gui.  if you really aren't going to use it, you should consider getting rid of it (gui).

---

### Post by kerry_s on 2007-04-23
> **notwen said:**
> Does Flux run better on Edgy or Feisty, or would I even notice a difference?  Keep in mind, this box will just about be FTP services only and maybe eventually a web server.

It runs great on all ubuntu versions. No, i don't think you will notice a difference fluxbox looks and acts the same no matter what version. The 1 in feisty is just the most up to date, the only new feature i noticed was the overlay, which is a hidden feature, if i didn't look around i wouldn't even know about it. It's just to set some personal settings for themes that you want to carry over no matter what theme you change to, so you don't have to tweak each theme.

---

### Post by DJiNN on 2007-04-23
> **Sunflower1970 said:**
> Ah. That's probably what I'm looking for: fluxconf. Will have to try that tonight when I get home :)

Fluxbox is superb and definitely worth a look. But i notice that you have installed the Xubuntu suite....? Although you'll notice a difference using Fluxbox instead of XFCE, you'll REALLY notice the difference if you do a server install & then just install Fluxbox on top of that. 

kerry_s can definitely point you in the right direction there as he's done it sooo many times, and although it looks a little daunting at first, it's really quite straightforward, and even easier on old machines as there's less exotic hardware to screw things up! :)

---

### Post by notwen on 2007-04-23
> no window manager? just do a server install if you really only use it for that. if you really need a window manager you can use screen for a text based system when i was running a box at my house for hosting files etc i found a pretty good difference in speed between gui and no gui. if you really aren't going to use it, you should consider getting rid of it (gui)

I also like to remote into this machine to pull down additional files to add to the FTP from my main machine.  I realize I could do this all w/o a GUI using SSH, but I'd rather keep the GUI for ease of use.  Plus sometimes my significant other will be pulling files from my main machine to add to the FTP when I'm not able to(does that make sense? =p)  Anyway, my point is a light weight window manager would help more than it would hurt.  Give me some time to teach her CLI and we'll see if we can eventually do away w/ the GUI all together, but for now a WM is needed. =]

---

### Post by RedSquirrel on 2007-04-23
> **kerry_s said:**
> The 1 in feisty is just the most up to date, 

Are you sure? I think edgy and feisty have identical versions of Fluxbox. If you want a newer version, you have to compile one (not hard). :)


> the only new feature i noticed was the overlay, which is a hidden feature, if i didn't look around i wouldn't even know about it. It's just to set some personal settings for themes that you want to carry over no matter what theme you change to, so you don't have to tweak each theme.Hasn't that been around for a while? 

From: [http://fluxbox.sourceforge.net/version-0.9.php](http://fluxbox.sourceforge.net/version-0.9.php)

> [COLOR=DarkGreen] **News in 0.9.15:** 
    * Added styleOverlay resource 
       * session.styleOverlay: ~/.fluxbox/overlay
       Style settings in this file override any settings from a
       regular style[/COLOR]

---

### Post by kerry_s on 2007-04-23
> **RedSquirrel said:**
> Are you sure? I think edgy and feisty have identical versions of Fluxbox. If you want a newer version, you have to compile one (not hard). :)


Hasn't that been around for a while? 

From: [http://fluxbox.sourceforge.net/version-0.9.php](http://fluxbox.sourceforge.net/version-0.9.php)

I meant up to date from the repos. I try and only use app's that are in the repos. I don't browse the fluxbox site often, so i only just learned about the overlay, before that i just tweaked each theme as i used them. :)  oh, and of course i'm never sure. :lolflag:

---

### Post by notwen on 2007-04-24
Would waiting until the Fluxbuntu release based on Feisty be worth it(Mid-Late May according to the Fluxbuntu forums)?  Or should I go ahead and do a server install, followed by adding fluxbox on top?

---

### Post by ofek on 2007-04-24
Server install with fluxbox will be very close to what fluxbuntu is  (have tried it so I know) but I still think openbox is better.
Open box is faster and more responsive and in my mind more configurable and don't restrict u to its own toolbar or anything (yeah I know u can disable it in fluxbox).
I've been through probably all the windows environments offered for linux  and I settled on openbox for the last few years.
Openbox blackbox fluxbox fvwm and fvwm-crystal are all as light as can be and they all are highly configurable though like I said openbox is my favorite one. 
There are lighter WM out there but I wouldn't recommend them for the novice user. (They don't suit my needs though they might suit urs)

---

### Post by notwen on 2007-04-25
Alrighty, so I've backed up everything off my current FTP box and I'm hoping to do the install over the weekend.  I've looked around the forums and briefly on th web for a how-to/walkthrough on installing ubuntu server edition + fluxbox and am coming up w/ very little.  It's not the server install that concerns me, more so the installation of Flux and then getting it to start automatically.  Anyone know of such a site? =]

---

### Post by DJiNN on 2007-04-25
> **notwen said:**
> Alrighty, so I've backed up everything off my current FTP box and I'm hoping to do the install over the weekend.  I've looked around the forums and briefly on th web for a how-to/walkthrough on installing ubuntu server edition + fluxbox and am coming up w/ very little.  It's not the server install that concerns me, more so the installation of Flux and then getting it to start automatically.  Anyone know of such a site? =]

There's not really a lot to do after you've installed the base system. Have a look [here]("http://www.psychocats.net/ubuntu/minimal#barebones") for some help. Also, [this thread]("http://ubuntuforums.org/showthread.php?t=415905&highlight=kerry_s") may be of help. Any post with either kerry_s or RedSquirrel  as a participant, and you're likely to get some relevant info & seriously good help! :)

Have fun.......

DJiNN

---

### Post by frylock on 2007-04-25
I initially really liked fluxbox. It wasn't until i was moving a playing video that i noticed it stopped rendering output until I stopped - kinda felt like the dark ages.

I'd go with E17

---

### Post by notwen on 2007-04-26
Don't see me playing too much video on this box, doubt that will be an issue.

---

### Post by DJiNN on 2007-04-26
While Fluxbox/Openbox etc are great for much older machines, i don't see a lot of difference on my Xubuntu machine between using XFCE as per installation, and using the other "Lightweight" WM's.  

XFCE works really well, is fast, responsive, Modern (Well, in it's own way at least) and that's on a 1Ghz PIII with 512mb RAM & a 30Gb HD & onboard Graphics, so nothing special or powerful.

Yet using Xubuntu as standard, i have a really great, lightweight OS with plenty of functionality, the ability to play almost any media that i wish to play etc etc.

In short, it does pretty much everything that i throw at it, and it does it well. So, although i love to play around with different WM's etc because it's fun & interesting, i'd have to ask..... why Bother!? If all one wants is a great little OS that just works & is fast & flexible, even on older machines, then why not just stick with the standard Xubuntu.

I'm just being curious here & would really like to hear other opinions & reasons as to why others use such things as OB or FB or Ice. Is it the (often marginal) speed increase that's achieved or is it something else altogether?

DJiNN

---

### Post by notwen on 2007-04-26
I may try a clean xfce4 install over server edition and see how that goes as well.  I will say that I am somewhat eager to try flux tho, being I've toyed w/ Gnome, KDE, and XFCE.  Only flux I've experienced so far has been on the Gparted liveCD. =p

---

### Post by DJiNN on 2007-04-26
> **notwen said:**
> I may try a clean xfce4 install over server edition and see how that goes as well.  I will say that I am somewhat eager to try flux tho, being I've toyed w/ Gnome, KDE, and XFCE.  Only flux I've experienced so far has been on the Gparted liceCD. =p

I did that about a year ago, and it was OK & everything worked well, but it was nowhere near as tight & integrated as the Xubuntu release with all the bells & whistles etc. Still, when you do it, please post your results because i'd be interested to hear about your experiences. 

DJiNN

---

### Post by RedSquirrel on 2007-04-26
> **DJiNN said:**
> In short, it does pretty much everything that i throw at it, and it does it well. So, although i love to play around with different WM's etc because it's fun & interesting, i'd have to ask..... why Bother!? If all one wants is a great little OS that just works & is fast & flexible, even on older machines, then why not just stick with the standard Xubuntu.

I'm just being curious here & would really like to hear other opinions & reasons as to why others use such things as OB or FB or Ice. Is it the (often marginal) speed increase that's achieved or is it something else altogether?

DJiNN


Yeah, I agree about the marginal speed increase. On my box (Duron 600 MHz, 320 MB RAM), Xubuntu runs very well, certainly a big improvement from GNOME. It is a nice environment to work with.

The are probably lots of reasons I prefer Fluxbox, but here are three:

(1) I know it very well, so when I want to configure something, I have a good idea of which text file to look in and what to do. I find pointing & clicking through endless dialogs rather tiring. I know you can edit the config files for other WM/DE too, but with Fluxbox the modularity is excellent and the syntax in the files is self-explanatory (IMO).

(2) About once a week or so, I grab the latest svn code and compile that. I must admit, it is fun using a bleeding edge version and the idea of compiling my own WM is sort of a kick. :) It's somehow more exciting than compiling a kernel, although that can be fun too. I think it's the fact that a WM is a visual thing, so when you compile a newer version, you can see & feel the difference. Compiling the lastest kernel source doesn't necessarily make much of an improvement.

(3) I like Fluxbox's default desktop -- uncluttered! I don't have to go around turning off a bunch of stuff. It's barebones to begin with.



> **notwen said:**
> I may try a clean xfce4 install over server edition and see how that goes as well. I will say that I am somewhat eager to try flux tho, being I've toyed w/ Gnome, KDE, and XFCE. Only flux I've experienced so far has been on the Gparted liceCD. =p

I would recommend giving Fluxbox a try. IMO Xfce (Xubuntu) has a similar feel to GNOME in many ways, it's just faster. OTOH, Fluxbox is really quite a different experience. There is a bit of learning curve (perhaps), but IMO Fluxbox repays careful study.


EDIT

IMO, one *will* see a difference in performance between Xubuntu and using Fluxbox if they are running on really old hardware and/or have very little RAM.

---

### Post by notwen on 2007-04-27
During the Select & install software, I select LAMP and the installer proceeds to error out.  Anyone else having this issue w/ the Feisty server install?

Error has this on the screen w/ a very lovely red BG.

>  [!!] Configuration -- An installation step failed.  You can try to run the failing item again from the menu, or skip it and choose something else.  The failing step is: Select and install software. 

---

### Post by DJiNN on 2007-04-27
> **RedSquirrel said:**
> Yeah, I agree about the marginal speed increase. On my box (Duron 600 MHz, 320 MB RAM), Xubuntu runs very well, certainly a big improvement from GNOME. It is a nice environment to work with.

Yep, i can imagine it would run well.... certainly does OK on this old PIII 1ghz. :)  (Although i have to say that Zenwalk does it better & faster, and copes a lot better when there's more stuff running at once).

But Xubuntu is a lovely environment to work in. Friendly, functional..... the only thing that i really miss (Which i've just found in Zenwalk & it works REALLY well) is something like the "FuseSmbTool" for network shares etc..... I did see a post a week or two ago explaining a great way to set up Thunar for Net Shares, and that worked really well.... but not as well as FuseSmbTool. :)

> other WM/DE too, but with Fluxbox the modularity is excellent and the syntax in the files is self-explanatory (IMO).

Yep, you can't beat knowing something well eh? :) It is an easy syntax to follow i have to say. I have bodhi.zazen to thank for getting me into fluxbox..... he spent a lot of time with me last year and really brought me on with flux & many other Linux things. 

> (2) About once a week or so, I grab the latest svn code and compile that. I must admit, it is fun using a bleeding edge version and the idea of compiling my own WM is sort of a kick. :) It's somehow more exciting than compiling a kernel, although that can be fun too. I think it's the fact that a WM is a visual thing, so when you compile a newer version, you can see & feel the difference. Compiling the lastest kernel source doesn't necessarily make much of an improvement.

Seeing as how i've never compiled a Kernel yet (Nor do i feel so inclined) i wouldn't know what that feels like, although i have compiled my own fluxbox release several times and that felt great, so i can imagine how it would feel. :)  I've heard that the svn versions are a bit more complicated than standard compiles, do you find this?

> (3) I like Fluxbox's default desktop -- uncluttered! I don't have to go around turning off a bunch of stuff. It's barebones to begin with.

Yep, makes it a lot easier to make it how you want it, that's why i like server installs, talking of which, maybe you could help me if you don't mind?

I'm thinking of doing a Feisty server install on a machine that already carries several partitions across 2 hard drives, on which is installed both XP & Feisty (Gnome edition).  If i do a server install on the partition i'd like to put it on (That's already setup, as it's carrying Fluxbuntu at the moment) will it mess up my grub for my Feisty install that i already have on there?  (Does that make sense?)

In other words, is it going to cause any problems that you can forsee, & is there any changes that i should make to the Grub menu that i'm already using? Or can i just install the server install etc, then reboot into my standard feisty and run something like "sudo dpkg-reconfigure grub" to pick up the new install?

Confused? I am..... :)

---

### Post by notwen on 2007-04-27
Tried the Feisty server install using the alternate cd, still having issues at the same point.  I have went back and d/l the edgy server install and the install had no issues.  So far I've sudo apt-get update/upgrade & sudo apt-get install xorg gdm fluxbox.  Anything else you can think of that needs to be done?  Also taking recommendations on a ftp server.  I was running pro ftp on my xubuntu machine previously.  Thanks for any info. =]

---

### Post by RedSquirrel on 2007-04-28
> **DJiNN said:**
> I've heard that the svn versions are a bit more complicated than standard compiles, do you find this?

You have to setup a few things initially, but you only have to do it _once_ and then it's trivial to obtain the latest code. I can give you all the gory details if you want them, but I won't post them just yet in case you *don't* want them. :lol:

> 
Yep, makes it a lot easier to make it how you want it, that's why i like server installs, talking of which, maybe you could help me if you don't mind?

I'm thinking of doing a Feisty server install on a machine that already carries several partitions across 2 hard drives, on which is installed both XP & Feisty (Gnome edition).  If i do a server install on the partition i'd like to put it on (That's already setup, as it's carrying Fluxbuntu at the moment) will it mess up my grub for my Feisty install that i already have on there?  (Does that make sense?)

In other words, is it going to cause any problems that you can forsee, & is there any changes that i should make to the Grub menu that i'm already using? Or can i just install the server install etc, then reboot into my standard feisty and run something like "sudo dpkg-reconfigure grub" to pick up the new install?

Confused? I am..... :)


I think I know what you're saying. I'm pretty sure you'll be OK. Near the end of the server install, it will ask something about the other OSes you have on your system and then it *should* adjust the grub menu accordingly. I have a dual boot at the moment: edgy GNOME and feisty server. When I installed the server, everything went well and the grub menu has both the edgy OS and the feisty OS.

As usual, **backup** everything you want to keep in case something goes horribly wrong with your install. Ubuntu installers seem to work very well, but the one time you don't take precautions is the one time it will fail, right?? :)

---

### Post by RedSquirrel on 2007-04-29
> **notwen said:**
> During the Select & install software, I select LAMP and the installer proceeds to error out.  Anyone else having this issue w/ the Feisty server install?

Error has this on the screen w/ a very lovely red BG.

Hmm. I used the feisty server CD (not the net installer) and when I selected LAMP everything worked fine.


> **notwen said:**
> Tried the Feisty server install using the alternate cd, still having issues at the same point.  I have went back and d/l the edgy server install and the install had no issues.  So far I've sudo apt-get update/upgrade & sudo apt-get install xorg gdm fluxbox.  Anything else you can think of that needs to be done?  


I also grabbed gksu, synaptic, and xterm.

You might also want feh so you can set a background (unless you have something to set this already, such as eterm). And leafpad is a nice lightweight text editor if you get tired of editing in a terminal with vim/nano.

Have you configured your X server settings?

```
sudo dpkg-reconfigure xserver-xorg
```Have you started X yet?

```
sudo /etc/init.d/gdm start
```> 
Also taking recommendations on a ftp server.  I was running pro ftp on my xubuntu machine previously.  Thanks for any info. =]I don't run an ftp server, so I have no recommendations here. :|

---

### Post by notwen on 2007-04-30
Any recommendations for a light a light file manager?  I'm setting my sights on pcmanfm.

---

### Post by RedSquirrel on 2007-04-30
> **notwen said:**
> Any recommendations for a light a light file manager?  I'm setting my sights on pcmanfm.


I use the command line, but emelFM and Rox filer are two others that people seem to like. pcmanfm looks pretty nice. 

You can actually use Rox as a full desktop too. Have a look at [ROX Desktop]("http://rox.sourceforge.net/desktop/static.html"). The [fluxbuntu community]("http://community.fluxbuntu.org/") site also had some ideas for using Rox. I haven't visited the site in a while, but the HOWTOs are probably still there. Worth a look.

---

