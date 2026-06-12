---
title: "A Better Desktop Environment"
date: 2006-09-14
forum: Desktop Environments
---

### Post by akshaysrinivasan on 2006-09-14
I am tired of super memory consuming desktop environments,and having to wait 15 s for firefox to start.Here is my test of the 4 i am running,
I used the default desktop(i created a new user),running asmem meant for X and xterm.So this pretty much indicates the basic usage at idle.

             Physical         Swap
Gnome          58%              8%
Enlightenment  37%              8%
KDE            51%              8%
XFCE           56%!             8%


Enlightenment is no doubt very fast but it is hardly usable.Any suggestions??

---

### Post by kazuya on 2006-09-14
I feel your pain. You could try fluxbox as well. It is more on the CLI side, but it is much speedier I believe and cleaner to work from. DSL linux is based on Fluxbox as well.

Fluxbox is more useable than enlightenment, but you may lack in ease of customizing your desktop icons, wallpapers, menu, etc. However, it could be a rewarding experience trying it out. Many lightweight- enthusiasts switch in this direction.

Some would also recommend BUM. Or tools for turning off services that get launched by default.., apache, spamassasin., acpi, etc.

Give it a try. Fluxbox / Blackbox. There is afterstep, but I did not like it. And icewm {windows 9x look.} Very light though.

Hope this helps.

Something else to check is what type of CPU are you using? pentium 4, athlon, or athlon 64.. The default Dapper install is i-386. Some testify that i-686 is the best one to use for newer Pentiums, , while k6 or k7 is for AMD archetecture..., and k7-smp, k8 - - -> for 64 bit architecture..  You have to research on these.

---

