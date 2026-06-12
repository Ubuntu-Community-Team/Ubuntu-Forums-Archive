---
title: "Gnome will not run on new Dapper install"
date: 2006-12-21
forum: Desktop Environments
---

### Post by Sparkius on 2006-12-21
I was finally able to get Ubuntu to install using the alternate Dapper iso. I can boot the system to the command line and have no problems. However, Gnome simply refuses to run. The log-in screen appears and I am able to enter my username and password, but as soon as the next screen loads, the keyboard stops working and there is a jumbled, pixelated, grey dialog box in the middle of the screen. I'm not certain it's a video problem, but I reinstalled the nVidia package and ran the other commands suggested in the Announcement post.

Here is my hardware:
Pentium D 820 on an intel motherboard
2GB RAM
SigmaTel onboard audio
Onboard NIC
nVidia 7800GT by BFG

This same problem prevented me from using any of the Live CD installs. I would like to check the xorg.conf file, but I'm not sure where it is located.

Any other suggestions would be appreciated. I would like to experience Ubuntu, but I have no interest in using a strictly command-line interface.

---

### Post by iamhugeinjapan on 2006-12-21
The xorg.conf is located in /etc/X11/

What kind of monitor do you have?

---

### Post by Sparkius on 2006-12-21
It's a Sony SDM-HS94P 19" LCD panel. I tried, during the Live CD install, to use its native resolution of 1280x1024, but it did not affect the problem.

Also, there is sound playing once the post-login screen loads.

---

### Post by iamhugeinjapan on 2006-12-21
It does sound like xorg is having trouble talking to your video card and/or monitor.  

Are you able to edit your xorg.conf in console mode?  Press Ctrl+Alt+F1 at the login screen.

```
sudo vim /etc/X11/xorg.conf
```

There are some instructions on using Vim editor on this page : [http://www.linuxhelp.net/guides/vim/](http://www.linuxhelp.net/guides/vim/)

 Look for this section which probably says 'nv' or 'nvidia' for your driver. You could try changing it to 'vesa' to try more generic drivers.

```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option		"Nologo" "true"
EndSection

```

Make sure correct refresh rate settings are set in the Monitor section below too.

Of course another option if you have a good Internet connection is to download the 6.10 Edgy Eft cd and try installing that.

---

### Post by Sparkius on 2006-12-21
I can edit the file in console mode, and I'll give it a shot. I'll check the refresh rates also. I tried Edgy, during the alternate install it locked up at 85% while installing applications.

During this most recent attempt, I went back to the command line from the login screen using CTRL-ALT-BACKSPACE. A second later, Gnome reappeared with the message: "A greeter appears to be crashing, attempting to use another" at which point the screen got a bit messed up and the keyboard stopped working.

Thanks for the help so far.

---

### Post by iamhugeinjapan on 2006-12-21
Ctrl+Alt+Backspace restarts the Xserver so it's not the cleanest way to get to a console. Though you did remind me that I left out an important Ctrl+ in my console mode instructions ;) (Ctrl+Alt+F1)

---

### Post by Sparkius on 2006-12-21
I'm posting this from Firefox in Gnome, so thank you for all of your help, IAmHugeInJapan!

It appears to be working fine using the vesa driver, so is there a reason to try to get the nVidia driver working? And if so, should I download the latest driver and try it rather than the supplied driver?

Thanks again!

---

### Post by iamhugeinjapan on 2006-12-21
Glad you got in ok!

What driver you continue with depends on what you want to do. The official nvidia driver is best if you want to do 3D stuff like Beryl/Compiz or fancy screensavers.  Try the latest drivers you can, at least you know now that you can fall back to vesa drivers if the experiments go wrong :)

---

### Post by hopiakuta on 2008-01-06
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/launchpad/+question/21397](https://answers.launchpad.net/launchpad/+question/21397) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				

"greeter appears to be crashing,..."

"...attempting to use another,..."

Virtually all of what appears above makes absolutely zilch sense to me; but, I did locate it via:

< [http://google.com/search?q=%22greeter+appears+to+be+crashing%22+%22attempting+to+use+another%22+%22%22+%22%22](http://google.com/search?q=%22greeter+appears+to+be+crashing%22+%22attempting+to+use+another%22+%22%22+%22%22) >.

Therefore, I am receiving a similar message, & I need several answers & explanations.

Please??


< [https://answers.launchpad.net/launchpad/+question/21397](https://answers.launchpad.net/launchpad/+question/21397) >.

---

