---
title: "Ubuntu 8.10 screen resolution problem stuck to 800*600"
date: 2008-12-05
forum: General Help
---

### Post by alfredborg on 2008-12-05
Hi, I am a newbie, and just installed ubuntu 8.10 on a pc. It is working ok but screen resolution is stuck to 800*600 and cannot get it any higher. I would like to put it to 1280 at least, and I know my monito supports it. Any help would be appreciated. Thanks.

---

### Post by utnubuuser on 2008-12-05
Does your computer use a Nvidea card?  This issue has been coming up with some video cards

And have you tried opening a terminal and typing
> sudo dpkg-reconfigure xserver-xorg then ctrl+alt+backspace to restart x

Here's a launchpad thread > [https://answers.launchpad.net/ubuntu/+source/xorg/+question/11767](https://answers.launchpad.net/ubuntu/+source/xorg/+question/11767)
And another forum thread:> [http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787)

---

### Post by blackened on 2008-12-05
As stated in the launchpad thread posted by utnubuuser, these problems are usually caused by incorrect monitor auto-detection. The easiest fix is to consult your monitor's user manual (or, failing that, the web) for your monitor's hsync and vrefresh ranges, then add those ranges to xorg.conf's monitor section.

```
gksudo gedit /etc/X11/xorg.conf
```

```
Section "Monitor"
	Identifier	"Configured Monitor"
[B]	HorizSync          30-82
	VertRefresh        56-76[/B]
EndSection
```

You will likely only need to add the lines in bold (replacing my hsync and vrefresh ranges with those you find in your hardware documentation).

After that you need to restart the xserver with

```
sudo /etc/init.d/gdm restart
```

---

### Post by alfredborg on 2008-12-05
Thanks, fixed settings. The only thing that I have is that I have a 1cm black column on the left of the monitor and on the right I have missing text. I use a kvm switch to switch between one pc and another and the settings of the monitor are fine on the other pc. Is there a setting I can do to shift the image to the left? thanks

---

### Post by blackened on 2008-12-05
> **alfredborg said:**
> Thanks, fixed settings. The only thing that I have is that I have a 1cm black column on the left of the monitor and on the right I have missing text. I use a kvm switch to switch between one pc and another and the settings of the monitor are fine on the other pc. Is there a setting I can do to shift the image to the left? thanks

Odd. If it's an LCD, then can you use the auto-adjust button on the monitor to fix it? Otherwise, can you use the on-screen display to adjust the horizontal alignment manually?

---

### Post by awg1011 on 2008-12-07
I just wanted say that I have been having similar problems with screen resolution, only for me it was random, I might boot up Ubuntu and only have 800 x 600 then after a reboot it might have all the resolutions available, I prefer 1024 x 768, so if it booted at 800 x 600 I would just keep rebooting until I had 1024 x 768. 

I am also using a KVM and have often wondered if Ubuntu had trouble detecting the monitor's capabilities because of the KVM.

I came across this thread and followed Blackened's instructions for editing xorg.conf in post #3 of this thread and problem solved.

I just wanted to let Blackened know that his advice has also helped me. 

Thank you Blackened. ):P

-AWG

---

### Post by Westerberg on 2008-12-07
test

---

### Post by blackened on 2008-12-07
> **awg1011 said:**
> ...I am also using a KVM and have often wondered if Ubuntu had trouble detecting the monitor's capabilities because of the KVM...

Did you try doing a cold boot with the cable plugged straight into your monitor? That would be the only way to tell whether or not it was interfering with monitor auto-detection. Regardless, explicitly specifying the ranges in your xorg.conf will avoid the problem altogether.

> I just wanted to let Blackened know that his advice has also helped me. 

Thank you Blackened. ):P

-AWG

You're very welcome, glad it worked for you.

---

### Post by awg1011 on 2008-12-07
> **blackened said:**
> Did you try doing a cold boot with the cable plugged straight into your monitor? That would be the only way to tell whether or not it was interfering with monitor auto-detection. Regardless, explicitly specifying the ranges in your xorg.conf will avoid the problem altogether.


No I did not try plugging straight in to the monitor, the way everything is setup, it would be a big PITA. The main reason I suspected the KVM was interfering is I know it is interfering with the cordless mouse's ability to report battery level, neither XP or Ubuntu see it as a cordless mouse and XP did before the KVM.

---

### Post by kparry on 2009-03-20
I have the same problem, I am  also a newbie. xI use a KVM and have found that I could not get a better resolution than  800x600 while plugged in - I also could not get any of the auto-config scripts to work nor could I manually update my xorg.conf file successfully... so I plugged the Unbuntu PC direct to my monitor and ... no issues it lets me set 1600x1200 no problem - but - it reverts back to 800x600 upon connection to my KVM. No other PCs (WinXP) do not do this through the KVM  -- my question is -- how can I capture my current settings (no KVM) so that it will defautl to them when I connect my KVM? 
Please help

---

### Post by CTolley on 2009-03-21
utnubuuser,
That line fixed mine as well.  Thanks.

blackened,
I am waiting for a reply email from Polaroid for my specs since it's not on the web, nor in the manual.  After I get the specs I will use your directions and post results.  Thanks.

---

### Post by awg1011 on 2009-03-21
> **kparry said:**
> I have the same problem, I am  also a newbie. xI use a KVM and have found that I could not get a better resolution than  800x600 while plugged in - I also could not get any of the auto-config scripts to work nor could I manually update my xorg.conf file successfully... so I plugged the Unbuntu PC direct to my monitor and ... no issues it lets me set 1600x1200 no problem - but - it reverts back to 800x600 upon connection to my KVM. No other PCs (WinXP) do not do this through the KVM  -- my question is -- how can I capture my current settings (no KVM) so that it will defautl to them when I connect my KVM? 
Please help

