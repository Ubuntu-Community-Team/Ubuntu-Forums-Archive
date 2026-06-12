---
title: "Today's update broke X11"
date: 2006-06-15
forum: Desktop Environments
---

### Post by xenomorph99 on 2006-06-15
Hi,

Ubuntu is supposed to be the user friendly and stable...Can someone tell me why the updates today broke it?

I suppose I could fix it but why should I trawl around 58,000 unfathomable text files just to get it back to a working state?

Back to Windows, methinks. It's more stable and you're not afraid to download anything for fear of it going completely belly up.

Cheerio,
Xeno

---

### Post by bruce89 on 2006-06-15
```
sudo dpkg-reconfigure xserver-xorg
``` should fix it, don't be so rash.  Of course I can't stop you from giving up.

---

### Post by xenomorph99 on 2006-06-15
When I install new nvidia drivers for WIndows, which I believe todays update did, I don't recall having to resort to the command line then mess about with an n-entry questionnaire about my graphics setup asking me questions which, even as an engineer, I'm not sure about.

I could understand it if I had some "HankyTonky Corp." bizarre graphics card but a GF4 Ti4200 is neither new (i.e. unsupported) or non-mainstream.

It's stuff like this which makes me think that having to spend an arm and a leg upgrading to a spec for Vista isn't such a bad idea after all.

---

### Post by bruce89 on 2006-06-15
(rubbish)

---

### Post by hod139 on 2006-06-15
My guess is that you simply don't have the restricted modules.  Try installing linux-restricted-modules-686 and rebooting.

---

### Post by xenomorph99 on 2006-06-15
So, I complain about a problem that I also had in 5.04 and I'm a troll? Well done - what a fabulous community you have ;)

I tried the package reconfigure...it made no difference. I now have to copy a backup file over the xorg.conf then run startx in order to get me into the desktop with 800x600 with a refresh rate of about 3Hz.

I do have the restricted repositories enabled. Well, at least I did..judging by the nvidia problem, anything is possible after that last update.

The last time I spent so much time messing around with an OS, rather than enjoying myself/doing some work, was Windows 95. User friendly and stable, that was not.

---

### Post by hod139 on 2006-06-15
[quote=xenomorph99]
I do have the restricted repositories enabled. Well, at least I did..judging by the nvidia problem, anything is possible after that last update.[/quote]

Often times people install the restricted modules specific to their running kernel, and when a new kernel appears, the restricted modules do not come with it.  The linux-restricted-modules-686 package is actually a meta-package that will always point to the newest restricted-module package.  

I should have also added that if you are using the 386 kernel, you should install the linux-restricted-modules-386 package.

---

### Post by xenomorph99 on 2006-06-15
OK, thanks for that more constructive reply.

I suppose my point is that I would expect the update tool to know what it needs to download install EVEN if the items are from a restricted repository. After all, if you've enabled them, then you've most likely got restricted items already, so it would simply be better for the update tool NOT to meddle with the drivers because it can break something. I can understand if there are legal implications in not automatically supplying restricted items but my point is that should be handled automatically, especially for a so-called user friendly distro.

Call it a whine if you like but the only time (IMO) Linux distros work properly is out of the box. Be it this, Vector Linux, Suse or Slax. it seems to be the case that meddling with something is at your absolute peril. In that respect, it's probably better for someone "like me" to just download live distros as they come out and use them. At least you don't have to mess about reconfiguring things all the time...or spending time moaning about it.

---

### Post by FredB on 2006-06-15
There are a lot of updates today : new kernel (2.6.15-25 instead of 2.6.15-23), Gnome 2.14.2, and I had no problem upgrading my ubuntu which is using a GeForce FX5200 and its 3D accelerated driver.

I let apt-get dist-upgrade do its job and it works flawlessly.

As it is said in italian (I'm learning it) : è la vita = that's life ;)

---

### Post by xenomorph99 on 2006-06-15
OK then, as your installation is clearly flawless, would you care to explain the steps you took, from installing Ubuntu onwards, in getting your Nvidia card working properly and, as you suggest, through a security update?

