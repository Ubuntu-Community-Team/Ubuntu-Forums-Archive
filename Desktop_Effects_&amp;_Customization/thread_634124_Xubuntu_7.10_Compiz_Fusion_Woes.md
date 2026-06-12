---
title: "Xubuntu 7.10 Compiz Fusion Woes"
date: 2007-12-07
forum: Desktop Effects &amp; Customization
---

### Post by Kornowski on 2007-12-07
Hey Guys,

First off, I'd like to say "Hi" ):P

I've got Xubuntu installed on an old laptop, it has;

1.3Ghz Celeron
384MB of RAM
and an SiS 630 intergrated video chip.

Ater much time and effort I got the wireless internet to work, but now I have another problem...

I can't get Compiz to work, I think I've installed it, but when I go to:

Applications > Settings > Advanced Desktop Effects Settings

It opens the CompizConfig Settings Manager, but it's empty, there isn't anything in it... I have the Filter, Preferences and Advanced search down the side, but nothing else? ](*,)

What gives?

Thanks!

---

### Post by djfolsom on 2007-12-07
I had same problem with a Toshiba P205-s6347, compiz was not installed had to go to Synaptic
and install from there..also found on video when I uncheck vedio playback my vlc started working with Compiz running..](*,)

---

### Post by Kornowski on 2007-12-07
> **djfolsom said:**
> I had same problem with a Toshiba P205-s6347, compiz was not installed had to go to Synaptic
and install from there..also found on video when I uncheck vedio playback my vlc started working with Compiz running..](*,)

I can't find it in the Synaptic, do I need to search for it or something?

Uncheck video playback, where and what is that? :confused:

Thanks for the help :)

---

### Post by Kornowski on 2007-12-07
I got it working using the update thing, but for some reason the effects don't happen, none of them, even if I restart...

I have an SiS 630 chipset, I haven't installed drivers for it, I don't know where I'd get them...

---

### Post by DJiNN on 2007-12-07
By all means try, but you may find it makes your Laptop somewhat slow. I've used Xubuntu with Compiz, and while it works well on my AMD dual core & on my Core 2 laptop, on my old P4 (2.6 gig with 1 gig ram and intel Graphics) it's just not worth doing. 

Good luck with it though.... i hope that you get it working, it does look good, but unless your Graphics card is reasonably modern, it may well struggle.

---

### Post by celticbhoy on 2007-12-07
With your spec I would also give compiz a swerve, but if you want to improve the looks a little you could install E17 window manager it has a good amount of bling for little resources.

---

### Post by smartboyathome on 2007-12-07
If you want to install e17, you can use [this]("http://ubuntuforums.org/showthread.php?t=546746") thread.

---

### Post by Kornowski on 2007-12-07
I apprciate the replys, thanks guys!

I wouldn't mind giving Compiz a bash though, any ideas on how to get it working?

---

### Post by Kornowski on 2007-12-09
No ideas on how I'd get it to work?

---

### Post by JordanII on 2007-12-10
First of all, welcome to the forums! :) 

Whenever I run Compiz or Beryl on a comp with under 512MB of RAM it doesn't work. :-P When you run it does the screen go white? If so it's pretty hopeless. As the others have said your best bet for an old comp like that is [e17]("http://www.enlightenment.org/p.php?p=about&l=en"). 

PS: Are you from ComputerForum?

---

### Post by santiagoward2000 on 2007-12-10
> **Kornowski said:**
> I can't find it in the Synaptic, do I need to search for it or something?

Uncheck video playback, where and what is that? :confused:

Thanks for the help :)

Hi!
Have you installed **compizconfig-settings-manager**? That's the package which contains Compiz manager. Perhaps you could try to reinstall it.

> **JordanII said:**
> First of all, welcome to the forums! :) 

Whenever I run Compiz or Beryl on a comp with under 512MB of RAM it doesn't work. :-P When you run it does the screen go white? If so it's pretty hopeless. As the others have said your best bet for an old comp like that is [e17]("http://www.enlightenment.org/p.php?p=about&l=en"). 

Well, I'm not sure which are the minimum requirements, but Compiz-Fusion runs fairly well on my laptop with 192mb of RAM...

---

### Post by JordanII on 2007-12-10
> **santiagoward2000 said:**
> Hi!
Have you installed **compizconfig-settings-manager**? That's the package which contains Compiz manager. Perhaps you could try to reinstall it.



Well, I'm not sure which are the minimum requirements, but Compiz-Fusion runs fairly well on my laptop with 192mb of RAM...

Hmm... must be the video card then.... the computers that I tried to run it on an didn't work didnt have good video cards. Btw, you might want to try [Screenlets]("http://www.screenlets.org/index.php/Screenshots"). It'll make your desktop look better. :)

