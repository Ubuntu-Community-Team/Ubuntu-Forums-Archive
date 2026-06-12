---
title: "Annoying black full screen flash with nvidia"
date: 2007-11-13
forum: Desktop Effects &amp; Customization
---

### Post by AndyCR on 2007-11-13
I'm using the nvidia driver with a geforce 7600 go and compiz fusion on gutsy with all the newest updates. Every once in awhile - sometimes frequently, sometimes not at all for a half hour - the entire screen will flash to black for a split second, then it's fine again. It's very distracting, and doesn't happen with compiz disabled.

---

### Post by travist120 on 2007-11-14
Hi, I'm getting the EXACT same problem. I've been getting it for a while now, especially more noticeably with compiz fusion enabled. Sometimes, I take the long route, and do a reset. Usually, that will stop the flicker for a few days. Other times, I just completely turn compiz off, and revert back to good ol' metacity. Anybody else know how to stop this? Permanently for that matter?

---

### Post by FuturePilot on 2007-11-14
Sounds like the black window bug. It's a bug in the Nvidia driver.
Try running Compiz like this
```
compiz --replace --indirect-rendering --loose-binding
```

---

### Post by Zorael on 2007-11-14
It happens for me too on my Nvidia GeForce Go 7600. I found a workaround on these forums that I tweaked a bit, though, and now it's completely gone!

I made two scripts. The first one will call **glxinfo** every 25 seconds, which apparently helps both with fullscreen flashing and with animations being sluggish at first and then smooth after one second. The second will first call the glxinfo loop script, and then launch compiz.

```
zorael@azrael:~$ cat /usr/bin/compiz.start
#!/bin/bash

# kill earlier glxloops
killall glxloop

# start new
glxloop

# invoke compiz with KDE and Nvidia tweaks. pass arguments to compiz and leave terminal control to the user
__GL_YIELD="NOTHING" compiz --loose-binding --ignore-desktop-hints ccp $@ &

zorael@azrael:~$ cat /usr/bin/glxloop
#!/bin/bash

echo
echo glxloop: starting loop
echo \* killall glxloop to terminate.
echo

while true; do glxinfo >/dev/null; sleep 25; done &
```

Then I made them executable (sudo chmod +x /usr/bin/glxloop /usr/bin/compiz.start) and lastly put a symbolic link to compiz.start in my KDE autostart folder. I guess you can just add an entry in Sessions in Gnome, if you're using Ubuntu.

As for the --ignore-desktop-hints argument, I think you can omit that with Gnome. It's to make Compiz ignore KDE's virtual desktop settings (else I get 4x4 desktops instead of just 4).

Since you seem to have the same card as I do, though, the rest of them might actually help.


My xorg.conf sections, with tons of tweaks that I don't know if they help at all, but it's rock stable and with stellar performance:
```
Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce Go 7600]"
    Driver         "nvidia"
### copy/paste
    Option         "AllowGLXWithComposite" "True"
    Option         "DisableGLXRootClipping" "True"
    Option         "RenderAccel" "True"
    Option         "DamageEvents" "True"
    Option         "RandRRotation" "on"
    Option         "UseEvents" "True" # may cause frequent lockups
    Option         "AddARGBGLXVisuals" "True"
    Option	   "Coolbits" "1"
    Option         "TripleBuffer" "True" #increases latency slightly (delay between user input and displayed result)
### copy/paste
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce Go 7600]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "NoLogo" "true"
    Option         "NvAGP" "0"
### copy/paste
    Option         "AllowGLXWithComposite" "True"
    Option         "DisableGLXRootClipping" "True"
    Option         "RenderAccel" "True"
    Option         "DamageEvents" "True"
    Option         "RandRRotation" "on"
    Option         "UseEvents" "True" # may cause frequent lockups
    Option         "AddARGBGLXVisuals" "True"
    Option	   "Coolbits" "1"
    Option         "TripleBuffer" "True" #increases latency slightly (delay between user input and displayed result)
### copy/paste
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
EndSection
```

I never got a clear answer as to which section those options go, so I copy/paste them into both. Some say they should go into the Device settings, but then nvidia-xconfig (which likely should know what it's doing) puts them in Screen.

---

### Post by AndyCR on 2007-11-14
Thanks guys! I'll try that.

Does anyone have issues with suspending while compiz is enabled on an nvidia card? I kind-of solved it with a hack that I can share if anyone has the issue.

---

### Post by Zorael on 2007-11-14
Do share!

---

### Post by AndyCR on 2007-11-15
OK, like I said, this is a -really- ugly hack. This will allow you to sleep successfully by killing compiz before you sleep and restarting it after you resume. There is undoubtedly a better way to do this, but it works for me, so here you go. Backup all files we're editing before continuing.

Open /etc/acpi/sleep.sh. Add this to the end:

```
killall compiz.real
```

Now, create a file in /usr/bin called checkcompiz.py. Add this to it:

```
import os, time

while True:
        if not 'compiz' in os.popen("pstree").read():
                os.popen("compiz")

        time.sleep(1)

```

Now, start the script by pressing ALT+F2 and running python /usr/bin/checkcompiz.py. You can add it to System->Preferences->Session->Startup Programs to have it start when you turn on the computer. If you switch to metacity, the script will not keep turning compiz back on since it doesn't use --replace (it'll run compiz once a second and fail to start because metacity is enabled.)

