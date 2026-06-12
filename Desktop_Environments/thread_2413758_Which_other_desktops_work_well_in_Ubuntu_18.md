---
title: "Which other desktops work well in Ubuntu 18"
date: 2019-03-01
forum: Desktop Environments
---

### Post by dean.w.schulze on 2019-03-01
The GNOME 3 that Ubuntu 18 uses is very disappointing.  Terrible support for multiple monitors, even when the multi-monitor add on is installed (only one monitor can have a launch bar, the time/date display is different on different monitors).

I've tried the Unity desktop, and it left my system unusable.  Launching apps (especially the Settings) from the launch bar hangs the whole system.  Had to purge Unity.  Others have tried KDE and it ruined their systems too.  See the commnents at [https://linuxconfig.org/how-to-install-kde-plasma-desktop-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-kde-plasma-desktop-on-ubuntu-18-04-bionic-beaver-linux) .

What other desktops have others tried on Ubuntu 18, and did they work well?  I'm so fed up with Ubuntu 18 that I'm ready to go back to Ubuntu 16.

---

### Post by DuckHook on 2019-03-01
There is nothing wrong with continuing to run on 16.04. All of my servers are still on Xenial because I have not seen the need to upgrade them. It will continue to be supported for two more years, so there's plenty of time to try out other flavours or even distros before making changes.

That said, your experiences seem to be the exception to the thousands (millions?) of users who have successfully and happily updated to 18.04 (including yours truly—I run all of the 'buntus in various machines including bare metal and VMs). Your question about the reliability of other DEs assumes a premise that just isn't true except in your individual and anecdotal case.

In passing, I should note that layering on a different DE on top of an existing one is often fraught with problems. Some users manage to do so without problems, but I've seen enough go sideways on these forums that I advise against it. If you want to try KDE, download and install Kubuntu. Don't just download and layer Unity or KDE on top of Ubuntu (which now uses Gnome) because slight configuration differences can bork your system.

Given your experiences, I would recommend a series of LiveUSB trials before settling on the flavour that works for you. From your join date, it would appear that you are an Ubuntu old-timer and should be familiar with the various 'buntu flavours, so try them all out. You may enjoy the simpler desktop flavours without all the extraneous bells and whistles. They have the additional advantages of being lighter and running a bit faster too.

No one can advise you on "better" flavours because—using myself as an example—they all work very well for me. You'll just have to try them all out to find the one that you like best.

But again, do not make the mistake of downloading Ubuntu, then adding another DE. Start with a proper and pristine install of each native flavour so that you don't mix up config files. And LiveUSB first to eliminate the ones you don't like.

---

### Post by dean.w.schulze on 2019-03-02
Your cautions about using different desktops on Ubuntu confirm my experience.  It's not a good idea.  Unfortunately most Linux distros use GNOME, which is my main disappointment with Ubuntu 18.  Not supporting multiple monitors in 2019 is pathetic.

Thanks for mentioning live USB.  I was going to try different distros on virtual machines, but that isn't a valid trial.  I'll use live USBs

---

### Post by dean.w.schulze on 2019-03-02
After reading this review I'm having second thoughts about Kubuntu 18.04:

[https://www.dedoimedo.com/computers/kubuntu-beaver.html](https://www.dedoimedo.com/computers/kubuntu-beaver.html)

Is he too pessimistic?

---

### Post by dean.w.schulze on 2019-03-02
Here's another data point on how terrible GNOME 3 is.  I have a 3 monitor setup (laptop monitor and two external monitors all running 1080p).  The same setup worked well under Ubuntu 16.04 / Unity.  Now in Ubuntu 18 / GNOME 3 when I open Settings the displays get blown away.  All I did was open Settings.  I didn't change any display settings.  Here's what happened to my display resolutions:

  1: 3840 x 2160 (laptop)
  2:  1024 x 768  (external)
  3:   1920 x 1080  (external)

Rebooting was able to restore my displays.  Just like Windows 3 used to be.  Remember how bad Windows 3 was?  That's how bad GNOME 3 is.

---

### Post by QIII on 2019-03-02
Are you still asking for support or are you using this thread to vent?

---

### Post by dean.w.schulze on 2019-03-04
If there is a fix for these problems I'd like to know about them.

---

### Post by DuckHook on 2019-03-04
> **dean.w.schulze said:**
> …[https://www.dedoimedo.com/computers/kubuntu-beaver.html](https://www.dedoimedo.com/computers/kubuntu-beaver.html)

Is he too pessimistic?
I found this article silly and impossible to take seriously. The author comes across as a drama queen churning out clickbait by throwing tantrums as a whiny, bratty, macho poseur. If you are unbothered by such juvenile conduct, then take his erstwhile "advice" and write off Kubuntu. No one is forcing you to use it.

I prefer analysis that is level-headed, dispassionate and devoid of profanity, snark and axe-grinding. The word "objective" comes to mind. For better or worse, it's what we try to do around here.
> **dean.w.schulze said:**
> If there is a fix for these problems I'd like to know about them.
I am only repeating myself, but for what it's worth:
> **DuckHook said:**
> There is nothing wrong with continuing to run on 16.04…It will continue to be supported for two more years, so there's plenty of time to try out other flavours or even distros before making changes.
> You may enjoy the simpler desktop flavours without all the extraneous bells and whistles. They have the additional advantages of being lighter and running a bit faster too.
> Start with a proper and pristine install of each native flavour so that you don't mix up config files. And LiveUSB first to ***eliminate the ones you don't like.***
There's no substitute to you simply taking the time to try them out and see which work and which don't. No one here can read your mind, do your experimenting for you or duplicate your gear and setup. Unlike the gilded jails of the proprietary world, there is no charge for downloads and no cost to trying them all out—one after the other.

---

### Post by monkeybrain20122 on 2019-03-06
Did you upgrade or is it a fresh install? If upgrade probably a bad upgrade.

I find gnome shell awkward and sluggish but unity works great in 18.04. One of my two machines runs 18.04 with unity, work machine still on 16.04.

Did you add the unity [ppa]("https://launchpad.net/~unity7maintainers/+archive/ubuntu/unity7-desktop-proposed")? It fixes a few bugs. If you have questions and bugs to report visit [https://community.ubuntu.com/c/desktop/ubuntu-unity-dev](https://community.ubuntu.com/c/desktop/ubuntu-unity-dev)

---

### Post by olduse78802 on 2019-03-07
I am using kubuntu 18.04 lts on a dell precision T3500 with 750 Ti nvidia drivers and external storage.  No , I say again , no problems what ever.  Been using it for about 3 months now just recently it updated to 04 and i am satisfied with it.  I also use kubuntu on 2 dell optiplex 960s and again no problems at all.  the 960s are using built in graphics and audio.  Oh and i am using audigy Z sound card using kernel 4.19 and no problems with that on the T3500.

---