---

### Post by santiagoward2000 on 2007-12-10
> **JordanII said:**
> Btw, you might want to try [Screenlets]("http://www.screenlets.org/index.php/Screenshots"). It'll make your desktop look better. :)

Yes! They look so cool! Kiba-Dock doesn't look bad either. :popcorn:

---

### Post by JordanII on 2007-12-10
> **santiagoward2000 said:**
> Yes! They look so cool! Kiba-Dock doesn't look bad either. :popcorn:

But you need compositing for Kiba-Dock... Try [Simdock]("http://sourceforge.net/projects/simdock/") instead.

---

### Post by santiagoward2000 on 2007-12-10
> **JordanII said:**
> But you need compositing for Kiba-Dock... Try [Simdock]("http://sourceforge.net/projects/simdock/") instead.

Don't screenlets need compositing too?

---

### Post by JordanII on 2007-12-10
> **santiagoward2000 said:**
> Don't screenlets need compositing too?

I don't remeber... lol

Probably. :-P

---

### Post by santiagoward2000 on 2007-12-10
> **JordanII said:**
> I don't remeber... lol

Probably. :-P

I think so, I get a horrible black background with them when I turn my WM to xfwm. However, I use Compiz, so I don't worry about it! :)

---

### Post by JordanII on 2007-12-10
> **santiagoward2000 said:**
> I think so, I get a horrible black background with them when I turn my WM to xfwm. However, I use Compiz, so I don't worry about it! :)

Oh :-P Try gDesklets then... that doesn't use compositing.

---

### Post by santiagoward2000 on 2007-12-10
> **JordanII said:**
> Oh :-P Try gDesklets then... that doesn't use compositing.

Nah... I like my Screenlets, and as I'm using Compiz-Fusion I have compositing.

---

### Post by Kornowski on 2007-12-11
Thanks!

Nope, it doesn't go white, it just start up as normal... Hmmm, I may give it a go, is it good?

Yeah, I'm from CF :P So are you! :D

EDIT: Just seen the other replies, I'll read them now...

---

### Post by Kornowski on 2007-12-11
Yeah, I've installed Compiz Settings Manager :)

---

### Post by gatoz on 2007-12-11
its possible your graphics card is blacklisted, the way to fix is in a thread at desktop effects. here basically

---

### Post by JordanII on 2007-12-11
> **Kornowski said:**
> Thanks!

Nope, it doesn't go white, it just start up as normal... Hmmm, I may give it a go, is it good?

Yeah, I'm from CF :P So are you! :D

EDIT: Just seen the other replies, I'll read them now...

It's good that it doesn't turn white... that's the only problem I've ever had with it. Maybe your fx aren't installed?

---

### Post by Kornowski on 2007-12-11
> its possible your graphics card is blacklisted, the way to fix is in a thread at desktop effects. here basically


Do you think it is?

> It's good that it doesn't turn white... that's the only problem I've ever had with it. Maybe your fx aren't installed?


FX?

---

### Post by JordanII on 2007-12-11
> **Kornowski said:**
> Do you think it is?



FX?

Desktop effects. Maybe they somehow didn't get installed with the manager.

---

### Post by Kornowski on 2007-12-12
I don't know, I installed everything that was in the options... 

I don't think I have a video driver installed though, that could be the problem...

---

### Post by JordanII on 2007-12-12
> **Kornowski said:**
> I don't know, I installed everything that was in the options... 

I don't think I have a video driver installed though, that could be the problem...

Oh... could be.

---

### Post by Dapman01 on 2007-12-12
I believe that if you go to the terminal and type

compiz --replace

than that activates it

---

### Post by ashijit007 on 2007-12-14
@Kornowski,

Check if you have installed :
>>Graphics card drivers. I would suggest you use envy : [http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu2_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu2_all.deb)
Read the faq/requirements here : [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

>>Compiz (meta-package in synaptic)

>>CompizConfig-settings-manager (synaptic)

Now go to Applications->Settings->Autostarted Applications
Here, Click on Add and then fill in as follows:
Name         :    Compiz Fusion
Description :    Desktop Effects
Command  :     compiz --replace --disable-gtk

Then <Ctrl><Alt><Bkspace> to restart X.

After X restarts, if you don't see the window decorations, just go to CompizConfig-Settings-Manager and select "Window Decorations" under "Effects". That should do it. It worked for me....

---

### Post by cardinals_fan on 2007-12-14
If you have a video card driver, and all the compiz files are installed, hit alt-F2 and enter
```
compiz --replace
```

---