My steps were as follows:

1. Installed Ubuntu 6.06
2. Installed nvidia drivers as per the Wiki
3. Found they weren't working.
4. Used EasyUbuntu (oxymoron?) to set up flash etc..and nvidia.
5. Found they still weren't working. Only it was worse now as I got a blue screen telling me that my x11 config was cobblers at startup. Replaced the conf file with a backup...then...
6. Moaned about the aggro I was having. Someone posted this guide: [http://www.ubuntuforums.org/showthre...ghlight=nvidia](http://www.ubuntuforums.org/showthre...ghlight=nvidia)
7. Followed guide, actually got an nvidia logo but a lousy set of display resolutions.
8. Hand modified the xorg.conf file to give me some more resolution settings.
9. Managed to get the display res to 1280x1024@85Hz (desired setting)
10. Used Ubuntu for a few days with only one complete system crash (while playing a DVD)
11. Installed the security update today only to have the same aggro as I had following step 4.

How does your version compare? Also, what display res/frequency are you running and were those settings available 'out of the box' after installing the driver or did you have to go through the same tedious rigmarole as I did?

---

### Post by xenomorph99 on 2006-06-15
Hmm, no further responses. Not that I expected any.

I'll give it another year before trying Ubuntu again. Maybe you'll have it working then.

---

### Post by ajifans on 2006-06-15
[QUOTE=xenomorph99]Hmm, no further responses. Not that I expected any.

I'll give it another year before trying Ubuntu again. Maybe you'll have it working then.[/QUOTE]

Had the same problem, and installing the linux restricted modules worked fine for me.  Thanks guys.

xenomorph99:  Maybe in another year you'll be mature enough to ask questions politely.  Why should people give up their free time to help people who are just childish and rude to them?

---

### Post by FredB on 2006-06-15
restricted modules are a dependancy for nvidia drivers (and for ATI too ?)

No problem at all. The only question is : how to remove safely previous kernel ;)

---

### Post by dan828 on 2006-06-15
[QUOTE=xenomorph99]Hmm, no further responses. Not that I expected any.

I'll give it another year before trying Ubuntu again. Maybe you'll have it working then.[/QUOTE]

I sympathize.  After having Dapper bork itself time and time again during the alpha/beta phase, I get pretty fed up and decided to wait for the "final" release.  But now the frequency of patches seems to be pretty much the same as when it was still beta.  It's been out two weeks and we are seeing major patching that is borking peoples' installs.  This is a stable enterprise ready release?

---

### Post by xenomorph99 on 2006-06-15
You mean like calling someone a troll? Oh yes, you're right.

Call me old fashioned but when something is described as user-friendly, you'd expect it to be as such. 

