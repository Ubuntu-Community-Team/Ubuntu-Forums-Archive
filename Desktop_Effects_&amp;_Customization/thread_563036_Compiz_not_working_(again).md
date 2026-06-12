---
title: "Compiz not working (again)"
date: 2007-09-29
forum: Desktop Effects &amp; Customization
---

### Post by nikoPSK on 2007-09-29
K so I just put back on feisty (I should change that...;)) And I got compiz using this guide [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/")(didn't update with envy because they have a bug that stops your x-windows from working right now, great app though). So I got the fusion icon as well and emerald. I start compiz and: 

no bottom thingy and, 
I can't move windows and, 
no window borders! 

So I Know that window decorations is enabled. And it's set to use gtk (but I can't get compiz-gtk)

When I mark compiz-gtk for installation It asks me to remove compiz and compiz-gnome. I say yes then II get:

```
compiz-gtk:
  Depends: compiz-core (=1:0.3.6-1ubuntu13) but 1:0.5.5~git20070928+3v1ubuntu0 is to be installed

```

??? And I know somethings not running due to the fact I can't move my windows with alt-drag or alt+F7:confused:

---

### Post by reacocard on 2007-09-29
> **nikoPSK said:**
> K so I just put back on feisty (I should change that...;)) And I got compiz using this guide [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/")(didn't update with envy because they have a bug that stops your x-windows from working right now, great app though). So I got the fusion icon as well and emerald. I start compiz and: 

no bottom thingy and, 
I can't move windows and, 
no window borders! 

So I Know that window decorations is enabled. And it's set to use gtk (but I can't get compiz-gtk)

When I mark compiz-gtk for installation It asks me to remove compiz and compiz-gnome. I say yes then II get:

```
compiz-gtk:
  Depends: compiz-core (=1:0.3.6-1ubuntu13) but 1:0.5.5~git20070928+3v1ubuntu0 is to be installed

```

??? And I know somethings not running due to the fact I can't move my windows with alt-drag or alt+F7:confused:

In upstream compiz-gtk has been merged into compiz-gnome, so that's the one you want. Try running
```
compiz --replace
```
in a terminal, and if it crashes or anything post the output (or post it anyway), and then (in a new terminal), try
```
gtk-window-decorator --replace
```
and again, if it crashes or anything post the output (or post it anyway).

---

### Post by nikoPSK on 2007-09-29
I get this
```
niko@home:~$ compiz --replace
Fatal: Compiz can't be ran using VESA or VGA divers.
niko@home:~$ 

```

I can't update using envy right now because theres a bug that stops your x-windows system from working... Had to re-install ubuntu 3 times....:(

---

### Post by reacocard on 2007-09-29
> **nikoPSK said:**
> I get this
```
niko@home:~$ compiz --replace
Fatal: Compiz can't be ran using VESA or VGA divers.
niko@home:~$ 

```

I can't update using envy right now because theres a bug that stops your x-windows system from working... Had to re-install ubuntu 3 times....:(

yeah, you need the driver from envy to get compiz support.

---

### Post by overdrank on 2007-09-29
> **nikoPSK said:**
> I get this
```
niko@home:~$ compiz --replace
Fatal: Compiz can't be ran using VESA or VGA divers.
niko@home:~$ 

```

I can't update using envy right now because theres a bug that stops your x-windows system from working... Had to re-install ubuntu 3 times....:(

