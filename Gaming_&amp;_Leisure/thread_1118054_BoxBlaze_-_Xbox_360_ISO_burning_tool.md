---
title: "BoxBlaze - Xbox 360 ISO burning tool"
date: 2009-04-06
forum: Gaming &amp; Leisure
---

### Post by Nevon on 2009-04-06
I've created a simple frontend for growisofs that helps the user burn an Xbox 360 ISO to a dual layer DVD. Wicked ([http://www1.roob.us:53535/blog/](http://www1.roob.us:53535/blog/)) created the original CLI version, and of course I asked for his permission before creating a GUI for it.

[img]http://img10.imageshack.us/img10/6037/boxblaze.png[/img]

The script doesn't really do a whole lot in its current state. It asks the user for a file to burn, checks if the filesize sounds resonable for an Xbox 360 ISO, and then burns it to a DVD. If for some reason the user decides to try to burn something completely different (a .png, .ogg, a directory, etc.) the script won't stop them - just warn them. However, I'm pretty sure growisofs will spit out some kind of error if you try. 

This script has both a GUI and a CLI version. The CLI version usage is: ./BoxBlaze.sh --no-gui /full/path/to/game.iso

The dependencies are (although it should work using the CLI option even without it) Zenity and growisofs. Both of these packages should be installed by default in Ubuntu. 

If you have any ideas, suggestions, or comments, please post them here. Note that this is the first time I'm using Zenity, and I'm not exactly an experienced bash scripter, so I won't take offence if you point out some obvious flaw. ;) However, I'm trying it out live now, and it seems to be working just fine.

Anyway, enough talk. [SIZE="4"][COLOR="Red"]The script is available at my blog, which can be found [here]("http://www.blastfromthepast.se/blabbermouth/2009/04/how-to-burn-xbox-360-isos-in-linux/").[/COLOR][/SIZE]

To use it, save it to your desktop, make it executable (sudo chmod u+x ~/Desktop/script_name.sh) and then just run it by double clicking. If you want to use the CLI option just run it from the command line by typing ./script_name.sh --no-gui /full/path/to/game.iso 

Note that if this makes your DVD burner blow up, kill your cat and burn down your house, I take absolutely no responsibility. The same applies if it ruins your DVDs. I would also recommend that you read up on what DVDs to use, and the neccessary modifications you need to make to your Xbox before you do anything.

---

### Post by crazyfuturamanoob on 2009-04-07
Does the Xbox need to be modded to be able to play those DVD's?

---

### Post by Nevon on 2009-04-07
> **crazyfuturamanoob said:**
> Does the Xbox need to be modded to be able to play those DVD's?

Yes. They do not work on unmodified Xboxes. However I would prefer not to discuss that here, as the Ubuntuforums administrators might not approve of it. However, if you google for Xbox 360 chipping/flashing you'll find more information.

---