Believe me, I'd really like to have a Linux system that worked for long enough for me to learn about it in a constructive manner. Or maybe that's the idea? Make it unreliable so you keep the forums ticking along nicely and give the perception of a speedy turnaround in support (which, frankly, you wouldn't need if anything worked properly in the first place).

A colleague and I were discussing Linux today while we were trying out Suse 10.1 on an old desktop. Another colleague liked the look of Suse and was asking about why he should go with Linux over Windows and we couldn't think of a good reason unless, like I said, you booted from a live distro that is in a known, good condition when you download it.

Perhaps I sound a little negative? Oh well, c'est la vie.

I was looking forward to an explanation of how easy it is to set up a well known Nvidia card and to keep it working but I doubt I'm going to see one (irrespective of my attitude) because it's simply not possible.

---

### Post by ajifans on 2006-06-15
To be fair it is annoying, but I guess it is a price you pay for using a bleeding edge distribution.  I wouldn't install it Ubuntu for an enterprise installation however.

Look on the bright side of these things, they aren't that hard to fix and you learn a lot from doing so.  If something on Windows breaks the usual response is to overhaul all your drivers, failing that you reformat and install again.  Either way you learn nothing.

---

### Post by xenomorph99 on 2006-06-15
Well, if it isn't so hard to fix, why can't someone give me an idiot guide in setting up the Nvidia drivers for my desired settings?

I just run the X11 package reconfig thingy and was met with a barrage of, quite frankly, unfathomable questions about hardware. Does the average user PC punter really know the PCI address of his/her card? Or, more importantly, should they care?
Perhaps I could venture a suggestion that a drop down box/list would be a better way of dealing with that?

For your viewing pleasure, here is my xorg.conf:

> 
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon May 15 13:23:42 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280×1024" "1152×864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280×1024" "1152×864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280×1024" "1152×864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280×1024" "1152×864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280×1024" "1152×864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280×1024" "1152×864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

The interesting thing is that when the system boots, I get an Nv logo but, in the desktop settings, I cannot see the res settings I added (the first two) whereas, the other day and following the same procedure, I could. You see, that's part of the annoyance....you do something one day and it works and the next time you try it, something else happens. What happened to consistency?

---

### Post by angkor on 2006-06-15
[QUOTE=xenomorph99]I was looking forward to an explanation of how easy it is to set up a well known Nvidia card and to keep it working but I doubt I'm going to see one (irrespective of my attitude) because it's simply not possible.[/QUOTE]

Well, despite your attitude (remember people here are just users not developers) I'll bite.

```
sudo apt-get install linux-restricted-modules-`uname -r` nvidia-glx 
sudo nvidia-glx-config enable
sudo /etc/init.d/gdm restart
```

Gives me a perfectly working nvidia driver (1280x1024, 60hz on a tft monitor). Haven't had a single crash since I installed dapper in march. But then again, your mileage may vary as you might have noticed.

Btw, I agree a security update shoudn't bork your X.

---

### Post by xenomorph99 on 2006-06-15
Now, that's more like it. I now have some decent res settings. Thanks.

I had to re-chksum the xorg.conf file. Now, would that be the reason why the security update knackered things up? (Logic: "It" installed new drivers, tried to do a 'reconfigure' but found the MD5 was wrong so didn't bother = ballsed up X?)

Unfortunately, my attitude is a function of things not working properly ;)

Regardless, thanks again (genuinely)

Cheers,
Xeno

---

### Post by mrvw0169 on 2006-06-16
Actually, that sounds about right... I fortunately did not have this problem, but upon grabbing nvidia-glx, it did fail to update xorg.conf to use the driver due to the MD5 being incorrect (since I had modified it by hand)... Though, from the looks of it, nvidia-config enable just changes "nv" to "nvidia" in xorg.conf... so I went in and changed that myself... And assuming the nVidia driver worked for you  beforehand, there shouldn't be any changes needed...

Thus, it seems more like you were never able to grab the new updated nvidia-glx for the new kernel in the first place when you grabbed the new kernel...

In the future, it is not that effective to "threaten" the community to return to Windows to elicit an answer and hence the troll remarks on your attitude... And also "Hmm, no further responses. Not that I expected any." is not conducive to getting a response - we all try our best to help each other in our free time and an instant reply isn't possible if we happen to be at work or sleeping...

---

### Post by tseliot on 2006-06-16
Please, read the part of my guide where it says "WHAT HAPPENS IF YOU CHANGE YOUR KERNEL OR IF YOUR KERNEL IS UPDATED":

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

### Post by Thund3rstruck on 2006-06-16
I can remember trying to upgrade my ATI catalyst drivers to get a Windows XP Media Center Working a few months back, only to have that upgrade blue-screen/reboot loop every 5 minutes.

What about the XPSP2 windows update that broke nearly all of my company's socket applications in one fell swoop. 

Stop crying guys... if you don't investigate what the upgrade is and what it's going to do to you machine then you get what you get.

---

### Post by reztho on 2006-06-16
Is "automatic login" broken or there is a new obscure feature without a graphical way to configure it?

I explain myself. I have got automatic login enable for my account (i'm the admin). Before the update, automatic login works as it's expected. But now, after gdm close and before the welcome screen of gnome appears i'm getting a mini-window only asking me for the password of my account. I don't know now how to disable the thing.

---

### Post by xenomorph99 on 2006-06-16
> In the future, it is not that effective to "threaten" the community to return to Windows to elicit an answer and hence the troll remarks on your attitude... And also "Hmm, no further responses. Not that I expected any." is not conducive to getting a response - we all try our best to help each other in our free time and an instant reply isn't possible if we happen to be at work or sleeping...

My 'no response' retort was in response to the usual throwaway post of "well, I didn't have any problems so there can't be a problem" of the previous poster. These posters, when questioned about how they mangaged their feat, never reply...as indicated above.

> I can remember trying to upgrade my ATI catalyst drivers to get a Windows XP Media Center Working a few months back, only to have that upgrade blue-screen/reboot loop every 5 minutes.

What about the XPSP2 windows update that broke nearly all of my company's socket applications in one fell swoop.

Stop crying guys... if you don't investigate what the upgrade is and what it's going to do to you machine then you get what you get.

I never had a problem with XPSP2 so there can't be one (oh, the irony) ;)

Call it crying/whining/what you will; I shouldn't have to inspect a security update to see what it's going to do. All of the update, presumably, is necessary as it's a security update. Who am I to decide that 'oh well, I won't need that bit..but I will need that..' etc when it's a user friendly distro? Yes, I thought it was a bit odd when I saw it trying to download a new display driver but I put my faith into the people behind the distro (they're the experts, after all) and assumed that, because they'd decided it was a good idea to include it in the security update, then it must be a good idea.

And that's my point - if there are going to be automatic updates, they should be a little more intelligent. Whether that revolves around warning punters about what is going to be happening so they can ignore it, giving them an informed choice (e.g. having a list where you can tick/untick what you want), or making the update bombproof, I don't care. What I do care about is a security update that simply breaks a working system after it told me that everything had installed OK with no errors.

Ta
xeno

---

### Post by Sukarn on 2006-06-16
Not every update is a security update. Some are to add/remove/fix a feature as required, some to fix bugs in programs. Security updates to Ubuntu would be the ones you'd get from [http://security.ubuntu.com](http://security.ubuntu.com)

Windows gave me a lot of problems very often, the solution for which was normally given as "Just reformat/reinstall the damn thing and it should be fixed". Thats not what we want, is it? In Linux we can just go mess with some files to fix it. Everyone has access to the source code so bugs can be fixed easily and hence open source is the most stable and secure.
Windows 98 and even XP gave me a lot of problems with my sound card not being detected, my resolution being stuck at 640x480 (on my 17" monitor) untill I installed Nvidia drivers, a hell full of BSODs (Blue Screen of Death) that occured whenever any process accessed my sound card and graphics card *too fast*.
There are so many more problems I had that if I start listing them, they would probably take up more than 5 pages (A4 sized).

Stop whining about something having broken your X. People here have seen much bigger problems and have had others helping them find the solution when they asked the questions in a friendly manner instead of shouting at them that its not working and I am probably going back to stupid old windows that was made by microsoft by stealing most of the stuff from other companies (like Apple) and making it into one big package full of errors.

*phew, that was one long sentence. it came out of me in a kind of semi-rage*

---

### Post by bruce89 on 2006-06-16
[QUOTE=xenomorph99]So, I complain about a problem that I also had in 5.04 and I'm a troll? Well done - what a fabulous community you have ;)[/QUOTE]
Mabye I was a bit harsh, sorry.

---

### Post by I_Like_Pie on 2006-06-16
Xenomorph,
 
I agree with everthing that you have said so far 100%. There is really no excuse for this to happen on an enterprize ready distribution...in an automated update that you can not pick and choose from...made to increase security. You are absolutly, 100% right. 
 
I had the same problem last night. I kicked off the updates last night before bed and it broke my system. Would have waited until today to fix it, but I am actually showing Ubuntu off to some friends tonight and it would be bad if I couldn't fix it.
 
I couldn't remember how to reconfigure X, using the terminal, from memory so I actually had to log into Windows XP to find a fix. 
 
I did eventually figure out that the drivers for Nvidia had to be updated when the kernal does...How in the world would anyone other than a geek know this?
 
-----------------------------
The bottom line is this... I am still going to hang on to Ubuntu and here is why. 
 
In XP I have to figure out how to keep my illegal copy under the update radar. I have to install Antivirus and Antispyware and keep it updated as well. This usually takes 5-10% of my total time on Windows XP.
 
In Ubuntu I have to figure out how to Iron out all of the little quirks that keep Linux from being mainstream. How to do all of this stuff in the terminal, how to -not- break my system, and how to fix stuff that breaks when I do something wrong. This usually takes 15-20% of my total time on Ubuntu.
 
However...I am learning that most of my problems are typically the same...I somehow broke X. I _am_ learning how to work with Linux very rapidly. I suspect that in another month I will be spending the same amount of time manuvering through Linux as I would have spent updating and bullitproofing XP.
 
So please...please do not dump Ubuntu yet. Yes some of the people here are typical Linux geeks that get easily offended when you say, heaven forbid, anything bad about their distro. I still believe that *nix is 5 years behind XP but it is catching up QUICK. The people here in the forums are are all here for one reason, and that is to help us with problems try and enjoy learning Ubuntu. 
 
Thank you Xenomorph for letting everyone know your frustration with Ubuntu...This is very valuable in setting the tone of the new user. Really! 
 
Thank you everyone else for not being brash and still helping out despite your egos getting a little bruised.
 
Have a great day,
I_Like_Pie

---

### Post by jgcamp99 on 2006-06-16
Xeno, you're the other end of the spectrum of where I am with Windows, I'm tired of KB's that don't install (my Dell P4 at work) with a less than 50 % success rate and this is using auto update. Why would I have to make 6 runs @ installing 29 updates and the first cut 14 of them go on, each subsequent attempt to re-install an update that fails produces similar failure rates, that's why it takes 6 attempts.

Ubuntu, really the only problem I've had with their updates is the auto login for gnome now prompting for a password entry to boot into Ubuntu. Not bad for a kernel update and gnome update. It appears to be an issue with gdm.

At any rate, MS puts out 8, June 2006 security updates, then a day later, everyone of those flaws have instances of code found on the internet that exploit those flaws according to security experts (story @ Tech Republic).

Yes, I want Windows running on my system. I've been using Ubuntu 6.06 since it was available for donwload/released, I don't miss Windows XP one bit @ home. My internet experience is faster across the board. For downloads for example the best my DSL Lite connection ever downloaded was 25 Kb/sec. In Ubuntu, even the slowest are very close to 30 Kb/sec and often are into the low 40's Kb/sec. Why do I want to be on Windows XP at all ? Hey, and don't use MS Office and MS Access as an excuse, I log in using Citrix when traffic on the company server's is wide open and virtually unused and get the benefit of running MS Server 2003 on a quad cpu server thru my broadband connection.

---

### Post by xenomorph99 on 2006-06-16
Hi,

Thanks for the responses and no need to be sorry, Bruce89..I was annoyed last night and I was being a little unreasonable in some respects.

I'd like to say that I'd really like to get on with Linux/Ubuntu. I tried 5.04 out but had no end of trouble with it and switched to Slax which has always been pretty reliable albeit a little transient. I'm no major problems with Windows XP - I don't particularly have a problem with Microsoft because I almost anyone who has grown a business from nothing would do whatever to make it the biggest/best. Besides, Bill does a lot of work for 'charridty' (as Mike Smash would say) ;) I think XP is stable, reliable and indispensible especially for some tasks like playing games or dealing with some of the more obscure hardware devices and also that it was a big setback for Linux because MS finally had an OS that didn't crash every 10 microseconds.

But, XP is also a security nightmare not because it's much more bug-riddled than your average Linux distro but because it's *targetted* more. Having said that, I've had XP on my machine for a few good years and had no major problems in that department (and, no, that isn't an open invitation) or any department for that matter - I think I can count the number of complete system crashes on one hand in that time...not including my thumb. Besides, if Linux had no problems, there would be no need for updates every 5 mins(!) 

