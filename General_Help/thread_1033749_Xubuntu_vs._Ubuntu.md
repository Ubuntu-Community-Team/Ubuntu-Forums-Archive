---
title: "Xubuntu vs. Ubuntu"
date: 2009-01-07
forum: General Help
---

### Post by Luther11 on 2009-01-07
I've been wondering if I should switch from Gnome to Xfce. In the past I figured that when my computer gets old enough to slow down significantly, I'll just switch to Xubuntu to get more use out of it. But today I realized I could just speed my computer up as much as possible by installing Xubuntu now.

So my question is: Is there any advantage that Gnome has over Xfce? I can install the same software on both, so why not just make Xubuntu my main distro?

---

### Post by Elfy on 2009-01-07
I think that gnome is a bit easier to deal with myself - but then I've not spent much time on Xubuntu.

You could also look into different window managers as well - I've used fluxbox personally, but there are many available for you to install from the repos. There is also lxde - another desktop environment.

You cna install these things from within ubuntu - then choose them from sessions at the login window.

You can do the same with xubuntu

[http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

lxde, fluxbox and many others are all available through the repos.

Try them out and choose one - then get rid of the others.

---

### Post by bumanie on 2009-01-07
Why not install xubuntu desktop and choose to either boot into gnome or boot into xfce at login? > sudo apt-get install xubuntu-desktopAt the username/password screen, click in the bottom left of the monitor and you will have the choice of gnome or xubuntu. You can then see A) If you like xfce and B) Whether the speed increase is up to your expectations. You can easily get rid of either desktop environment later, or keep both, if you wish.

---

### Post by bodhi.zazen on 2009-01-07
Xubuntu is not *that* much lighter then Ubuntu.

The difference is not with XFCE (window manager) but rather in lighter weight applications, ie Abiword rather then Open Office.

With that said, of the "Big 3" I prefer XFCE > Gnome > KDE

---

### Post by Luther11 on 2009-01-07
> **bumanie said:**
> Why not install xubuntu desktop and choose to either boot into gnome or boot into xfce at login?

Seems to me like there could be issues that can't be found just by using the software. If I have to do something in Ubuntu I've never done before, I can usually figure out how just by poking around the GUI. So if I'm doing something new in Xubuntu, and it doesn't have the feature incorporated into the GUI, I'd have to go to the forums or log over to Ubuntu. Either way, it would take more time to get stuff done. If issues like this exist, it's better to ask now before I download it.

Also, community support could be a big factor. Ubuntu may or may not have a huge community advantage over the other flavors because so many more people use it.

Anyway, if nobody can think of any real problems with Xubuntu, I'll install it tomorrow.

This looks a lot longer than my OP. If I wasn't specific enough to begin with, I apoligize.

---

### Post by bodhi.zazen on 2009-01-07
XFCE is a window manager, ie the boxes on the screen.