Hi you could try this
[http://packages.ubuntu.com/feisty/misc/nvidia-glx-legacy](http://packages.ubuntu.com/feisty/misc/nvidia-glx-legacy)

---

### Post by nikoPSK on 2007-09-30
I *might* try that but when do you think this bug is going to be fixed (in envy)?:confused::(

---

### Post by overdrank on 2007-09-30
> **nikoPSK said:**
> I *might* try that but when do you think this bug is going to be fixed (in envy)?:confused::(

I do not know, this is the first I have heard of a problem with Envy script. :KS

---

### Post by skip-br on 2007-09-30
Envy killed my ubuntu too...

After got a fresh install, I just enabled Restricted Drivers (System -> Administration -> Restricted Drivers Manager) and installed the nvidia driver. In fact, it installed the driver by itself.

Installed the compiz-fusion.

Then I  had to add a few lines in xorg.conf.
Under "Device" section
```
	Option		"AllowGLXWithComposite" "True"
	Option 		"TripleBuffer" 		"True"
	Option 		"AddARGBGLXVisuals" 	"True"
	Option		"RenderAccel"		"True"
```

and 
```
Section "Extensions"
        Option "Composite" 	"Enable"
EndSection
``` at the end of the xorg.conf

That did the tricky.

---

### Post by nikoPSK on 2007-09-30
> **overdrank said:**
> I do not know, this is the first I have heard of a problem with Envy script. :KS

Hmmm... Well I don't know. The restricted driver that "...sorry whatever your name is" was talking about did the same thing in gutsy but If that happened I'd reboot choose a different kernel then disable the driver. The same thing happened when i tried it in fiesty... no x-windows... But now envy has a bug... At least for me. And I'm not into that deep down complicated stuff so... I'll wait until the next driver version is out.:(

---

### Post by cowkiller on 2007-10-01
Hi, I've seen the guide you followed and it's not updated (the trevinho repos didn't work with my pc), try following [this one]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty"), since it worked perfectly fine with me. 
About Envy, it would be the first bug I've ever heard of too, but anyway a new version has been released not long ago so check out the[ Alberto Milone's web]("http://albertomilone.com/nvidia_scripts1.html"). Wich graphic card are you using?
Don't give up :D good luck!

---

### Post by nikoPSK on 2007-10-01
> **overdrank said:**
> I do not know, this is the first I have heard of a problem with Envy script. :KS

Well, I tried, but no luck.... :(

---

### Post by nikoPSK on 2007-10-01
> **cowkiller said:**
> Hi, I've seen the guide you followed and it's not updated (the trevinho repos didn't work with my pc), try following [this one]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty"), since it worked perfectly fine with me. 
About Envy, it would be the first bug I've ever heard of too, but anyway a new version has been released not long ago so check out the[ Alberto Milone's web]("http://albertomilone.com/nvidia_scripts1.html"). Wich graphic card are you using?
Don't give up :D good luck!

I have an nvidia geforce 5200 GTX. So I started with ubuntu 5 weeks ago... That guide worked fine. I decided I wanted to give gutsy a try... Some things didn't work. So I switched back. I did a clean install and the first things I wanted on it was compiz again. So the gide.. Then no X-windows!!! :( well I'll try yours. Thanks:)

---

### Post by tenjin1 on 2007-10-01
Hmm not sure why Envy is not working for you. If it is messing up you X-Windows current seesion..then the best thing you should do is run envy from a terminal without X-Windows running. Log out and press CTRL+ALT+F1 (to get out of the Desktop Environment, i.e. you'll see ONLY the command line) and just type *envy* (or envy -t) from command line. I would uninstall the drivers first then install the new ones. Once installed. reboot. I think you can also download your specific Graphic Card drivers from NVidia site and then exit out of X-Windows session and install from command line (which is basically what the envy script does for you automatically) So you have several choices. Like mentioned earlier you will need the current graphic card drivers to run Compiz to fix your original problem.

Good luck :)

---

### Post by nikoPSK on 2007-10-01
It doesn't mess up my x windows until I reboot. Then I'm stuck.. I will try your tip when I get back from my trip.:)

---

### Post by tenjin1 on 2007-10-01
> **nikoPSK said:**
> It doesn't mess up my x windows until I reboot. Then I'm stuck.. I will try your tip when I get back from my trip.:)

Ok. Just remember to remove your nvidia drivers and then install the new ones all while working in termial outside X-Windows. If all that is done and is not working you may need to reconfigure your xserver settings.

Anyways, let us know how it goes! :guitar:

---

### Post by nikoPSK on 2007-10-02
Okay I just got back from a trip and will try that tomorrow.:KS

---

