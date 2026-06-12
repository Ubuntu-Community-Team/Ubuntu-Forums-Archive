---
title: "Why does Fedora feel so smooth and animated?"
date: 2008-11-05
forum: Fedora/RedHat and derivatives
---

### Post by Mr. Picklesworth on 2008-11-05
So after playing with the Fedora 10 preview off an external hard drive, I have gained an uncontrollable urge to *gasp* replace Ubuntu 8.10 with it. I feel kind of bad doing this since I have some unfinished business with Ubuntu, but the fact is Fedora has performed about twice as well on my computer (plus zero recurring kernel panics). I like that they aren't afraid to use the technically superior new GDM; the advantages really show.

Something that interests me is their collection of cool *little* adjustments. For example, when entering fullscreen mode in an application, there seems to be a little sliding animation as the title bar disappears and the window client area moves to fill the screen. It feels really smooth. With Ubuntu, the process has always been super quick but a bit flickery as the window client catches up with its resizing.
There's also a delightful fading effect when I change the wallpaper background which definitely didn't happen before.
Some other instances of unusual bounciness are things like the toolbars in some applications growing into place somehow. It's... strange.

So are these all patches applied downstream to Fedora a little bit ahead of other distros, or something with configuration?

This is also the point where you can try to talk me out of it. Don't worry, I'll still use Launchpad and run Ubuntu off my ext disk ;)

---

### Post by rudihawk on 2008-11-05
I was just looking at Fedora 5min ago, feel the urge to download it :D

---

### Post by Mr. Picklesworth on 2008-11-05
Oh, and Plymouth helps. I have *never* seen such an awesome boot-up! Now I really hate my Nvidia card :(
Next time it'll be Intel all the way unless NVidia does something magical.

---

### Post by Antman on 2008-11-05
Well, I do like Fedora more than Ubuntu, but I haven't been able to run F10 since Beta snapshot 2; it just won't boot on my laptop. Maybe the Preview version fixed the issue, but I will just wait until the final is released and try that.

---

### Post by T2manner on 2008-11-14
I love the new fedora, but i don't like the file browser.
It just seems so bare.

---

### Post by Sorivenul on 2008-11-15
F10 is the best thing to happen to Fedora since F8, which has been the highlight of the project, as far as I'm concerned.  I've been running it as part of a tri-boot setup since the last Beta, and it has been amazing.  I think I will probably replace one of the other systems on the box completely when it goes final.

---

### Post by igknighted on 2008-11-15
> **T2manner said:**
> I love the new fedora, but i don't like the file browser.
It just seems so bare.

You can change that to the ubuntu-default one in gconf-editor.  That's always the first thing I do on a fresh fedora install (that and install wget)

---

### Post by Kingsley on 2008-11-16
> **igknighted said:**
> You can change that to the ubuntu-default one in gconf-editor.  That's always the first thing I do on a fresh fedora install (that and install wget)
If he's referring to how the toolbar isn't showing in the file browser, he can just go to preference, click on the behavior tab, and make sure that "Always open in browser windows" is checked.

---

### Post by igknighted on 2008-11-16
> **Kingsley said:**
> If he's referring to how the toolbar isn't showing in the file browser, he can just go to preference, click on the behavior tab, and make sure that "Always open in browser windows" is checked.

Yeah, you can do it that way too... I usually change other stuff in gconf so I do it there.

---

### Post by jeyaganesh on 2008-11-27
Fedora 10 is very nice. Today I tried its live CD. Webcam just worked with Cheese without doing anything. Wallpaper is elegant. It is a decent distro. But I feel like at home when using ubuntu.:)

---

### Post by Sand Lee on 2008-11-28
~10 cds later I've finally got F10 up and running.
I must agree everything is smoother. The minimize/restore animation is smooth, alt-tab is smooth and improved enough that I don't have to replace it with ring-swithcher, and Nodoka just plain looks good.

but

YUM is UBER-SLOW ...sigh

---

### Post by shuttleworthwannabe on 2008-11-29
Yes, i have installed on one of my desktop PC; but where
1. is OpenOffice?? I have Abiword, bu tno OOo?
2. Also how does one get the Configuration Editor (gconf-editor) installed? 
3. How does one configure software updates, choice of mirrors, and settings for proxy in software updates?

I agree this Fedora 10 is something else; smooth and snappy! Well done to the developers,
S

---

### Post by YeOK on 2008-11-29
> **shuttleworthwannabe said:**
> Yes, i have installed on one of my desktop PC; but where
1. is OpenOffice?? I have Abiword, bu tno OOo?
2. Also how does one get the Configuration Editor (gconf-editor) installed? 
3. How does one configure software updates, choice of mirrors, and settings for proxy in software updates?

I agree this Fedora 10 is something else; smooth and snappy! Well done to the developers,
S

1. You used the Live CD, which is why you got AbiWord. You can install openoffice from the repo's. (Fedora DVD will install OpenOffice.)

2. ```
 # yum install gconf-editor 
```

3. Mirrors.

```
 # yum install yum-fastestmirror.noarch 
```

That will install a yum plugin which will use the fastest mirrors for you.

I'm not sure on the proxy, or really what you want to configure. So, I'll leave it at that.

---

### Post by mthei on 2008-11-29
OpenOffice is easy to install with YUM, with the added bonus of each app being install individually, so you can have openoffice.org-impress without having openoffice.org-draw installed automatically as is the case with Debian and I assume Ubuntu as well.

