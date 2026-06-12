---
title: "No Graphics"
date: 2008-04-19
forum: Desktop Effects &amp; Customization
---

### Post by KrGAce on 2008-04-19
After installing to Hardy, all is well until I enable my restricted drivers.  Then I must reboot in order to use Desktop effects.  The problem is on reboot, the screen is unreadable as I have one black bar down the middle of my desktop and the other colors are faded.  My only option (because I dont know what to do) is to go back and reinstall.

I know there are still 5 days left until a final release, but is there something else I should be doing?  Right now without my restricted drivers all is working well..but no desktop effects.  

Any help?  Much appreciated.


AceMan

---

### Post by Zorael on 2008-04-19
I'm not sure I understand.

Could the resolution be too high for your monitor to handle? Or is this something that ensues when desktop effects start? In that case the login screen wouldn't be affected.

What kind of videocard do you use?

---

### Post by KrGAce on 2008-04-19
My laptop is a Dell Latitude D830 with an Nvidia Quadro NVS 130-140.  As long as I don't enable desktop effects (and where is the fun in that) as well as long as I don't enable the proprietary drivers, all is well.  The minute I try to enable desktop effects, it then says "you need to enable the nvidia pro drivers, so I do that, and it needs to restart.  When it does my logon screen I can't even make out what it is.

The logon screen has nothing to do with the effect, other than it reboots and I can't read my logon screen.

Between this problem, and my problem of getting Ubuntu to work with dual monitors, it really isn't a surprise why users "have" to stick with Windows.  I am not a Windows fan, however I have to use something, and at this pace, I hate to say it, but Windows is working!


AceMan

---

### Post by Zorael on 2008-04-19
If you can't read what's on your screen that sounds like something to do with your monitor. There's a chance your videocard is trying to detect available resolutions, and sets it too high. Or too high a refresh rate. Your videocard isn't exactly the most common out there either, so this might be a rare bug, too. I'm making educated guesses, now, seeing as I've no idea how it actually looks.

