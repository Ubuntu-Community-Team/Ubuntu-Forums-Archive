---
title: "Fiesty hangs like windows"
date: 2007-04-30
forum: Desktop Environments
---

### Post by krypto_wizard on 2007-04-30
I did a fresh install of Fiesty and often when using certain apps it just hangs like windows. No other windows would open not even terminal to kill the process. Apps when this hang happens are terminal (while installing a new app), while using firefox, while using synaptic etc.

I am using Toshiba Satellite A70-S249 Laptop with atheros WiFi card and ATI 9000 radeon graphics card, 3.06 P4 with multithreading CPU etc.

Any help will be greatly appreciated.

Thanks

---

### Post by krypto_wizard on 2007-05-01
Please help with this problem.

---

### Post by blamecanada on 2007-05-01
Possible compatibility issues with some of your hardware maybe.

---

### Post by krypto_wizard on 2007-05-06
This is the hardware config of my laptop. 
[http://www.superwarehouse.com/Toshiba_Satellite_A70-S249/PSA70U-00L00F/p/440711](http://www.superwarehouse.com/Toshiba_Satellite_A70-S249/PSA70U-00L00F/p/440711)

It hangs like windows suddenly sometimes when some app is running while sometimes just hangs if it is standalone.

What should I do to make it work. I already have tried twice. Please help.

Thanks

---

### Post by bailout on 2007-05-08
Despite all the hype about linux stability this does happen. I have had it happen quite frequently with both dapper and edgy. Dapper was definately linked to my wireless usb device but edgy was a bit more random. I think it will probably be due to your hardware but trying to identify exactly what is causing it and fixing it can be difficult.

---

### Post by Ozeuss on 2007-05-08
did you check memory and cpu usage to detect the cuplrit? you know, system monitor, top, free, etc.
when i did the beta install of feisty, it didn't like the swap's uuid settings, and did not turn it on (i had to swapon manually), which slowed my system terribly. after editing fstab to the regular system everything worked fine

---

### Post by ridgeland on 2007-05-08
I expect the low RAM 256MB and/or swap error.
What's in /etc/fstab?
What does does 'free' show?
Watch top while launching the program that hangs the system.  Any clues?
With just 256MB of RAM maybe Xubuntu would be better.
I once had swap working fine but a later install on a different partition formated the swap space and gave it a new UUID!  Then swap was no longer there.  So now I edit fstab to dump the UUID and use the /dev/ address.
Also when updatedb is running each morning on my machine I can sometimes notice things are not as fast. (380GB of hard drives to index).  Could be too many cron jobs etc.

---

### Post by orb9220 on 2007-05-08
> I did a fresh install of Fiesty 

Did you try edgy or dapper liveCD?

Just cuz it is the latest does not mean it is the best for your setup.

---

### Post by jimbo99 on 2007-05-08
Boot with the feisty livecd and run the memory tests over and over.  If you only have 256mb of ram (some used by the video) you should consider more memory for your laptop (if it is possible).

---

### Post by FishRCynic on 2007-05-13
i don't know if this will help - i have 896 m of ram but this worked for me

[http://ubuntuforums.org/showthread.php?t=417819&page=2](http://ubuntuforums.org/showthread.php?t=417819&page=2)

---

### Post by jimbo99 on 2007-05-13
There's not enough information.  You stated that you were having problems with linux hanging like windows.  What does that mean?  Does your Windows hang too?  Are you talking about having problems with Windows lock and you switched to Ubuntu to see if the problem went away?

If this is so, then it is your computer, something is wrong with it.  You need to get your hardware checked out.

How many times have I had to tell people that it is impossible to resolve software problems when the core cause is your hardware.

FIX THE HARDWARE FIRST!

---

### Post by Wiebelhaus on 2007-05-13
happening in windows & Linux , sounds like hardware issues , Laptop..... I bet thermal problem , research this on the mighty google.

---

