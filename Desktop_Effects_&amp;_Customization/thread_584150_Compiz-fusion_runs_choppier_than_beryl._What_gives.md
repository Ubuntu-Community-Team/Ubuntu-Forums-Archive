---
title: "Compiz-fusion runs choppier than beryl. What gives?"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by kirk ammon on 2007-10-20
After upgrading to Gutsy and using compiz-fusion, my wobbly windows look like crap. My windows have significant tearing at the edges. It is very obvious and very annoying. I used the same hardware with Beryl and it looked great but after the "upgrade" it looks worse than before. 

I know compiz-fusion is still in the works and is susceptible to bugs, but other people dont seem to have this problem. Can something be done or do I just need to wait for a better version of Compiz-fusion to come out?

I am using a nVidia GeForce 6800 with 256mb memory, 1GB of RAM, and I have an Intel 3.33 GHz cpu.

Please let me know if this is fixable!

---

### Post by medicineman24 on 2007-10-20
same problem here.  ati radeon 9550 256MB AGP, pt4 ht 2.8Ghz (Dual Core), 512 MB 333Mhz ram

---

### Post by fart_flower on 2007-10-20
Right after installing Gutsy I too noticed poor framerates.  However, this was quickly fixed by going into System > Preferences > Screen Resolution and selecting 60 Hz from the drop down menu.  (I also changed the corresponding value in CCSM.)

For some reason, Gutsy had my refresh rate set at 50 Hz, and Compiz was subsequently trying to run at this rate.  However, according to my monitor's onscreen display, a 60 Hz signal was being received from Gutsy, despite being set to 50 Hz during installation.

I've noticed a few other framerate issues in Compiz.  With anti-aliasing turned on, the cube rotates fluidly without screen tearing, but moving a single window around the desktop gives slight-but-noticeable choppiness.

I've also have no filtering when spinning the cube.  Perhaps it's not using mipmaps?  A few plug-ins, such as Switch Shifter, appear to have mipmap options, but I couldn't find anything for the cube.  

I used to run Beryl smoothly with both 4X anti-aliasing and 4X anisotropic enabled.  But with compiz the former causes framerate lag, and the latter has no affect.  (Which isn't surprising, seeing as mipmaps don't appear to be enabled.)

---

### Post by victor9098 on 2007-10-21
Hi,

I seem to have the same problem. Using the advice above I matched the refresh rates to 60 each (screen was 60, Compiz was at 50) but that has not solved the problem.

I have an Intel GMA 950, Intel Core 2 Duo T5500 Processor (1.66GHz) and 1GB DDR2 SDRAM. Beryl ran and looked perfect, this has only been an issue since my upgrade to Gutsy.

What next?? :confused:

---

### Post by kirk ammon on 2007-10-21
Ok I matched the framerates and unfortunatly it did not help one bit.

---

### Post by victor9098 on 2007-10-21
After messing with the refresh rates, after rebooting the machine the screen resolution was all messed up. Tried to fix, but when I rebooted again I could not even log on!!

So several reboots later I am back were I started...the gibbon is certainly living up to it's name!

Right, my desktop effects are now turned off and I hope that someone figures out what is going on. Should I log this problem as a bug in launchpad?

:cry:

---

### Post by UMDGaara on 2007-10-21
In the compizconfig settings manager under the Display Settings tab in General Options make sure Sync to VBlank is UNCHECKED.

If you really can't stand the screen tearing, Set the Refresh Rate to 60 and then go to your Nvidia settings (Applications -> System Tools -> Nvidia Settings) and force VSync for GL applications (under OpenGL settings)

In my experience, compiz/beryl/compiz-fusion are all choppy turning on Sync to VBlank. The driver does a much better job.

Also when doing this I've occasionally run into problems that I don't really undersand involving my mouse cursor disappearing that I read might be related to this VSync method and/or the Enhanced Zoom plugin. Your mileage may vary.

*Edit*
There are several xorg.conf options you can add to improve performance. I recently read a good page explaining most of them. If I find the link again I'll post it here. In the meantime, these are the ones I use:

Under the "Screen" section (not "Screen #" if it's there)
    DefaultDepth    24
    Option         "NvAGP" "0" # (Only if not using an AGP card. Yours should be PCI-E I'm pretty sure)
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "DisableGLXRootClipping" "True"
    Option         "RenderAccel" "True"
    Option         "DamageEvents" "True"
    Option         "UseEvents" "False"
    Option         "TripleBuffer" "True"
    Option         "BackingStore" "True"

Also this at the bottom:
Section "Extensions"
    Option         "DAMAGE" "Enable"
    Option         "RENDER" "Enable"
    Option         "Composite" "Enable"
EndSection

*edit again*
Evidently the nvidia vblank setting gets applied to GL applications started after the option is set. This means you might have to restart compiz in order to see an effect.

To see the command Gusty used to start compiz, use the following in a terminal:

```
$ ps -ef | grep compiz.real
```

copy all the stuff after compiz.real, press Alt+F2 and type:

```
compiz 
```

then paste all the options along with it that you copied from the currently running process

---

### Post by siaco on 2007-10-22
Thanks for this, it gave me back my speed under Gusty on Compiz as I had under last Ubuntu version. :-)

---

### Post by fart_flower on 2007-10-22
> **UMDGaara said:**
> In my experience, compiz/beryl/compiz-fusion are all choppy turning on Sync to VBlank. The driver does a much better job.


That certainly was my experience with Beryl for the past year. But now that I'm using Compiz Fusion, the opposite is true.  I find using the CCSM options is the only way to get a consistently smooth experience.  Quite surprising considering my past experiences.

