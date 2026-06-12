---
title: "Desktop Effects/NVIDIA Driver Issues/Low Graphics Mode/Why the F*ck Won't This Work"
date: 2008-04-14
forum: Desktop Effects &amp; Customization
---

### Post by Not So Smart Guy on 2008-04-14
[B]HP Pavilion s3400t
Intel Pentium Dual CPU 2.2Ghz
Integrated NVIDIA GeForce 7100/i630
17" LCD HP w1707 Display
Ubuntu 7.10 Gutsy[/B]

First, it should be noted that I don't post often. I'm what you would call a "lurker." I tend to only peruse through these forums when I'm trouble shooting a problem, and I'm actually quite proud to say that opposed to immediately posting like a some typo happy noob, I seldom have a problem that the search feature and some patience can't fix. You guys are all so damn smart you've probably already answered 99.999 percent of any questions I could ever have. 

Consider my current cerebrum wrecking dilemma the exception to this rule. 

As the title would suggest, I'm trying to simply (oh the ******* irony) enable desktop effects in Ubuntu (7.10 Gusty). For my efforts I have been firmly ****** up the *** repeatedly by my graphics card (thanks NVIDIA), X server (thanks Ubuntu), my computer in general (thanks HP), and I'm pretty sure a homeless guy just took a piss on me a second ago. 

**THE RELEVANT PART STARTS HERE**

Upon attempting to enable desktop effects I was prompted to install and enable the restricted driver for my NVIDIA card (nvidia-glx, if I'm not mistaken), to which I happily complied. After a restart Ubuntu starts in "low graphics mode" and I'm asked to configure or continue, regardless of what I choose I remain in low graphics mode until I can log in (looking at 800x600, mind you) and go System>Administration>Screen and Graphics> to change my settings to a working state. 

Now at this point the first option (the one that should work), is out of the question. So I proceed to try my usual google search/Ubuntu forums search to find some answers. I'm not going to recap everything I tried, but suffice to say I attempted just about everything described in the following threads:

[http://ubuntuforums.org/showthread.php?t=738786](http://ubuntuforums.org/showthread.php?t=738786)
[http://ubuntuforums.org/showthread.php?t=679366](http://ubuntuforums.org/showthread.php?t=679366)
[http://ubuntuforums.org/showthread.php?t=694072](http://ubuntuforums.org/showthread.php?t=694072)
[http://ubuntuforums.org/showthread.php?t=586651](http://ubuntuforums.org/showthread.php?t=586651)
[http://ubuntuforums.org/showthread.php?t=585784](http://ubuntuforums.org/showthread.php?t=585784) 

I tried all that plus some stuff from a few other threads. 

None of it worked. In fact, none of it even came close to working. 

The only progress I've made came from following the instructions in **[this blog post]("http://amazingrando.wordpress.com/2007/04/10/compiling-and-using-newest-nvidia-drivers-in-ubuntu-its-easier-than-you-think/")**. That got me the semi-failed result of having "NVIDIA X Server Settings" available in Applications>Systems Tools. Nevertheless, upon trying to access it I receive the message, *"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."* 

And yes, I've tried doing just that. Nada. I do believe I may have some other underlying problems, however, as restarting X server didn't quite seem to work properly. I was tossed out to a screen I occasionally see appear briefly upon start-up... loading something rather... the same thing happens upon attempting to stop the X server all together (sudo /etc/init.d/gdm stop).

**RAMBLING NOW CONTINUES**

I quite honestly I have no ******* clue what to do. I'm nearly resigned to the fact that I may be so remarkably stupid that I can't get a simple desktop effect option turned on. I'm not even asking how to get this to work, more asking if it can work at all. Judging by a lot of the threads I've read, it doesn't seem very likely. 

I just want to know if this can be done with at least relative ease. If I have to twist my nuts into a salty pretzel any more than I've already done, then **** it, I'd rather do something else with my time like go outside and get some sun, and get drunk, and have  sex with girls. Quite honestly being a geek takes too much damn energy. And I'm barely like a semi-geek, I have no idea how you full time geeks do it, but you have my gratitude. 

Any answers would be much appreciated. Thanks.

P.S: I'm currently posting this from Vista... yeah, I'm that frustrated right now with Ubuntu.

---

### Post by Inxsible on 2008-04-14
I don't know if you have tried this :

1) System>>Administration>>Restricted Driver Manager. Enable your NVidia drivers there(I think you need to check mark a box as far as I remember)

2) Restart your machine.

3) System>>Preferences>>Appearances. On the Visual Effects tab, select Extra or Custom. 

That should do it. I have a 17 inch HP dv9000t and that's the only steps i performed when I got my effects running.

---

### Post by JSorrell on 2008-04-14
I just went through this same thing, but it was my fault the drivers broke.

What I did to get around the problem you described was to download the drivers and install script from nVidia, stop GDM, install the drivers via the scripts (it rebuilds kernels modules, etc) then start GDM again.

[EDIT] I see the blog post you linked to contained this process. It probably isn't helpful for you, then, but others may need the following.

The code for that is:
[after downloading the scripts to, say, ~/Desktop]
```
sudo /etc/init.d/gdm stop
```
```
sudo sh ~/Desktop/(the installer's name)
```
```
sudo /etc/init.d/gdm start
```

From there I just did a
```
sudo nvidia-settings
```
to fix the xserver configuration for my dual monitors.

Maybe that will be helpful?

---

### Post by Not So Smart Guy on 2008-04-15
JSorrell,

Yeah, I pretty much went through that process. I really felt like it would work, and despite the fact that the NVIDIA X server settings are an option in the menu, I'm still not apparently using the proper NVIDIA drivers I thought I installed (as outlined in the process in your post and the blog link in my original post). 

Inxsible, 

That was the first thing I tried. If only it were that simple.

---

### Post by game_plan on 2008-04-15
I to rarely post about issues. I had a really hard time getting default NVIDIA drivers to work.

BUT NVIDIA has amazing Linux support, so you can download drivers from nvidia.com, start your system without x-server and install the drivers.

Hope that helps

---

### Post by mattalexx on 2008-05-16
This is a driver conflict. Disable the other one:

[LIST=1]
[*]Install the correct driver from [nvidia.com]("http://nvidia.com"). You have to exit Gnome first.
[*]In /etc/default/linux-restricted-modules-common, add "nv" to DISABLED_MODULES.
[*]Restart.
[/LIST]

I wasted the whole day trying in vain to fix this problem, that that worked. Here's where I found it:

[http://quail.southernvaleslug.org/webblog/archives/48](http://quail.southernvaleslug.org/webblog/archives/48)

---

### Post by wally83 on 2008-05-17
Not So Smart Guy:

I guess it's very unfair to blame Ubuntu about something that's purely nVidia's fault. nVidia drivers are not open source, so Debian/Ubuntu/whatever folks can't fix them and issues like this happens.

I had similar issue with Hardy alphas and nVidia 7300 gt. Fortunately 8.04 final solved this issue.

---