### Post by whizbaby on 2006-09-14
The ultra-lightweight WMs have to be configured a bit to fit your needs and you will have to learn how they are supposed to be used, then you will see they're all *usable*. I have good experiences with enlightenment, blackbox and LarsWM (the latter took a bit longer to turn out a good experience). Each of these has it's own homepage
[http://www.enlightenment.org/](http://www.enlightenment.org/)
[http://blackboxwm.sourceforge.net/](http://blackboxwm.sourceforge.net/)
[http://home.earthlink.net/~lab1701/larswm/](http://home.earthlink.net/~lab1701/larswm/)
to learn more about them.

---

### Post by akshaysrinivasan on 2006-09-14
I use a AMD athlon,and have already installed the k-7 kernel and stopped non-essential services,still i find it lacking performance.Think i'll try the other wms

---

### Post by PathSpace on 2006-09-14
Another one you might give a shot is WindowMaker.  It is pretty lightweight, and usable if you get used to it.  It's what I used to use before I installed Compiz (now I use Compiz/GNOME).

---

### Post by lagagnon on 2006-09-14
How much RAM do you have? I personally would never consider running either KDE or Gnome with less than 512MB of RAM. If you don't have that much you are banging your head against a a brick wall, despite what the "OS requirements" might be.

I like Fluxbox, but as with anything lightweight you have to set it up and it does not automatically pick up new menu items.

---

### Post by Ramses de Norre on 2006-09-14
I use fluxbox have a gig RAM and I've got 39% used and 1% swap.
Programs running: firefox (8 tabs) two amsn conversations, two open office windows, nautilus file manager, two gnome-terminals, amarok, apache webserver.

So it's pretty good on resources ;)

---

### Post by brucevangeorge on 2006-09-14
My system with XFCE installed uses 59megs (11.5% memory) when it starts up and it can jump up as high as 80 megs with swiftfox. (2-3 tabs).

And no swapfile usage.

And it looks almost exactly like Gnome (thanks to the themes, and icon packs).

My firefox is now swiftfox (AMD k7 optimized.) it literally takes 2 seconds to start. I also have prelink and preload which helps to decrease the startup time of swiftfox and the system.

As well, I spent the time doing a custom, step by step install of only what I needed. So there is no bloatware. And I have the K7 kernel. A jfs filesystem which is speedier than the default.

Specs: Althon XP1800+ (voltage increased to 1.850v :-\"  ). 512 Ram, Ti4600. Very speedy and no bottlenecks. Yeeeeeehaaaawwwwww!!!

---

### Post by anthro398 on 2006-09-14
I've always been partial to [Openbox]("http://www.icculus.org/openbox/").  It runs swimmingly on my 600 Mhz Celeron-powered Dell laptop with 128 MB of PC100 RAM.

---

### Post by Omnios on 2006-09-14
Hi umm how did you install  Enlightenment, Did you use the Ubuntu gnome build and use the tweek to use it. If this is the case then it is running all the power hugry packages and would not run as low as a base build. 

 Also I remember a few releases ago I tryed out E-16 following Pickled's how to which basicly runs all the Gnome components with E-16. The interesting thing here was I was talking to Pickled and asked about installing E-16 or E-17 with other desktop packages sych a xfce etc. Though the mod might not use the same commands it is supposidly doable. Basicly what he was saying is take a desktop package and mod it to run E-17. Xubuntu might be interesting as there is a new file manager available with icon and trash can support. 

 ANyways its something worth looking into.

 Also I made this post in forum discutions which has an interesting quote from a E-page with system requirments mentions.
[http://ubuntuforums.org/showthread.php?t=248880&highlight=E-17](http://ubuntuforums.org/showthread.php?t=248880&highlight=E-17)

---

### Post by akshaysrinivasan on 2006-09-15
I have to admit i have less memory than most of you 256 MB RAM from which 16MB is reserved for shared graphics card.I have heard Gentoo Linux is way faster than ubuntu,is the problem with the desktop environment or with the dapper kernel?I am not quite satisfied with dapper as an upgrade to breezy.Bruce how did you make xfce use so little memory?My xfce 4.39 desktop never goes below 120 MB even when idling!

---

### Post by nalmeth on 2006-09-15
This guide makes setting up fluxbox a lot easier:
[https://wiki.ubuntu.com/Fluxbox](https://wiki.ubuntu.com/Fluxbox)
I have a slower laptop that I run xfce and fluxbox on, and xfce doesn't take up nearly that much memory... I can't explain why yours would.. Are you running a lot of heavy apps like amarok?

---

### Post by akshaysrinivasan on 2006-09-15
I have amarok installeed,but hardly use it.I run xmms most of the time.

---

### Post by nalmeth on 2006-09-15
Whats the output of 
top 

when you're running idle in xfce?

---

### Post by akshaysrinivasan on 2006-09-15
Output of the top,whats that?

---

### Post by nalmeth on 2006-09-15
Sorry, I meant in the terminal, the command 'top'

Just to get an idea of whats running and bogging up memory

You don't have to post it, but it will show you how much weight apps are using.

That guide for fluxbox is excellent, it renewed my faith in the excellent minimalistic WM/DE

---

### Post by akshaysrinivasan on 2006-09-15
Well i was quite confused with that,i got this

pluto@Neptune:~$ top

top - 13:25:53 up 12 min,  2 users,  load average: 2.27, 1.77, 0.90
Tasks:  80 total,   4 running,  75 sleeping,   0 stopped,   1 zombie
Cpu(s):  7.3% us,  3.6% sy,  0.0% ni, 65.6% id,  1.0% wa,  0.0% hi, 22.5% si
Mem:    239528k total,   235904k used,     3624k free,     1248k buffers
Swap:   321260k total,    78392k used,   242868k free,    51612k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5584 root      15   0  112m  40m 5516 S  4.7 17.5   0:48.76 Xorg
 6741 pluto     15   0 46436 6336 3832 R  2.7  2.6   0:03.38 xmms
 6895 pluto     15   0 50232  19m  13m R  2.3  8.3   0:02.28 gnome-terminal
    4 root      RT   0     0    0    0 S  0.3  0.0   0:00.29 watchdog/0
 6389 pluto     15   0  2348  932  808 R  0.3  0.4   0:01.48 gam_server
 6400 pluto     15   0  111m  11m  10m S  0.3  5.1   0:01.35 update-notifier
 6936 pluto     15   0  2192 1088  856 R  0.3  0.5   0:00.05 top
    1 root      16   0  1568  476  444 S  0.0  0.2   0:01.12 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.23 events/0
    6 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.23 kblockd/0
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  123 root      15   0     0    0    0 S  0.0  0.0   0:00.02 pdflush
  124 root      15   0     0    0    0 S  0.0  0.0   0:00.04 pdflush

---

### Post by ootput on 2006-09-15
I've used a whole host of WM's (windowmaker, icewm, *box, ratpoison, ion2-3 etc.) and I've found that the performance of a particular environment strictly depends upon the type of applications used in that environment. 

For instance, were I to use any of the *box', k3b would load up significantly slower than if I were to use KDE. If a majority of your frequently used apps depends on a particular widget/toolset, you're better off using a wm that was built with that widget in mind.

Enlightenment may load up fast, but execution times of apps aren't impressive.

---

### Post by akshaysrinivasan on 2006-09-15
Yes what you are saying is right.i hardly open applications of other DEs in the running one.Like amarok in KDE and Banshee in Gnome...I didn't find any lag in the application startup time in enlightenment,in fact it was faster!

---

### Post by akshaysrinivasan on 2006-09-15
I can't log into fluxbox,says some error when logging in.But i can log in as root.

---

### Post by Ramses de Norre on 2006-09-15
What's in your .fluxbox/startup file?
This is mine, but there are probably things inside you don't need:
> #!/bin/sh
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# You can set your favourite wallpaper here if you don't want
# to do it from your style.
#
# fbsetbg -f ~/images/wallpapers/140154main_image_feature_481_ys_4.jpg
#
# This sets a black background

# /usr/bin/bsetroot -solid black

# This shows the fluxbox-splash-screen
# fbsetbg -C /usr/share/fluxbox/splash.jpg

# Other examples. Check man xset for details.
#
# Turn off beeps:
# xset -b
#
# Increase the keyboard repeat-rate:
# xset r rate 195 35
#
# Your own fonts-dir:
# xset +fp /home/ramses/.font
#
# Your favourite mouse cursor:
# xsetroot -cursor_name right_ptr
#
# Change your keymap:
# xmodmap ~/.Xmodmap



# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &

#Monitoring tool
gkrellm &
kmix &

#insert Gnome
GSDPID=`pidof gnome-settings-daemon`
if [  "x$GSDPID" == "x" ]; then
gnome-settings-daemon &
fi

#makes the gnome-theme-manager work
gnome-settings-manager &

#Automount volumes
gnome-volume-manager &

#keep this export line just before "exec fluxbox &" !
export LC_ALL=C

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.
exec /usr/bin/fluxbox &

# or if you want to keep a log:
# exec /usr/bin/fluxbox -log ~/.fluxbox/log

#Following lines execute programs after fluxbox is started
fbpid=$!

sleep 3
{
   fbpager -w &
   tilda &
} &

wait $fbpid


---

### Post by akshaysrinivasan on 2006-09-16
Well i wanted to differentiate between breezy and dapper.So i installed breezy.The Desktop is so fast!It seemed as if i had a new computer!Breezy is much more faster than dapper.Firefox 5secs!

---