Kperry, 

Why are you unable to edit xorg.conf? did you follow the instructions in Blackened's post #3 in this thread? It explains how to edit the xorg.conf file. It worked like a charm for me. 

Did you try auto-config without the KVM then reconnecting the KVM? Just a thought

---

### Post by CTolley on 2009-04-30
ctrl+alt+backspace doesn't seem to work in Jaunty.  Is there another resolution fix?  The code to get to that point works fine but ctrl+alt+backspace does nothing.

---

### Post by maxxmenon on 2009-04-30
Hi friends,

I am faced with an almost similar problem. I just upgraded my Ubuntu from 8.10 to 9.04 and I tried to fix the resolution (as I thought it was not fixed or something). 

Now, it looks like my browser (Firefox 3.0) shows up all the font size too big (looks like a 800 by 600 resolution to me than a higher one) and also at the start while opening the "System->Preference->Display" option it gave me a choice of a resolution higher than 832 by 624; now it does not. 

Could you tell me what I need to do to make my monitor display as normal as it was before? My monitor is a 17" AOC Intl make. 

Any help or suggestion is appreciated. 

Regards,

Madhu

---

### Post by CatKiller on 2009-04-30
> **CTolley said:**
> ctrl+alt+backspace doesn't seem to work in Jaunty.  Is there another resolution fix?  The code to get to that point works fine but ctrl+alt+backspace does nothing.

They took it out in Jaunty. Apparently people were pressing it by accident. You can either re-enable it by putting ```
Section "ServerFlags"
        Option          "DontZap"       "False"
EndSection

``` in your xorg.conf (you'll need to re-start X anyway to have it work, naturally), or just restart GDM with 

```
sudo /etc/init.d/gdm restart
``` on a virtual console (Ctrl-Alt-F1)

---

### Post by CTolley on 2009-04-30
> **CatKiller said:**
>  or just restart GDM with 

```
sudo /etc/init.d/gdm restart
```

Here's a cool oddity.  I did that, and my system got stuck after "Checking battery state      [OK]".  So I ctrl+alt+del for a reboot, it rebooted.  My mouse got small like a good resolution, then became the monster mouse that I fear.  So I was upset, but I checked display properties anyway, and I had options.  It was nice.  I was able to read your post again without scrolling.  Thank you very much CatKiller.  Is there some sort of advanced manual you smart folks refer to, or does your knowledge come from experience?

---

### Post by CatKiller on 2009-05-01
> **CTolley said:**
> Is there some sort of advanced manual you smart folks refer to, or does your knowledge come from experience?

Mostly that would be this forum :) We all learn from each other.

I don't know about anyone else, but if I've had a problem with a particular area then I get to know how that bit works. That's how I started out here; I could pass on what I'd learned when I'd fixed things myself. Then you just pick things up. These days, most of the things I've learned have been helping people on this forum; now that I'm more comfortable with the way things in Ubuntu work, I'm more comfortable poking around on my own system than the OP when they post a problem. Having found out something new in the process, I squirrel the knowledge away for future use. But then I **like** poking around to see how things work.

---

### Post by blackened on 2009-05-01
> **CTolley said:**
> Here's a cool oddity.  I did that, and my system got stuck after "Checking battery state      [OK]".  So I ctrl+alt+del for a reboot, it rebooted.

For a soft lock I prefer the sysrq+REISUB or sysrq+RSEIUB (they do the same thing in a different order) method described here -> [http://kember.net/articles/231/...]("http://kember.net/articles/231/reisub-the-gentle-linux-restart") and more in-depth here -> [http://en.wikipedia.org/wiki/Magic_SysRq_key#Purpose]("http://en.wikipedia.org/wiki/Magic_SysRq_key#Purpose").

These will usually work as long as the kernel hasn't completely seized and are a great exercise in hand dexterity.

---

### Post by CTolley on 2009-05-01
That is a pretty cool trick.  Thank you.  Not too sure if I'll remember when the time comes, but I will definitely remember it the second time...  :D

---

### Post by CatKiller on 2009-05-01
I believe the standard mnemonic is "Raising Elephants Is So Utterly Boring."

---

### Post by blackened on 2009-05-01
> **CatKiller said:**
> I believe the standard mnemonic is "Raising Elephants Is So Utterly Boring."

I was about to say that as well. Memorizing the mnemonic really helps it stick and be useful when the time comes.

---

### Post by CatKiller on 2009-05-01
> **blackened said:**
> I was about to say that as well. Memorizing the mnemonic really helps it stick and be useful when the time comes.

I've never even needed to use it, and the mnemonic has still managed to lodge itself in my brain. Might be useful some day, though.

---

### Post by blackened on 2009-05-01
> **CatKiller said:**
> I've never even needed to use it, and the mnemonic has still managed to lodge itself in my brain. Might be useful some day, though.

I've needed to use it alot less since learning it a year or so ago. Before that it would've come in very handy.

These days I know just enough of what *not* to do to lead to these problems.

---

### Post by CTolley on 2009-05-02
I've already used it a half dozen times on my laptop.  Just installed Jaunty on it, but every time I reboot I get a "Couldn't Authenticate" error.  So I do the Elephantitus thing an it reboots good.  I really need to stop playing with crappy computers...

---

