---
title: "Ubuntu Netbook Remix is for Atom?"
date: 2009-03-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Riot@ct on 2009-03-23
I haven't understand :)
Ubuntu Netbook Remix is for Netbook pc, right?
Ubuntu MID Edition is for Mobile Internet Device, right?

If I would install Jaunty in my Dell Mini 9 I must use Netbook Remix and not MID Edition, right?

But I not understand if Ubuntu Netbook Remix is for Atom processor or not.
Infact in [http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/) I find only i386 image and not lpia.
Why?

Thanks.

gp

---

### Post by snowpine on 2009-03-23
> **Riot@ct said:**
> I haven't understand :)
Ubuntu Netbook Remix is for Netbook pc, right?
Ubuntu MID Edition is for Mobile Internet Device, right?

If I would install Jaunty in my Dell Mini 9 I must use Netbook Remix and not MID Edition, right?

But I not understand if Ubuntu Netbook Remix is for Atom processor or not.
Infact in [http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/) I find only i386 image and not lpia.
Why?

Thanks.

gp

The intel Atom processor is fully capable of running the i386 kernel, and Jaunty Netbook Remix should run fine on your Mini 9 (I tried it briefly on mine and had no major problems). However, if running an lpia-specific kernel is really important to you, I suggest Dell's Mini 9 Ubuntu 8.04 Remix. It uses an lpia kernel, which gets you slightly faster bootup and battery life, at the expense of a smaller and older repository. I personally tried 8.10 and 9.04 before switching back to the Dell 8.04 (for now).

Starting with kernel 2.6.29 (probably Ubuntu 9.10), lpia support will be built in to the kernel, so a separate lpia kernel will no longer be necessary. 

ps I think the reason Ubuntu NBR uses i386 instead of lpia is that lots of older netbooks have a Celeron instead of Atom processor. They don't want owners of older eee pcs to feel left out!

---

### Post by Riot@ct on 2009-03-23
Ok, but why [here]("http://www.canonical.com/projects/ubuntu/unr") I read:
[INDENT]All of the initial Ubuntu Netbook remixes combine optimisations from the Moblin project for Intel® Atom™ processors and it is specially designed for netbooks. Intel and Canonical are working to create a new computing experience across a rapidly expanding category of portable devices.

.....

Rapid route to market - UI configured to work with Intel Atom processor-based netbooks so you are ready to go
[/INDENT]

And I not understand because [here]("http://cdimage.ubuntu.com/ports/daily/current/") I can find a Jaunty (not UNR) lpia image.

gp

---

### Post by snowpine on 2009-03-23
The Dell Mini 9 is capable of running either the i386 or lpia kernel. Jaunty Netbook Remix is a good choice.

My theory why Ubuntu Netbook Remix uses the i386 kernel (instead of lpia) is for compatibility with non-Atom netbooks (for example, the popular eee 700, which has a Celeron processor). 

Ubuntu MID is designed for small touchscreens (like an iPhone type of device).

---

### Post by Riot@ct on 2009-03-23
> **snowpine said:**
> The Dell Mini 9 is capable of running either the i386 or lpia kernel. 

Yes, I know...but not is this the problem.
But if I want use an optimized version for Atom processor of UNR (Jaunty) I can't.
Instead if I want install an optimized version for Atom of Jaunty (or Intrepid) I can.
I think that it makes no sense...the UNR must be principally optimized for Atom processor.

> **snowpine said:**
> 
My theory why Ubuntu Netbook Remix uses the i386 kernel (instead of lpia) is for compatibility with non-Atom netbooks (for example, the popular eee 700, which has a Celeron processor). 

Yes, but why not make a lpia image?

gp

---

### Post by snowpine on 2009-03-23
This conversation is going in circles. :) 

According to your own quote, Ubuntu 9.04 NBR "combine[s] optimisations from the Moblin project for Intel® Atom&#8482; processors and it is specially designed for netbooks." Sounds good to me.

Or, if you want a special version of Ubuntu with an lpia kernel customized for your Dell Mini 9, it is available pre-installed on the Mini (or as a download from dell.com if you bought the Windows version). It is based on 8.04, which is the current Long Term Support release of Ubuntu.