I haven't found a better way to do this beyond nVidia fixing their drivers, but it works well.

---

### Post by BoardDWorld on 2007-11-15
Actually the black screen flicker is "very" easy to resolve. Just go to  the **System ---- Preferences ---- Advance Desktop Effects** menu. Select **General Options** then **Display Settings** untick **Detect Refresh Rate** and manually set the refresh rate to 60Hz. Restart your system, done!

---

### Post by tvnz on 2007-11-15
same card here :) 7600 go , same problem , i will try these hacks, thks

---

### Post by BoardDWorld on 2007-11-15
The only problem I have with suspend/hibernate & sleep is the screen goes really ugly, looks more or less like my laptop is dying. The screen will go a pixelated black and areas of white will start spreading around the screen. It doesn't get much chance entering and exiting sleep mode as this action is quite fast. However you really get a good show going in and out of hibernate.

---

### Post by AndyCR on 2007-11-15
> **BoardDWorld said:**
> Actually the black screen flicker is "very" easy to resolve. Just go to  the **System ---- Preferences ---- Advance Desktop Effects** menu. Select **General Options** then **Display Settings** untick **Detect Refresh Rate** and manually set the refresh rate to 60Hz. Restart your system, done!

It's been set that way from the beginning (it acts sluggish for me any other way). The problem occurs with that done. Thanks though. I haven't tried the X hacks yet, I'll try those.

---

### Post by BoardDWorld on 2007-11-15
"Detect Refresh Rate" is ticked by default (click the reset to default button and you will see it tick itself). Also make sure you have have your screen resolution specified under output, example: 1440x900+0+0

---

### Post by AndyCR on 2007-11-15
Sorry, when I said "from the beginning" I meant "I set it that way right after installation". That's exactly how I have it set up.

---

### Post by blackvd on 2007-11-15
Crazy i was having the same problem with my nVidia GeForce Go 7300 when running Sabayon 3.4e with compiz. Haven't had the problem since running Gutsy tho, but I'll bookmark in case.

I have a weird problem that happens every once in a while. When my screen sits for a while with nothing happening sometimes it'll go black and won't come back. Only way to fix it is with a hard reset. I have it set to never sleep while plugged in, so I don't think thats the cause.

---

### Post by BoardDWorld on 2007-11-16
Actually I can confirm I'm still having the problem with my recommended fix (it's happening again:().

---

### Post by BoardDWorld on 2007-11-16
> **FuturePilot said:**
> Sounds like the black window bug. It's a bug in the Nvidia driver.
Try running Compiz like this
```
compiz --replace --indirect-rendering --loose-binding
```

Well it's been 7 hours straight and not a single flicker, this method just may have resolved it thank you.

---

### Post by BoardDWorld on 2007-11-16
Speak of the Devil, it's back to haunt me. Roughly 8 hours without. I executed "sudo nautilus" as I did there was a quick flash now it's fairly repetitive. This really sucks.

I'm also getting occasions where my system sticks, everything locks up for half a minute sometimes more, though this usually happens only about once or twice every couple of days...

The screen flicker bug has been around before Feisty, why isn't this fixed?

---

### Post by Amaranth on 2007-11-16
It isn't fixed because it's not a problem with compiz but rather a problem with the nvidia driver. To make it go away (for awhile) when it happens switch to vt1 then back to X (Ctrl-Alt-F1, Ctrl-Alt-F7).

---

### Post by BoardDWorld on 2007-11-19
Thanks for the heads up on the driver bug. Just thought I better let you know that the that 3 out of the 5 times I have Ctrl-Alt-F1 out then Ctrl-Alt-F7 back in, my system has completely locked up. Only hard killing my system with the power button will work.

