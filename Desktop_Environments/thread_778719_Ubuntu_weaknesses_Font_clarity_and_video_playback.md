---
title: "Ubuntu weaknesses? Font clarity and video playback"
date: 2008-05-02
forum: Desktop Environments
---

### Post by thebordella on 2008-05-02
I have recently installed Hardy Heron (8.04) on my laptop, a Thinkpad T60 (w/ATI x1400 video). I have played a bit with many earlier releases of Ubuntu, and some of my comments/questions below aren't specific to Hardy.

There is a lot I like about Ubuntu. I especially love Compiz Fusion. Desktop usability with this configuration is, IMHO, far ahead of either Windows or OS X. I always try out new Ubuntu releases and give them a test run to see if I can use it as my primary OS. But there are some issues that nag at me. 

My primary OS is currently Vista, and XP before that. Without getting into an OS war, suffice it to say that I don't hate Windows (including Vista!), but am well aware of its many shortcomings.

One thing that bugs me with a default Ubuntu install is the appearance of fonts. I don't know how to describe what I am seeing, but something about the fonts looks "thin". In OS X, for example, text is rendered with excellent weight and clarity. In Windows, the rendered text also has good weight and clarity, although not quite as elegant as on the Mac.

But in Ubuntu, fonts seem kind of "computer-y". If that makes sense. They lack a certain polish. I am wondering if there are packages or substitutions people install to bring the Ubuntu text rendering up to Windows/Mac standards? (I am sure that some people will say they prefer the thinner, "cleaner" look of Ubuntu fonts, which is fine, but I do not.)

My second issue with Ubuntu is video playback. I have a large collection of videos in many formats -- wmv, avi, mpg, divx, etc. Hardy did make it very easy to install the codec packages. I can play these videos in Totem (movie player), or Mplayer/SMPlayer.

But the video quality just isn't the same as when I play them back in Windows. As far as I know, I am using accelerated video drivers in Ubuntu (I have installed the proprietary ATI driver to enable Compiz+Fusion on my X1400, and this all works great.) Still, videos do not play back with the silky smoothness as they do under Windows. In addition, their appearance looks more "rendered" than under Windows. This is difficult to describe, but it is almost as if there is more visible pixelation or compositing on videos played back in Ubuntu.

I look forward to hearing your thoughts on these issues. Can these matters be improved with configuration/software, or are these characteristics intrinsic to this OS? I'm not trying to start a debate, am just seeking technical discussions.

thanks!

---

### Post by Steveway on 2008-05-02
Can you provide screenshots. Because I don't have those problems.
Fonts are sharp and very smooth and video looks great here.

---

### Post by XemeX on 2008-05-02
Well, my impression as far as fonts are concerned is completly different but I am using KDE so this may do the trick.

Moving on to videos I always say that on Linux they have far beter quality then on Windows XP or Vista.
I experienced this both using my Desktop PC with NV + compiz and laptop with Intel graphics.
The best choice for me is mplayer + SMPlayer + w32codecs from Medibuntu repository.

---

### Post by Zorael on 2008-05-02
Enabling anti-aliasing of fonts would likely enable you to reach that 'heaviness' you're describing. Setting hinting to medium or so makes them even heavier.

Firefox fonts are another issue. It uses its own font renderer which inevitably makes sites look slightly different than they do in Windows. As for whether this is a good or a bad thing I chalk up to personal preference.

Lastly, I can't relate at all to the media playback peeve you're describing, but then I'm using an Nvidia card. Quite the contrary; on high-resolution files where players in Windows have a hard time keeping sync, kaffeine does a wonderful job without as much as a hitch. Star Wars ep1 pod race in 1080p makes a great benchmark.

---

### Post by thebordella on 2008-05-02
Thanks for the font aliasing tips, I will play with that.

I can certainly believe that others have different (and better) video experiences. With so many combinations of hardware and drivers, situations inevitably differ. 

I don't mean to give the impression that video playback under my Ubuntu is "bad". But it different than I am seeing in Windows, and not, IMHO, better. 

To give an example, when I play back videos in Windows, I sometimes use "media player classic" and sometimes use VLC. When I use VLC, the videos look more like they do under Ubuntu. I understand that VLC uses its own internal codec and possibly rendering?

Presumably, Media Player Classic is using some kind of hardware rendered via the video drivers? I could be wrong here, I just observe that videos in MPC are a little cleaner looking than in VLC. Could this be related to the video card "overlay", whatever that is?

Ubuntu is display two issues: one is this issue of rendering quality. The other is stuttering; my videos are on a networked drive. Playback from the same laptop booted into Windows does not stutter -- the G connection is strong. I'm not sure if the stuttering under Ubuntu is a network streaming issue, something to do with how buffering is being handled by mplayer, or what...

---

### Post by hodenkat on 2008-05-02
It sounds to me like the font problem should be easy to tweak. The video problem might not be so easy. Is it fair to say that some hardware is better supported than others?

---

### Post by salvador_luna on 2008-05-02
how do i tweak the anti-aliasing?

---

### Post by marriedman on 2008-05-02
This is purely my opinion, but go to Synaptic and grab the **ttf-xfree86-nonfree** package. These are Red Hat (I think) fonts that are great. Then go to **System -> Preferences -> Appearance.** Third tab over is **Fonts**. Look for Luxi Sans. Then go to the bottom right hand corner above the Close button is the **Details...**