One thing you could try would be to give [Envy](http://albertomilone.com/nvidia_scripts1.html) a try. It'll fetch and install drivers from the Nvidia servers themselves, rather than prepackaged ones from the repositories.

There are benefits and drawbacks to doing this. The benefits would be that you'd have the very latest driver (...that the creator of the script deemed stable enough to include). The drawbacks would be that if and when you upgrade your kernel, you will need to reinstall the drivers. Else you'll just get bumped into safe graphics mode upon boot.

Envy can be run from a terminal, so if you use Grub and you have that Recovery Mode option, you can just pick it and then entering '**sudo envy -t**' once it's booted up. There's also a graphical interface that'll show up in your Applications menu.


My advice would be to try Envy. If it doesn't seem to help, use Envy again to remove the drivers and all will be well. If you didn't have it earlier, you will get the Nvidia Settings app for sure with Envy's installation, with which you can set up your dual monitors. Do make sure to make a backup of your **/etc/X11/xorg.conf** file first; better play it safe.

What I'd recommend further is that upon installing the driver with Envy, tell it to automatically configure your xorg.conf file (at the end). Then, before rebooting your computer, enter this in a run box (Alt+F2).
```
gksu gedit /etc/X11/xorg.conf
```
Scroll down to where it looks similar to this. It is usually near the bottom of the file.
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24

	[b]SubSection "Display"
		Depth	24
		Modes	"1280x1024" "1024x768" "800x600"
	EndSubSection[/b]
EndSection
```
Pay particular attention to the parts in bold. If this part is missing completely, that means your X server (the graphical server which runs Gnome, KDE, and similar desktop environments) will tell the nvidia driver to automatically determine the best resolution.

So what you want to do is to first see if that setion is there at all. If it is, make sure there aren't any resolutions listed that is outside of your monitor's supported range.
If it isn't there, you could try copying and pasting the example I posted here (only the parts in bold, SubsSection "Display" to EndSubSection) into the "Screen" section, as illustrated above.


If you end up in safe mode, just use Envy to remove the drivers again.
If you can't even get back into a graphical environment, pick Recovery Mode and (as mentioned earlier) enter '**sudo envy -t**'. Then remove.

Once removed, you can either restore your xorg.conf file to the backup you made, or enter '**sudo dpkg-reconfigure xserver-xorg**' in a terminal. This will launch a guide that'll set up a new xorg.conf file after asking you some questions about your computer setup. If you're to do this, remember; **nvidia** is the accelerated "restricted" driver, and **nv** is the boring, normal one.

---

### Post by KrGAce on 2008-04-19
I will give this a try and I thank you for your help, I do.  However do you see my point?  What user in his right mind is going to want to have to do this?  Again, I am not a Windows fan, I love Ubuntu, I do.  But to have to do this everytime a new distro comes out, is nonsense.  That's unfortunately why Windows is where it is.  Someday I hope..



AceMan

---

### Post by Zorael on 2008-04-19
Ideology and opinion ahead.

As for Windows just working and Linux requiring effort; it is uncontestable that Windows has had more time to mature. Moreover, it is equally uncontestable that the corporate support for Linux is vastly overshadowed by that for Windows, so it's little wonder that the official Linux drivers that do surface are often buggy, and always incomplete feature-wise when compared to their Windows cousins. What Linux needs is general acceptance, to escape the stereotype it's been given, to be considered as much an operating system alternative as Windows is. Microsoft *has* a monopoly; just try to find any brand computer (say, laptop) sold without Vista already installed - they exist, but they're few and far between. Which operating system you want to use ceased to be a choice at some point.

Microsoft is doing their utmost to bully Linux around, whatwith their "Get The Facts" site, not to mention [the whole Mandriva/Nigeria deal.](http://blog.mandriva.com/2007/10/31/an-open-letter-to-steve-ballmer/) And it might sound tinfoil-y, but I don't find it particularly difficult imagining Microsoft striking similar "deals" with manufacturers and game developing companies. "Make this game/program Windows/Xbox 360-only, and we'll give you some 'marketing bonuses'. Then you can slap a sticker saying 'Works Great With Windows Vista Premium' on the box." The first versions of DirectX sucked, being overshadowed by OpenGL (which is open and supported by several platforms), but then Microsoft suddenly convinced everyone to make DirectX stuff instead, and there you go.


One thing making it difficult is that Linux is always improving, which sometimes breaks stuff making people need to revise code, whereas Windows has stood still for years. On the other side of that coin, Linux is always improving whereas Windows has stood still for years.



Now, as your reward: if you get your restricted Nvidia drivers running you can set up your dual monitors with considerable ease.

edit: And your situtation is not the norm; most just have to tick the 'Enable Restricted Driver' box, reboot and then it works. At least there's some solace to be found there.

---

### Post by KrGAce on 2008-04-19
You make great points.  My heart feeling is I just wish it wasn't this way.  I love Linux, I do.  I love what it does/how it does it, and the ideaology behind the software.  I also love choice.  Again, my hope is someday.

As for my dual monitors that's on my workstation.  I have an ATI Radeon 8600 in that, and can install Ubuntu really well.  All is well if I like "cloned" mode, which I do not, I want spanned, or Big Desktop.  My frustration relating to the above is that I have tried just about everything on this forum, as well as searching Google for help all to no avail.  Part could be because of my mediocre Linux experience.  Add to it, the fact that all I have to do is install Windows and everything works (never thought I'd say that) and you understand where I am at.  

On my laptop, the first issue, it works well with 7.10, but when I upgrade to 8.04, then I have no screen.

AceMan

---

### Post by Zorael on 2008-04-19
If I'm right then it's the Hardy driver that's being unruly. This would explain why it worked in Gutsy. Upon typing this, I realize that's an alternative too; installing [the Gutsy driver](http://packages.ubuntu.com/search?keywords=nvidia-glx&searchon=names&suite=gutsy&section=all) onto your Hardy installation. Hmm.

I'd try Envy first, though, since it'll download fresh drivers with hopefully overall fewer bugs. Also, newer is better! Just because it works doesn't mean it can't be improved! :>

---

### Post by KrGAce on 2008-04-19
I am re-installing Hardy, and then will try Envy.  As for which driver it is, yeah pretty much Hardy tells me there are restricted drivers, I go to enable them, restart and.....no screen, or I should say I have a white screen with a black bar down the middle.

Starting the process now..Stay tuned  :)


Aceman

---

### Post by KrGAce on 2008-04-19
Just installed envy...ran it, it needed to reboot, now I have a white screen with a black line (vertical) down the middle.  Exactly what I got when I enabled the restricted drivers.  I didn't get a graphical menu either, I had to run it from terminal, I then picked install driver, now..nothing.


AceMan

---

### Post by Zorael on 2008-04-19
Blast.

Okay, my last idea then (without going into xorg.conf details) would be to use Envy to remove all installed drivers, reboot, and then install [that Gutsy driver](http://packages.ubuntu.com/search?keywords=nvidia-glx&searchon=names&suite=gutsy&section=all). If that driver still doesn't work, then there's either a bug in the Hardy version of X, or there've been some behind-the-scenes changes that require you to go fine-tune your xorg.conf. Progress and breakage. :(


Before you do anything, I would like to see the contents of your **/etc/X11/xorg.conf** file and your **/var/log/Xorg.0.log** file, when it's in its broken state. Then you're free to dpkg-reconfigure xserver-xorg.


edit: The xorg.conf file will tell us what your resolution settings are, and the Xorg.0.log file will tell us what the X server thinks of them. If there aren't any resolution modes defined, it'll try to autodetect, and the log file will say the results.

---

### Post by KrGAce on 2008-04-19
well...

I don't know what to do.  I restarted in recovery mode, had it detect my display and then resume boot. It allowed me to log in.  It then said that the drivers were in use, so I tried desktop effects..."Unable to enable desktop effects" So I look at restricted drivers and it wasn't enabled. I enable it, reboot and same damn thing...white screen with black bar down the middle.

Frustrating, this laptop is only a few months old, and it will kill me to have to put Winblows back on it.

I am lost, scratching my head.

---

### Post by KrGAce on 2008-04-19
Here is the contents of my file.  Right now without enabling the Nvidia driver, although it says "in use" and no desktop effects I have a system that can run, I am also up after booting into recovery mode.  here is my file.

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by Zorael on 2008-04-19
You're likely running the standard vesa driver now, then.

```
Section "Device"
Identifier "Configured Video Device"
Driver "**nv**"
EndSection
```
If you add that Driver line to the pertaining section in your xorg.conf, you will switch to Nvidia's non-accelerated driver. As to what advantages you'd enjoy over the vesa driver you're running now, I'm really not sure. To explain, what you're really doing when enabling the restricted driver is adding that driver line, but with the second field as "nvidia" instead of "nv".

At least you have a semi-working system so your laptop isn't reduced to a lap-warmer. When/if you're feeling adventurous, try downloading and installing that Gutsy driver. :>

---

### Post by KrGAce on 2008-04-19
Only thing is, as it is now the only way I can get it to come up (log in) is by going into recovery mode.  I have added that line you stated and rebooting.




Update-I have a working system, however no desktop effects.  Perhaps there will be updates before the launch in 5 days?

Thanks for your help.

AceMan

---

### Post by Zorael on 2008-04-19
At least that's something.

You should (either/both) file a bug over at [Launchpad](https://launchpad.net/ubuntu/hardy) and/or [generate a bug report and mail it to Nvidia themselves](http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=44&p_created=1097083033&p_sid=2CYSwH1j&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NzAsNzAmcF9wcm9kcz0wJnBfY2F0cz0wJnBfcHY9JnBfY3Y9JnBfc2VhcmNoX3R5cGU9YW5zd2Vycy5zZWFyY2hfbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1saW51eA**&p_li=&p_topview=1). Also, there's IRC, the Hardy development forum (before it closes), etc.

If no one realizes there's a bug, the chances of it fixing itself are slim. :>

---

### Post by Zorael on 2008-04-19
And, to leave room for further adventure, if you learn how to use the terminal **nano** editor, you can troubleshoot things without constant reboots.

For the sake of the argument, say that you've suddenly installed that Gutsy driver (since it worked earlier). If you switch to a tty console (say, Ctrl+Alt+F1), then open up /etc/X11/xorg.conf with nano, you can make changes to the file and restart X from another tty console. So, you make changes in the first console, switch to the second where you restart X (**sudo /etc/init.d/gdm stop** then **sudo gdm**), whereupon the graphical interface loads and you'll see what fruit your changes bore. If you're not happy with the results, Ctrl+Alt+F1 back to nano, make further changes, restart X with the second console, note changes, etc.

I've yet to see if your xorg is a horrid mess after Envy or Nvidia's X configurator have had a go at it (the one you posted was the failsafe one), so there's still a minute chance of it working if you just add Driver "nvidia". Minute.


edit: I guess my point is that even if you can't get into the X environment, if you have basic terminal knowledge you can reset/change settings and try again. And that complete system reboots are rarely needed, except when you've installed new drivers or changed kernel; Ctrl+Alt+Backspace will restart the X server, which is enough for most changes that can't automatically apply.

---

### Post by KrGAce on 2008-04-19
I dunno, like I said in relation to regular Windows users, it's getting over my head in a hurry.

---

### Post by Zorael on 2008-04-19
[Linux is not Windows.](http://linux.oneandoneis2.org/LNW.htm) :>

Drawbacks and benefits, of course. And that some prefer Linux and others prefer Windows means choice exists, which is awesome.

---

### Post by KrGAce on 2008-04-19
Although I agree with that article, it is also the reason Windows has a great majority of the market share.  Again, I am not a Windows fan, however like I said, Linux may be different, but it's Linux' complexities that keep Windows users...Windows users.

I understand that Linux isn't Windows, however to go through what I had to, in order to get some desktop candy to work, and then to find it out it won't work, or "may" work, is a frustrating task to say the least.  I am also researching a Fedora problem as well, now there is two major distros with errors, and I am just saying that if Linux (any distro here) that wants to grab Windows users, will have to fix things like the above mentioned, otherwise Linux will stay to those who love to problem solve.

I am sure the debate now is "do I pay $200 for a Windows distro that will work (okay that might be strong considering Vista) or do I download one that may or may not work for free.  This should answer the question as to why users pay for Windows.

Again, like you said "choice".  I am just lucky I have a workstation and a laptop, so I can research, while the other isn't working.


AceMan.

---

### Post by Zorael on 2008-04-19
Aye, I wish it were different. Until such time, I'll just lurk around and try to help with the most basic stuff while people who know what they're doing keep developing.

And, as I said early in the thread, it varies from machine to machine; for some it never ever works, not after following every howto and reading everything there is to know about whatever's not working - whereas for some their system is made up of components that just happen to work out-of-the-box.

---

### Post by KrGAce on 2008-04-19
yeah, as do I (wish it were different), but I do thank you for your help.  I suppose if everything did go smooth, there would be no need for Forums such as this, and that would be a crime.

Thanks again,

AceMan

---

