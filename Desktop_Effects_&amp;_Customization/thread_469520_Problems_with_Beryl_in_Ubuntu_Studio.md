---
title: "Problems with Beryl in Ubuntu Studio"
date: 2007-06-10
forum: Desktop Effects &amp; Customization
---

### Post by Chamelion on 2007-06-10
I have celeron 2.8, 1gig ram, Ubuntu studio and dual boot with xp. I recently installed Beryl with synaptic Package manager. I downloaded everything except the unstable packages. When I start the Beryl manager, my screen turns white. It actually does not seem to crash, but I do have a white cube with the Beryl Logo on top. It also is very hard and slow to move this 'cube'.
There is no way back. All icons disappear and the only way out is to restart.
Could somebody please help.
Thank you:)

---

### Post by PaulFXH on 2007-06-10
I had exactly the same problem when I tried to instal Beryl in Ubuntustudio on each of two different computers (in one of which Ubuntustudio was a VM with VMware Server).
The only way I found to get back to normal was to type this in a terminal
```
sudo rm /etc/xdg/autostart/beryl-manager.desktop
```
Then I noticed that Ubuntustudio does NOT have a Desktop Effects option in System>Preferences.
So, it appears Beryl in Ubuntustudio is not meant to be, although I hope I'm wrong.

---

### Post by Chamelion on 2007-06-10
i sincerely hope there is a way to get Beryl working in Studio too. One of the reasons for me to dual boot was to try out a few things. I have Ubuntu with Compiz running on another computer without  problems. 
I just do not want to risk breaking that machine. Hopefully somebody will have an answer.:D

---

### Post by MetalMusicAddict on 2007-06-11
Ubuntu Studio will run any Beryl packages exactly the same as Ubuntu-Feisty. Theres NO difference in the base system. Uses the exact packages Ubuntu does. Any issues are user error.

---

### Post by PaulFXH on 2007-06-11
Believe me, I really would like to get this working.
Also, I have successfully installed Beryl on two computers running Feisty (NOT studio) so I'm reluctant to believe that I made an error the twice I tried to install Beryl with studio.
The guide I used was [this]("http://ubuntuforums.org/showthread.php?t=359367") which refers to System>Preferences>Desktop Effects. 
On my computers, a least, Ubuntustudio does NOT have a Desktop Effects button.
Perhaps you could be a little more specific and indicate where you think the error might have been made.

---

### Post by MetalMusicAddict on 2007-06-12
> **PaulFXH said:**
> Believe me, I really would like to get this working.
Also, I have successfully installed Beryl on two computers running Feisty (NOT studio) so I'm reluctant to believe that I made an error the twice I tried to install Beryl with studio.
The guide I used was [this]("http://ubuntuforums.org/showthread.php?t=359367") which refers to System>Preferences>Desktop Effects. 
On my computers, a least, Ubuntustudio does NOT have a Desktop Effects button.
Perhaps you could be a little more specific and indicate where you think the error might have been made.
The guide you refer to is using Compiz. Not Beryl. It only links to Beryl as a alternative. 

There is NO difference in the underlying packages in Ubuntu and Ubuntu Studio.

Drivers, xorg settings and restricted modules are the only thing I can tell you to check.

---

### Post by PaulFXH on 2007-06-12
[QUOTE][There is NO difference in the underlying packages in Ubuntu and Ubuntu Studio./QUOTE]
Thanks for your reply.
I'm not at all interested in arguing with you but I do genuinely want to get Beryl on Ubuntustudio.
Despite your assurances, it seems very strange that System>Preferences has NO Desktop Effects in Studio but DOES in Feisty.
Surely this indicates that there IS a fundamental difference between Studio and Feisty as far as compositing packages are concerned.
If you or anybody else can show me that I'm wrong in my belief that Beryl doesn't work on Studio, I will be very happy.
Perhaps somebody out there has actually got Beryl (or even Compiz) to work on Studio. If so, please let us know.

---

### Post by kerrigan778 on 2007-06-17
The WSOD which is unfortunately common in Beryl, especially with ATI cards is usually fixed by downgrading the beryl packages down to the previous versions or earlier.

If this does not fix it on its own my own findings are that Beryl doesn't like the Low-Latency kernel so I just disable XGL when I enter the Low-Latency kernel when I need to do audio work. When I'm using the PC as a regular desktop I use the generic kernel with XGL.

(The main difference between the low latency kernel and the generic one is the latency for sound playing which is important for audio editing and not so important for regular desktop use)

I can live without XGL when I just need to edit audio/video so this fix worked for me.

---

### Post by clitmaster on 2007-06-25
beryl worx in ubuntuStudio

[http://img505.imageshack.us/img505/9375/desktop2dd1.png](http://img505.imageshack.us/img505/9375/desktop2dd1.png)

---

### Post by PaulFXH on 2007-06-25
Absolutely marvellous. Many congratulations (I'm assuming that is your screenshot).
Please provide some details on how you accomplished this; 
e.g. what graphics card?
How did you overcome the lack of Desktop Effects option in Ubuntustudio?
What guide or procedure did you use?

---

### Post by clitmaster on 2007-06-25
umm, it was pretty easy
i typed sudo apt-get install beryl...that installed it!

im using a HP laptop with an Nvidia GeForce Go 7400 Graphics card


yea, the 'desktop effects' dint work for me either...so i just ignored it and installed beryl

---

### Post by dangerzau on 2007-06-28
I too am running ubuntu studio with Beryl, as stated the easiest way to install it was simply run 

sudo apt-get install beryl

This installed all the required packages for beryl, then its simple a matter of going to applications --> System Tools --> Beryl-Manager

Of course this can also be setup to run automatically, however as I VNC into my desktop and getting VirtualGL to run and work properly is still causing some issues for me, this is how i do it.

Graphics card: NVidia FX5200

You are correct in what you say that certain options are different between "standard" ubuntu and ubuntudesktop, but none of these negate that you can't run anything you like with a little tinkering :D

---

### Post by linuxuser/palmprogrammer on 2007-07-27
I know I am a little late, anyone still around?

I have ubuntu studio, like you said, compiz(desktop effects) is NOT installed. Maybe that is why beryl doesn't work for me either?

WSOD is usually caused by your drivers (video), update xorg.conf.

I think my problem is caused by different version of lib???, maybe GTK. I fixed WSOD, now when I enable it it  crashed immediatly.

---

### Post by khaije1 on 2008-05-25
you may be interested to see this [http://ubuntuforums.org/showpost.php?p=5036824&postcount=8](http://ubuntuforums.org/showpost.php?p=5036824&postcount=8)

---

