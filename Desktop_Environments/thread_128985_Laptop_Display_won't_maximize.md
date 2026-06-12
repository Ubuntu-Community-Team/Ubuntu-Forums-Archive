---
title: "Laptop Display won't maximize"
date: 2006-02-12
forum: Desktop Environments
---

### Post by racsw on 2006-02-12
Hi,
  I just got through installing Umbutu on my Dell Inspiron 1100 with a 12" wide screen. (roughly)  Although I selected 1024 x 768 as the only selectable screen resolution on the install, it installed 640x480.  So I need to fix this somehow.

But the most immediate problem is that the entire desktop area is about 7" across and 6" high, and nothing I do can make it use the entire laptop screen area.  I can't install updates, because apparently, the Install button is below the screen area, but i can't be sure.   Everything seems to work correctly, including Internet usage, except for the screen size and resolution settings.

Sure could use some help.

Thanks,
Robert

---

### Post by %hMa@?b&lt;C on 2006-02-12
boot into terminal
run this
sudo dpkg-reconfigure -p high xserver-xorg
then reboot

---

### Post by racsw on 2006-02-12
Hi Jeff,
  Thank you for responding.  It appears we have another problem, although I believe I know what it is.

Before my wife gave me this laptop to install Umbutu, she had it configured for use with an external 15" LCD flat-screen monitor.  Now she tells me that I have to press the Fn (function) key + F8 to switch between the LCD screen and the External monitor output.  I'm guessing this is what it is.  I tried your suggestion, and it did not improve my situation.
   Problem is, this function was probably Windows-XP based, and as I do not have that installed anymore, I have no way of using that key combination.
Do you know how I can switch this back without reinstalling Windows, then reinstalling Umbutu?

Thanks,
Robert

---

### Post by chele on 2006-02-12
Can you make any changes from System > Preferences > Screen Resolution?

---

### Post by mcduck on 2006-02-13
The problem with small picture in the middle of the screen is caused by using smaller resoulution than what is native for your laptops display. There might be some key combination that allows you to force your display to scale the image to fit the screen. BTW, Switching between internal/external monitor should not have anything to do with this soo no need to worry about that..

Your best bet is to find out what is the native resolution of the display, and then configure Ubuntu to use that by editing /etc/X11/xorg.conf.

---

### Post by racsw on 2006-02-13
Hi guys,
  Yes, I did try the screen resolution thing, but the only resolution listed was 604x480, even though I checked 1280x...down to 640x..., a total of about 6 different ones.
Standard for this laptop is 1024x768 using a SPWG-A LCD interface.
To add to my dilemma, the wife is PO'd now because she swears I screwed up her laptop with the Linux install.
So, to try something, I reinstalled Windows XP, Service Pack 1, that came with the restoration CD, which involved reformatting the drive obviously, which the Install CD did automatically.
  When WinXP finished, I ended up with the same 640x480 minitiature screen that I had in Umbutu.
  So I went to the Display properties, and resized it to 1024x768, and it comes in at an 8 bit color setting, and nothing else is available.
  Because she swears that everything was ok prior to Umbutu, we are temporarily leaving it in WinXP, and she will call Dell to see what this is.  I still think it's a video card failure, and I hope the Umbutu installation didn't overdrive it to cause this failure.  We will let Dell weigh in on the problem before I make any other attempts to reinstall Umbutu.
  I'm installed a dozen or so different Linux systems over 6 years, and I do know that Xconfigurator can overclock the video card and cause damage.
But my last system install was SuSe 9.1 almost 2 years ago, so I'm not sure what's changed since I've been gone.
  Hopefully, Dell will give us an answer today as to the probable cause, and once it's fixed, I'll let you know.
  The one thing I'm not used to with Umbutu, is not stepping through the total configuration steps like SuSe, Mandrake and RedHat used to do.  You used to get to the video card configuration, and be able to try different settings, change the hor and vert refresh rates, etc, etc, and end up with something that works good.  While the Umbutu Install was totally without interruption, I was totally dependant on the decision-making process Umbutu used to make it's decisions.

Regards,
Robert

---

### Post by racsw on 2006-02-13
Well, I talked to a hardware guy, and in his opinion, the video card is ok, it's a driver problem.  In his best guess, the Dell laptop had some specific video drivers that were wiped out by the Umbutu installation when the entire drive was reformatted, and Umbutu didn't have the correct drivers to restore what it wiped out.
We're going to download some Dell video drivers to test his theory.

Robert

---

### Post by racsw on 2006-02-13
It seems it's definitely a driver issue.
There are several known issues with wiping out the original video drivers for this computer, and even another Debian issue that addresses this Inspiron problem others have had identical to this.
  So the wife was right...

This PC requires an Intel Graphics Technology 845GL Video Driver.  Intel has a Linux driver, albeit with a few small problems.
If anyone else has specific Umbutu fixes for this, I would be willing to try a reload.  I can't afford to keep screwing around with this for days, though.
If there's a fix, I'll try it, if not, Umbutu doesn't get installed.

Thanks,
Robert

---

### Post by racsw on 2006-02-13
This thread is somewhat humorous, as I am it's greatest contributor ;-)

Anyhow, it's confirmed.  I downloaded the correct video driver from the Intel website, installed it in WinXp, and the problem is resolved.  Full 32 bit color, multiple resolutions, it's all there now.  At least we know what the problem was.

OK boys, do you have an Umbutu resolution for this driver?   I'm willing to give it another shot.  At least I know I can recover from this now.

Regards,
Robert

---

