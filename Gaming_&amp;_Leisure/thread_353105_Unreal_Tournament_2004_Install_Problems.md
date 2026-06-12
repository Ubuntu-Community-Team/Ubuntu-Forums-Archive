---
title: "Unreal Tournament 2004 Install Problems"
date: 2007-02-04
forum: Gaming &amp; Leisure
---

### Post by liamwithers on 2007-02-04
Hi, I bought Unreal Tournament a few months ago and had edgy put on the pc yesterday. I have tried to install the game but im stuck! I have read posts and websites for about an hour no with no luck. Please help me!!!!

---

### Post by AthlonMDK on 2007-02-04
What does not work? a bit more info would be welcome.

:guitar:

---

### Post by liamwithers on 2007-02-04
i try to click the installer but it doesnt load

---

### Post by Perfect Storm on 2007-02-04
Run the installer script from the terminal. If you encounter any trouble remember to post the output of the terminal (and input).

---

### Post by liamwithers on 2007-02-04
sorry, im not very experienced with ubuntu and its my 2nd day on for 6 months, how do i access my DVD drive in the terminal? and im only 12 lol so im a bit confused

---

### Post by Albi on 2007-02-04
what is in your /media/ folder?

---

### Post by M_the_C on 2007-02-04
> **liamwithers said:**
> sorry, im not very experienced with ubuntu and its my 2nd day on for 6 months, how do i access my DVD drive in the terminal? and im only 12 lol so im a bit confused
```
cd /media/cdrom0
```
That should work.  Then type:
```
sh linux-installer.sh
```

---

### Post by liamwithers on 2007-02-04
nice 1 m the c, installing ;)

---

### Post by liamwithers on 2007-02-04
damn it says no write permission to /usr/local/games

---

### Post by M_the_C on 2007-02-04
> **liamwithers said:**
> damn it says no write permission to /usr/local/games
Sorry, forgot about sudo:
```
sudo sh linux-installer.sh
```

---

### Post by liamwithers on 2007-02-04
installing, thnks ;) is it supposed to keep doing the base install?

---

### Post by M_the_C on 2007-02-04
Yes, it will say Base install and the bar will reach the end several times.

---

### Post by liamwithers on 2007-02-04
kk , its just came off tht, ill keep u updated

---

### Post by Perfect Storm on 2007-02-04
Just remember to exit the installer and not hit the ut2004 run button, but exit the installer afterwards. Else you'll run into permission problems.

---

### Post by liamwithers on 2007-02-04
> **Artificial Intelligence said:**
> Just remember to exit the installer and not hit the ut2004 run button, but exit the installer afterwards. Else you'll run into permission problems.

too late.. what shall i do now? it came up with the start screen then that went off after a minute

---

### Post by Perfect Storm on 2007-02-04
```
sudo chown -R USERNAME:USERNAME ~/.ut2004
ut2004
```

---

### Post by liamwithers on 2007-02-04
in the username bit i take it i put my user? LIAM:LIAM? got it now, same screen as before, it might dissappear

---

### Post by liamwithers on 2007-02-04
yep its gone? 

open /dev/[sound/]dsp: Device or resource busy
Couldn't set video mode: Couldn't find matching GLX visual


History: 

Exiting due to error

---

### Post by Perfect Storm on 2007-02-04
Have you installed the 3D driver for your card?
Patched ut2004?

---

### Post by liamwithers on 2007-02-04
nope, my graphics card isnt very good and im not sure which one it is, its actually on my motherboard. What do i have to do now?

---

### Post by Perfect Storm on 2007-02-04
Well that depends what brand of a graphic card you have and which type. You better find out.
If you are looking for a better card in the near future go for Nvidia as they have the best performance (driver) and it's easist to install.

---

### Post by liamwithers on 2007-02-04
i am thinking about using them, how do i check system information in linux because its different to windoze lol?

---

### Post by Perfect Storm on 2007-02-04
There's a cool tool under adminstration called Device Manager, you can check there.

---

### Post by liamwithers on 2007-02-04
ive got that up but i cant find anything with graphics card to do with it

---

### Post by liamwithers on 2007-02-04
ahh found it.. 

it says:

Intel corporation

82815 CGC

Compaq computer corporation

Unknown (0x0019)

I have searched 82815 into google and found a webite, i think it is for a different graphics card though. [http://www.intellinuxgraphics.org/index.html](http://www.intellinuxgraphics.org/index.html) will this work?

---

### Post by Perfect Storm on 2007-02-04
I have no experience with that chipset, bu you might search this forum and/check : [http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

---

### Post by liamwithers on 2007-02-04
i have searched there and the intel 8xxxx series are compatible. Should i try and install from that site i shown you?

On that site i found my care but when i go to the download page and put the code into a new terminal it doesnt do anything, it says the command is not found =S

---

### Post by Perfect Storm on 2007-02-04
I can't give you any advise about getting it working as I said I have no experience with intel chipset. You might start a new thread about getting 3D acc. for your card working.

---

