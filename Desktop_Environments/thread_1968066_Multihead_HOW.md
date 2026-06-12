---
title: "Multihead HOW?"
date: 2012-04-28
forum: Desktop Environments
---

### Post by JasonFWard on 2012-04-28
Oh my, every single time a new release of Ubuntu comes out I have the same problem.

I can't make it work on multiple monitors without hours and hours and hours of messing around.

So this time I install XUbuntu into a VirtualBox (configured as 3 heads) and installed.

What do I have?  3 identical screens and nothing I can find that will alter this.

So tell me, please please please someone tell me, how do I make multihead work in XUbuntu?

---

### Post by QIII on 2012-04-28
This is a limitation of Virtualbox, not Xubuntu, if you installed it in a virtual machine.  In a virtual machine you are limited by the hardware abstraction layer that provides the "graphics card".

I've never attempted to run multiple monitors in a virtual machine, but I'll try to find out if it can be done without identical screens.

If you have had trouble using multiple screens on a bare metal installation, there are those here who can help.

Edit:  It looks like you should at least be able to use dual monitors, spanned, with VBox.  Not sure about 3.  I'm sorting through the Virtualbox forum right now.

---

### Post by JasonFWard on 2012-04-28
From where I stand right now, the problem on bare metal vs VirtualBox seems identical.

And it seems I am doomed yet again to hours of fiddling with Xconf while everyone assures me its not needed.

Yet this I have tried this now on 3 different machines (different video cards, different motherboards etc) and on the VM, all results so far identical.

It cannot be this hard!  Surely, someone, somewhere has this working?  I cannot be the only one.

---

### Post by QIII on 2012-04-28
I use two monitors on metal with Kubuntu and Xubuntu without trouble with ATI.  Others have no problem with NVIDIA.

I just changed my virtual OpenSUSE to work perfectly on two monitors.

Did you set the VM settings to use multiple monitors?  In your virtual machine, did you use the system settings to span the monitors?

Do you have the Virtualbox extension pack installed?  Are you using the OSE version from the repos or the full version from virtualbox.org?

Edit:  BTW, I'm not sure if people with NVIDIA cards succeed in getting three monitors to run.  I do know that ATI now supports Eyefinity in Linux, which should make three (or more) monitors possible.

---

### Post by JasonFWard on 2012-04-28
> **QIII said:**
> I use two monitors on metal with Kubuntu and Xubuntu without trouble with ATI.  Others have no problem with NVIDIA.Bare metal I always go with Nvidia.

> **QIII said:**
> Did you set the VM settings to use multiple monitors?
Yes

> **QIII said:**
> In your virtual machine, did you use the system settings to span the monitors?No, since I can find no such option.  It knows I have three monitors, shows me them in the monitor configuration thing, but show me them is all it does.

> **QIII said:**
> Do you have the Virtualbox extension pack installed?Yes

> **QIII said:**
> Are you using the OSE version from the repos or the full version from virtualbox.org?There is only one version now, but I downloaded the latest release from the website.

---

### Post by QIII on 2012-04-28
(I use ATI bare metal.  The "ATI doesn't support Linux" stuff is a myth, a leftover from the days before AMD bought ATI.  Back then, ATI did suck.  Also, it is a myth that ATI doesn't support hardware acceleration.  It just doesn't use VDPAU, NVIDIA's proprietary acceleration.  You have to use VAAPI, the open standard, and the XvBA back end -- which takes the addition of four packages from the repos.  End of off topic parenthetic ramble.)

The OSE version is still actually available in the repos, by the way.

I will have to reboot to Xubuntu in a moment (while I had my OpenSUSE vm running I decided to zypper update, so I'm going to let that finish) and look at how the settings are done.  I can't recite it from memory.  More of a muscle memory thing.

If I have to, I'll install it in a VM and see if we can work this out together.

---

### Post by JasonFWard on 2012-04-28
Ok here is what I see

[[img]http://www.zimagez.com/miniature/screenshot-290412-013016.php[/img]](http://www.zimagez.com/zimage/screenshot-290412-013016.php)

That's my real 3 screens on an existing 11.10 XUbuntu install.  With 2 virtual screens on the far left and one on the middle monitor.

As you can see all three virtual monitors have the same content.

Yet if you look you can see that XFCE recognises that there are 3 screens, but that there is no way to configure them.

---

### Post by JasonFWard on 2012-04-28
OK, solved it for VirtualBox by entering this into a terminal

```
sudo apt-get install arandr
xrandr --output VBOX0 --auto --output VBOX1 --auto --left-of VBOX0 --output VBOX2 --auto --left-of VBOX1
```

But OMG, really?  I have to do all that JUST to get multihead to work?

However will this work on my bare metal?

---

### Post by JasonFWard on 2012-04-28
Scrap that

[LIST=1]
[*]Doesn't survive a reboot
[*]RandR seems to have totally screwed up my mouse location and its just about impossible to click on anything after a reboot
[/LIST]

Why is multi head so insanely hard?!

---

### Post by QIII on 2012-04-28
Remember, we are talking VBox here, right?

I was not able to get span to persist through reboot on OpenSUSE in VBox.  I still got two monitors, but had to go to settings to set the DE to span.

I have two (not three) monitors that work just fine, without any headaches, on bare metal in both Kubuntu and Xubuntu.

When I was experimenting with Ubuntu, I was able to do the same.

So, this seems to me to be something in Virtualbox.

---

### Post by QIII on 2012-04-29
I haven't had time to test this in a vm, but dual screens work on bare metal with Xubuntu and the ATI driver.

Again, since Eyefinity supports Linux, I'm sure that if I hooked up three monitors this would be about the same.

---

### Post by JasonFWard on 2012-04-29
> **QIII said:**
> dual screens work on bare metal with Xubuntu and the ATI driver.Ok, but how did you do this?  How did you tell Xubuntu to span multiple monitors?

---

### Post by Elfy on 2012-04-29
Try using arandr - set them up, save the script, add the script to startup.

---

### Post by JasonFWard on 2012-04-29
OK been looking at that quite extensively, however have yet to find out how to do it successfully.

Basically it needs to run for all users, after X has loaded but before they login, and ideally only run if all three monitors are present.

---

### Post by JasonFWard on 2012-04-29
Anyone?

---

### Post by JasonFWard on 2012-04-30
Hello?

---

### Post by Elfy on 2012-04-30
No idea hwo you would get it to run if there were all 3 monitors present. 

Maybe look at adding the script to /etc/rc.local

That would run "at the end of each multiuser runlevel"

---

