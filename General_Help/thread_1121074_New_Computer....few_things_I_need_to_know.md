---
title: "New Computer....few things I need to know"
date: 2009-04-09
forum: General Help
---

### Post by hyburn on 2009-04-09
hey guys,

I recently fried my intel board(what a surprise) I am having a brand new asus barebone kit mailed to my house. 

1. can I just plug my linux HD in and boot up? or do I need to put my ubuntu CD in first to load the kernal.

2. will my Ubuntu recognize the new hardware right away(or do I need to run an update.

P.S. this is my first time switching HD's into a new tower. Should I be worried, about problems arrising?

-hyburn

P.P.S. please leave responses and I will grant thanks to all that help. I JUST WANT MY LINUX BACK. NOOOOOO MORE WINDOWS!!!!!

---

### Post by lisati on 2009-04-09
Good question.
If the hardware is sufficiently similar to your previous installation I don't anticipate many problems. You'll probably find that you still have a little bit of work, but not having done similar I'm not too clued up on the specifics.

---

### Post by Pasdar on 2009-04-09
From my experience with Windows in the same situation, and it should not be any different with linux in this case, it should not work. Your OS has been installed/configured to work with a set of hardware and you just want to put in your HD and make it run? It won't work, it shouldn't... it needs to be installed on your new system. However if your hardware is very similar, thats something else.

But it won't hurt your system to try. Whether it will recognize your hardware right away or if it would need updates depends on what kind of hardware you have.

---

### Post by hyburn on 2009-04-09
I'm affraid my linux will lock me out. thats the controller thrower of linux :@

---

### Post by miegiel on 2009-04-09
I replaced my motherboard a few months back with a better one with a similar chip set and I didn't need to reinstall ubuntu. It just booted (and M$ windows just crashed :-\"). New hardware installed automatically, as far as I can remember.

If your new barebone differs a lot from your old motherboard it might not work though. But I see no reason not to try booting to your installed ubuntu.

> **hyburn said:**
> I'm affraid my linux will lock me out. thats the controller thrower of linux :@

Lock you out!? In the worst case you just need to reinstall (I hope you've put your /home on a seperate partition :))

---

### Post by hyburn on 2009-04-09
my old board was an intel 775. the new board is an Nvidia something or other. issues?

---

### Post by coffeecat on 2009-04-09
> **Pasdar said:**
> From my experience with Windows in the same situation, and it should not be any different with linux in this case, it should not work. Your OS has been installed/configured to work with a set of hardware and you just want to put in your HD and make it run? It won't work, it shouldn't... it needs to be installed on your new system. However if your hardware is very similar, thats something else.

Sorry, that just isn't so. You can't make an analogy with Windows, which is a completely different OS. The reason Windows won't boot up if you change all the hardware is because changing too much hardware will activate certain anti-piracy measures built in to Windows. Windows keeps a sort of inventory of hardware that it is installed to. It even keeps a record of the MAC of your network card. You can change your RAM, or your graphics card, and so on, so long as you do it over a period of time, but change too much too quickly and Windows will fail. It is programmed to fail.

Linux is a free system with none of this nonsense. Moreover, drivers for the vast majority of common hardware are already installed as kernel or kernel module drivers. When Linux boots up it detects all hardware afresh. Therefore, so long as the new hardware is not too exotic, it will boot up.

However, some things may fail, because of configuration systems independent of the kernel. Sound may fail and need to be reconfigured. And the most likely serious failure is the xserver. For example, say the first machine had an AMD graphics card with the appropriate driver, configured from /etc/X11/xorg.conf, and the second machine had a nvidia driver. Then at bootup in the second machine the xserver would fail. Fixable, if you are comfortable at a command console, but unnerving for a beginner.

Four years ago, I installed a very early version of Foresight Linux to a machine with an AMD processor and VIA chipset motherboard  (with VIA graphics). Fortunately, the xserver was set up with the vesa driver. I then took the hard drive out and put it in a machine an Intel processor, Intel motherboard and Intel graphics. I booted up and **EVERYTHING WORKED**.

**hyburn**, give it a try. You have nothing to lose. :wink:

---

### Post by SoCalChris on 2009-04-09
> **coffeecat said:**
> The reason Windows won't boot up if you change all the hardware is because changing too much hardware will activate certain anti-piracy measures built in to Windows.

I can't comment on whether Ubuntu will boot properly or not, but the problems with Windows not booting properly isn't just related to their activation scheme. As far back as Windows 2000 (Before they required you to activate each copy), and possibly NT this wouldn't work. Booting after putting your drive into another computer caused all sorts of nasty errors. I'm pretty sure that it had to do with things in the registry expecting a certain configuration.

> **coffeecat said:**
> You can change your RAM, or your graphics card, and so on, so long as you do it over a period of time, but change too much too quickly and Windows will fail. It is programmed to fail.

This doesn't always work properly either. I replaced a faulty DVD drive on my grandfather's XP machine, it required a reactivation afterwards. The reactivation failed, and I had to call MS and convince them that the OS wasn't pirated before they would activate it. ](*,)

Everything that I've read says that what I did should not have triggered a reactivation, but it did.

---

### Post by coffeecat on 2009-04-09
> **SoCalChris said:**
> Booting after putting your drive into another computer caused all sorts of nasty errors. I'm pretty sure that it had to do with things in the registry expecting a certain configuration.

Yes, of course, thanks for that - the registry. :-| I'm sure you're right that it's the registry that's the primary cause of the boot failure. But the activation scheme is there to make doubly sure. Two reasons not to use Windows then!

> **SoCalChris said:**
> This doesn't always work properly either. I replaced a faulty DVD drive on my grandfather's XP machine, it required a reactivation afterwards. The reactivation failed, and I had to call MS and convince them that the OS wasn't pirated before they would activate it. ](*,)

Three reasons! :evil:

---

### Post by hyburn on 2009-04-09
whew,

thats what I wanted to hear. AMEN to linux gods weeeeeeee. thanks. I'll let you guys know when I get back up and running.

time for the thanks. how do I do thgat again? lol been a while

---

### Post by Pasdar on 2009-04-09
> **coffeecat said:**
> Sorry, that just isn't so. You can't make an analogy with Windows, which is a completely different OS. The reason Windows won't boot up if you change all the hardware is because changing too much hardware will activate certain anti-piracy measures built in to Windows. Windows keeps a sort of inventory of hardware that it is installed to. It even keeps a record of the MAC of your network card. You can change your RAM, or your graphics card, and so on, so long as you do it over a period of time, but change too much too quickly and Windows will fail. It is programmed to fail.
I find it very doubtful that Linux could handle it, especially in the way it is built, while windows can not. While linux tries to configure itself as much as possible to the hardware you have installed, compared to that Windows is almost like a superficial layer... and this still makes it crash.
What you say is only partly true. It is true that from VISTA and later they keep a record of what hardware you have running and it will be licensed to that hardware. Even changing the processor means you need to buy a new windows license, as written in their terms.
However, this is not the reason it will crash. It will crash because it can simply not make the jump from one hardware configuration to another. I'm not talking about just any hardware. The problem caused, in some cases, when putting in a new Graphics card is easily solved. I'm talking about things like motherboards and what not.
I've worked as windows helpdesk, so i think i know what im talking about.. at least about windows.

Anyway, nothing will happen if you just try it.

---

### Post by Woody1987 on 2009-04-09
it WILL work. I have done it dozens of times, and it ALWAYS worked without a problem.

---

### Post by miegiel on 2009-04-09
> **Woody1987 said:**
> it WILL work. I have done it dozens of times, and it ALWAYS worked without a problem.

I tend to agree, but I haven't used linux long enough to be able to say "it always works" from experience. I just don't build new PCs that often :)

Something I did do about a year ago was install ubuntu on my mp3 player (it's 40GB enough room to make some room for my music plus a ext3 and swap partition). The plan was to leave my PC at home, but take my ubuntu with me while visiting a friend abroad. My PC then was a old AMD athlon XP and my friend had a pretty new Intel laptop. Hardware wise barely on the same continent :D. The only thing that didn't work was the GUI and all I had to do to fix it was edit some stuff in /etc/X11/xorg.conf

---

### Post by speedwell68 on 2009-04-09
I'm not trying to teach anyone's grandmother to suck eggs here.  But please make sure you have a backup of your files on that HDD before you try any of this.

---

### Post by Woody1987 on 2009-04-09
i think the fact that its possible to install ubuntu onto an USB stick and then boot that stick on any computer and run the operating system from it without having to reinstall everytime kinda proves that it is easily possible to simply move your hdd to a brand new computer. Please note that installing onto an USB stick is not the same as running a livecd, the OS runs just as if it were installed onto a normal HDD.

---

### Post by Pasdar on 2009-04-10
> **Woody1987 said:**
> i think the fact that its possible to install ubuntu onto an USB stick and then boot that stick on any computer and run the operating system from it without having to reinstall everytime kinda proves that it is easily possible to simply move your hdd to a brand new computer. Please note that installing onto an USB stick is not the same as running a livecd, the OS runs just as if it were installed onto a normal HDD.
It's not the same. Because the LiveCD/USB configures itself to run with your PC and loads part of its information into the memory. It does this upon every boot into the LiveCD/USB. That's why the LiveCD/USB needs more memory to load and that's also the reason why it remembers things upon second boot into LiveCD.
That's why it takes significantly longer to load from the LiveCD/USB. The low speed of loading from LiveCD is not related to your drive speed, if that is what you thought.

---

### Post by Tony Flury on 2009-04-10
I moved my HD from an HP laptop to a custom built none branded laptop and it booted up fine - despite all the hardware being different.

You may need to do some work on the graphics and wireless cards (if you have one), and maybe some of the other peripherals - but in my experience it should work ok.

---

### Post by Tony Flury on 2009-04-10
> **Pasdar said:**
> I find it very doubtful that Linux could handle it, especially in the way it is built, 

I can confirm that linux can absolutely handle it. My new laptop has a  entirely different m/b, CPU, graphics card etc - and linux booted up without a problem - the only thing i had to do was fix the X server to get high-rez graphics working, and download a new wireless card driver. But I can guarantee that my Linux HD booted up without any problems - grub and everything worked out of the box.

---

### Post by miegiel on 2009-04-10
> **Pasdar said:**
> It's not the same. Because the LiveCD/USB configures itself ....

**Pasdar**, I think you should let it go. **Woody1987** wrongly assumed I used the LiveCD/USB ubuntu on my mp3 player. In fact I did a normal ubuntu installation. You're just confusing the matter by transposing your windows experiences to linux.

I'm just saying that, from the little experience I have with this, **hyburn** should just try booting his old ubuntu installation on his new hardware. Other people have confirmed that, from their experience, it should work. And unless you can share experiences with us where it didn't work, I can only assume your assumption that "it won't work" is purely theoretical.

I think this thread is better served with mentioning problems **hyburn** might encounter when he boots his old installation on his new hardware.

On that note, besides possibly needing to edit /etc/X11/xorg.conf, as I mentioned earlier. There might be a small hiccup with the network configuration. I just realised that when I boot ubuntu complains about a missing eth0, that's the onboard network of my old motherboard. The onboard network of my new motherboard is called eth1, and to my best recollection it only needed to be configured.

I think it's safe to say that **hyburn**'s old ubuntu installation will work with his new hardware regarding drivers, etc. But that he might need to reconfigure stuff like the network and /etc/X11/xorg.conf and, who knows, maybe something else too.

---

### Post by hyburn on 2009-04-18
go on, I cant even get into my system to do a back-up genious, did you read the first post? sorry to sound rude, but Feck I have no back-ups. I am moving the HD from one PC to another. How do I load the Linux kernal to the motherboard? I know its not a simple plug and play system, or is it? I wont need to re-install ubuntu on my HD will I?

can we all agree on a final answer? 

Mr. Alex Trebec is waiting (HA HA HA jeopardy humour)

---

### Post by mercenaryhmster on 2009-04-18
it will work.  at most, some user-land configurations will need to be changed.

---

### Post by hyburn on 2009-04-19
can you all please explain the situation you mention? if you think it wont work, please let me know why. and how to fix the situation if it arrises.

---