---

### Post by Riot@ct on 2009-03-23
> **snowpine said:**
> This conversation is going in circles. :) 

:)

> **snowpine said:**
> 
According to your own quote, Ubuntu 9.04 NBR "combine[s] optimisations from the Moblin project for Intel® Atom™ processors and it is specially designed for netbooks." Sounds good to me.

Or, if you want a special version of Ubuntu with an lpia kernel customized for your Dell Mini 9, it is available pre-installed on the Mini (or as a download from dell.com if you bought the Windows version). It is based on 8.04, which is the current Long Term Support release of Ubuntu.

I have Dell Mini with Ubuntu. I want try Jaunty UNR with a lpia kernel and not with a i386 kernel. lpia is for Atom, right? Why I can't use a lpia architecture for Ubuntu Netbook Remix? Instead why I can use Jaunty (desktop version) with a lpia architecture? No sense for me.

Or UNR i386 kernel is also optimized for Atom architecture? And use UNR i386 kernel has the same vantage of to use a lpia kernel from jaunty desktop edition?

gp

Sorry if my English is not perfect but I'm Italian. :)

---

### Post by snowpine on 2009-03-23
Don't worry, your English is fine, and I am enjoying the conversation. :)
I am a Dell Mini 9 owner too, with similar concerns to yours. I want the fastest possible boot and longest battery life.

Here is a suggestion: I think we can install Jaunty lpia desktop, and then add the NBR launcher:

```
sudo apt-get install netbook-launcher
```

I think that will give you the netbook interface but with an lpia kernel. I am downloading Jaunty lpia right now to test my theory. :)

---

### Post by Riot@ct on 2009-03-23
> **snowpine said:**
> Don't worry, your English is fine, and I am enjoying the conversation. :)

Great. :)

> **snowpine said:**
> 
I am a Dell Mini 9 owner too, with similar concerns to yours. I want the fastest possible boot and longest battery life.

Here is a suggestion: I think we can install Jaunty lpia desktop, and then add the NBR launcher:

```
sudo apt-get install netbook-launcher
```

I think that will give you the netbook interface but with an lpia kernel. I am downloading Jaunty lpia right now to test my theory. :)

I thought the same thing :)
I think that the UNR is Ubuntu Desktop + some optimization for small display and some general optimization for netbook.
This optimizations (IMHO) we can get from ubuntu netbook remix repository and if we install Ubuntu-Desktop-lpia and after we install 
```

go-home-applet
human-netbook-theme
maximus
metacity
netbook-launcher
window-picker-applet

```
,  we can get Ubuntu Netbook Remix with a lpia architecture.

When I come back at home I will try this. :)

