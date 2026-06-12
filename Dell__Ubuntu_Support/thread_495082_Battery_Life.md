---
title: "Battery Life"
date: 2007-07-07
forum: Dell  Ubuntu Support
---

### Post by weaver4 on 2007-07-07
I am using Ubuntu Fiesty on a Dell Inspiron 6000 laptop with a 85watt hour battery.

When using WinXP I get 4.5 hours of use out of the battery.  With Ubuntu I get 2.5 hours.  Similar task, similar brightness for the back light.  I checked and frequency scaling is working on the laptop, what else do I need to check?  Is it possible to get close to WinXP battery life with Ubuntu?

Thanks,

---

### Post by LMP900 on 2007-07-07
I don't use an Ubuntu notebook, but I would suggest using the [**PowerTOP**]("http://www.linuxpowertop.org/") tool to find the culprits. Some [**known issues**]("http://www.linuxpowertop.org/known.php") are listed on the site. I hope that helps!

---

### Post by weaver4 on 2007-07-07
Where do you get/compile PowerTop?  I downloaded the latest version and tried to do a make but I got tons of errors.  Like the following.

 make
cc -Os -g -Wall  -W -Wshadow   -c -o powertop.o powertop.c
powertop.c:25:20: error: unistd.h: No such file or directory
powertop.c:26:19: error: stdio.h: No such file or directory
powertop.c:27:20: error: stdlib.h: No such file or directory
powertop.c:28:20: error: string.h: No such file or directory
powertop.c:29:20: error: stdint.h: No such file or directory
powertop.c:30:23: error: sys/types.h: No such file or directory
powertop.c:31:20: error: dirent.h: No such file or directory
powertop.c:32:21: error: libintl.h: No such file or directory
powertop.c:33:19: error: ctype.h: No such file or directory
powertop.c:34:20: error: assert.h: No such file or directory
powertop.c:35:20: error: locale.h: No such file or directory
powertop.c:36:18: error: time.h: No such file or directory

---

### Post by LMP900 on 2007-07-08
Unfortunately, I'm not using an Ubuntu computer at the moment (still waiting for my Ubuntu Dell to arrive), so I can't be of much help. Just thought I'd give this thread a bump since this will be relevant to me in the near future.

Also, I'm sure there are multiple threads in these forums about this particular issue. Good luck!

Edit: Do you have the build-essential package installed?

---

### Post by metromari on 2007-07-13
To get PowerTop installed you have to have a more recent kernel than the one that shipped with Feisty. You can get the Kernel.org sources or, I believe, get the package that will go into Gutsy.

Compiling a kernel is no cakewalk. I'm no stranger to it because I used Gentoo for awhile.

After upgrading the kernel, I remember that Powertop was easy to compile and install. I didn't manage to squeeze power usage much, but I wasn't doing too badly to begin with.

---

### Post by Rocket2DMn on 2007-07-13
All of us with laptops suffer from this.  Hopefully Gutsy will have a little better support for laptops in the areas of power, wireless devices, suspend/hibernate, and of course, video drivers.
Until then, take your power adapter with you.

---

### Post by defishguy on 2007-07-15
There really isn't a whole lot that you can do.

Try the following:

Turn off Compiz or Beryl if you're using it.  It drives the graphics card very hard.  This is what is causing the vast majority of battery problems with Vista (People leaving Aero running)

Dim the screen as much as possible, this will greatly impact the battery.

Disable wireless if you're not using it.

You could try "laptop mode" but it doesn't have a noticeable impact on the battery life.

Good luck.

---

### Post by ntetreau on 2007-07-19
laptop-mode makes a huge impact on my setup. Follow the first post in my howto to turn laptop-mode on by default when you boot unplugged (this is not the case in Feisty), and then you can also enable power saving on your wireless card if you want to:

[http://ubuntuforums.org/showthread.php?t=419772](http://ubuntuforums.org/showthread.php?t=419772)

Nic

---

### Post by brettr on 2007-07-19
I agree with the previous post i am running an inspiron 6000, and this little tweak made a noticible difference for me.

---

### Post by fjgaude on 2007-07-19
I'm running Ubuntu Feisty, e1505n with the 53-watt hour, 6-cell battery, and I get something over three hours, like 25 minutes over. I have the laptop-mode on tweak and run on-demand CPU freq-scaling. Happy with it all; runs fast, cool and quiet.

frank

---

### Post by whistle on 2007-07-19
I have an E1505/T7200/7300Go... 3-4 hours 9 cell full brightness. Do you have frequency scaling on? I think I just use the gnome one, the proc usually runs at 1 MHZ

---

### Post by kmcq on 2007-08-09
> **whistle said:**
> I have an E1505/T7200/7300Go... 3-4 hours 9 cell full brightness. Do you have frequency scaling on? I think I just use the gnome one, the proc usually runs at 1 MHZ

man three hours.. im very jealous... my dell c400 is cranking out a whopping 60 minutes... but it might just be gnome power management under estimating the battery's ability... oh and i hope you mean 1 Gigahertz not megahertz..

---

### Post by kuja on 2007-08-09
I've not actually timed it, but I'm getting really good battery life. Hmm, battery monitor says that I'm at 87% and suggests that I might have 6 hours left :D

---

### Post by skyel on 2007-11-04
could anybody please help me to compile the powertop :). I've downloaded the 1.9 but i have no idea what files i should compile and how could i do that

---

### Post by rcatman on 2007-11-14
powertop is in the repositories. You can either search for powertop in synaptic and install it or type "sudo apt-get install powertop" in a terminal window.

---

### Post by geeree on 2007-11-15
I use an Inspiton 640m with a 6 cell battery, It used to last a little more than half an hour under Feisty but that has improved a lot in Gutsy. Now I reach more than three hours many times!

Girish.

---

