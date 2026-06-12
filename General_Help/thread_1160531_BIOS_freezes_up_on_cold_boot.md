---
title: "BIOS freezes up on cold boot"
date: 2009-05-15
forum: General Help
---

### Post by originalsynthesis on 2009-05-15
So I've recently built a new machine, a pretty basic setup. My setup looks like :

Asus M2N68-AM SE2 motherboard
    which has these components:
    AMD Athlon64 X2 5000 processor, @ 2.6ghz      
    nvidia geforce 7025/nforce 630 chipset
    a Crucial 2gb ddr2 memory stick in one of the two slots
     
as for the BIOS, the Mobo manual states:
   8mb Flash ROM, AMI BIOS, PnP, DMI2.0, WfM2.0,
   ACPI2.0, SM BIOS 2.5
   (dont know if it matters, the chip itself says "winbond"    on it)

It's all powered by a 450watt power supply
And ive got a 320 gb SATA hd hooked up to it, as well as an older dvd rom drive(on a budget...)

I took a lot of care hooking everything up, double checked my connections, all parts are definitely getting power. My cpu fan seems to be working well enough, the hottest i've seen the cpu get to was about 50 degrees c.

I put a copy of xp pro on to get it working and run some games to check out the graphics chip, and everything on the OS side worked fine. I did seem to have a wierd issue installing the drivers from the motherboards support disk. It had a bunch of different ones besides the graphics drivers. The one that acted up was the nvidia ethernet driver, which seemed a bit odd, as i've never known nvidia to do anything besides sound and video. When the installer got to this driver, it said that older drivers were present and the system would need to delete them and reboot to install the new ones. I let it do it's thing a couple times and it never seemed to erase the drivers. the ethernet port worked fine anyway, so i just ended up installing everything besides that one driver. No problems.

 However, I turned it off later that day and left for a few hours. I had shut down from windows and left the power supply on. Upon coming back and booting up again, no video was going to the monitor, mouse and keyboard had no power. The hard drive spun up, and the dvd drive was working OK. It was late so after trying a couple restarts and a couple cold boots, i just killed the power supply (no other way to shut down). I turned it on the next day, booted up just fine. No damage to files on disk, xp seemed healthy as a lark. 
   I restarted and checked the BIOS setup to find nothing amiss, so i tried shutting down altogether and booting. It happened again. To me, everything pointed to something being up with the BIOS, so i cleared it with the jumper, replaced it to normal mode and booted successfully, as if nothing had happened. Once again, no problems with xp or the bios settings.  I tried a cold boot one more time (xp shut down,power supply off) and the same problem occured. 
  This time, clearing the BIOS did not seem to do a damn thing except make it act a bit funkier. This time, the power and hdd leds were flashing on and off in succession. Neither restarting or cold booting changed it. I pulled the hd and the dvd drives out, same thing. I tried clearing Bios once or twice more with different hardware configs (nothing, hd + no dvd, dvd + no hd). I finally gave up on it and shut everything off and left it for a few hours. 
  Surprise!!! It booted up again normally after some time had passed. This was yesterday, and since then i haven't shut it down. Im considering a few things here: 

a. somehow the bios is corrupted already, or maybe the chip is faulty. Im thinking about flashing it, but im leery of doing that until i get some more informed advice on this.  

b. something is up with voltages or power flow. maybe too much power is going through the bios chip, and its overheating? A friend of mine claimed he had trouble when he installed a new 450 watt pwr supply to replace an old 250 watter on his pc. He says that it acted up for the first week he had it, nothing like what my machine is doing, just glitchy stuff here and there. After leaving it running for a few days, it was fine. The theory he gave was that the circuitry needed time to adjust to the larger power flow. Never heard that before, but its interesting.....   

c. maybe a borked motherboard (but its brand freaking new and everything else seems fine!!)

I am far from being an expert here, but im sure that the fact that it works fine after a cool down period with no power to the system is a big clue. I was pretty freaked out, though, when the second time i reset the bios, it acted even worse. So I'm admitting a temporary defeat here, I don't know if resetting too much can cause problems or not. Oh, the first time this happened, i tried pulling the BIOS battery for a moment as well with no change. 


It seems that the next thing to try would be to flash the bios, but I'm wondering what someone more knowledgeable thinks of all this. Everything in the machine is brand spanking new, with the one exception of the dvd drive i put in. It isn't exactly archaic, but from around '01-'02.   

If any more specs are needed just ask, i tried to give as much info as i could.

thanks for your time....

---

### Post by originalsynthesis on 2009-05-15
i dont know why i put this in 'general', could a mod put this into hardware for me?

---

