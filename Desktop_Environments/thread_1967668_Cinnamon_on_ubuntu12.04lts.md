---
title: "Cinnamon on ubuntu12.04lts?"
date: 2012-04-28
forum: Desktop Environments
---

### Post by ubto66 on 2012-04-28
[SIZE=4]Anyone succeeded in running [http://cinnamon.linuxmint.com/](http://cinnamon.linuxmint.com/)[/SIZE]
 [SIZE=4]on ubuntu 12.04  lts?[/SIZE]
 [SIZE=4]I installed cinnamon like this:[/SIZE]
 [SIZE=4]sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable[/SIZE]
 [SIZE=4]sudo apt-get update[/SIZE]
 [SIZE=4]sudo apt-get install cinnamon muffin[/SIZE]
 [SIZE=4]When I log into ubuntu I choose cinnamon, but instead I get gnome classic.[/SIZE]

---

### Post by orange2k on 2012-04-28
It works fine here...

I don't know what causes your problem....:(

---

### Post by ubto66 on 2012-04-28
And you are running ubuntu **12.04  lts**?

---

### Post by jfeist1 on 2012-04-28
Hey ubto66, 12.04 lts clean install here, I am not getting gnome classic, but have found that Cinnamon with Muffin does not give the UI you might have been expecting coming from Mint 12. Is this maybe what you are seeing?

---

### Post by orange2k on 2012-04-28
> **ubto66 said:**
> And you are running ubuntu **12.04  lts**?

yes

---

### Post by ubto66 on 2012-04-28
I asked, because your tag says ubuntu 11. Then I don't know why I cannot get the cinnamon ui.

---

### Post by ubto66 on 2012-04-28
The ui I'm out for, is this one:
[http://www.youtube.com/watch?v=fTKBwqvCYrU](http://www.youtube.com/watch?v=fTKBwqvCYrU)
What I'm getting is the ui where applications and places are located on top to the left. I'm running ubuntu 12 in a virtualbox, could that be causing it?

---

### Post by kalkems on 2012-04-29
I installed cinnamon on my beta unstall and it worked perfectly. Doesn't cinnamon require compiz type graphics? Maybe this causes problems in virtualbox as the graphics there  aren't that perfect.

---

### Post by kurt18947 on 2012-04-29
> **kalkems said:**
> I installed cinnamon on my beta unstall and it worked perfectly. Doesn't cinnamon require compiz type graphics? Maybe this causes problems in virtualbox as the graphics there  aren't that perfect.

I'm not certain but I think cinnamon installs on top of gnome 3 which doesn't use compiz.  Doesn't gnome use mutter?  I'm not certain but I don't think it uses compiz.  You might be onto something with virtualbox though.  Cinnamon works fine for me on 12.04 and current Nvidia video drivers.

---

### Post by movieguy1920 on 2012-04-29
I have the same problem. I had loaded Gnome first, because Unity was having issues with my older computer, and then added the ppa. Logged out, logged into Cinnamon - and there was absolutely no change - I still have the Gnome settings. I had originally installed cinnamon on 11.10 with no problem, worked beautifully. Now...not so much...

---

### Post by skompier on 2012-04-29
Open a terminal and type:

```
cinnamon --replace
```

What happens?

---

### Post by 00negative on 2012-04-30
> **ubto66 said:**
> The ui I'm out for, is this one:
[http://www.youtube.com/watch?v=fTKBwqvCYrU](http://www.youtube.com/watch?v=fTKBwqvCYrU)
What I'm getting is the ui where applications and places are located on top to the left. I'm running ubuntu 12 in a virtualbox, could that be causing it?

It could be virtualbox issue, did you check 3d acceleration in settings of that machine? Or maybe try installing the virtualbox additions.

---

### Post by Sorinux on 2012-04-30
Can someone help with my problem?
I have Ubuntu Studio 12.04 and I have the MATE ppa and Cinnamon ppa added to the repositories. I went to the Synaptic to install them and when selecting Cinnamon, in the marked files for installing also Unity was present. What is happening? This is normal not to be able to install Cinnamon without Unity? Or this is happening only because I use a variation of Ubuntu?
For the moment I installed only MATE. 
I am interested to know if somebody noticed this and if there is a workaround.

---

### Post by RichardCain on 2012-04-30
I did a clean install of 12.04 with Cinnamon from the same repository but without Muffin, and it works perfectly, just like your clip.  I suggest you get rid of the muffin package.

---

### Post by joops on 2012-04-30
Hallo.

I did the same install like you without muffin and it works fine.

I tried to install the debs from [https://github.com/linuxmint/muffin/downloads](https://github.com/linuxmint/muffin/downloads) and the software center tells me that already installed a newer version.

---

### Post by Sorinux on 2012-04-30
Did you noticed if also Unity was installed together with Cinnamon?

---

### Post by BobVila on 2012-05-01
I'm in the same boat. Looks like it's got something to do with the nvidia driver (for me, at least). If you remove nvidia-current, Cinnamon will load just fine. I wonder if it would work if I switched from xinerama to twinview, but I'd rather not lose two of my four monitors...

---

### Post by cloyd on 2012-05-01
> **ubto66 said:**
> [SIZE=4]Anyone succeeded in running [http://cinnamon.linuxmint.com/](http://cinnamon.linuxmint.com/)[/SIZE]
 [SIZE=4]on ubuntu 12.04  lts?[/SIZE]
 [SIZE=4]I installed cinnamon like this:[/SIZE]
 [SIZE=4]sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable[/SIZE]
 [SIZE=4]sudo apt-get update[/SIZE]
 [SIZE=4]sudo apt-get install cinnamon muffin[/SIZE]
 [SIZE=4]When I log into ubuntu I choose cinnamon, but instead I get gnome classic.[/SIZE]


I did the same, and get the same results. I know that I have an old ati graphics card . . . like to never got it to run unity . . . I know what I did, but have no idea as to why it made it work. The interesting things is, I'm always running Unity 2d, even when I specify Unity. Old ATI graphics card?  

Got Cinnamon to run on another machine, and first impression is that I like it a lot.

---

### Post by livewire94 on 2012-05-03
I installed Cinnamon with Muffin and it seemed to work but Cinnamon also installed Gnome Classic and Gnome Classic no effects.  

Cinnamon is slow on my PC.  

How would I uninstall Cinnamon with Muffin?  I don't want to use it and would like to take it back off.

Thanks

---

### Post by RichardCain on 2012-05-04
> **livewire94 said:**
> I installed Cinnamon with Muffin and it seemed to work but Cinnamon also installed Gnome Classic and Gnome Classic no effects.  

Cinnamon is slow on my PC.  

How would I uninstall Cinnamon with Muffin?  I don't want to use it and would like to take it back off.

Thanks

Open a terminal and enter:
```
sudo apt-get purge cinnamon muffin
```
Then open Software Sources and remove these two lines:
[FONT="System"]http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main
[http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu) precise main (Source Code)[/FONT]

---

### Post by ubto66 on 2012-05-05
[SIZE=4]Thank you for your answers.[/SIZE]
 [SIZE=4]I tried to install ubuntu 12.04 lts on a usb stick. And now cinnamon runs.[/SIZE]
 [SIZE=4]It's not that stable when I make settings adjustments, and when it freezes[/SIZE]
 [SIZE=4]I have to use the reset button. But maybe that is to be expected, because the cinnamon website says, it's for ubuntu 11. Maybe an update solves that.[/SIZE]
 [SIZE=4]Cinnamon would not run in my virtual box config.[/SIZE]
 [SIZE=4]What I can't find, is where to make task bars broader/higher? Not in [/SIZE] 
 [SIZE=4]unity, not in gnome classic no effects, and not in cinnamon.[/SIZE]
 [SIZE=4]Thanks.[/SIZE]

---

### Post by Sorinux on 2012-05-08
It seems that nobody can explain why Cinnamon needs Unity. 
For those that want to install Cinnamon on top of Ubuntu 12.04, keep trying until you get lucky, if you do... I installed also Ubuntu Server 12.04 and Ubuntu 12.04 and all the time I end up with Gnome Classic, butt no Cinnamon. Sometimes also the wireless was saying &#8221;Device not managed&#8221; (or something like that).
It seems that Ubuntu is getting worse day by day!!!!!!!!!
Seems like I have to use Win 7 until Mint 13 is coming out!
Good luck Ubuntu, but this is why you have less users! Just check Distrowatch!!!
):P):P):P

---