### Post by roob85 on 2009-04-15
hey cool to see you finally did something with this script. Ive updated some of the articles over at [http://blog.roob.us]("http://blog.roob.us") and moved the blog from [http://www1.roob.us:53535/blog/]("http://www1.roob.us:53535/blog/") to [http://blog.roob.us]("http://blog.roob.us")

---

### Post by hikaricore on 2009-04-15
> **Nevon said:**
> Yes. They do not work on unmodified Xboxes. However I would prefer not to discuss that here, as the Ubuntuforums administrators might not approve of it. However, if you google for Xbox 360 chipping/flashing you'll find more information.

Yea be careful the mods here are evil and they will eat your souls for breakfast.

---

### Post by Nevon on 2009-04-16
> **hikaricore said:**
> Yea be careful the mods here are evil and they will eat your souls for breakfast.

I may be walking a thin line, but at least I'm careful about where I set down my foot. ;)

---

### Post by Gushter13 on 2009-08-17
Nice man. Just one question (sorry for doubting) does this change the size of the first layer or not?

P.S. The blog link seems dead

---

### Post by Nevon on 2009-08-17
> **Gushter13 said:**
> Nice man. Just one question (sorry for doubting) does this change the size of the first layer or not?

P.S. The blog link seems dead

It doesn't change the size of the first layer, however, it does set the layer break to the correct position for Xbox 360 isos - if that's what you were wondering. 

As it turns out, I'm actually trying to rewrite this in Python, which allows me to do better better sanity checks, properly auto-find DVD-burners with the right comparability, and build a proper GUI. However, doing it in Python is also damned hard - as I have to make it multithreaded, which really is a pain when you're also using a GUI toolkit. I'll be sure to bump this thread once I've got it released. But don't hold your breath, because I'm sure it'll take a while, as I'm also working hard on [Caffeine](http://www.blastfromthepast.se/caffeine/).

---

### Post by Gushter13 on 2009-08-18
Thank you for your quick reply.

---

### Post by mal93 on 2009-11-26
Working very fine. Thank you very much for this script! Now I have it as a nautilus script and burning a dvd is fast and easy!

---

### Post by Nevon on 2009-11-26
Nice to hear. I was actually working on rewriting the thing in Python, with a proper GUI. But a combination of multithreading being a little bit of a bitch, and university taking up more of my time, has caused me to abandon that project for a little while. Good thing this script still works, even if the actual code hurts my soul a little bit every time I look at it.

---

### Post by thumpszilla on 2009-12-14
will this do regular xbox games as well or do I need something else entirely?

---

### Post by del_diablo on 2009-12-14
> **thumpszilla said:**
> will this do regular xbox games as well or do I need something else entirely?

My guess is that you need to be a pro with DD to burn out "fake" xbox games.

---

### Post by thumpszilla on 2009-12-14
well I used to do it alot in windows as both my xbox's have modchips. my kids use one and I use the other. I just don't remember the program name. My backup disks are looking pretty rough so really need to replaced.

---

### Post by del_diablo on 2009-12-14
Oh, you should have said so. This will do the job perfectly.

---

### Post by thumpszilla on 2009-12-15
thanks

---

### Post by leomelo on 2009-12-16
Since a long time ago,Brasero burns dual layer dvds and xbox isos.

---

### Post by Nevon on 2009-12-16
> **leomelo said:**
> Since a long time ago,Brasero burns dual layer dvds and xbox isos.

Yes it does, since it uses the exact same backend as I do. However, does Brasero set the correct layer break automatically, or do you have to manually edit that somehow - like in k3b?

---

### Post by Nick_Jinn on 2010-03-23
So this is for burning your ISO images?

First of all I would like to thank you for doing this. I really appreciate it and you are making linux better with your contributions. Thank you.


Second....Any help with making ISOs from our legally owned games that we wish to make our perfectly legal backups from?

Since I already legally own my games I would rather not have to "pirate" a game I aleady own just to make a backup....so the only responsible thing for us to do would be to work on making a ripping tool so that we can get ISOs from our purchased games directly.

---

### Post by Nevon on 2010-03-23
> **Nick_Jinn said:**
> So this is for burning your ISO images?
That's correct.

> **Nick_Jinn said:**
> First of all I would like to thank you for doing this. I really appreciate it and you are making linux better with your contributions. Thank you.
You're very welcome. I originally made it for my brother, so that he didn't have to search for the correct settings every time he wanted to burn a game. I figured it might be of use to someone else as well.


> **Nick_Jinn said:**
> Second....Any help with making ISOs from our legally owned games that we wish to make our perfectly legal backups from?
I haven't tried it myself, but it doesn't seem that complicated.
[http://forums.xbox-scene.com/index.php?showtopic=651146](http://forums.xbox-scene.com/index.php?showtopic=651146)

---

### Post by Nick_Jinn on 2010-03-23
I tried downloading it but the installation directions failed. 

> 
starbucks@starbucks-desktop:~$ 
starbucks@starbucks-desktop:~$ tar xzvf uxrip360-0.2.tar.bz2
tar: uxrip360-0.2.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
starbucks@starbucks-desktop:~$ 
starbucks@starbucks-desktop:~$ tar xzvf uxrip360-0.2.tar.bz2
tar: uxrip360-0.2.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
starbucks@starbucks-desktop:~$ tar xzvf uxrip360-0.2.tar.bz2
tar: uxrip360-0.2.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
starbucks@starbucks-desktop:~$ cd uxrip360-src
bash: cd: uxrip360-src: No such file or directory
starbucks@starbucks-desktop:~$ make
make: *** No targets specified and no makefile found.  Stop.
starbucks@starbucks-desktop:~$ sudo make install^C
starbucks@starbucks-desktop:~$ 


---

### Post by Nevon on 2010-03-24
> **Nick_Jinn said:**
> I tried downloading it but the installation directions failed.

Then unpack the archive graphically.

---

### Post by c4po on 2010-05-04
you can't unpack it because the cmd ur using is for tar.gz files for tar.bz2 u need to put
tar -xjvf [filename].tar.bz2

---

### Post by southzeztpdot on 2010-05-27
Don't mean to bump an old thread but I get this error at the end of the burning.

":-( unable to reload tray: No such file or directory"

---

### Post by mklinux on 2010-05-28
I don't get an error, but even if I set my burn speed to 2x (so that I don't get skipping) it automatically bumps it up to 3x or more. I get the same results when using the growisofs command or when using k3b with the correct speed settings; which are also bumped up to 3x once burning begins - resulting in the disc being recognized, but not play smoothly - tons of skipping. Anyways, I was making backups on the same computer with windows running 3 months ago using CloneCD, which made perfectly readable backups. I'm wondering what changed. As I said before the media I'm using to burn and the computer hardware is the same, the only difference is that I'm using Ubuntu now.

---

### Post by samirfor on 2010-09-25
I build abgx360gui:
[http://www.mediafire.com/?a7rj8hb7bbea7b1](http://www.mediafire.com/?a7rj8hb7bbea7b1)
and abgx360 core:
[http://www.mediafire.com/?bkk2bawsf23wxhk](http://www.mediafire.com/?bkk2bawsf23wxhk)

Both built on Ubuntu Lucid (10.04) [2010-09-25]

Good luck!

---

### Post by hornedfiend on 2011-02-17
the boxblaze link is broken. Can anybody send it to me please, or maybe provide a new link?
Thanks.

---

### Post by Dr.Paneas on 2011-03-21
[http://tommybrunn.com/2011/03/boxblaze/](http://tommybrunn.com/2011/03/boxblaze/)

I can't burn my DVD. It seems that the boxblaze tries to burn /dev/dvd while my DVD-DL is /media folder

btw this is my guide: [http://wp.me/p1qJXE-E](http://wp.me/p1qJXE-E)

---