I got around to downloading and burning the liveCD today. I'm not surprised that I'm impressed, as I've used Fedora 8 and 9 for several months. It's what I recommend to a lot of people. It's also nice to see that the artwork has definitely improved since F9, and even copied the Solar wallpaper to a USB key. I probably won't install it, as I'm comfotable with what I have now, but it's good to know that if I ever need to change operating systems, Fedora is just as reliable as ever.

Also of note, this is the fastest that the liveCD has ever run for me. Having always used to liveCDs for installing, as the installation is often less than five minutes, but having the CD boot up often takes twice as long.

---

### Post by shuttleworthwannabe on 2008-11-29
Thanks yeok,

I also found this helpful: [http://www.my-guides.net/en/content/view/125/26/1/2/#yum_graphical](http://www.my-guides.net/en/content/view/125/26/1/2/#yum_graphical)

---

### Post by CrucifiedEgo on 2008-12-02
I think that the OP has a valid question.  I too feel that F10 seems to be more 'polished' then Ubuntu 8.10, but I can't quite put my finger on what about it is.  The color scheme and wallpaper are more towards my personal preferences, but it's more than that.  Any thoughts?

---

### Post by amersault on 2008-12-02
before the current versions of F10 and U8, i dabbled w/ both and the former lost out due to the unbearably complicated scenario of getting my WiFi card to work. 

Fedora lost immediately to Ubuntu in that Ubuntu just worked right out of the box.

yes, Fedora is prettier but i just found Ubuntu more functional - and easier for noob that i was to handle.

(sorry, Fedora)

now if F10 wireless works out of the box, i might give it a second go...

---

### Post by Therion on 2008-12-03
> **CrucifiedEgo said:**
> ... F10 seems to be more 'polished' then Ubuntu 8.10, but I can't quite put my finger on what about it is.
Could have been my post right there.  I installed F10 about a week ago and I'm liking it a lot.  It IS hard to say exactly what it is about Fedora that appeals to me. It just seems more polished, more professional in its overall execution.  It's not any one, single, "Killer" feature, it's a hundred little tweaks that leave you with the feeling that a lot of attention went into the distro.
  
I'm finding it a little more difficult than 8.04 to customize.  I did find the lack of things like cool screensavers to be a bit of a bummer.  Whereas 8.04 has dozens of screensavers to choose from right out of the box, F10 has maybe 10.  Having to modify my boot grub/conf file to get a graphical bootscreen was a big surprise.  The fix was admittedly simple but  seemed oddly out of synch with the overall sense of polish that F10 shows.  Putting aside my very, VERY minor nit-picking, though, I'm liking Fedora 10 a great deal.  

I don't want to take anything away from Ubuntu 8.04 but Fedora just feels like a more "grown up" distro.

---

### Post by Sorivenul on 2008-12-03
> **Therion said:**
> I don't want to take anything away from Ubuntu 8.04 but Fedora just feels like a more "grown up" distro.

I think you just answered the original question.

---

### Post by CrucifiedEgo on 2008-12-03
> **Sorivenul said:**
> I think you just answered the original question.

I actually used that exact same terminology when talking to some friends.. it's just more an OS for grownups IMHO.

...after getting burned by centos4 though, i'm still not comfortable enough with yum to switch my servers from ubuntu 8.04.

---

### Post by Mr. Picklesworth on 2008-12-03
Part of this may also be that Fedora's release cycle inherently makes it less bleeding edge. It is released once the kernel, GNOME and the like have been somewhat stabilized and it seems to me that they are a bit more flexible with it.

Something that struck me recently is that Fedora *released* with [this showstopper bug]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/286285") **fixed** (since the patch existed before their final release), while Ubuntu has yet to release the appropriate patch to the stable repositories. (It's been hovering precariously in proposed updates for weeks now).
My more crazed side likes that Fedora stays truer to upstream, with relatively unmangled GNOME. The shutdown and logout dialogs all look right all the time, without any unusual icons, and Nautilus defaults to spatial mode. I'm going out on a limb, but something which may be benefiting them is that they seem to put more trust in upstream, working closer to the GNOME project and as a result accepting the logic in what it offers by default.

Otherwise, there are all sorts of little things, and I too just can't quite put my finger on what it is that gives it the extra charm... I suppose the new GDM helps, and they have really good art work. I like that they keep it consistent across everything, now with crossfades galore. Especially consistent with ATI graphics.
I like that the artwork is [community selected]("https://admin.fedoraproject.org/voting"). For a distribution that some claim is more [corporate]("http://www.redhat.com/"), Fedora has an extremely good community thing going on.

It's not that Fedora is superior in all ways. Indeed, Ubuntu has some awesome stuff too. Ubuntu's name really drives home the free software ethos, and Jono does an amazing job again with [the community]("http://hall-of-fame.ubuntu.com/"). Launchpad is going to be one of free software's most powerful tools in the coming years. I consider it that already. It isn't just a bug tracker; it is really empowered by the unique model we use to develop software.

However, there are many notes to be taken. I hope they are taken and acted upon soon, because I for one am hopelessly split at the moment. (At least until Fedora can adopt Launchpad).

---

### Post by Sorivenul on 2008-12-03
> **CrucifiedEgo said:**
> ...after getting burned by centos4 though, i'm still not comfortable enough with yum to switch my servers from ubuntu 8.04.
Have you tried the latest CentOS?  It is quite good and, IMO, much improved from the 4.x series.  yum is always an adventure when you move away from long-time use of the dpkg system or some other package system.  The more I use it though, the more I almost prefer it.

---

