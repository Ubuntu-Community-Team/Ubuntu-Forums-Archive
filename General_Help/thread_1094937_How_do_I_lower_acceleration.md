---
title: "How do I lower acceleration?"
date: 2009-03-13
forum: General Help
---

### Post by berrypievision on 2009-03-13
New user to Ubuntu and I want to know how to lower acceleration on my computer in Ubuntu?

---

### Post by nelskurian on 2009-03-13
What you mean by lower accileration?

---

### Post by berrypievision on 2009-03-13
I mean lower the hardware acceleration.  It was easy to do on Windows, all you did was right click and then you'd get the option to lower the graphical acceleration and such.  Not sure how to do that on Ubuntu.  Its only a temporary thing I want to try out.

---

### Post by nelskurian on 2009-03-13
Do ypu want to save your menory and cpu usage..Fot that you can goes to 'appearence preferences' by just right click on the desktop and goes to 'visual effects'and select 'none'.This will reduce the graphical acileration.

---

### Post by berrypievision on 2009-03-13
Thanks, I will try that out.  I'll come back if there is any issues.  Thanks very much!

---

### Post by berrypievision on 2009-03-15
While it does lower the acceleration somewhat when I do that, it doesn't lower it enough.  I am having issues with compiling videos and with using multiple programs, as the acceleration seems to hit a limit at times and freeze the computer.  Is the best bet I have to go into safe mode?

---

### Post by 3rdalbum on 2009-03-15
No, you are applying your knowledge of Windows problems to Linux. On Linux, there is no such thing as too much (graphics?) acceleration. Heck, I don't even think there is such a thing on Windows, but not being a Windows user I don't know for sure.

What issues are you having with videos? Or compiling? What do you mean by "the acceleration seems to hit a limit"?

What graphics card do you have? Are you using proprietary drivers? Have you tried updating to the latest version of your proprietary driver?

---

### Post by linuxd00 on 2009-03-15
There should be a formular for help like:

Headline: (eg. Lower acceleration)

What i want to achieve in the end: eg."i want to enconde videos and mp3 wihtout redering my system unusable when the cpu usage hits 100"

What i think is the way to do it:"lowering the acceleration"

what i meant in the last point:"i want to lower the acceleration of the graphics hardware like in windows"



my wild guess is that you want to somehow lower the cpu or gpu usage so that you get more power in other programs?
First of all i guess that you want to lower graphics effects because your graphics card manufacturer claims that the GPU supports video rendering. so you want to turn off the fancy effects to improve video renreding?

how about turning compiz off for a while?
does the gpu renders the video under linux at all?



what other programs are you using? (try ffmpeg for the fastest encoding of all!)
what is your goal?

explain all you can if you need help. (and dont threaten to go back to windows if we dont solve your problem ;))

---

### Post by berrypievision on 2009-03-15
> 
What issues are you having with videos? Or compiling? What do you mean by "the acceleration seems to hit a limit"?

Well, I guess I was talking sort of blind there, I really don't know if it is an issue with acceleration.  I just assumed.  The problem I have with making videos on programs like Kdenlive or Open Movie Editor is basically that if a video takes longer than a minute to encode and process, the computer freezes.  Also (but this has happened more rarely now and doesn't happen periodically or always when using the computer) sometimes the computer just freezes for no apparent reason.  Again, I assumed it was an acceleration issue.

> 
What graphics card do you have?

Nvidia Geforce 6800 GS.

> Are you using proprietary drivers? Have you tried updating to the latest version of your proprietary driver? 

No, kind of low on money, so at this moment, I have to stick with this bucket of a computer.

> 
my wild guess is that you want to somehow lower the cpu or gpu usage so that you get more power in other programs?

Well, yeah.

> what other programs are you using?
what is your goal?

Browsers, torrent programs, audio programs, all the basic stuff.

My goal is to get my computer to stop freezing when apparently too many things are running in the background, and mainly to get it to encode and make videos again.

> (and dont threaten to go back to windows if we dont solve your problem ) 

I couldn't even if I wanted to.  For some strange reason, months ago (or maybe even a year now, I'm not sure when it happened) my computer stopped being able to install windows.  I'm not sure why, and I gave up trying to find out since I haven't had any issues installing or running any Linux or other OS's.

---------------------------------

I have asked more directly on a different thread about my video programs, and I brought this up on there, and I'll bring it up here too since it is relevant:

"Oh, I completely forgot, can this be related? For months now, whenever I turn on my computer, I've had to turn my monitor on and off over and over again (or restart the computer, or whatever I do that makes the screen register any activity) before a picture comes on. I'm not even sure why it does that, but can it be related?"

---

### Post by 3rdalbum on 2009-03-15
Okay; that's what we wanted to hear! (well, not really; I'm sorry you're having freezing problems!)

When you're encoding videos, it basically runs the CPU at 100% of capacity. This generates a lot of heat and eats a lot of power. The first thing you'd want to check is the CPU temperature; check that it isn't overheating. Install the "lm-sensors" package and run "sensors" from the command-line to see the temperature of your CPU core(s). If the CPU gets too hot, it will automatically shut down - that means a freeze. It's ironic that too much temperature causes freezing! :-)

The sensors program requires you to run a seperate program the first time, to detect what sensors you have. After doing this, you can run the command "watch sensors" and every 2 seconds you will get an update on what the hardware sensors say.

If the CPU is getting too hot, you'll want to check that your computer's fans are spinning. Maybe take the side off your computer and point a pedestal fan onto the insides. And check that you don't have dust build-up.

