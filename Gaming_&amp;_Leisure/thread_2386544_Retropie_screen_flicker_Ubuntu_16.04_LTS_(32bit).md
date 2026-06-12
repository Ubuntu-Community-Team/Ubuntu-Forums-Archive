---
title: "Retropie screen flicker Ubuntu 16.04 LTS (32bit)"
date: 2018-03-07
forum: Gaming &amp; Leisure
---

### Post by jameswilles on 2018-03-07
Hi there,

I'm a new user when it comes to Ubuntu so please bare with me... I recently decided to breathe some life in to a really old desktop PC I had sitting around by installing Ubuntu 16.04 LTS (32bit) and installing Retropie.

I'm having a screen flicker issue when I open retropie? I don't have the issue when on the Ubuntu desktop screen.
this is my first ever install of Ubuntu so wondering if I have some drivers missing for the graphics card?



My PC spec:


[LIST]
[*]Dell Dimension 8300
[*]Intel Pentium(R) 4 CPU 3.20GHz
[*]2GB Ram
[*]ATR R350 graphics
[*]VGA output to a Cibox C1905 moniter 1440 x 900 pixels
[*]Ubuntu 16.04 LTS (32bit)
[*]Emulationstation V2.7.5RP
[/LIST]

Hope I've provided enough information if you need more let me know and I will do my best to get it.

Thanks in advance

---

### Post by cruzer001 on 2018-03-07
Download link please.

---

### Post by jameswilles on 2018-03-07
I downloaded it from here:

[https://mirror.umd.edu/ubuntu-iso/16.04/](https://mirror.umd.edu/ubuntu-iso/16.04/)

then selected: 

ubuntu-16.04.4-desktop-i386.iso [[FONT=microsoft sans serif][/FONT]]("https://mirror.umd.edu/ubuntu-iso/16.04/ubuntu-16.04.4-desktop-i386.iso")
[[FONT=microsoft sans serif][/FONT]]("https://mirror.umd.edu/ubuntu-iso/16.04/ubuntu-16.04.4-desktop-i386.iso")[URL="https://mirror.umd.edu/ubuntu-iso/16.04/ubuntu-16.04.4-desktop-i386.iso"]
[/URL]

---

### Post by cruzer001 on 2018-03-07
No, the download link for Retropie.

I can only find a download for ARM architecture (Raspberry).

---

### Post by mörgæs on 2018-03-07
Considering its age the R350 is a fairly strong card but still I suggest that you try X/Lubuntu or another lighter distro in stead of Ubuntu.

---

### Post by jameswilles on 2018-03-07
@cruzer001 oh ok, I got it here:

[https://github.com/retropie/retropie-setup/wiki/Debian](https://github.com/retropie/retropie-setup/wiki/Debian)

i downloaded it by just copying and pasting the code in to terminal

---

### Post by jameswilles on 2018-03-07
@[**[COLOR=#DD4814][B]mörgæs**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=939075") ok i'll try that, thanks. :)

---

### Post by jameswilles on 2018-03-07
Still no luck :( still getting exactly the same flicker after installing Lubuntu 17.10.01 and reinstalling retropie via the script from [https://github.com/retropie/retropie-setup/wiki/Debian](https://github.com/retropie/retropie-setup/wiki/Debian)

any ideas what else this could be?

this is what it looks like:
[https://www.youtube.com/edit?o=U&video_id=YZ_lTjNXoQw](https://www.youtube.com/edit?o=U&video_id=YZ_lTjNXoQw)
 
something else I have discovered if I press f11 which takes me out of full-screen mode the flicker stops??

---

### Post by cruzer001 on 2018-03-08
> **jameswilles said:**
> something else I have discovered if I press f11 which takes me out of full-screen mode the flicker stops??
That suggest your system resources are being used to their limits.  Try monitoring your CPU & RAM usage with htop.
```
sudo apt-get install htop
```
To run htop:
```
htop
```

---

### Post by jameswilles on 2018-03-08
i opened htop, then emulation station, then windowed emulationstation & htop showed

CPU.......18 to 25%
Mem......169M/1.97G

---

### Post by cruzer001 on 2018-03-08
169M sounds like normal lubuntu usage.  1.97G?  Are you saying that ram is maxing out?  Google tells me the your box supports 4G of ram.  I bet for 10 or 20 bucks you could upgrade ram to 4G.

---

### Post by jameswilles on 2018-03-09
No, what I ment was its using 169m of 1.97G available with retropie running. So there is still pleanty of fuel in the tank. 

If i can get retropie to run without the flicker on this system then i probably would upgrade it to 4gb. But other than a retropie system i cant think what else to use this dinosaur of a computer for? 

I cant think what else could cause this flicker? I cant find any resolution settings in the retopie config ether? 

I tried to turn the computer resolution down as well but after I click apply it goes to a black screen with a cursor and stays that way... I think i have greater underlying problems with the system. 

Do I need to set anything up with Lubuntu after an install, I did nothing regarding drivers.... I just installed it and ran with it?

---

### Post by jameswilles on 2018-03-09
One other thing, I read somewhere else that overscan caused a flicker for someone else, but that was just on the splash screen, I was going to try and turn that off, but i cant find the overscan option anywhere ether?

---

### Post by mörgæs on 2018-03-09
I wouldn't call it a dinosaur. It's one of the strongest within the 32 bit breed (maybe it's actually an old 64 bit processor; we don't know yet) and it should be capable of normal browsing usage, Libreoffice and watching films.

If you want old school gaming have you tried installing games from the Ubuntu repository without Retropie?

---

### Post by jameswilles on 2018-03-10
Thing is, what I like about retropie is the nice frontend, where I can simply turn on the system and it boots straight into retropie and all the emulators are accessible from one place with a control pad. I wanted to have the system in my living room with a couple of USB connected controllers, then operate the whole thing without the use of keyboard and mouse. I just wanted a nice neat & easy to use system, I know the raspberry pi will do the same thing but I just thought with it sitting around doing nothing, it would be a great use for it. 

does anyone have any suggestion what else could cause a screen to flicker when retropie is running? if not I think I'll give up with it & it'll have to go back into the loft for another 10 years :lol:

when it comes to doing anything else on a pc I use my i7 Extreme, 32gb ram, Nvidia GTX 970, maybe I'll install retropie on that machine? Gamecube should run lovely on it LOL

---