This is where it is my preference, tinker until you find what you like. I like ***Grayscale*** for the smoothing and ***Slight*** for the hinting. I don't mess with the Subpixel order.

Try that and report back with your results.:)

---

### Post by thebordella on 2008-05-03
Thanks for all the advice.

I have made big improvements in my font issues.

System, Preferences, Appearance, Fonts

Rendering, Subpixel smoothing, 96dpi, smoothing "subpixel (lcd)", hinting "slight", subpixel order "rgb"

I have played with a few fonts, including the Luxi Sans, but actually I prefer the default Sans the most. Setting the subpixel rendering to slight made all the difference for me. Now, my desktop fonts look awesome -- as professional as Windows and Mac (in my eyes).

As someone else said, Firefox has its own internal font system, and so it needed some tweaking to bring it up to this level of goodness.

In Firefox: Edit, Preferences, Content, Fonts & Colors, Default Font "DejaVu Serif", Size 17.

Love it. Web pages now render with a very professional, typeset look. 

(Still having issues with quality of full screen video playback -- posted again separately about this in the video forum)


> **marriedman said:**
> This is purely my opinion, but go to Synaptic and grab the **ttf-xfree86-nonfree** package. These are Red Hat (I think) fonts that are great. Then go to **System -> Preferences -> Appearance.** Third tab over is **Fonts**. Look for Luxi Sans. Then go to the bottom right hand corner above the Close button is the **Details...**

This is where it is my preference, tinker until you find what you like. I like ***Grayscale*** for the smoothing and ***Slight*** for the hinting. I don't mess with the Subpixel order.

Try that and report back with your results.:)

---

### Post by marriedman on 2008-05-03
hey thats great to hear that the font's worked out for you. With asome tweaking, the fonts in GNOME look almost as good as they do in KDE. Way better than windows IMHO.

The video playback, that is news to me. I have had much better video experience with Ubuntu than I did with Vista and about the same as XP. Kaffiene or VLC give the best video in my opinion.

---

### Post by Kokopelli on 2008-05-03
I sort of agree with your video playback experiences.  OS X does have more consistent and better playback than Linux in many cases.  I can't really comment that much about Windows one way or the other but I can see it doing well also.

The thing I have noticed on Linux is that the video card and driver can make a large difference, as can enabling/disabling compiz.  For instance With NVidia using the nvidia driver I get shearing on rapid horizontal movement that annoys the crap out of me.  This happens whether I have compiz on or not.  I find that with compiz on the shearing is less but the overall video quality for playback is less as well.  On the other hand on a different box using the nv driver there is never any shearing and quality is good (though not great).

The intel gpu laptops I have do not have much problem with shearing either though I still notice a drop in quality with playback when compiz is active.

My "multimedia machine" I have tweaked to maximize video quality, and it is good.  On the rest I accept the compromises and live with mediocrity.

---

### Post by Lantesh on 2008-05-04
Although it seems you have already found a solution to your font issues, since you did mention how you liked the fonts in Windows I thought I'd let you know you can have the actual Windows fonts by installing the package "msttcorefonts", without the quotes of course, in Synaptic Package Manager.

As far as your video problem...well that is not so easy.  Different PC's with different video cards tend to give varied results in Linux from what I can tell.  Getting all the right codecs installed tends to make a big difference, and trying out different players can yield different results as well.  One player might work better on one hardware setup, while a different player works better on another.  "ubuntu-restricted-extras" is a nice package that installs several codecs as well as the msttcorefonts all in one shot.

You might also want to add Medibuntu as a repository if you haven't already.  Google them and you will find the info on how to add them.  After you have them set up grab "w32codecs" and "libdvdcss2".

---

### Post by Zorael on 2008-05-04
Remember that you shouldn't set Compiz up to automatically detect refresh rates with Nvidia cards, since the drivers inaccurately report the wrong refresh rates, ending up in choppy performance. I've gotten rid of my tearing with the vsync options in nvidia-settings, and by disabling said option in ccsm while manually setting the refresh rate to my monitor settings, but I agree that many drivers need improvements.

Comparing Linux/Windows to Mac's OSX is not really fair, since Apple has absolute control over what hardware their customers run. Windows, while arguably of a worse design when it comes to drivers, is still in a position where manufacturers *need* to provide drivers for their products to survive out in the wild, merely because of the overpowering majority of Windows users on the PC platform. As such, effort and manpower are invested into developing such. Sadly, most still feel they can safely ignore the Linux platform because of the old stereotypes and Microsoft FUD, so most drivers are backwards-engineered and written by developers unaffiliated with the manufacturing company. Since they (largely) don't have access to the specifications, these drivers can end up buggy or inferior to their Windows counterparts. Intel has open sourced their stuff, at least the graphics and sound drivers, which is awesome. Lead by example!

Opinion, by I'd really like to see both Nvidia and ATI put more effort into developing Linux drivers. Open sourcing them (and accepting patches from outside developers) "should" make performance and stability skyrocket, due to Linus' Law.

[http://en.wikipedia.org/wiki/Linus'_law](http://en.wikipedia.org/wiki/Linus'_law)

---

### Post by nezam05 on 2008-07-20
I am a newbie to ubuntu. i faced video motion problem in ubuntu 6.10 while playing dvd. why?
any solution?

---