There is also the possibility that your power supply can't keep up with the power requirements of your CPU. If your CPU can't get enough power, the contents of its internal memory get corrupted and the computer crashes. A power supply is not a cheap thing to replace and there's not a cheap way of testing whether it's the problem. Unfortunately.

You could try doing Memtest - at the GRUB menu there is an option to test your memory. Keep it running overnight if possible.

After such a freeze, check in the System Log program under "kern.log" and "messages" to see if any error messages were logged at the time your computer froze.

Proprietary graphics drivers are also known to crash computers. If there is a newer version of the Nvidia driver that works with your card, then try installing it and seeing if the problem goes away. Alternatively, try disabling the proprietary graphics card driver and using the "nv" driver - it doesn't provide 3D graphics acceleration, but it is generally more stable than the proprietary driver.

The last thing to try would be the Phoronix Test Suite program from [www.phoronix.com](www.phoronix.com).  This program has a bunch of tests that can stress each part of your computer. If you get errors or crashes occurring during one particular test, you might have narrowed down your problem.

---

### Post by berrypievision on 2009-03-15
Well, I'm glad this forum has been very helpful.  I've generally had a better time with Ubuntu than with Mandriva.  No insult meant towards Mandriva, mind you.

> 
If the CPU is getting too hot, you'll want to check that your computer's fans are spinning. Maybe take the side off your computer and point a pedestal fan onto the insides. And check that you don't have dust build-up.

The side is already off, and do you mean a normal fan?  I can buy a cheap fan and point it at the inside.  Also, my window is always open, letting in cool air that always directly hits the inside of the computer.  Does that help?

> There is also the possibility that your power supply can't keep up with the power requirements of your CPU. If your CPU can't get enough power, the contents of its internal memory get corrupted and the computer crashes. A power supply is not a cheap thing to replace and there's not a cheap way of testing whether it's the problem. Unfortunately.

I agree, and my computer has been tossed around a few times.  I'm basically going to have to raise the money for a new computer (around 600 dollars) but for now I'm trying to fix this sucker as much as I can.


My power supply isn't something new, it's one I've used for two years (or maybe one and a half, I'm bad with exact dates and time periods) and as far as I know, it has a lifespan of at least 11 years.  It's a Thermal Master 350W ATX12V.  However, I'm not exactly sure this is the issue, since these problems began to slowly emerge over time, over the past few months that is.

> Proprietary graphics drivers are also known to crash computers. If there is a newer version of the Nvidia driver that works with your card

I believe I have the most up to date drivers for Ubuntu, however I am not sure and will have to check with a friend of mine.

As for everything else you suggested, I will try it soon enough.  Very soon I'm going to turn off this computer and basically let it rest for 15 or 20 hours, hoping that helps.

---

### Post by berrypievision on 2009-03-16
Er..have I hit a crossroads?

---

### Post by jocko on 2009-03-16
> **berrypievision said:**
> Er..have I hit a crossroads?
Did you install lm-sensors? How hot does the cpu get before it freezes?
Did you run the memtest? Did you get any errors?

When you say you can't install windows anymore, exactly what do you mean?
And you also say the problem has built up over time. This sounds like some piece of your computer is dying, as it's not limited to ubuntu. Either your cpu cooler does not work anymore (is the fan running? have you cleaned the fins of the heat sink from dust?), or some other piece of your computer is failing (maybe you have a bad stick of ram?).

---

### Post by blazemore on 2009-03-16
To lower the acceleration, simply decrease the resultant force, or increase the mass.

---

### Post by berrypievision on 2009-03-16
> Did you install lm-sensors? How hot does the cpu get before it freezes?
Did you run the memtest? Did you get any errors?

I'll do that today, but I have to ask, if I get results, and show them to you guys, does that mean you can help?  Plus, I'm never sure when it will freeze, some days it will not freeze, some days it will.

Plus, about the monitor, got any ideas?  That problem has been around way longer.

> 
When you say you can't install windows anymore, exactly what do you mean?

All I know is that it just won't install, any windows os I have at hand.  All other OS's install just fine though.

