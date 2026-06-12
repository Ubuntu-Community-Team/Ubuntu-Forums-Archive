---
title: "Unable to start X server"
date: 2005-10-31
forum: Desktop Environments
---

### Post by icekin on 2005-10-31
Using breezy on a compaq armada 1750. Since its old limited hardware, I decided to do a minimal server install and then install whatever needed packages later using aptitude. I installed fvwm and fluxbox using the apt-get install command. 

1) When I type fluxbox or fvwm at the prompt, I get "can not connect to X server" and "<<ERROR>> can't open display". So, I installed Xorg by doing "apt-get install xserver-xorg". I also installed the xorg-common. I checked aptitude, I can see these 2 packages as listed with "i" next to them. But, when I run dpkg-reconfigure xserver-xorg I get "package not installed and no info is available."

I tried "startx" and "xinit", but I get "bash: command not found". How do I get X working properly?

2) How do I make X start automatically everytime?

I read that aptitude and apt-get auto resolve dependencies. That means if fvwm is dependent on X, shouldn't it download and install that automatically?

---

### Post by RAOF on 2005-10-31
Did you get any errors when you ran "sudo apt-get install xserver-xorg"?  It looks like X isn't actually installed.  And you're right - fvwm & fluxbox should depend on X, so it should have been automatically installed when you installed them.

---

### Post by icekin on 2005-10-31
Okay, I don't remember getting any errors except that backports repository not found. But, that I read is because there are no backports at that time. I enabled all repositories, including universal on the server.list. 

Anyway, I ran apt-get install xserver-xorg again and I get a graphical Xserver install screen this time; didn't get that before. So, I proceed along and select my graphic card, monitor settings and whatever.

Then, I select the option to sync values with configuration file and the graphical install exits and this comes out "xserver-xorg postinst warning : overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf .200511011021"

"startx" and "xinit" still return "command not found"

What next?

---

### Post by RAOF on 2005-11-01
Does /usr/bin/startx exist?  Because it should.  That warning message seems to be benign.  I really don't know what's going on here.

As a last resort you could try apt-getting ubuntu-desktop.  That'll install a standard install, which will bring in X and gnome.  If that works, you could start selectively removing stuff...  Not nearly as good, but perhaps worth a try.

---

### Post by icekin on 2005-11-01
Yeah, no usr/bin/startx found. There is a startfluxbox though, and that of course returns the error : "Could not connect to X server. Start X server before you start fluxbox"

I could do apt-get install ubuntu-desktop, but I really don't like gnome (or kde); prefer the simple, light interface of fluxbox or fvwm. Which is probably better for my RAM-starved laptop anyway.

I previously tried the normal "expert" install and got the full ubuntu desktop with all eye candy loaded. Then, I started removing unnecessary stuff using aptitude, but somewhere along the way I screwed up and removed something necessary for other programs. For some reason, aptitude failed to check resolve the dependency again. Besides, there seems to be no way to completely remove gnome and metacity once they are installed. Every time, it keeps saying that other packages depend on it so can't do.

Is synaptic better than aptitude at handling package dependency?

---

### Post by RAOF on 2005-11-01
I think that synaptic and aptitude are both front-ends to the same thing, apt.  Synaptic has the advantage of being more graphical, though.  Synaptic will tell you what you will additionally remove if you remove a package, and you should be able to resolve broken dependencies.

Of course, if you try and remove everything gnome-related, you'll get rid of all sorts of stuff.  All the gnome apps depend on gnome-libs, for example.

Oooh, actually, you could try xubuntu-desktop.  That'll install an xfce desktop, which is lighter than gnome/kde.

---

### Post by felix_stegerman on 2005-11-01
Try installing x-window-system.
That should include xbase-clients, which includes startx.


Felix

---

### Post by felix_stegerman on 2005-11-01
[QUOTE=icekin]
2) How do I make X start automatically everytime?
[/QUOTE]

Install gdm or xdm.


Felix

---

### Post by icekin on 2005-11-01
Wish I had read felix_stegerman's post a little sooner. Anwyay, went ahead and installed XFCE and its pretty fast, even on my laptop! Thanks to RAOF. Certainly, one heck lot better than Gnome and KDE despite an equal amount of eye candy.

Now, when I run startx, the XFCE desktop automatically jumps up. Is there anyway to just start Xserver alone so that in the next line I can type "fluxbox" or "fvwm" or "xfce" and start that separately?

I tried running "fluxbox" from within the terminal in XFCE, but that brought "Bscreen Error : another window manager already running on display : 0.0" Makes sense too. Only one window manager can use X at a time?

I will also try installing gdm, I recall that used to allow a person to choose what window manager they wanted to use for the the session at login.

---

### Post by felix_stegerman on 2005-11-01
[QUOTE=icekin]Wish I had read felix_stegerman's post a little sooner. Anwyay, went ahead and installed XFCE and its pretty fast, even on my laptop! Thanks to RAOF. Certainly, one heck lot better than Gnome and KDE despite an equal amount of eye candy.[/QUOTE]

XFCE is pretty nice indeed. I used it for a long time.


[QUOTE=icekin]
Now, when I run startx, the XFCE desktop automatically jumps up. Is there anyway to just start Xserver alone so that in the next line I can type "fluxbox" or "fvwm" or "xfce" and start that separately?
[/QUOTE]

It's not easy to be "asked". But to can start an X session with fluxbox,
you could try:
# xinit /usr/bin/fluxbox

You may also want to try openbox. It's very configurable.

[QUOTE=icekin]
I tried running "fluxbox" from within the terminal in XFCE, but that brought "Bscreen Error : another window manager already running on display : 0.0" Makes sense too. Only one window manager can use X at a time?
[/QUOTE]

Yes.


[QUOTE=icekin]
I will also try installing gdm, I recall that used to allow a person to choose what window manager they wanted to use for the the session at login.[/QUOTE]

Exactly.


Felix

---

### Post by icekin on 2005-11-01
Installed gdm, now everything works great. However, Openoffice Writer takes a full minute and 40 seconds to load. I even tried the advice given here : [http://www.linuxjournal.com/article/8308](http://www.linuxjournal.com/article/8308) , but it really didn't make much of a difference. Some people suggested trying Abiword; that's okay as far word processing goes, but impress is the only power point replacement for linux, it seems. Haven't tried the KDE office suite yet. Anybody has better ideas?

---

### Post by felix_stegerman on 2005-11-01
According to LXF71 (Linux Format Oct '05):
* Koffice is a good, well integrated, office suite, but not good at reading files created by other office suites (notably MS Office).
* Abiword & Gnumeric are "a winning combination".
* OO.org is the only good "suite".

So I guess you'd have to use OO.org Impress for presentations.
But you can always use Abiword for your word processing needs ;-)


Felix

---

