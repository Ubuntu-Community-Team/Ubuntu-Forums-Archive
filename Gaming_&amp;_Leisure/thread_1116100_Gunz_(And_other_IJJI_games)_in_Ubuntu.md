---
title: "Gunz (And other IJJI games) in Ubuntu"
date: 2009-04-04
forum: Gaming &amp; Leisure
---

### Post by gWX0 on 2009-04-04
This is actually a tutorial I've posted on a number of Gunz/IJJI boards, hoping to just spread some news that Gunz will run in both Virtualbox and VMWare (Virtualbox providing a very seamless, almost lag-free solution).

Tutorial:

Demo of Gunz on Debian: [http://www.youtube.com/watch?v=mnlBCUPqssw](http://www.youtube.com/watch?v=mnlBCUPqssw)

If you're interested in setting up DirectX in the non-free copy of Virtualbox (Free for use, not free for modification), you can download a copy of VBox at the official website ([www.virtualbox.org](www.virtualbox.org)).

From there, setup a copy of Windows XP (Home/Pro) or Windows 2000 (Vista/later is not supported as far as I know) in VirtualBox.

In the virtual machine, setup Guest Additions, then download the WineD3D installer ([http://aybabtu.com/rmh/wined3d/](http://aybabtu.com/rmh/wined3d/)).

Execute the installer while in safe mode (To enter safe mode, reboot your virtual machine, and repeatedly press F8 until an options menu pops up) 

NOTE: During WineD3D setup, only select DirectX8 and DirectX9 - anything else may cause problems!.

After that, the rest is self-explanitory.  Enjoy!

_____________

I'll see if ReactOS supports any of the IJJI games.  Considering the aggressive nature of GameGuard, relying on many undocumented kernel calls, I doubt it'll function at this point in time.

Anyone a fan of IJJI games?

---

### Post by etnlIcarus on 2009-04-07
Wow, blast from the past there. Shame someone doesn't rip off Gunz's ideas and implement them competently with their own engine. 

Actually reinstalled the NA version last year and it reminded me why I quit: buggy, glitchy and the #1 cause of arthritis in your digits. Butterflying/wall hovering becomes physically excruciating after only a single round.

Was also disappointed to discover no one played attack/defence anymore. A/D in the mansion was the best part of the entire game. How that user-created game mode died is beyond me.

---

### Post by Grishka on 2009-04-07
> **etnlIcarus said:**
> Wow, blast from the past there. Shame someone doesn't rip off Gunz's ideas and implement them competently with their own engine. 

Actually reinstalled the NA version last year and it reminded me why I quit: buggy, glitchy and the #1 cause of arthritis in your digits. Butterflying/wall hovering becomes physically excruciating after only a single round.

Was also disappointed to discover no one played attack/defence anymore. A/D in the mansion was the best part of the entire game. How that user-created game mode died is beyond me.

eh yea, butterflying was uncomfortable to pull off nicely, as well as unreliable. a simple block rendered it useless. I relied on it for effect only. ^^ and to confuse noobs, of course. good game it was. I've had an adrenaline rush often with this one. ^^ but it was bad for the mouse.

---

### Post by darkaizen on 2009-05-07
I love this game, but I have to switch out of linux to play it. Right now I'm in a situation where I don't have a working Windows box so I'm looking into a solution for Linux now.

I've searched around, and found very little in playing games in Linux. I've tried Wine, but it's irrelevant to this situation because of the nasty Gameguard that Ijji decided to use. This can be applied to nearly any game that has a web-based starting application, and has some kind of "auto install" gaurding/anti-cheat system.

So, I came across your situation, to run it in a Virtual machine. I didn't have high hopes for it, but it seems to be the only way reasonable, other than installing a fresh copy of windows on a separate partition, and have to restart my computer to switch between the two OS.

I've followed your instructions, but to no avail, GunZ freezes right after the Game Guard loads. In fact, the whole virtual system, Just VirtualBox, freezes. The machine still believes that the Virtual machine is running, but Nothing happens, and no amount of shortcuts/resolutions I try it doesn't work. At first, I thought it was a memory problem, but I've dedicated more than enough virtual Ram, and video memory (128MB of video, 1000MB of RAM) to it. I'm assuming there's something wrong with the graphics processing, or of a lack of resources.

I did install Wine3D on both the administrator account, and my own account but it didn't seem to do anyhthing.

I did install another game, UrbanTerror, a Counter-Strike type of FPS. Which does not work as well. It says it fails in loading some graphics, which I'm assuming is linked.

Any help and/or advice would be greatly appreciated.

---

### Post by wolfyking2 on 2009-05-07
could you tell us what your graphics card is?

---

### Post by darkaizen on 2009-05-07
```
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
```

---

### Post by YoShiy on 2009-05-17
Sorry for bumping that thread after a week, but i would like to know which settings you used for your visualbox configuration.

I set 768mb ram and 128mb graphic memory (3D is activated). 
I am using the latest VB version 2.2.2  
I am using a GeForce8800GT and a AMD64X2 5000+ BE.  
The 180ish drive for linux is installed successfully (Compiz works flawless). My only problem is that gunz runz terrible slow... :( 
I need like 5 seconds to turn the camera a little bit and i have to press space like 3 times to make one successfully jump :( 
I followed your instructions so far and i think it went well except that huge performance issue. 
I watched your video on youtube and really wondered on how you did get it that fast.  

I am using Kubuntu 9.04 Jaunty Jackalope with KDE4.2.3 btw.  

I appreciate any answer :)

---

### Post by darkaizen on 2009-05-20
Hmm.. Well, you got farther than I did, how did you get gunz even running in VirtualBox?

I installed both Ijji and Virtualbox as they should, along with WinXP, but they don't seem to agree with eachother.

---

### Post by gWX0 on 2009-07-28
> **darkaizen said:**
> Hmm.. Well, you got farther than I did, how did you get gunz even running in VirtualBox?

I installed both Ijji and Virtualbox as they should, along with WinXP, but they don't seem to agree with eachother.

Sorry to be bumping this (Again!), but I thought I deserved to let everyone know on some updates.

Firstly, Virtualbox 3.0 is out with experimental Direct3D support built-in now :)!  Install XP, install the guest additions, install IJJI Gunz, then enjoy!  I've successfully used it already on a Windows host, as well as Debian/Ubuntu.  Good luck!

EDIT: Settings for VirtualBox:

128MB of video ram, but it works fine with less.

512MB of system RAM, but more/less has worked for me (Up to 2048MB has worked, down to around 3XX-4XXMB has worked as well).

Enabled 3D acceleration.


During the "VirtualBox Guest Additions" installation, you'll have to check off the options for D3D9 (D3D8 should be optional, D3D7 is definitely not needed) experimental support.

---