> Either your cpu cooler does not work anymore (is the fan running?

The two fans are running fine.  Also, the computer gets plenty of contact from cool air, as I've said before, as one of the case is always open and my window is always open letting in air.  Does that help?

> have you cleaned the fins of the heat sink from dust?

I plan to dust it out today.  Can that really help though?

> Either your cpu cooler does not work anymore (is the fan running?

I have no idea how I could tell.

---

### Post by berrypievision on 2009-03-16
Well I ran the sensors in the terminal, and it tells me the templ (with the virtual device) is on average 58.5C to 60.0C.  What does that mean?

It tells me temp11 for the ISA Adapter is 39.01C while templ2 is 61.0C.  Again, what does that mean?


Random stuff related I hope helps:


Well, I think I got the lm-sensors thingie right, as I did this in the Terminal:

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): 
Probing for PCI bus adapters...
Use driver `i2c-sis96x' for device 0000:00:02.1: Silicon Integrated Systems SMBus Controller

We will now try to load each adapter module in turn.
Module `i2c-sis96x' already loaded.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): 
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SiS96x SMBus adapter at 0x10c0 (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x2f
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM78-J'...              No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `Analog Devices ADT7470'...                     No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83792D'...                            No
Probing for `Winbond W83793R/G'...                          No
Probing for `Winbond W83791SD'...                           No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG'...                          No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Winbond W83L786NR/NG/R/G'...                   No
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1029'...                     No
Probing for `ITE IT8712F'...                                No
Probing for `Fintek custom power control IC'...             No
Probing for `Winbond W83791D'...                            No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-3)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x4c
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Analog Devices ADT7466'...                     No
Probing for `Andigilog aSC7511'...                          No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `National Semiconductor LM90'...                No
Probing for `National Semiconductor LM89/LM99'...           No
Probing for `National Semiconductor LM86'...                No
Probing for `Analog Devices ADM1032'...                     No
Probing for `Maxim MAX6657/MAX6658/MAX6659'...              No
Probing for `Maxim MAX6648/MAX6692'...                      Success!
    (confidence 8, driver `to-be-written')
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Winbond W83L771W/G'...                         No
Probing for `Texas Instruments TMP401'...                   No
Probing for `National Semiconductor LM63'...                No
Probing for `Fintek F75363SG'...                            No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `Analog Devices ADT7461'...                     No
Probing for `Fintek F75383S/M'...                           No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): 
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found `Winbond W83697HF/F/HG Super IO Sensors'              Success!
    (address 0x290, driver `w83627hf')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): 
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `to-be-written' (should be inserted):
  Detects correctly:
  * Bus `NVIDIA i2c adapter '
    Busdriver `UNKNOWN', I2C address 0x4c
    Chip `Maxim MAX6648/MAX6692' (confidence: 8)

Driver `w83627hf' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `Winbond W83697HF/F/HG Super IO Sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# Chip drivers
# no driver for Maxim MAX6648/MAX6692 yet
w83627hf
#----cut here----

Do you want to add these lines automatically? (yes/NO)

-------------------------------

I ran some different test in the Terminal and got this:

Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found `Winbond W83697HF/F/HG Super IO Sensors'              Success!
    (address 0x290, driver `w83627hf')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): 
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `to-be-written' (should be inserted):
  Detects correctly:
  * Bus `NVIDIA i2c adapter '
    Busdriver `UNKNOWN', I2C address 0x4c
    Chip `Maxim MAX6648/MAX6692' (confidence: 8)

Driver `w83627hf' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `Winbond W83697HF/F/HG Super IO Sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# Chip drivers
# no driver for Maxim MAX6648/MAX6692 yet
w83627hf
#----cut here----

Do you want to add these lines automatically? (yes/NO)
tyler@tyler-desktop:~$ 
tyler@tyler-desktop:~$ This program will help you determine which kernel modules you need
AX16
bash: This: command not found
tyler@tyler-desktop:~$ to load to use lm_sensors most effectively. It is generally safe
Probing for `Maxim MAX1617A'...                             No
PThe program 'to' is currently not installed.  You can install it by typing:
sudo apt-get install casu
bash: to: command not found
tyler@tyler-desktop:~$ and recommended to accept the default answers to all questions,
robing for `Maxim MAX1668'...                              No
PrThe program 'and' is currently not installed.  You can install it by typing:
sudo apt-get install and
bash: and: command not found
tyler@tyler-desktop:~$ unless you know what you're doing.
obing for `Maxim MAX1805'...       
> 
> We can start with probing for (PCI) I2C or SMBus adapters.
Probing for `Maxim MAX1989'...                             
> Do you want to probe now? (YES/no): 
Probing for `Maxim MAX6655/MAX6656'.
> Probing for PCI bus adapters...
Probing for `TI THMC10'...     
> Use driver `i2c-sis96x' for device 0000:00:02.1: Silicon Integrated Systems SMBus Controller
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GLbash: unless: command not found
tyler@tyler-desktop:~$ 
5
tyler@tyler-desktop:~$ We will now try to load each adapter module in turn.
Probing for `Onsemi MC1066'...                      
bash: We: command not found
tyler@tyler-desktop:~$ Module `i2c-sis96x' already loaded.
Probing for `Maxim MAX1619'...     
> If you have undetectable or unsupported I2C/SMBus adapters, you can have
Probing for `National Semiconductor LM82/LM83'...           No
Probing f> them scanned by manually loading the modules before running this script.
or `National Semiconductor LM90'...                No
Probing for `Nation> 
a
> To continue, we need module `i2c-dev' to be loaded.
Probing for `National Semiconductor LM86'...       
> Do you want to load `i2c-dev' now? (YES/no): 
bash: syntax error near unexpected token `('
Probing for `Analog Devices ADM1032'...      
tyler@tyler-desktop:~$ Module loaded successfully.
Probing for `Maxim MAX6657/
bash: Module: command not found
tyler@tyler-desktop:~$ 

tyler@tyler-desktop:~$ We are now going to do the I2C/SMBus adapter probings. Some chips may
    (confidence 8, driver `to-be-written')
Probing for `Maxim MAX6680bash: We: command not found
tyler@tyler-desktop:~$ be double detected; we choose the one with the highest confidence
/MAX6681'...                      No
Probing for `Winbond W83L771Wbash: be: command not found
The program 'we' is currently not installed.  You can install it by typing:
sudo apt-get install xwpe
bash: we: command not found
tyler@tyler-desktop:~$ value in that case.
/G'...              
bash: value: command not found
tyler@tyler-desktop:~$ If you found that the adapter hung after probing a certain address,
Probing for `Texas Instruments TMP401'...                   No
Probbash: If: command not found
tyler@tyler-desktop:~$ you can specify that address to remain unprobed.
ing for `National Semiconductor LM63'...         
bash: you: command not found
tyler@tyler-desktop:~$ 

tyler@tyler-desktop:~$ Next adapter: SiS96x SMBus adapter at 0x10c0 (i2c-0)
Probing for `Maxim MAX6633/MAX6634/MAX6635'...      
bash: syntax error near unexpected token `('
tyler@tyler-desktop:~$ Do you want to scan it? (YES/no/selectively): 
Probing for `Analog Devices ADT7461'...       
bash: syntax error near unexpected token `('
tyler@tyler-desktop:~$ Client found at address 0x2f
Probing for `Fintek F75383S/
bash: Client: command not found
tyler@tyler-desktop:~$ Probing for `National Semiconductor LM78'...                No

Some chips are also accessible through the ISA I/O ports. We > Probing for `National Semiconductor LM78-J'...              No
> Probing for `National Semiconductor LM79'...                No
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you dobash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `National Semiconductor LM80'...                No
 not have any ISA slots!
Do you want to scan the ISA I/O ports?> Probing for `Analog Devices ADT7470'...                     No
 (YES/no): 
Probing for `National Semiconductor LM78' at 0x290.> Probing for `Winbond W83781D'...                            No
..       No
Probing for `National Semiconductor LM78-J' at 0x29bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
bash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `Winbond W83782D'...                            No
0...     No
Probing for `National Semiconductor LM79' at 0x290.> Probing for `Winbond W83792D'...                            No
..       No
Probing for `Winbond W83781D' at 0x290...          > Probing for `Winbond W83793R/G'...                          No
         No
Probing for `Winbond W83782D' at 0x290...          bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
bash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `Winbond W83791SD'...                           No
         No
Probing for `IPMI BMC KCS' at 0xca0...             > Probing for `Winbond W83627HF'...                           No
         No
Probing for `IPMI BMC SMIC' at 0xca8...            > Probing for `Winbond W83627EHF'...                          No
         No

Some Super I/O chips may also contain sensors. We bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
bash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `Winbond W83627DHG'...                          No
have to write to
standard I/O ports to probe them. This is usua> Probing for `Asus AS99127F (rev.1)'...                      No
lly safe.
Do you want to scan for Super I/O sensors? (YES/no): bash: syntax error near unexpected token `('
tyler@tyler-desktop:~$ Probing for `Asus AS99127F (rev.2)'...                      No
> Probing for `Asus ASB100 Bach'...                           No
> Probing for `Winbond W83L786NR/NG/R/G'...                   No
bash: command substitution: line 1: syntax error near unexpected token `('
bash: command substitution: line 1: `Asus AS99127F (rev.2)'...                      No'

Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/bash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `Analog Devices ADM9240'...                     No
Fintek'...                       Yes
Found `Winbond W83697HF/F/> Probing for `Dallas Semiconductor DS1780'...                No
HG Super IO Sensors'              Success!
    (address 0x290, > Probing for `National Semiconductor LM81'...                No
driver `w83627hf')
Probing for Super-I/O at 0x4e/0x4f
Trying fabash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
bash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `Analog Devices ADM1029'...                     No
> Probing for `ITE IT8712F'...                                No
mily `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying fa> Probing for `Fintek custom power control IC'...             No
mily `VIA/Winbond/Fintek'...                       No
Trying fabash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
bash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `Winbond W83791D'...                            No
mily `ITE'...                                      No

Some sou> Client found at address 0x50
th bridges, CPUs or memory co
> Probing for `Analog Devices ADM1033'...                     No
embedded sensors. Do you want to scan for them? (YES/no): 
Sil> Probing for `Analog Devices ADM1034'...                     No
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 4: syntax error: unexpected end of file
icon Integrated Systems SIS5595...                       No
VIAbash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `SPD EEPROM'...                                 Yes
>     (confidence 8, not a hardware monitoring chip)
 VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                       > Probing for `EDID EEPROM'...                                No
     No
AMD K8 thermal sensors...                              > Client found at address 0x51
     No
AMD K10 thermal senso> Probing for `Analog Devices ADM1033'...                     No
rs...                                  No
Intel Core family thebash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 4: syntax error: unexpected end of file
bash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `Analog Devices ADM1034'...                     No
> Probing for `SPD EEPROM'...                                 Yes
rmal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary>     (confidence 8, not a hardware monitoring chip)
 of the probes I have just done.
Just press ENTER t> Probing for `EDID EEPROM'...                                No
o continue: 

Driver `to-be-written' (should be inserted):
  Debash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
bash: Probing: command not found
tyler@tyler-desktop:~$ 
tyler@tyler-desktop:~$ Next adapter: NVIDIA i2c adapter  (i2c-1)
tects correctly:
  * Bus `NVIDIA i2c adaptebash: syntax error near unexpected token `('
tyler@tyler-desktop:~$ Do you want to scan it? (YES/no/selectively): 
r '
    Busdriver `UNKNOWN', I2C address 0x4c
 bash: syntax error near unexpected token `('
tyler@tyler-desktop:~$ 
 
tyler@tyler-desktop:~$ Next adapter: NVIDIA i2c adapter  (i2c-2)

Driver `w83627hf' (should be inserted):
bash: syntax error near unexpected token `('
tyler@tyler-desktop:~$ Do you want to scan it? (YES/no/selectively): 
  Detects correctly:
  * ISA bus, address 0x290bash: syntax error near unexpected token `('
tyler@tyler-desktop:~$ 

tyler@tyler-desktop:~$ Next adapter: NVIDIA i2c adapter  (i2c-3)
bash: syntax error near unexpected token `('
    Chip `Winbond W83697HF/F/HG Super IO S
tyler@tyler-desktop:~$ Do you want to scan it? (YES/no/selectively): 

I will now generate the commands needed to lobash: syntax error near unexpected token `('
tyler@tyler-desktop:~$ Client found at address 0x4c
ad the required modules.
Justbash: Client: command not found
tyler@tyler-desktop:~$ Probing for `National Semiconductor LM75'...                No
 press ENTER to continue: 

To load everything that is needed, > Probing for `Dallas Semiconductor DS75'...                  No
add this to /etc/modules:

#----cut here----
# I2C adapter driv> Probing for `Analog Devices ADT7466'...                     No
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
ers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe ubash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `Andigilog aSC7511'...                          No
nknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter N> Probing for `Dallas Semiconductor DS1621/DS1631'...         No
VIDIA i2c adapter 
# Chip drivers
# no driver for Maxim MAX6648> Probing for `Analog Devices ADM1021'...                     No
/MAX6692 yet
w83627hf
#----cut here----

Do you want to add thebash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
bash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `Analog Devices ADM1021A/ADM1023'...            No
se lines automatically? (yes/NO)
> Probing for `Maxim MAX16
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
bash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `Maxim MAX1617A'...                             No
> Probing for `Maxim MAX1668'...                              No
> Probing for `Maxim MAX1805'...       
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
bash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `Maxim MAX1989'...                             
> Probing for `Maxim MAX6655/MAX6656'.
> Probing for `TI THMC10'...     
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
bash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `National Semiconductor LM84'...                No
> Probing for `Genesys Logic GL5
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
bash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `Onsemi MC1066'...                      
> Probing for `Maxim MAX1619'...     
> Probing for `National Semiconductor LM82/LM83'...           No
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
bash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `National Semiconductor LM90'...                No
> Probing for `Nationa
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
bash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `National Semiconductor LM86'...       
> Probing for `Analog Devices ADM1032'...      
> Probing for `Maxim MAX6657/
> 
>     (confidence 8, driver `to-be-written')
bash: syntax error near unexpected token `)'
tyler@tyler-desktop:~$ Probing for `Maxim MAX6680/MAX6681'...                      No
> Probing for `Winbond W83L771W/G'...              
> Probing for `Texas Instruments TMP401'...                   No
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
bash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `National Semiconductor LM63'...         
> 
> Probing for `Maxim MAX6633/MAX6634/MAX6635'...      
> Probing for `Analog Devices ADT7461'...       
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 4: syntax error: unexpected end of file
bash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `Fintek F75383S/
> 
> Some chips are also accessible through the ISA I/O ports. We have to
> write to arbitrary I/O ports to probe them. This is usually safe though.
> Yes, you do have ISA I/O ports even if you do not have any ISA slots!
> Do you want to scan the ISA I/O ports? (YES/no): 
> Probing for `National Semiconductor LM78' at 0x290...       No
> Probing for `National Semiconductor LM78-J' at 0x290...     No
bash: Fintek: command not found
bash: Some: command not found
usage: write user [tty]
bash: Yes,: command not found
bash: command substitution: line 6: syntax error near unexpected token `('
bash: command substitution: line 6: `Do you want to scan the ISA I/O ports? (YES/no): '
bash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `National Semiconductor LM79' at 0x290...       No
> Probing for `Winbond W83781D' at 0x290...                   No
> Probing for `Winbond W83782D' at 0x290...                   No
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
bash: Probing: command not found
tyler@tyler-desktop:~$ Probing for `IPMI BMC KCS' at 0xca0...                      No
> Probing for `IPMI BMC SMIC' at 0xca8...                     No
> 
> Some Super I/O chips may also contain sensors. We have to write to
> standard I/O ports to probe them. This is usually safe.
> Do you want to scan for Super I/O sensors? (YES/no): 
> Probing for Super-I/O at 0x2e/0x2f
> Trying family `National Semiconductor'...                   No
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
bash: Probing: command not found
tyler@tyler-desktop:~$ Trying family `SMSC'...                                     No
> Trying family `VIA/Winbond/Fintek'...                       Yes
> Found `Winbond W83697HF/F/HG Super IO Sensors'              Success!
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
bash: Trying: command not found
tyler@tyler-desktop:~$     (address 0x290, driver `w83627hf')
> Probing for Super-I/O at 0x4e/0x4f
> Trying family `National Semiconductor'...                   No
> Trying family `SMSC'...                                     No
> Trying family `VIA/Winbond/Fintek'...                       No
> Trying family `ITE'...                                      No
> 
> Some south bridges, CPUs or memory co
> embedded sensors. Do you want to scan for them? (YES/no): 
> Silicon Integrated Systems SIS5595...                       No
> VIA VT82C686 Integrated Sensors...                          No
> VIA VT8231 Integrated Sensors...                            No
> AMD K8 thermal sensors...                                   No
> AMD K10 thermal sensors...                                  No
> Intel Core family thermal sensor...                         No
> Intel AMB FB-DIMM thermal sensor...                         No
> 
> Now follows a summary of the probes I have just done.
> Just press ENTER to continue: 
> 
> Driver `to-be-written' (should be inserted):
bash: syntax error near unexpected token `('
tyler@tyler-desktop:~$   Detects correctly:
bash: Detects: command not found
tyler@tyler-desktop:~$   * Bus `NVIDIA i2c adapter '
>     Busdriver `UNKNOWN', I2C address 0x4c
>   
> 
> Driver `w83627hf' (should be inserted):
bash: syntax error near unexpected token `('
tyler@tyler-desktop:~$   Detects correctly:
bash: Detects: command not found
tyler@tyler-desktop:~$   * ISA bus, address 0x290
bash: 01-Alien[1979]DvDrip-aXXo.avi: command not found
tyler@tyler-desktop:~$     Chip `Winbond W83697HF/F/HG Super IO S
> 
> I will now generate the commands needed to load the required modules.
> Just press ENTER to continue: 
> 
> To load everything that is needed, add this to /etc/modules:
> 
> #----cut here----
> # I2C adapter drivers
> # modprobe unknown adapter NVIDIA i2c adapter 
> # modprobe unknown adapter NVIDIA i2c adapter 
> # modprobe unknown adapter NVIDIA i2c adapter 
> # Chip drivers
> # no driver for Maxim MAX6648/MAX6692 yet
> w83627hf
> #----cut here----
> 
> Do you want to add these lines automatically? (yes/NO)
> 
> yes

------------------------------

What does this exactly tell me?


As for Memtest, I looked it up and found some cd program for sale.  Again, how can that help me?

---

### Post by berrypievision on 2009-03-16
It tells me fan1 is using 0 RPM while fan2 is using on average 2340 rpm.  What does that mean?

---

### Post by berrypievision on 2009-03-16
I'm still not sure how to work this lm-sensors, cause now when I open up a terminal and put in watch sensors, it just tells me the templ of the virtual device.  

I thought for a minute I might have found the problem, as twice I purposely crashed my computer and it said the virtual device templ reached 64, yet it just reached that same templ a few minutes ago without crashing, going up to 65.  I guess that's not the issue then.

---

### Post by 3rdalbum on 2009-03-16
Have you disabled the proprietary graphics drivers?

If you run "sensors" or "watch sensors" you should be getting some information like this:

```

w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.38 V  (min =  +0.00 V, max =  +1.74 V)   
in1:        +11.30 V  (min =  +1.27 V, max = +12.30 V)   
AVCC:        +3.31 V  (min =  +2.59 V, max =  +0.29 V)   ALARM
3VCC:        +3.31 V  (min =  +0.54 V, max =  +2.10 V)   ALARM
in4:         +1.59 V  (min =  +0.00 V, max =  +0.02 V)   ALARM
in5:         +1.66 V  (min =  +0.53 V, max =  +0.03 V)   ALARM
in6:         +5.09 V  (min =  +0.26 V, max =  +3.69 V)   ALARM
VSB:         +3.33 V  (min =  +0.06 V, max =  +0.05 V)   ALARM
VBAT:        +0.00 V  (min =  +2.66 V, max =  +1.55 V)   ALARM
Case Fan:      0 RPM  (min =  219 RPM, div = 128)  ALARM
CPU Fan:    1339 RPM  (min =  869 RPM, div = 8)
Aux Fan:    1140 RPM  (min =  215 RPM, div = 32)
fan5:          0 RPM  (min =  376 RPM, div = 128)  ALARM
Sys Temp:    +37.0°C  (high = -126.0°C, hyst = +49.0°C)  sensor = thermistor
CPU Temp:    +22.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:   +124.5°C  (high = +80.0°C, hyst = +75.0°C)  ALARM  sensor = thermistor

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +43.0°C  (high = +78.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +43.0°C  (high = +78.0°C, crit = +100.0°C)  

```

(Note: in my example, don't worry about the bits that say ALARM).

The Core 0 and Core 1 temperatures are what you need to look at to determine if it's an overheating problem. A Core 2 Duo should only hit 64 degrees under load during summer; for reference, mine is currently idling at 44 C during summer. If you're getting 60-odd degrees Celcius on a desktop when your computer isn't doing much, then you should take a look and see whether there's dust on the CPU cooler.

Memtest is already installed on your computer; you select it at the GRUB menu. If Ubuntu is the only operating system installed, you need to tap Escape at the GRUB countdown to access the GRUB menu. You could also take a look at the memory tests in Phoronix Test Suite ([www.phoronix.com](www.phoronix.com))

---

### Post by berrypievision on 2009-03-16
When I put in sudo watch sensors I get this:

Every 2.0s: sensors                                     Mon Mar 16 03:21:50 2009

acpitz-virtual-0
Adapter: Virtual device
temp1:       +65.5C  (crit = +100.0C)

w83697hf-isa-0290
Adapter: ISA adapter
VCore:       +1.28 V  (min =  +0.21 V, max =  +0.27 V)   ALARM
+3.3V:       +3.34 V  (min =  +0.61 V, max =  +1.02 V)   ALARM
+5V:         +5.03 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
+12V:       +11.80 V  (min = +11.00 V, max =  +0.24 V)   ALARM
-12V:       -12.28 V  (min =  -1.75 V, max = -14.91 V)   ALARM
-5V:         -4.65 V  (min =  -5.90 V, max =  -7.71 V)   ALARM
V5SB:        +5.46 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
VBat:        +3.12 V  (min =  +0.03 V, max =  +1.02 V)   ALARM
fan1:          0 RPM  (min = 5273 RPM, div = 4)  ALARM
fan2:       2376 RPM  (min =   -1 RPM, div = 4)  ALARM
temp1:       +42.0C  (high =  +0.0C, hyst = +64.0C)  sensor = thermistor
temp2:       +65.5C  (high = +95.0C, hyst = +95.0C)  sensor = diode
beep_enable:enabled

---

### Post by berrypievision on 2009-03-16
Another question, what would deactivating my Nvidia drivers exactly do?  Why do you advise I do that?  The computer still froze when it was deactivated anyway, so what's the point?

---

### Post by berrypievision on 2009-03-16
I can see within my computer at all times, and I do see a lot of dust.  Is it possible all these problems are from dust, and it can be fixed by um...dusting?  That would be weird, but good at the same time.

---

### Post by berrypievision on 2009-03-17
If it ends up being a heating issue, what exactly should I do?

---

### Post by jocko on 2009-03-17
> **berrypievision said:**
> I can see within my computer at all times, and I do see a lot of dust.  Is it possible all these problems are from dust, and it can be fixed by um...dusting?  That would be weird, but good at the same time.

Weird? If the air flow through the fins of the cpu cooler is blocked by dust you have a greatly reduced effective surface area of the cooler, leading to less efficient cooling. Dust may also act as an insulator between the metal of the cooler and the air (pretty much as a layer of wool clothing will trap a layer of stagnant air and keep you warm in the winter).

> **berrypievision said:**
> If it ends up being a heating issue, what exactly should I do?
Going from simple to advanced:
1. Clean out the dust from the cpu cooler. Use a vacuum cleaner (carefully) and perhaps a soft brush if some dust doesn't come off (a clean paint brush or an old toothbrush may work).
2. Try to tuck away any cables that may block or divert the air flow around the cpu.
3. Make sure you have not overclocked the cpu (if you don't know, you probably haven't).
4. Lower the voltage of the cpu if you can find such an option in the bios (but be careful not to lower it too much, that will also cause instability).
5. Install one or two fans in the case to ensure constant movement of air through the case. Fresh, cool air should go in to the case in the front and warm air should be blown out of the case at the back. An open case is not always better than a well ventilated, closed case.
6. Change the thermal compound between the cpu and the cooler to ensure efficient transfer of heat from the cpu to the cooler.
7. Get a better cooler or put a stronger fan on the one you have.

To see if it's a heating issue, first run "watch sensors" in a terminal, then start up something that causes a constant 100% cpu usage.
If you don't have anything that does this, install the package "cpuburn" and run the command "burnMMX" in a terminal.
If the cpu temperature stays below 90 C, I don't think it's heating up enough to become unstable (but with good cooling the temperature shouldn't go above 65-70 C even after a long time at 100% usage).

---

### Post by jerome1232 on 2009-03-17
> **jocko said:**
> 
1. Clean out the dust from the cpu cooler. Use a vacuum cleaner (carefully) and perhaps a soft brush if some dust doesn't come off (a clean paint brush or an old toothbrush may work).



My recommendation is get a can of compressed air instead, vacuums can build static electricity at their ends and zap things.

I know some people have used a vacuum for 6 years or so and never had problems or whatever but it can happen and it would fry your motherboard nice and toasty if it were to discharge static onto it.

---

### Post by berrypievision on 2009-03-18
> Weird?

Yeah, all of these problems being caused by dust would be pretty weird if you ask me.

> 
5. Install one or two fans in the case to ensure constant movement of air through the case. 

I've already had two fans in there for years.  Didn't I already say that?

> Lower the voltage of the cpu if you can find such an option in the bios (but be careful not to lower it too much, that will also cause instability).

I don't think I can do that, as I can't use my keyboard during the BIOS screen.  Can I do such a thing in GRUB?

> If you don't have anything that does this, install the package "cpuburn" and run the command "burnMMX" in a terminal.
If the cpu temperature stays below 90 C, I don't think it's heating up enough to become unstable (but with good cooling the temperature shouldn't go above 65-70 C even after a long time at 100% usage).

Well I looked up cpuburn and found this:

"Warning: The goal has been to maximize heat production from the CPU, putting stress on the CPU itself, cooling system, motherboard. This may cause data loss (filesystem corruption) and possibly permanent damage to electronic components. Use at your own risk."

My computer is already screwed up as it is.  Do I really want to risk overloading and breaking it?  Isn't there a safer way to find this stuff out?

It seems one of my fans is always in the 40sC, while the second gets up to the 60s a lot.  Does that indicate a heating issue?

> Every 2.0s: sensors                                     Wed Mar 18 01:42:22 2009

acpitz-virtual-0
Adapter: Virtual device
temp1:       +59.5C  (crit = +100.0C)

w83697hf-isa-0290
Adapter: ISA adapter
VCore:       +1.30 V  (min =  +0.21 V, max =  +0.27 V)   ALARM
+3.3V:       +3.34 V  (min =  +0.61 V, max =  +1.02 V)   ALARM
+5V:         +5.03 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
+12V:       +11.73 V  (min =  +9.06 V, max =  +0.24 V)   ALARM
-12V:       -12.20 V  (min =  -1.75 V, max = -14.91 V)   ALARM
-5V:         -4.75 V  (min =  -6.10 V, max =  -7.71 V)   ALARM
V5SB:        +5.46 V  (min =  +3.44 V, max =  +0.00 V)   ALARM
VBat:        +3.12 V  (min =  +0.03 V, max =  +1.02 V)   ALARM
fan1:          0 RPM  (min = 5273 RPM, div = 4)  ALARM
fan2:       2376 RPM  (min =   -1 RPM, div = 4)  ALARM
temp1:       +42.0C  (high =  +8.0C, hyst = +64.0C)  sensor = thermistor
temp2:       +59.5C  (high = +95.0C, hyst = +95.0C)  sensor = diode
beep_enable:enabled


That's my stats according to "watch sensors."  Can you guys tell me what it exactly means?

---

### Post by berrypievision on 2009-03-18
I don't know, none of my hardware exceeds the 60 mark when powering up, yet my computer is freezing whenever I try to encode a video (which is normally the only time it freezes, it has stopped freezing on its own, for now).  So for awhile, can we entertain some other notions on video encoding would cause freezing?

Yeah, I know this thread is called lower acceleration, and if I could change it I would, as the topic has shifted.

Thanks for your help people.

---

### Post by berrypievision on 2009-03-18
Wow, I think I have two bulging caps.  They were probably there for quite awhile, but just learning about them now, I believe I have them.

Can they be the source of the problems?

---

### Post by jocko on 2009-03-18
> **berrypievision said:**
> Well I looked up cpuburn and found this:

"Warning: The goal has been to maximize heat production from the CPU, putting stress on the CPU itself, cooling system, motherboard. This may cause data loss (filesystem corruption) and possibly permanent damage to electronic components. Use at your own risk."

My computer is already screwed up as it is.  Do I really want to risk overloading and breaking it?  Isn't there a safer way to find this stuff out?
The warning is there to warn you that **if **your cpu overheats, there is a risc of damaging your computer or loosing data. **If** your cpu cooler is not efficient enough, burnMMX will cause your cpu to heat up until it crashes your computer or triggers an emergency shutdown. **If** that happens you will know what the problem is, and you can take appropriate measures to avoid it in the future. Yes, you can loose data, but you run exactly the same risc of loosing data **every** time your computer freezes, for whatever reason. And your cpu may even be damaged by too much heat, but again, if your problem is caused by heat, you run the risc of damaging the cpu **every** time your computer overheats. Nothing special about the heat that is produced by burnMMX compared to the one that is produced by your video encoding or whatever cpu intensive task you run. And if your problem is *not* caused by too much heat, there is no risc of damage by running burnMMX.

The only way to find out if the problem is caused by over heating, is to really stress the computer and monitor the cpu temperature. If you see the temperature rising too much (above 90 C), then terminate the burnMMX process (Ctrl+C) to avoid further heating.

As a reference: My laptop's two cpu cores are usually around 45-50 C when I don't do anything intensive. If I start burnMMX on both cores the temperature rizes rapidly to about 65 C (when the fan starts), and then continues to rize very slowly to 75 C, but never gets higher than that. When I turn off burnMMX, the temperatures drop rapidly back to 55 C and then slowly down to below 50 again in a few minutes. A desktop computer normally have more efficient cooling than that, as the air flow is not as limited as in a laptop.

---

### Post by jocko on 2009-03-18
> **berrypievision said:**
> Wow, I think I have two bulging caps.  They were probably there for quite awhile, but just learning about them now, I believe I have them.

Can they be the source of the problems?
Bulging caps? What do you mean?

---

### Post by eeperson on 2009-03-18
If bulging caps means that there are capacitors on your motherboard that are bulging on top/leaking then that could very well be the cause of all of your problems.  This can definitely cause your computer to freeze and could explain your inability to install windows.  There is no way to know for sure unless you replace those capacitors.

This is fairly easy if you know how to solder or know someone that does.  If you do get them replaced make sure you also clean off any fluid that has leaked out of the capacitors.

There are certain generations of computers that are prone to this (Usually from the Pentium III era).

---

### Post by berrypievision on 2009-03-19
> Bulging caps? What do you mean? 

I mean, I believe I may have two bulging caps.

> As a reference: My laptop's two cpu cores are usually around 45-50 C when I don't do anything intensive. If I start burnMMX on both cores the temperature rizes rapidly to about 65 C (when the fan starts), and then continues to rize very slowly to 75 C, but never gets higher than that. When I turn off burnMMX, the temperatures drop rapidly back to 55 C and then slowly down to below 50 again in a few minutes. A desktop computer normally have more efficient cooling than that, as the air flow is not as limited as in a laptop.

I found out two things today, that I actually have three fans in this computer, and that my computer does have a heating problem, by having the fan in the graphics card.  Also, my computer does have its share of dirt, and I'm having a friend clean it with condensed air later.

However, I have seen in the watch sensors none of the temperatures ever go up to 70, even when an application (like a video program) is doing its thing which causes the computer to freeze.  I believe I have said that before.  Doesn't that not support the idea that heating is the issue?

> 
There are certain generations of computers that are prone to this (Usually from the Pentium III era).

I have a Pentium IV, and at the moment, I am checking at badcaps.com if I do have bulging caps.  It seems more likely this is the cause of my problems.

I'm not sure if you know, but is it expensive to replace caps?  I might just convert an old Xbox into a PC (do to the fact I'm low on money at the moment and can't buy a new PC) if replacing the caps is expensive, which means this computer isn't very salvageable.

---

### Post by jocko on 2009-03-19
> **berrypievision said:**
> I found out two things today, that I actually have three fans in this computer, and that [COLOR=Red]my computer does have a heating problem, by having the fan in the graphics card[/COLOR].  Also, my computer does have its share of dirt, and I'm having a friend clean it with condensed air later.
Not sure what you mean. Do you say that the graphics card gets too hot? Or that the gpu fan does not work?
> **berrypievision said:**
> However, I have seen in the watch sensors none of the temperatures ever go up to 70, even when an application (like a video program) is doing its thing which causes the computer to freeze.[COLOR=Red]  I believe I have said that before.  Doesn't that not support the idea that heating is the issue?[/COLOR]
I have not seen that you said anywhere that the sensors output you posted was from when the computer ran at 100% cpu usage. If it runs at 100% cpu usage for several minutes without going above 70 C, you don't have a cpu heating issue. But bad capacitors may very well be the cause of the problem...

---

### Post by berrypievision on 2009-03-20
> 
Not sure what you mean. Do you say that the graphics card gets too hot? Or that the gpu fan does not work?

I have no idea personally, but I do known this is a lemon computer, and I'm pretty sure I have bulging caps, which seems to fit with my problems.

> I have not seen that you said anywhere that the sensors output you posted was from when the computer ran at 100% cpu usage.

I think you said, but I'm not sure, that when a video is rendering and encoding, 100 percent CPU usage is used.  Well, this computer doesn't even get up to 70 (well, once in awhile I say it get to 70) when massive programs are used, so I doubt very much its heating alone.  I think a dirty and otherwise overlooked motherboard, combined with some heating has caused bulging caps which are causing my hardware issues.  I can't be sure, but I'm trying to find out now.

Does anyone know how I can find out what model my motherboard is on Ubuntu?  That would help.  Thanks.

---

### Post by berrypievision on 2009-03-24
Anyone know how to find what model my motherboard is on Ubuntu?

---

