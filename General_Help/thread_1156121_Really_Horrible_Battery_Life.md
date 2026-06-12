---
title: "Really Horrible Battery Life"
date: 2009-05-11
forum: General Help
---

### Post by jlacroix on 2009-05-11
Hello everyone.

I have a Gateway M7315u laptop. Recently, I'm getting about an hour or less of battery life, and this machine is less than a year old. I'm a student, and this has prevented me from doing homework when I am out on the road, and has been VERY frustrating to me.

Up until recently, my laptop shared it's hard drive with Windows Vista. Vista claimed about 50GB of my 500GB drive and Kubuntu got the rest. I used to do my homework while I booted my machine under Vista, because there were some programs that my school demanded I use that are proprietary to Windows. With Vista, I got about 3 hours of battery life on this machine which was plenty.

Now, I passed the class that required proprietary programs and I went ahead and removed my Vista install completely. In fact, I wiped my drive and started it over with Kubuntu 9.04.

Around the same time as I went Kubuntu-only, the battery life has been really horrible. I keep the screen brightness low (it's impossible to control the screen brightness on this laptop with the kernel that ships with Jaunty, so I lower it at the POST screen before Linux boots) and I keep the sound turned down as well. I keep all my resources, including CPU throttling as low as I can, basically at the same levels as I did when I had Vista installed.

I'm thinking one of the following is the case:

1.) Kubuntu is unable to manage the battery properly and drains it fairly quickly due to a defect or bug.

2.) All of this is a coincidence and my battery became defective around the time I wiped my drive.

Basically after a full charge, Kubuntu's battery widget informs me that I have about an hour and twenty minutes of battery remaining. During a one hour lunch break while I work on my homework, the battery has drained to the point my laptop is useless during the following day's lunch break.

Is there any way I can tell what is causing this?

Thanks so much you guys :popcorn:

---

### Post by alexandari on 2009-05-11
hmm did u check the settings of the battery? I mean it`s set to powersave on default when it`s on battery life. You can change the performance settings. Have you tried disabeling both Kwim composing and Dim display from the battery settings?

---

### Post by Alterax on 2009-05-11
Another option that should be looked into is the powertop program.  Install it and run from the terminal "sudo powertop".

Go through its suggestions.  Many will not make sense to you, but the bulk of the time there will be an option of doing what it says to.  Do it.  That should reduce the amount of power you use by a fair bit.

I've also gotten a performance and power boost by dropping my screen colors from 24-bit to 16-bit.  As I'm on a laptop myself, I don't really notice the difference, but the amount of RAM used per screen refresh and the resultant amount of power required to maintain and update those values definitely notices the change.

---

### Post by jlacroix on 2009-05-11
> **alexandari said:**
> hmm did u check the settings of the battery? I mean it`s set to powersave on default when it`s on battery life. You can change the performance settings. Have you tried disabeling both Kwim composing and Dim display from the battery settings?

KWin compositing is on, I forgot about that.

I set the battery saver mode to either "Powersave" or "Extreme Powersave". 

As far as dimming the display, that is impossible since no one has figured out how to get that to work on this laptop yet. I do dim the display during POST when I first turn it on, which is the only time I am able to adjust the brightness.

> **Alterax said:**
> Another option that should be looked into is the powertop program.  Install it and run from the terminal "sudo powertop".

Go through its suggestions.  Many will not make sense to you, but the bulk of the time there will be an option of doing what it says to.  Do it.  That should reduce the amount of power you use by a fair bit.

I've also gotten a performance and power boost by dropping my screen colors from 24-bit to 16-bit.  As I'm on a laptop myself, I don't really notice the difference, but the amount of RAM used per screen refresh and the resultant amount of power required to maintain and update those values definitely notices the change.

I'll try powertop. As far as lowering the colors, I don't know about that, this worked fine in Intrepid. (I think I forgot to mention that part, sorry).

---

### Post by jlacroix on 2009-05-12
I tried Powertop, and it has made a pretty good increase on my machine. I followed everything it said to do. I'm hoping that the changes I made won't negatively impact performance while I'm plugged into AC Power, can anyone elaborate? Also, are the changes I made going to stick when I reboot the machine?

Powertop gave me around 45 minutes extra. It's still not to the point where it used to be, but we're definitely getting somewhere!

What else might I try?

YOU GUYS ROCK

---

### Post by farlander762 on 2009-07-12
I have no idea what to tell you about Kubuntu.  I am running Ubuntu Jaunty 64 bit and have over 2 hr battery life (about 1:45 if watching a DVD) and I also have an M7315u.  

That might be something to look at...are you running the 32 bit or the 64?  The 64 will definitely give better battery life and faster responses.

---

### Post by jlacroix on 2009-07-12
> **farlander762 said:**
> I have no idea what to tell you about Kubuntu.  I am running Ubuntu Jaunty 64 bit and have over 2 hr battery life (about 1:45 if watching a DVD) and I also have an M7315u.  

That might be something to look at...are you running the 32 bit or the 64?  The 64 will definitely give better battery life and faster responses.

64-bit here. I am not sure if there is something specific in Kubuntu that is draining the battery life. I know that the screen brightness cannot be fixed to work though so it sucks I Have to adjust the brightness at the BIOS screen. :(

As far as the battery life it really sucks. I am probably getting rid of this laptop because keys are falling off the laptop and Acer/Gateway will not cover it even though it's not under warranty. That's another story though.

---

