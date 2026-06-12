---
title: "Frustrations!!!! (why I might go back to windows)"
date: 2009-02-25
forum: General Help
---

### Post by gregg0000 on 2009-02-25
I like Ubuntu for the basics...just being able to surf the net without worrying about a virus....but

with windows I could usually fix things....and when I couldn't there were always geek sites available for help. They actually spoke in a language that I believe is called English.

Getting help with ubuntu seems to be a frustrating ordeal of software designers who can't or won't dummy their directions for those of use who don't know how or where to enter commands, use wine, or to extract a program that disappears somewhere in the linix jungle after you download it.

I have a headache trying figure out how I can use an old version of photoshop 6.0 (the disk loaded but the exe file would not open)....I read something about, all you need is wine...I assume they weren't referring to getting drunk, though that might help...today I downloaded gimpshop...it would be nice if it actually put an icon on my desktop...I have no idea where it is...who designs a program that hides itself in your hard drive after you download it?

I went to do my taxes only to find out that turbo tax doesn't work with linix....so I will be doing my taxes at an internet cafe or the library

now I have a friend that uses the linksys wireless G usb adapter WUSB54GSC on xp...works great...I just did some research and it seems that you need a database administrator to make it work...go figure

Aside from the enjoyment never catching a virus...and that is a big plus...I may go back to windows.

Is there anyone that can help with the above in simple, easy to understand steps?

thanks

---

### Post by HermanAB on 2009-02-25
Hmm, you have chosen a strangely popular, but somewhat hard to use version of Linux.  Ubuntu somewhat resembles a Volkswagen Beetle - a dreadful car, but everybody loved it. If you want something more mature that has wizards for everything, then you need to consider installing Suse or Mandriva Linux instead.

Note that you cannot easily run Windows programs on Linux, because, big surprise! Linux isn't Windows...

However, it is possible to run some Windows programs on Linux, by using a translation layer called Wine.  

The easiest way to install programs on Linux is to use the software package manager.  Installing stuff off some random web site is not a good idea, unless you already know what you are doing.

Cheers,

Herman

---

### Post by scouser73 on 2009-02-25
> **HermanAB said:**
> Hmm, you have chosen a strangely popular, but somewhat hard to use version of Linux.  Ubuntu somewhat resembles a Volkswagen Beetle - a dreadful car, but everybody loved it. If you want something more mature that has wizards for everything, then you need to consider installing Suse or Mandriva Linux instead.

Note that you cannot easily run Windows programs on Linux, because, big surprise! Linux isn't Windows...

However, it is possible to run some Windows programs on Linux, by using a translation layer called Wine.  

The easiest way to install programs on Linux is to use the software package manager.  Installing stuff off some random web site is not a good idea, unless you already know what you are doing.

Cheers,

Herman

I find it funny that you should be taking a swipe at Ubuntu on the Ubuntu forums, very strange indeed.

Regardless of that, this thread should be in testimonials.

---

### Post by mb_webguy on 2009-02-25
Okay, first of all a little advice...

You'll get better responses to your problem if you use a meaningful title.  A title like "HELP!!!" (or "Frustrations!!!") may easily get overlooked by someone who might otherwise be able to help.

You'll also get better responses if you put individual problems in separate posts.  This is especially true if you want to cut down on the confusion (which is one of your key points), since you won't have crosstalk from several different posts about several different problems.  And, as I mentioned above, a post about one particular problem with a meaningful title will tend to grab the attention of people who can help with that problem.

Also, you need to view tutorials and HowTo's on other sites with a critical eye.  If it's a few years old, there's a good chance the information will be outdated.  Also, unless it's specifically written for Ubuntu, it could be misleading, confusing, or outright wrong.  Ubuntu is a distribution of Linux, and in general Linux is Linux, but there are subtle differences between distributions that mean that a tutorial written for one might not apply to another.  For example, Ubuntu has a slightly different security model than most other distributions, and any tutorial that tells you to log in as root doesn't apply.

Based on this advice, you may want to consider making a couple of different posts addressing your problems individually.  I'm sure you'll get more answers with less confusion.  However, because I know that's not what you want to hear when you're frustrated, I'll see what I can do as far as addressing your problems...

As far as GimpShop, that's actually just a modification of GIMP, which comes preinstalled with Ubuntu.  You'll find it in Applications->Graphics.  GIMP can do anything that Photoshop can do, though you may go about it a bit differently.  All GimpShop does is make the GIMP interface look more like that of Photoshop.  Personally, while it takes a bit to get used to it, I like the GIMP's regular interface better than GimpShop.

The next thing you need to realize is that Linux is not Windows.  Wine will let you run quite a bit of Windows software on Linux, not all Windows software will run under Wine, and not all of the Windows software that *does* run under Wine runs perfectly.  You can check for the compatibility of a particular Windows application at the [Wine AppDB]("http://appdb.winehq.org/").  It's also generally easier to get applications running if you have the most recent version of Wine, so it's best to add the [WineHQ repository]("http://www.winehq.org/download/deb") to your software sources.

Generally, however, you don't *need* to run Windows software.  There is a *huge* amount of software available for Linux.  You can find pretty much anything you want in the Ubuntu repositories using Add/Remove Applications or Synaptic Package Manager.  While there may not be a Linux version of a particular application available, there is almost always an equally good (if not better) equivalent.

Unfortunately, tax software is one weak spot when it comes to Linux, which is partly due to poor support for the Linux operating system by commercial tax software developers, and partially because tax software isn't fun to write.  There are a few tax applications available for Linux, but nothing as well-supported and mature as TurboTax.  TurboTax does have a web-based service, but they don't have a Linux version, and the Windows version doesn't work with Wine.

As for your wireless adapter, *I've* done a bit of research, and it looks like you just need to use the Windows driver and ndiswrapper.  The basic process really isn't bad, and unless you need to do some troubleshooting, you can be up and running in about 5 minutes.  Here's a link to the [HowTo]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"), and here's the [troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=885847").

---

### Post by sim-value on 2009-02-25
> **gregg0000 said:**
> Getting help with ubuntu seems to be a frustrating ordeal of software designers who can't or won't dummy their directions for those of use who don't know how or where to enter commands, use wine, or to extract a program that disappears somewhere in the linix jungle after you download it.

You enter commands in the Terminal
Applications->Accesoires Terminal !

Then just copy and paste commands given to you by any tutorial ...

Files you download will be in your download directory ...

Programms you install always get arranged in the Apllications menu...

Greetings /me

---

### Post by dgoosens on 2009-02-25
hi,

just wanted to post my opinion on this...

first, if you have a bug or a special request in Windows, you most of the time can not do anything about it... 

next to that, well... I find the Ubuntu community very very very (x100) helpful.
If you have an issue, you most probably will find someone on this forum that already encountered it and managed to arrange it. (Don't think this exists for Windows).
If by any chance you do not find the answer you are looking for, you can post a subject in the forum... but DO TRY TO DO THIS CORRECTLY (there is a tutorial about this somewhere... I know, I read it). This means, using a correct title, a good description and treat one problem at the time.

Finally, I am sorry, but if you want to use a new OS, it is quite logical that you have to learn a little about it.
Internet is full of great tutorials and howto's about more or less everything that you might want to do with your Ubuntu... But you should SEARCH, READ and LEARN.

Obviously, if you are happy with a .reg file that arranges everything for you but you do not know at all what it does, stick with Windows...

Maybe we can bundle all this into one simple sentence from Goethe: 
> Only those who must conquer them every day
Deserve freedom as well as life. 

---