I agree with you, i_like_pie in as much as there seem to be no major flaws but niggling little 'pain in the arse' problems that keep cropping up time and time and time again. That's why they're so irritating. And, like you say, if you don't own 58 pairs of sandals and a Morrocan fez or whatever, you are unlikely to know the fixes for them. Yes, I could spend the time trawling for HowTos (thanks for the excellent nvidia one, tseliot) and forums but, to be perfectly frank, I went for Ubuntu because I precisely wanted to avoid having to mess about with the system. In fact, I was trialling it for a granny PC but I can honestly say that I would feel more comfortable putting an image of Windows 2000 (patched) with Firefox, Open office, a decent firewall and AV on a granny machine (and replacing the image periodically) than Ubuntu at present. Sorry to say that but I'm not sure that a user-friendly distro should rely on the command line so much and I know that if I was called up about it not working, I'd know how to fix it in a jiffy.

OK, so you've established that I'm too idle to bother to learn. Not quite true - I spend maybe 12 hours a day with a PC but I'd prefer to decide how much time I'm going to spend with it rather than the other way around. *I* will stick with Ubuntu for a little while longer (although a security update bubble just appeared and I might be annoyed again if I go for it) but I can honestly say that the little things really need to be ironed out before it can mount a challenge for the average Windows user.