There really is almost no (can't really say never as never is a really long time) you would have to re-start gnome.

Still uses the same applications (XFCE draws from gnome applications).

If you look, very little of the support on these threads is window manager specific.

The feature I like most in XFCE is that you can right click anywhere for a menu (rather then having to go to the gnome/kde "start" box on the panel).

I also like that feature in Fluxbox (Fluxbox FTW !!! ).

Now I spend half my time (or more) in the terminal, so window manager is not so critical. Your mileage may vary.

---

### Post by Luther11 on 2009-01-07
> **bodhi.zazen said:**
> 
There really is almost no (can't really say never as never is a really long time) you would have to re-start gnome.

If you're saying I don't have to go into Gnome to find functions that aren't in Xfce, then I think that's pretty much the information I was looking for. Thank you!

---

### Post by sameat on 2009-01-07
I've been down that road a few times, and I have to say that the performance gains are marginal at best.  I kind of "felt like" I had a slightly faster system when I ran one of the lighter weight de's, but it never knocked my socks off.

There is generally less community support for the alternative DE's, but that just makes it a little more of a challenge.  I don't believe that I ever hit a problem that just couldn't be solved (in xubuntu, or running flux).  Occasionally, I had to adjust my expectations a little bit, but I think that has the benefit of teaching you new ways to do things. 

If you enjoy the process, by all means go for it...I'm a hobbyist that way too.  If you're looking to make that old Pentium II run like lightning, you'll probably be disappointed.  After all, the apps that you use every day will probably be the same (especially with xubuntu).

In any case, good luck and happy computing.

---

### Post by jsroth on 2009-01-09
I have used both, Xubuntu and Ubuntu, on my laptop by now and I like Ubuntu a little bit better. This is because most HowTos are written for Gnome and I don't have to "translate" them into XFCE when trying to do the same. Of course there seems to be nothing that doesn't work in XFCE but is working in Gnome but for me, being a (X)Ubuntu and Linux beginner Gnome seems to a little bit easier to user and only a very, very tiny bit slower on this machine (Thinkpad T60, not the typical slow machine ;)). 

But talking about the applications I would prefer Abiword and Gnumeric to OpenOffice in most cases because Abiword is much faster and much more leightweight and most of the functions Abiword gives you are absolutely enough (since I'm using LaTeX for anything more then 50 words). This improves the speed much more than just the difference between Gnome and XFCE.

---

### Post by adamlau on 2009-01-09
Xubuntu is not that much faster than Ubuntu, true. The key is to install Ubuntu Minimal + XFCE for more appreciable gains in UI responsiveness. The overlooked benefit of Xfce is the path towards using alternative applications which oftentimes outclass their GNOME counterparts. Three things irk me about Xubuntu: 1. Additional hard drives are not auto mounted. Not a real problem, but an annoyance when you have to modify fstab and mount and unmount varying drives and partitions all the time. 2. Text below icons on the Desktop are truncated and not wrapped (nor are they in Xfce 4.6 Hopper). Annoying to have to decipher which file is which when they start with the same naming convention. 3. No drag and drop support for panel icons. Time consuming to set up on new installs which use specific apps.

---

### Post by hyper_ch on 2009-01-09
to add to the previous poster:

4. Not being able to select multiple files with a selection box on the desktop or in thunar.

---

### Post by adamlau on 2009-01-09
5. Menu Editor does not edit the default desktop menu (at least not fully). Manunally editing a custom menu.xml is required. 

6. Orage and clock do not feature multiple timezone support. 

7. 'Settings Manager > Printing system' does not allow you to set a default printer. Printers must be specified in each application from which to print. Else, xfprint4 must be run and settings saved.

---

### Post by bodhi.zazen on 2009-01-10
> **hyper_ch said:**
> to add to the previous poster:

4. Not being able to select multiple files with a selection box on the desktop or in thunar.

Yes you can select multiple files on both, hold down the control key as you select.

> **adamlau said:**
> 5. Menu Editor does not edit the default desktop menu (at least not fully). Manunally editing a custom menu.xml is required. 

6. Orage and clock do not feature multiple timezone support. 

7. 'Settings Manager > Printing system' does not allow you to set a default printer. Printers must be specified in each application from which to print. Else, xfprint4 must be run and settings saved.

5. Yes it does. The menu is a bit odd, but claiming it does not work is a bit of an overstatement. I have altered the menu the way I like, including changing some icons, all without manually editing the xml file.

6. Pass, I do not use that feature at all.

7. Try Main Menu -> Settings -> default printer ;)

---

### Post by hyper_ch on 2009-01-11
> **bodhi.zazen said:**
> Yes you can select multiple files on both, hold down the control key as you select.
I know that.. but it still does not offer a selection box...

---

### Post by PGScooter on 2009-01-11
8. no "arrange icons" for the desktop

---

### Post by fredbird67 on 2009-01-17
A weird quirk I've noticed with XFCE is that, other than the base menu that contains all the categories of the other menus that fly out from it, it's difficult if not impossible to edit menu items in secondary menus.

Case in point:  I used to have Xubuntu on my desktop PC (I have it on our laptop, though) until my wife told me that our niece might be coming up here to go to college after she graduates from high school this coming May to earn an AA in photography.  One program I was sure they'd be teaching her is Photoshop, and I thought to myself "I bet Shayla would like to have GIMPShop on here, and so I tried fooling around with the menus in XFCE but never could figure out how to edit them, so I gave up on it and went with Ubuntu and GNOME.  That way, if she comes up here next fall to go to school, I'll be ready to set it up for her.

Another thing I've noticed is that, by default, XFCE is REAL bad to want to give you text sizes that are too small, plus it's inconsistent in what text sizes it gives you, and it's very annoying (a bug, perhaps?).

Oh, and the clock is a real pain to get to display in white text on a dark panel background -- so much so that I instead installed GNOME-Panel and installed the GNOME clock instead.  If I were creating a distro that used XFCE for its desktop, that's one thing I'd definitely include by default instead of XFCE's clock.

Other than that, it's not bad, and I enjoy using it, but I will say that XFCE definitely seems to have more than its share of odd little quirks.

---

### Post by walterp98@gmail.com on 2009-05-23
FWIW, my experience showed me that with only 512mb ram, my system was **much** faster with xubuntu than ubuntu.  Specifically, audacity is much more responsive to selecting different sections of audio files.

Of course my recent jump to 1 Gb may have solved that issue, so I'll try gnome again.

Cheers.

Walter

---

