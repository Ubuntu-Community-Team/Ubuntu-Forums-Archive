---
title: "Latitude D630 suspend (or rathe, resume) problems"
date: 2008-03-18
forum: Dell  Ubuntu Support
---

### Post by robin_reala on 2008-03-18
Hey all, I've trawled through all the related threads I can find but no luck. Apologies if this has already been addressed and I've just missed it.

I've got a shiny new D630 on my lap, but despite doing my research I've ended up with the nvidia card instead of an Intel one (long story short, I really wanted a WXGA+ screen so when one came up on the outlet I took it). This is a Quadro 135M.

The install went perfectly and lured by my lust for flashy graphics I ticked the restricted drivers box which got me nice fast glxgears and shiny compiz effects. It does however appear to have broken resuming from suspend (or at least according to the few other threads on this subject) this seems to be the case. My exact problem is that when resuming from standby one of the following happens:

1) Everything works perfectly (10% of the time)

2) I get a white screen with a mouse pointer that works. Swapping to the console (Ctrl+Alt+f1) and back to X fixes things (40%)

3) Same as 2 but it doesn't fix it - I end up having to kill X with Ctrl+Alt+Backspace (40%)

4) Hard lock - have to power off the computer (10%).

So, what do people suggest? I can try dropping down to the nv drivers (or noveau?) and give up on Compiz I suppose, but I'd rather not if I can get around it. Is this a known problem that has a fix? Might a new nVidia driver fix this and if so what sort of schedule do they run on? End of the day, suspend/resume is more important to me than compiz - I've come over from the Mac world and a computer without suspend/resume seems intolerable :)

TIA!

---

### Post by robin_reala on 2008-03-25
Bump (hope that's acceptable here!)

One thing I didn't mention is that I'm running the AMD64 flavour. Also, for some reason it tends to resume more consistently if it's running on battery, not mains power.

Any help much appreciated! I'm now on Hardy Beta if that makes any difference.

---

### Post by robin_reala on 2008-04-10
Apparently the 2.6.25 kernel has a bunch of suspend/resume Intel fixes that should help out with this problem. Hopefully it'll appear as a Hardy upgrade.

---

### Post by notwen on 2008-04-10
Are you suspending to ram by chance and if so how much ram/swap space do you have?  =]

---

### Post by robin_reala on 2008-04-11
I've got the choice of Hibernate and Suspend - I'm suspending so I guess that's to ram right? I've got 2gig in there at the moment, but if it gets suspend working I'll happily buy a 2gig stick and whack it up to 3.

---

### Post by LightEngineer007 on 2008-04-11
I have the same unit you have though I am running 32 bit for now. Don't know if these will help a 64 bit but I have suspend to Ram working perfectly, though can't use Compiz for now. Will try 64 bit again when full release is out as I couldn't even get install to run right on beta on mine. 

Here is what I did for 32 bit:

1) There is a bug in the NVidia driver that is causing the white screen on resume. For now need to disable Compiz until Nvidia can fix it. (I found this in the forums last week while tweaking mine, search the forums and should find it). I Love Compiz on my desktop, but don't really miss it on the laptop (well maybe some).

2) Standard edits in /etc/defaults/acpi-support need to be done. 
SAVE_VBE_STATE = FALSE
POST_VIDEO = FALSE

FYI, It seems that ACPI is in a transition for the last 2 releases as I also have a D610 that used to suspend perfectly "out of the box" since Breezy and all following until Gutsy... Starting with Gutsy there have been many people complaining about suspend on Dells.l

---

### Post by supercheetah on 2008-04-11
Do you have the KVM modules loaded?  I was having the same problems until just recently when I realized that they manifested when I turned on KVM.  Just have ACPI support unload those modules before it suspends the computer.

I posted about this [here](http://ubuntuforums.org/showthread.php?t=750565).

---

### Post by robin_reala on 2008-04-13
Light: thanks! I'll try disabling Compiz and see if that helps.

Supercheetah: yep, got KVM loaded (even though I can't get virtualisation going, but that's for another day). I'll try getting rid of it for the time being, see if that helps.

---

### Post by TheFuzz4 on 2008-04-13
I upgraded to Hardy and that fixed all of my suspend/resume issues that I was having.  Also if your still looking to stick another two gigs in there I just got 4 gigs from new egg for $66 bucks.  I have 4GB of ram in this sucker now which is awesome only problem is and I knew this when I got it is that Kubuntu only sees it as 3GB oh well it still rocks.  But anyways if your feeling up to it try out Hardy and see if that fixes the problems that your having with your suspend. Oh and my compiz is still enabled as well.

---

### Post by mimizone on 2008-04-28
I have the same issue with my Dell d630 and the latest Hardy 8.04

I so far saw only the white screen problem.
I sometime can just switch to a console and restart gdm.
But I also observed that if I dont' logged out from the console, it is frozen after the next standby.

What fix (even temporary) has been working?

---

### Post by mimizone on 2008-05-05
recent patches/updates from last week solved apparently part of the problem.
The lockup hasn't happened to me lately.

I also disabled Compiz in the meantime, but lockups occurred without compiz before.

---

### Post by irish8890 on 2008-05-12
Do any of Dell D630 users have lock-up issues with the touchpad/mouse/keyboard?

It seems to happen a lot with wireless and the touchpad and much less often with a wired connection and and external mouse (at least for me).

Thanks

John

---