We can follow this istructions:
[https://wiki.ubuntu.com/UNR#Ubuntu%208.10%20(Intrepid)%20UNR%20Package%20Installation](https://wiki.ubuntu.com/UNR#Ubuntu%208.10%20(Intrepid)%20UNR%20Package%20Installation)

gp

---

### Post by psifertex on 2009-03-29
I'd love to hear back from folks that have tried this.  I've got a dell mini 9 and am pretty concerned about battery life, but there are also some annoying bugs in the 8.04 distro that comes with it that I'd like to upgrade to jaunty to resolve.

Please make sure to post your updates here if you're successful with the lpia-desktop install with post-install UNR upgrades!

---

### Post by snowpine on 2009-03-29
Hi there, I didn't forget about our project. :)

I tried to test 9.04 lpia, but there was no live CD, and the alternate install CD did not work on my system (couldn't find the CD). Curious if you had better luck.

I am currently dual booting Dell Ubuntu 8.04 and Crunchbang 9.04 i386. Battery time is approximately the same. Updates are lagging on Dellbuntu--for example Firefox is still 3.0.5 while current is 3.0.8. I haven't totally made up my mind yet, but I have a hard time recommending the Dellbuntu at this point. :)

---

### Post by psifertex on 2009-03-29
Thanks -- that's good feedback.  

I've considered going to a different (lighter weight) window manager, so crunchbang sounds like a pretty good box.  I've always been tempted to go try ratpoison, but get scared off everytime I actually look too close.  Maybe this is a good in between state.  I was a big fan of fluxbox on my gentoo build a while back.

I'm still mostly happy with my dell build for now, but I suspect I'll find more and more annoyances as I go on.  Will definitely be thinking about upgrading soon (and I'm regretting not getting the 8gb SSD so I could dual-boot) ;-)

---

### Post by Riot@ct on 2009-03-30
> **snowpine said:**
> Hi there, I didn't forget about our project. :)

I tried to test 9.04 lpia, but there was no live CD, and the alternate install CD did not work on my system (couldn't find the CD). 

I have the same problem...not find the CD...but the CD\DVD Recovery of Dellubuntu to restore the system, working? Find the CD?

gp

---

### Post by Riot@ct on 2009-04-01
ok people...I'm trying a different way...
I'm installing the MID (that is compiled for Atom)...install MID is hard because the GUI not is perfect for display netbook  and touchpad not work (I must use mouse, keyboard and...intuit :D  )...after I will try to remove ubuntu-mid and install ubuntu-netbook-remix.
I hope...stay tuned... 

gp

---

### Post by Riot@ct on 2009-04-02
> **Riot@ct said:**
> ok people...I'm trying a different way...
I'm installing the MID (that is compiled for Atom)...install MID is hard because the GUI not is perfect for display netbook  and touchpad not work (I must use mouse, keyboard and...intuit :D  )...after I will try to remove ubuntu-mid and install ubuntu-netbook-remix.
I hope...stay tuned... 

gp
this way works :D

gp

---

### Post by Auslegung on 2009-04-05
> **Riot@ct said:**
> ok people...I'm trying a different way...
I'm installing the MID (that is compiled for Atom)...install MID is hard because the GUI not is perfect for display netbook  and touchpad not work (I must use mouse, keyboard and...intuit :D  )...after I will try to remove ubuntu-mid and install ubuntu-netbook-remix.
I hope...stay tuned... 

gp

So this gives all the functioning of the UNR, but with the lpia of the MID?  I'm in the MID Live right now and it seems pretty fast, especially off a USB.  I'm gonna try installing it, then removing MID and installing UNR like you said.  I'll report on the progress.

UPDATE: I tried to install the MID but I had trouble.  During the installation, it said, "The Installer has detected that the following disks have mounted partitions: /dev/sdb.  Do you want the Installer to unmount the drives?  If you do not, your installation will continue and the disks will not be available as installation targets."  It gave two options: Go Back and Continue.  I didn't want to install to the USB anyway, so I chose continue.  The page refreshed bu nothing happened.  I clicked it again and still nothing.  I clicked Go Back and it said "Partman failed with exit code 141.  Further information may be found in /var/log/syslog.  Do you want to try running this step again before continuing?  If you do not, your installation may fail entirely or may be broken."  It gives three options, Quit, Continue Anyway, and Try Again.  Quit obviously quits, Continue Anyway pauses, then repeats the same message, as does Try Again.

I'll try again later and see what happens, but Riot, how did it work for you?  And, does doing it this way give you the benefits of lpia and the function of UNR?  Thanks

---

### Post by Riot@ct on 2009-04-05
> **Auslegung said:**
> So this gives all the functioning of the UNR, but with the lpia of the MID?  I'm in the MID Live right now and it seems pretty fast, especially off a USB.  I'm gonna try installing it, then removing MID and installing UNR like you said.  I'll report on the progress.

UPDATE: I tried to install the MID but I had trouble.  During the installation, it said, "The Installer has detected that the following disks have mounted partitions: /dev/sdb.  Do you want the Installer to unmount the drives?  If you do not, your installation will continue and the disks will not be available as installation targets."  It gave two options: Go Back and Continue.  I didn't want to install to the USB anyway, so I chose continue.  The page refreshed bu nothing happened.  I clicked it again and still nothing.  I clicked Go Back and it said "Partman failed with exit code 141.  Further information may be found in /var/log/syslog.  Do you want to try running this step again before continuing?  If you do not, your installation may fail entirely or may be broken."  It gives three options, Quit, Continue Anyway, and Try Again.  Quit obviously quits, Continue Anyway pauses, then repeats the same message, as does Try Again.

I'll try again later and see what happens, but Riot, how did it work for you?  And, does doing it this way give you the benefits of lpia and the function of UNR?  Thanks
Yes...to make a UNR with lpia must install MID (or alternate lpia if cd works), remove ubuntu-mid* and kourou...and install ubuntu-netbook-remix and ubuntu-minimal

Install MID is hard because the touchpad not work (can use the mouse) and the display is not feel for netbook display...when the installation process asks:
"The Installer has detected that the following disks have mounted partitions: /dev/sdb.  Do you want the Installer to unmount the drives?  If you do not, your installation will continue and the disks will not be available as installation targets."
instead I have showed two choice: YES or NO ...I choiced NO...

About benefits:
I'm noticing a boot very fast, start applications is fast, battery is more longer and the OS is more fluid...and some improves...yes, there are benefits.

gp

ps: when UNR is installed is also possible to remove some other residual applications...you can search via Synaptic "Mobile Internet Device".

---

### Post by kjamc1982 on 2009-04-06
Has anybody tried this with a stock dell mini 9.  I would really like to use this or maybe cruchbang with my mini 9.

---

### Post by snowpine on 2009-04-06
> **kjamc1982 said:**
> Has anybody tried this with a stock dell mini 9.  I would really like to use this or maybe cruchbang with my mini 9.

Crunchbang is really the easier option.

---

### Post by epohs on 2009-08-31
> **Riot@ct said:**
> Great. :)



I thought the same thing :)
I think that the UNR is Ubuntu Desktop + some optimization for small display and some general optimization for netbook.
This optimizations (IMHO) we can get from ubuntu netbook remix repository and if we install Ubuntu-Desktop-lpia and after we install 
```

go-home-applet
human-netbook-theme
maximus
metacity
netbook-launcher
window-picker-applet

```
,  we can get Ubuntu Netbook Remix with a lpia architecture.

When I come back at home I will try this. :)

We can follow this istructions:
[https://wiki.ubuntu.com/UNR#Ubuntu%208.10%20(Intrepid)%20UNR%20Package%20Installation](https://wiki.ubuntu.com/UNR#Ubuntu%208.10%20(Intrepid)%20UNR%20Package%20Installation)

gp


I followed this method.  

When I reboot I go back to command line. How do I boot into the Netbook-remix desktop?

---

### Post by Riot@ct on 2009-08-31
> **epohs said:**
> I followed this method.  

When I reboot I go back to command line. How do I boot into the Netbook-remix desktop?
Have you installed ubuntu-netbook-remix package ?

giuseppe

---

### Post by epohs on 2009-08-31
Not specifically, no.

I installed the base system from a Jaunty lpia live USB ([found here]("http://cdimage.ubuntu.com/ports/releases/jaunty/release/")).

Then the following packages```

go-home-applet
human-netbook-theme
maximus
metacity
netbook-launcher
window-picker-applet

```

---

### Post by Riot@ct on 2009-08-31
> **epohs said:**
> Not specifically, no.

I installed the base system from a Jaunty lpia live USB ([found here]("http://cdimage.ubuntu.com/ports/releases/jaunty/release/")).

Then the following packages```

go-home-applet
human-netbook-theme
maximus
metacity
netbook-launcher
window-picker-applet

```

I think you must install ubuntu-netbook-remix package...

giuseppe

---

### Post by epohs on 2009-08-31
That was it, thank you!

Works perfectly.

FWIW, I used unetbootin to create a bootable USB from the jaunty alternate lpia iso.  Worked first shot.

Only somewhat tricky thing was that I chose the Yahoo! keyboard configuration during xorg config.

---

### Post by Riot@ct on 2009-09-01
> **epohs said:**
> That was it, thank you!

Works perfectly.

FWIW, I used unetbootin to create a bootable USB from the jaunty alternate lpia iso.  Worked first shot.

Only somewhat tricky thing was that I chose the Yahoo! keyboard configuration during xorg config.

Good ;)

giuseppe

---