I recommend anyone with this problem look to this thread: [http://ubuntuforums.org/showthread.php?t=579761](http://ubuntuforums.org/showthread.php?t=579761)

Edit: There's now a new driver that fixes these lock-up screen flash issues!:
[http://www.nvidia.com/object/linux_display_ia32_169.04.html](http://www.nvidia.com/object/linux_display_ia32_169.04.html)

---

### Post by AJerman on 2007-11-19
I have an 8800GTS and I don't flicker black, my screen acutally goes all distorted for a split second, then comes back. Kind of weird and a little annoying, but it goes away and come back in less than a second and I just keep on working. I've seen it happen a couple of times now, but it doesn't seem to have any specific pattern that I've noticed. Do you guys think that this is related?

---

### Post by BoardDWorld on 2007-11-20
I have been using the 169.04 since last night and can confirm that it "doesn't" resolve the issue.

---

### Post by BoardDWorld on 2007-12-01
The following fixed the screen flashes and system freezes for 30 straight days without problems until I installed the current 169.07 driver using ENVY.
The problem, for those who don't know, is caused by the nVidia PowerMizer (in the nVidia Driver) changing the clock speeds from 2D to 3D. People have been blaming Compiz but Compiz just brings out this flaw in the driver because of the frequent change between the 2D and 3D clocks. The following fix locks your video card to the single 3D clock speed.


The fix below is for the nVidia driver from Ubuntu only(Synaptic or clicking the Restricted Drivers check box etc). 

Open nvidia-kernel-nkc using Terminal with the following command:

```
sudo gedit /etc/modprobe.d/nvidia-kernel-nkc
```

Copy & Paste the following at the bottom in a new line:

```
options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"
```

Save the file and restart your PC.


Source:
[http://www.nvnews.net/vbulletin/showthread.php?t=96673&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=96673&page=2)

For those using ENVY to install their drivers or are downloading them from nVidia and installing them manually (there's no point doing it manually, use ENVY) scroll further down the page.

Notes: As said this fix locks the video card to the 3D clock, for some this could cause heat problems and greatly reduce battery life. For myself I don't have heat problems at all. It sits at 58degrees in both the 2D without this fix and at the constant 3D clock speed with this fix. Battery life, when I use it on battery to that extent, is reduced by 10-20 minutes which still gives me over 1 hour. This makes sense as even though it's at the 3D clock it really only starts causing heat/using power when it gets used/stressed, eg playing games. No negative reports have been made on the nvniews forum and I keep pretty frequent tabs on it.

---

### Post by phenest on 2007-12-06
Yep. That fixed it for me too. I previously installed xserver-xgl to fix the flicker but that caused a blank screen after 10 minutes. Uninstalled it now.

If you use F11 to view Firefox full-screen, you will occasionally see a full screen flash. But that seems to be it.

Is it true this fix causes higher temperatures and shorter battery life? Can anyone confirm?

Also, should this fix be implemented in the nVidia driver or should it be Compiz that is fixed?

---

### Post by Amaranth on 2007-12-07
This 'fix' locks the nvidia card in full 'performance' mode so it's certainly going to cause more heat and less battery life.

Also, there is nothing to fix in compiz, this happens without compiz running.

---

### Post by phenest on 2007-12-07
> **Amaranth said:**
> This 'fix' locks the nvidia card in full 'performance' mode so it's certainly going to cause more heat and less battery life.

I see. I didn't know what the 'fix' did. Thanks for the info.

> **Amaranth said:**
> Also, there is nothing to fix in compiz, this happens without compiz running.

Are you sure that's correct? All reports I've seen show users have been running Compiz or some other composite manager. I only get the problem with Compiz running. If I disable Desktop Effects, the problem ceases.

---

### Post by BoardDWorld on 2007-12-12
> **Amaranth said:**
> This 'fix' locks the nvidia card in full 'performance' mode so it's certainly going to cause more heat and less battery life.

Also, there is nothing to fix in compiz, this happens without compiz running.

With my HP Laptop(Specs below) I don't have any heat issues with this temporary fix. Having something that resolves this has been "far" greater than the 15 minutes or so I have lost in battery life (when I actually use it on the battery to that extent). If you're playing games and want Compiz effects I recommend this fix until there is an actual driver fix. However if you don't mind not having these features simply change back to the default NV driver.

Also If you look at the link provided you will see what you have said is already mentioned.


> Are you sure that's correct? All reports I've seen show users have been running Compiz or some other composite manager. I only get the problem with Compiz running. If I disable Desktop Effects, the problem ceases.

Yes he's correct. Compiz only invokes the flaw in the driver more than anything else because the very frequent change between the videos cards dynamic 2D/3D clock speeds.

---

### Post by mdoube on 2007-12-13
I have applied the recommended fix to my Sony Vaio SZ650N with GeForce 8400M GS but the flicker remains and my CPU cores are both cranking at 100% and 73-77 degC .

nvidia driver 100.14.19 from nvidia.com, Ubuntu Gutsy 64-bit

Cheers

Mike

---

### Post by BoardDWorld on 2007-12-17
> **mdoube said:**
> I have applied the recommended fix to my Sony Vaio SZ650N with GeForce 8400M GS but the flicker remains and my CPU cores are both cranking at 100% and 73-77 degC .

nvidia driver 100.14.19 from nvidia.com, Ubuntu Gutsy 64-bit

Cheers

Mike

Hello Mike,

Then you most likely have a different problem to resolve. Go to here: [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14) and post your nvidia bug report log along with an explanation on what's happening. Hopefully you'll get some help.

---

### Post by BoardDWorld on 2008-01-11
For those using ENVY to install their drivers or are downloading them from nVidia and installing them manually you will need to place the option below:

```
options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"
```

Here:

```
sudo gedit /etc/modprobe.d/options
```

For the fix to take effect...


Edit: Thought I better to remind everyone to remember to test each time they update their driver to see if the problem is resolved. You can do this by opening options again as above and place a # in front as below then restart your PC.

```
# options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"
```

Of course if it's still not fixed just remove the hash...

---

### Post by cogitordi on 2008-01-18
AMD64 CPU, Gibbon/64, on-board Nvidia 6100, using Envy...

The flashing occurs whether or not I do anything mentioned thus far in this discussion, whether I have enabled Desktop Effects or not. 

The flashing is certainly related to changes in the CPU frequency. I can tell this from my use of "OnDemand" in the CPU Frequency Scaling applet. 

This is annoying to the point of being unusable.

---

### Post by cogitordi on 2008-01-19
Additional note...  I did not have this problem with my ATI-based PC. I wouldn't recommend Nvidia to Ubuntu users until this bug is fixed.

---

### Post by ph1 on 2008-01-25
Well, this fix worked great for me!  My appreciation for finally finding the solution to this maddening issue.

However, I have another concern:  I have a massively overpowered graphics card for the tasks I'm doing in Ubuntu (Go 7950).  So, in order to reduce heat and save power, I was wondering if there is a way to both lock the card in 3D mode and to underclock 3D mode to some sufficient but less extravagant value than 575,600.  

I've tried using coolbits in nvidia-settings, but the default clock speed for 2D or 3D overrides anything I try to apply when I'm locked at PerfLevelSrc=0x2222.  (Also, nvidia-settings erases its settings with each reboot and must be reset, or some magic must be worked with xinitrc, which I am willing to do, but nvidia-settings isn't actually responding to my custom settings and just returns that the clock frequencies have been set to the defaults.)

Does anyone know a way that I can change the default 3D clock frequencies or work around the performance level lock to get nvidia-settings to work?

Many thanks in advance.

---

### Post by Nando777 on 2008-01-31
Amazing, this was posted almost two years ago and nvidia still hasn't fixed this bug. 

It happens to me with Geforce 7600 go

I'll try the fix by BoardDWorld  

Hopefully it fixes it.

---

### Post by Nando777 on 2008-02-01
I need your help:

I sent this problem to nvidia bug reports (after 2 years is about time it got fixed) and they are trying to replicate the problem. I can tell them to just use it for a while with Compiz activated and so on and it will happen but can anyone say EXACTLY what to do for it to occur?

For me it doesn't happen right away, in fact at first it doesn't do it, it starts happening after I use the computer for a little while, but If I try to force it to do it on cue I don't know how to. Sometimes the clock changes and it doesn't do it at beginning, others it does.  

Please if you have any idea how to EXACTLY replicate this problem post it here or send it to 

[email]linux-bugs@nvidia.com[/email]

to Roland's attention.

Thank you very much

---

### Post by Nando777 on 2008-02-01
Oh and if you send it to their e-mail you may want to add a bug report as well. That would help.

Thank you!

---

### Post by ph1 on 2008-02-03
I find that I often (but not always) get the flicker when, after moving around my windows with wobbly windows turned on, swapping workspaces on the desktop cube, etc., I finally settle down and just start reading stuff on the internet--usually my screen will flash once after a few seconds of less activity.  Usually, but not always.  And I find that the flash seems mainly to be occurring when the clocks go down--I usually don't notice anything when the clocks go up to engage all the pretty compiz effects.  I'll experiment a little more and see if I can find an exact formula to make the flash appear.

---

### Post by Nando777 on 2008-02-05
Thank you Ph1, I sent your idea to nvidia. It seems that nvidia is unable to replicate this problem, they are still trying hard to find the problem but with no results -- so maybe it only happens to some people and sometimes? This is the worst kind of bug because is not obvious at all or easy to replicate. If any of you finds the exact formula let me know so I can send it to them. 

So if the problem isn't fix by next release you can't really blame nvidia, they are trying, it's just an elusive problem.

---

### Post by ph1 on 2008-02-05
Well, Nando777, I never really did blame Nvidia, since they did make my sweet graphics card.  And I do appreciate them working to make their drivers available to open source systems.

In fact, the 169.09 driver seems to have resolved the problem, at least on my computer.  I just installed it yesterday and I have been flicker-free since.  (Before I was using 100.69, or something along those lines, I don't have a good short-term memory.)

Thanks for your help, and I hope that if anyone else continues to experience this problem that a fix will appear somewhere for them.

EDIT:  Well, I guess I should have knocked on wood.  I've started seeing the black flash again.  It seems to occur every time I open a terminal window (desktop effects), and only after I've had an uptime of several hours.  I hadn't been up long enough to notice it before.

---

### Post by Nando777 on 2008-02-06
haha, welcome to the club of the new driver flickers.

You are right, I wish every company supported their Linux drivers as much as nvidia does. 

This must be a ghost bug, it shows up whenever and wherever it wants. It may hunt some nvidia users for a long time to come. Maybe we did something wrong in another life -- like using Windows NT or Windows 95. Actually I did that in this life, what am I talking about.  :-D


If you are up for it you should run nvidia-bug-report.sh from the terminal as you are getting the flickers, that will create a log with a bug report, then mail it to [email]linux-bugs@nvidia.com[/email] to Roland's attention. In the subject you may write something like "Regarding Black screen flickers" or something like that.

That may help him see the problem from two different computers and see what we have in common to reproduce it and fix it.

Thank you  Ph1

---

### Post by ph1 on 2008-02-06
Will do, Nando777.  Anything to help the cause!  

I would try the PerfSrcLevel hack again, but it makes my GPU run at ~10-15 degrees hotter, and I just get nervous.....for now I will live with the black flash and hope that nvidia can find the bug and squash it.

---

### Post by ph1 on 2008-02-06
In regards to the black flash:

I've been experiencing it constantly, spaced 10-30 seconds apart, for something like the past hour.  I opened nvidia-settings and checked the powermizer tab.  EVERY time the flash occurred, the powermizer mode changed from one level (1, 2, or 3) to another.  When I then went to change the clock speeds manually using Coolbits, the screen also flashed when applying my settings.  Every time the flashes start, they accompany the powermizer settings switching.  I've got the log created, and I'll be sending it to Nvidia, per your instructions, Nando777.

Meanwhile I will also be searching for a way to lock Powermizer in the middle mode or something in order to stop the flicker.  

Best,
ph1

---

### Post by Nando777 on 2008-02-06
Thanks a lot ph1

Send those descriptions to Roland as well, he may want to read them as it may help him to replicate the problem, it happens to me too, when the clock changes the thing flickers. Yes I don't like using the fix for the same reason even though I think one can be safe up to 100 degrees but it bothers me hearing the fan all the time going crazy, in fact I rather not use it and turn off al the effects and have a lifeless desktop.

Well we did the best we could, hopefully they squash the bug! Otherwise we can start an underground club, bring all our laptops, check each other flickers and see whose are cooler he!

By the way you use a laptop as well right? As far as I know this only happens on laptops.

---

### Post by ph1 on 2008-02-06
I do have a laptop (if you want to call my 17" box something you can put in your lap).  I am using a Dell, with a Geforce 7000 series graphics card.  It seems from the forums that other 7000 series users have this issue; ironically, by installing Linux, I have inspired some of my friends to do so, and none of them seem to be experiencing the problem so far (two have Geforce 8000 series laptops, another has a Quadro 135, another has.....a MacBook....?).  Is this problem unique to the 7000 Go series [and its predecessors]?  Any other people out there that can testify either way, if the black flash *related to clock speeds* is limited to certain GPUs?

---

### Post by Nando777 on 2008-02-09
I updated the core (prompted by an Ubuntu update) and the problem has stopped for three days and it came back again just now but it occurs less often. 

I just don't get what the problem is. It's time to move on for me :-D

EDIT: Now it happens just as often as it did before.

---

### Post by ph1 on 2008-02-12
So I finally caved and enabled the PerfSrcLevel option to lock my GPU in Performance Mode, as excellently recommended by BoardDWorld.  However, because my GPU was getting hot and causing "screen spasms," here are the steps I took to underclock it and reduce heat/power consumption:

1.  Installed the 169.09 Nvidia driver, using Envy.  This allows my laptop's mobile GPU (locked under the 100.xx driver) to be over/underclocked.

2.  Wrote (per the help of others) a simple bash script:

```
#!/bin/bash
nvidia-settings -a GPUOverclockingState=1 -a GPU3DClockFreqs=250,350
```

This sets my clock settings to 250 MHz GPU, 350 MHz memory, which is slightly above the "low 3D" setting.  It causes my GPU to idle at 50-55 degrees C.  (Individual clock frequency mileage may vary.)

3.  Set the script to execute on startup:  System > Preferences > Sessions > Startup Programs > Add > <browse & find your script> 

4.  I also installed i8kmon to help control temperatures manually (I have i8kmon open on startup automatically), and I also added my GPU clocks and temperature to Conky so I could keep track of them.  (If you're interested in how let me know.)  Now my black flash is solved and my temperature paranoia is placated.

Of course, the ideal solution would be a fix in the driver itself, but pending that, this works for me.

---

### Post by vervelover on 2008-02-13
@ph1

I have a problem with your script. I named it .nvidiaclock, put it in my home directory and made it executable, than added this command to sessions:

```
sh /home/myusername/.nvidiaclock
```

I also modified the clock frequencies this way:

nvidia-settings -a GPUOverclockingState=1 -a GPU3DClockFreqs=100,220

I can't go beneath 67 C° in the thermal monitor in nvidia settings, which is far above than before! Did I do anything wrong? I have an nvidia geforce go 7400 turbocash 256mb if this can help..

Thanks
Alessio

---

### Post by mlapaglia on 2008-02-13
i installed the 169.09 drivers with my geforce go 7600 and the flashy hasn't happened in 48 hours.

---

### Post by ph1 on 2008-02-13
> **vervelover said:**
> @ph1

I have a problem with your script. I named it .nvidiaclock, put it in my home directory and made it executable, than added this command to sessions:

```
sh /home/myusername/.nvidiaclock
```

I also modified the clock frequencies this way:

nvidia-settings -a GPUOverclockingState=1 -a GPU3DClockFreqs=100,220

I can't go beneath 67 C° in the thermal monitor in nvidia settings, which is far above than before! Did I do anything wrong? I have an nvidia geforce go 7400 turbocash 256mb if this can help..

Thanks
Alessio

Hmm, that's strange, especially since your clocks are set low.  It looks like the script isn't working.  Can you run 

```
nvidia-settings -q GPUCurrentClockFreqs
```

in a terminal after the script has been executed and see if the clock settings have actually taken effect?  

Also, instead of typing the file path, try browsing and selecting the file.  I find that sometimes letting the sessions manager setup the syntax for me makes everything work.

I'm sorry that my solution didn't work for you....I'll see if I can figure out what to do to help you.  Report back if you can't get it to work and I'll do what I can.

---

### Post by vervelover on 2008-02-14
@ph1

Thanks a lot for your help! I really appreciate!

so.. if I run in a terminal:

```
nvidia-settings -a GPUOverclockingState=1 -a GPU3DClockFreqs=100,220
```

it returns nothing, but if I run:

```
nvidia-settings -a GPU3DClockFreqs=100,220
```

it returns this:

```
The valid values for 'GPU3DClockFreqs' are in the ranges 112 - 900, 200 -
    1100 (inclusive).
    'GPU3DClockFreqs' can use the following target types: X Screen, GPU.s
```

so I tryed with:


```
nvidia-settings -a GPU3DClockFreqs=112,200
```

and again, it returned nothing.

While trying all of these I checked the nvidia settings, but the powermizer was always set to max. perf. settings (level 2), clock 450,800 Mhz

In fact, tyiping this every time:

```
nvidia-settings -q GPUCurrentClockFreqs
```

always reported the same:

```
Attribute 'GPUCurrentClockFreqs' (alessio-laptop:0.0): 450,800.
    'GPUCurrentClockFreqs' is a packed integer attribute.
    'GPUCurrentClockFreqs' is a read-only attribute.
    'GPUCurrentClockFreqs' can use the following target types: X Screen, GPU.
```

I forgot to mention that I also have BoarDWorld option enabled in /etc/modprobe.d/options ,that's why GPUfreq is set so I high.. ph1, you have that enabled too, right? But you solved the clock problem with your script,right? I also tryied with your same exact script without modifying the clock freqs, but nothing changed.. Thanks again for your help!

@mlapaglia

with 169.09 I still have the issue if don't follow BoardDWorld's solution..

---

### Post by ph1 on 2008-02-14
Vervelover (and, if you are speaking of the band, nice taste), I forgot to mention something quite important:  you have to enable the Coolbits option in nvidia-settings before you can overclock/underclock.  Right now, it looks like Coolbits isn't working (or isn't enabled--quite silly of me to fail to mention this step...) because you aren't able to assign values to be your clock frequencies. 

So, to enable Coolbits, you'll have to edit your xorg.conf file, which, if something goes wrong, can really screw things up.  So, to be safe, you should make a copy of it before you edit it.  You can do this however you like; I might do it with 

```
sudo cp  /etc/X11/xorg.conf ~/Desktop/xorg.conf.bak
```

Next, you'll need to enable the option for Coolbits by adding a line to the "Device" section. of your xorg.conf.  First open xorg.conf by typing 

```
sudo gedit /etc/X11/xorg.conf
```  The line should read 

```
Option     "Coolbits"     "0xffffffff"
```

I think some people also use "1" instead of "0xffffffff", based on some directions I've seen around the web.

So, after I'm done editing, my "Device" section looks like this:

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"NoLogo"	"True"
	Option		"Coolbits"	"0xffffffff"
EndSection
```

Now save, and close.  I'm not sure if a reboot or just a relog is necessary, but I'd run a reboot to be safe.  Now, if you open nvidia-settings, you should see a Coolbits option, and if you run your script, when you open nvidia-settings you should see Coolbits already configured for you.  You should also see your user-defined clock settings when you run 

```
nvidia-settings -q GPUCurrentClockFreqs
```.

If you don't, report back and we shall further plumb this problem.  Again, my apologies for failing to mention Coolbits....

---

### Post by vervelover on 2008-02-15
@ph1

Yes! Now It works like a charm! The temperature's been reduced to 62° degrees (I used your original script because mine was setting clock freqs too low and compiz was running too slow)

Thank you you rock (just like The Verve)!!

---

### Post by da0ud on 2008-02-19
Hi !
I read all the thread in order to find a solution to my problem... the same as yours.
I thank u Ph1 for ur bash script however there is something wrong with it on my laptop.

Your script works well, I execute it when the session starts.

Lets say I am executing it now :

```
 da0ud@da0ud-laptop:~/Scripts$ ./nvidiaclock 

  Attribute 'GPUOverclockingState' (da0ud-laptop:0.0) assigned value 1.

  Attribute 'GPU3DClockFreqs' (da0ud-laptop:0.0) assigned value 250,400.

```

Then I try :

```
da0ud@da0ud-laptop:~/Scripts$ nvidia-settings -q GPUCurrentClockFreqs

  Attribute 'GPUCurrentClockFreqs' (da0ud-laptop:0.0): 250,400.
    'GPUCurrentClockFreqs' is a packed integer attribute.
    'GPUCurrentClockFreqs' is a read-only attribute.
    'GPUCurrentClockFreqs' can use the following target types: X Screen, GPU.

```

 but when i use this query a while after :
```
da0ud@da0ud-laptop:~/Scripts$ nvidia-settings -q GPUCurrentClockFreqs

  Attribute 'GPUCurrentClockFreqs' (da0ud-laptop:0.0): 100,220.
    'GPUCurrentClockFreqs' is a packed integer attribute.
    'GPUCurrentClockFreqs' is a read-only attribute.
    'GPUCurrentClockFreqs' can use the following target types: X Screen, GPU.

```

the values are 100,220 even if it was specified in the bash script to put 250,400...

I think your script assigns values but does not lock them... Am I right ?

Need ur help.

---

### Post by ph1 on 2008-02-19
> **da0ud said:**
> Hi !
the values are 100,220 even if it was specified in the bash script to put 250,400...

I think your script assigns values but does not lock them... Am I right ?

Need ur help.

da0ud, 

I find that the script "locks" the settings on my computer without a problem, but there are a few things that could be causing your clock settings to "not stick".  Here are some possibilities (you may have already ruled some of these out, but I'll list all that I can think of for the sake of completeness):

1.  Coolbits isn't enabled.  Like I mentioned earlier, I forgot to mention this in the original post....  Check your xorg.conf and see if it is.  Though if the script is assigning values at all (it's really just one simple command), Coolbits is probably enabled.

2.  Your driver version doesn't support over/underclocking.  When I was using the 100.xx driver, I found that my clock settings would not "stick" even if the assignment was reported successful.  When I tried to force underclocking using nvclock, my screen became filled with static-y artifacts--because the driver I was using forbade over/underclocking.  See which driver you are using by opening nvidia-settings; you can use the envy script to update your driver if it looks like it's an older one (I'm using 169.09).  

3.  Switching between battery and ac power switches your clock speeds.  Even with mine locked in 3D mode, 3D mode while on battery is 200, 300 (Performance Level 1) for me.  (3D on AC is clocked down to 250, 350.)  I have a GPU clock frequency monitor in Conky, and I notice it change as soon as I switch from one to the other.  However, once it has switched, it doesn't adjust at all--only when you change your power state again.  One thing you can try if this is your problem is adding to the script 

```
-a GPU2DClockFreqs=x,y
```

where you change x and y to the same level as your 3D clocks (be careful, I don't know enough about GPU architecture to warn if this is dangerous--try assigning a lower clock setting first and see if it "sticks" before you try anything else).  Other than this I'm not really sure what to do about it, but I'll see if I can root around in some config files and find something that might address it.

4.  You have to have enabled the so-called "PerfLevellSrc" hack to lock your clock settings at a constant value.  There are instructions by BoardDWorld earlier in this thread if you need them.

Post back with your progress and/or more info, and I'll try to do what I can (as nothing more than a helpful noob, heh heh....)

---

### Post by da0ud on 2008-02-19
Thank you !

In fact, that was because I tought your script could work without the first one of our collegue [sorry dont remember his name].
Now it's okay it's locked.

I have a problem now with VLC or even Totem while watching a movie. I'd like to know if that happens to u too. I dont know if my problem comes after x hours (like the flashes) or if it is random or anything else.
But I have those kind of lines on the video (full screen) that flash very fast too (it's hard to explain, but if u have that kind of problem u'll understand what I mean).

I've tried to select the X11 video output but it wasn't working, tried the XV or something and it seems to work but for long ???


Btw, if u have information regarding our "general" problem, some "new" driver that solves it or anything else don't forget to post a response on that thread.

See u later, many thanks.

Daoud

---

### Post by ph1 on 2008-02-19
Da0ud,

I'm glad everything worked out!  Unfortunately, I have not had any issues with any artifacts while watching movies, even with my clocks locked and underclocked.  I have seen several threads, however, about people with issues in video playback that sound much like yours.  Depending on your problems, you might want to take a look at [one]("http://ubuntuforums.org/showthread.php?t=641581") [of]("http://ubuntuforums.org/showthread.php?t=202937") [these]("http://ubuntuforums.org/showthread.php?t=465695")  [several]("http://ubuntuforums.org/showthread.php?t=628511") [threads]("http://ubuntuforums.org/newthread.php?do=newthread&f=73").

If I find out or remember anything else helpful, I'll post it.

---

### Post by ph1 on 2008-02-19
On second thought--if you have a bunch of fast flashing lines on your screen, it could be related to the refresh rate.  Check and see if the refresh rate under System > Administration > Screens and Graphics matches the recommended refresh rate for your monitor.

Alternatively, your clock frequencies could be suitable for ordinary use, but when playing a fullscreen movie, possibly inadequate due to being low; and, because they are locked, they can't clock up to provide enough juice to play the video.  You could try setting the clocks higher; it also might be possible to write a bash script that locks and unlocks the settings, but I think a reboot, or at least a reloading of the kernel or driver,  is required for it to take effect, so I'm not sure how it could be implemented.

---

### Post by da0ud on 2008-02-20
Ok thanks I'm gonna check what it can be but it isn't the refresh rate cause it's specified everywhere at 60Hz (nvidia-settings and compiz-fusion...).

See u soon and don't forget to post when you'll have an answer from nvidia support or a new driver that works.
Hopefully it will work in 2 months with ubuntu 8.04...

---

### Post by mikael_b on 2008-02-23
Hi, 

I have the same problem but I can't fix the problem :(

I have nvida GO 7200. I installed drivers with ENVY and then added the script that ph1 wrote and made it auto run. But it seems not to run at start up? Then i went to xorg.conf to edit the line about coolbit, but there is no such line.

> Section "Device"
	Identifier	"nVidia Corporation GeForce Go 7200"
	Boardname	"nv"
	Busid		"PCI:5:0:0"
	Driver		"nvidia"
	Screen	0
EndSection


Anyone know how I should proceed to fix this problem?

---

### Post by mikael_b on 2008-02-23
Ok, it works now! But I have to run with sudo 

 sudo nvidia-settings -a GPUOverclockingState=1 -a GPU3DClockFreqs=250,350

which is a problem when i like to make the auto start, how could i go around this?

---

### Post by ph1 on 2008-02-23
> **mikael_b said:**
> Ok, it works now! But I have to run with sudo 

 sudo nvidia-settings -a GPUOverclockingState=1 -a GPU3DClockFreqs=250,350

which is a problem when i like to make the auto start, how could i go around this?

Hmm...I find that I don't need to run the command with sudo.  How did you set up the script to auto run?  Have you enabled Coolbits?  How did you make the script executable (did you use chmod 777 to give full permissions)?  I don't know if any of these things could be related, but if you could poke around a bit more and let me know what you find I'll try and see if I can figure out what the problem is.

---

### Post by ph1 on 2008-02-23
> **da0ud said:**
> Ok thanks I'm gonna check what it can be but it isn't the refresh rate cause it's specified everywhere at 60Hz (nvidia-settings and compiz-fusion...).

See u soon and don't forget to post when you'll have an answer from nvidia support or a new driver that works.
Hopefully it will work in 2 months with ubuntu 8.04...

Da0ud,

I was thinking and I realized that if your problem is that your video cards are clocked too low for fullscreen video playback, you can just run a quick command to clock up your card, watch your video, then clock it back down with another command.  Just run the assign command that you used before.  

Of course, if your problem is related to something different, this would be a useless suggestion....

---

### Post by mikael_b on 2008-02-24
> **ph1 said:**
> Hmm...I find that I don't need to run the command with sudo.  How did you set up the script to auto run?  Have you enabled Coolbits?  How did you make the script executable (did you use chmod 777 to give full permissions)?  I don't know if any of these things could be related, but if you could poke around a bit more and let me know what you find I'll try and see if I can figure out what the problem is.

Changed permissions and it works!

Thanks

---

### Post by vervelover on 2008-03-01
Latest drivers (169.12)  completely solve this issue for me!

---

### Post by ph1 on 2008-03-01
I am eagerly testing the 169.12 driver, hoping that it has worked for me, too!

*sooo excited...*

EDIT:  Appears to not have worked?  Still testing, but I noticed a black flash.  Will keep testing.

Double EDIT:  If it hasn't worked, it's still reduced the problem very significantly (even to the point of seemingly having solved it?), and my GPU is cooler than it was even clocked down under the PerfSrcLevel thing.  So I would recommend the new driver completely to anyone with this issue.

---

### Post by vervelover on 2008-03-03
EDIT: I experienced the flashes again (after hours of use), however I can confirm everything that ph1 sayed: everything is better with this driver, the issue is nearly solved, but still there..

---

### Post by Zorael on 2008-03-12
Things make sense if it's the driver putting it into a slower mode to save power. Again, I have a 7600 Go card on my laptop, and I not only get the black flashes but also a very noticable performance decrease in Compiz if I have it show any 3D animations after not having displayed any for a while.

So, it's as if it powers down, and then it's slow to power up when the animations need the performance. My script (posted at an early page) fixes both issues completely. But likely, as someone already mentioned, it keeps it in performance mode and uses more power. I run compiz for the eyecandy, and my eyes bleed at both the flickering and the sluggish animations, so I find it a fair trade-off. I don't run compiz when I'm on battery power anyway.

Nvidia should follow suit with ATI and release hardware specifications, so that community/corporate open source drivers can be written. After all, it is in their interest to have their cards performing well, isn't it? Or maybe they want us to complain and buy new models, heh.

End linux-bullying!

---

### Post by da0ud on 2008-03-15
> **ph1 said:**
> Da0ud,

I was thinking and I realized that if your problem is that your video cards are clocked too low for fullscreen video playback, you can just run a quick command to clock up your card, watch your video, then clock it back down with another command.  Just run the assign command that you used before.  

Of course, if your problem is related to something different, this would be a useless suggestion....

Yes I guess this is the solution. I think I got the pb because I locked the card too low...

Thanks.

daoud

---

### Post by andyhowington on 2008-07-23
> **BoardDWorld said:**
> Actually the black screen flicker is "very" easy to resolve. Just go to  the **System ---- Preferences ---- Advance Desktop Effects** menu. Select **General Options** then **Display Settings** untick **Detect Refresh Rate** and manually set the refresh rate to 60Hz. Restart your system, done!

Thank you BoardDWorld! This has been working for me so far!! I had teh exact same problem these people described:popcorn:

All that remained was that I had to tweak my GNOME deskbars to return to normal, which involved removing and reputting some things like User switcher and desktop switcher/trash in the right spot.

---