And, people might say that Linux isn't Windows blah blah but look at all the popular distros. They have a login screen. They have a desktop. They have a browser. They have office. They have an email client. They have some photo software. They have plug and pray with USB. They play MP3s. They play DVDs. They burn CDs etc. If that's not trying to nab the average Windows punter, I don't know what is.

Ta,
Xeno

---

### Post by dcstar on 2006-06-16
[QUOTE=reztho]Is "automatic login" broken or there is a new obscure feature without a graphical way to configure it?

I explain myself. I have got automatic login enable for my account (i'm the admin). Before the update, automatic login works as it's expected. But now, after gdm close and before the welcome screen of gnome appears i'm getting a mini-window only asking me for the password of my account. I don't know now how to disable the thing.[/QUOTE]
Me too, perhaps it is better to start a new thread on this problem rather than have is mixed in with the current cat fight?

---

### Post by Krislarsen on 2006-06-17
The update broke my X11 too.. Pretty annoying, because I was at work when I did the reboot... OK; getting paid for fixing the X11 config isn't too bad, but my boss for sure wouldn't like it too much.

How come there isn't any feature that automatically suggests to rewind the configuration when this kind of things happen? Set-up of X11 is the number 2 problem with Ubuntu as I see it.

The absolutely most annoying thing is that I accidently can press the "kill X" key combination while using backspace for doing what it's ment for. I usually loose more than a caps'ed letter....

But mostly I'm happy ;)

---

### Post by Joey French on 2006-06-26
So, it broke mine as well, and would have broken my machine in the lab today if it was updated properly, which would have been a nightmare. And no, my boss would not have liked it one bit if she had to pay me for the time it took to fix it. This is not what user friendly means. Don't get me wrong, I love linux, and haven't had anything but kubuntu on my home box since hoary, but I know for sure that every one of the people that I have shown off linux to, and I have helped install on their boxes will be calling me tonight trying to get this fixed. 

Why is there not a better way to do these automatic updates? The average user will not take the time to figure out what every one of these updates are, because one of the things that they are relying on, what they've heard about, what made them move to linux in the first place, is how reliable and safe it is? 

Heck, if I can't figure out what is going on when X will not start, and I know what I am doing, then surely knucklehead on the street will have no clue.  

Joey French

---

### Post by bogler on 2006-06-29
yep -me too - i performed the upgrade and X11 is fscked, anyone know how to fix?

Hold on - its working now.

Make sure you have the latest driver from nvidia, make sure nvidia-glx is installed, also all the usual stuff with xorg.conf and this should help.

Man, i have battled with nvidia installs for 5 years now...

---