---

### Post by kirk ammon on 2007-10-22
Ok, UMDGaara, I tried what you said with Sync VBlank and such and it did nothing. Then I copied and pasted those commands into xorg.conf (except the [Option "NvAGP" "0"] line, I do have an AGP card) and after restarting X my monitor was no longer functional. Just black with a box in the center that said "input signal out of range". I was able to restart and dpkg-reconfigure to get X working correctly again. What went wrong?

---

### Post by UMDGaara on 2007-10-24
Beats me, sorry.

I've set up beryl and compiz-fusion on half a dozen different systems and various linux distros all the same way. Never had a problem. Hopefully someone else has some ideas.

---

### Post by aaron13 on 2007-10-24
I was having this problem too.  I fixed it by clicking on the 'wobbly windows' button in the CompizConfig manager, in there under the 'general' tab there are some sliders.  Slide 'grid resolution' all the way to the right to max it out.

This worked for me, hope this helps you.

---

### Post by victor9098 on 2007-10-25
Yip, I killed wobbly windows to smooth things up a bit. But still clumsy with the desktop effects on...the annoying thing is that compiz ran perfect under 7.04 and it was supposed to be 'unstable' then!

There seems to be a couple of MB of updates each day, just hope they eventually get round to solving what has happened.:(

---

### Post by picopir8 on 2007-10-25
I am at work now and going off memory so pardon me for being a bit vague.  For me wobbly windows were especially choppy.  I was able to greatly improve it by unchecking the checkbox at the top of the wobbly window screen.  IIRC, it had something to do with forcing the window to adhere to a grid.

Most effects still stutter a bit for me the first time I use them but then they are fine.  I assume that is because the effect is being loaded into video memory.  I wonder if there is a way to force all effects to be loaded into video memory at startup and just reside there to speed things up.

*EDIT*
The wobbly window option mentioned above is "Snap Inverted". Unchecking that really improved my wobbly windows.

Also, thanks UMDGaara.  I followed your tips and it seems to have made things run a little smoother
*END EDIT*

---

### Post by pfh on 2007-10-30
I have read the entire thread for other people's experiences and solutions, but I must say: I still have this problem. 

Ihave an Nvidia 6600GT and a Samsung SyncMaster 226BW. I use the restricted driver. My system worked perfectly on Feisty. I used the backported compiz fusion from the Gutsy RC. 

On Gutsy, however, compiz seems choppy and slower. This is most obvious with wobbly windows, which have massive tearing.

I have tried everthing suggested in this thread. No luck.

One possibly related issue I have with Gutsy that I did not have with Feisty is this:

The System > Administration > Screen and Graphics detects my display incorrectly. Even if I manually set it to the correct screen, it still thinks that it cannot run 1680x1050@60. The best I have been able to produce is 1680x1050@50. 

It doesn't matter if I use the restricted driver or the nv driver. 

If I use the nvidia-settings tool, I am able to get 1680x1050 (according to this tool). But System > Administration > Screen and Graphics still reports incorrect stuff. 

Maybe all these differences and issues confuse compiz? 

I haven't tried using an older restricted driver. Maybe the one I used in Feisty was older and better?

Please help!

/David

---

### Post by cdekter on 2007-10-30
Turn off the "Detect Refresh Rate" option in CCSM and set the refresh rate slider to the correct value yourself - choppiness gone!

---

### Post by kirk ammon on 2007-10-31
Ok...I have an LCD monitor that has different refresh rates for vertical and horizontal. I turned off autodetection and set CCSM to the horizontal refresh rate. Everything looks much better...except....

There is still tearing on the left and right edges of windows when i move them! (but everything else looks great!)

Thanks for the help...maybe someone can figure out the tearing thing?

---

### Post by cdekter on 2007-10-31
You need to set it to the vertical refresh rate - usually 60 hertz.

---

### Post by kirk ammon on 2007-10-31
Thanks, cdekter, but it didn't quite do it. Here's something interesting that my be a problem: On my monitor's menu it says I have Horizontal Refresh rate of 70.5hz and vertical 75hz, but under System > Preferences > Desktop Resolution, my refresh rate is set to 50. if I click the pull down menu, I can get 50, 57, or 58. is there a way I can get this to be 75?

---

### Post by kirk ammon on 2007-10-31
After adjusting my refresh rate in CCSM to my monitors native rate, AND checking SyncToVBlank in CCSM, my windows do not tear anymore! Everything moves smooth as butter. Thanks everybody!

---

### Post by kirk ammon on 2007-10-31
Ok Correction....checking Sync to VBlank makes wobbly windows move smoothly, but now my desktop cube is a little choppier....

---

### Post by UMDGaara on 2007-10-31
> Ok Correction....checking Sync to VBlank makes wobbly windows move smoothly, but now my desktop cube is a little choppier....

That's normal. From what I've seen Cube and Sync to VBlank in CCSM don't play nice. I've only had a smooth cube with Sync to VBlank enabled when using cards higher than a 7600. That's why I posted all that jazz about using nvidia's driver settings to force Sync to VBlank for GL applications. It works better once you get it going.

---

### Post by salvadorveiga on 2007-11-01
I'm running compiz under an ATI 9200 and it runs smooth unless i activate transparency and skydomes on the cube... how can i make it faster ? if I turn transparent cube while rotating it gets choppy... I matched the compiz resolution with the screen.... but i did nothing else since i am complete noob concerning linux... still making baby steps... and the code on the first pages i believe was for nVidia...

thanks for the help

---

