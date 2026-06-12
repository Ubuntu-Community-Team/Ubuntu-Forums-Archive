---
title: "kubuntu-desktop package not found in Synaptic Package Manager"
date: 2011-02-05
forum: Desktop Environments
---

### Post by Mahboob Alam on 2011-02-05
[SIZE=4]I have a serious problem...  I like KDE desktop environment so I wanna install Kubuntu-desktop package.. but it is not there in the Synaptic Package Manager.. I opened the Package Manager and search for it but it was not found... is there any other way to install KDE desktop (Kubuntu-desktop) environment?... [/SIZE]

---

### Post by nothingspecial on 2011-02-05
Try a little K

as in k

not K

[COLOR="Red"]k[/COLOR]ubuntu-desktop not [COLOR="Red"]K[/COLOR]ubuntu-desktop

---

### Post by ankspo71 on 2011-02-06
Hi,
Did you find it yet? There is always the possibility that you might have tried installing the package when the servers were busy syncing those packages to newer versions. Refresh/reload your repositories and try again. If it still isn't there, you can always try switching to another server then try again.
Hope this helps.

---

### Post by inobe on 2011-02-06
i would advise not to install kubuntu desktop with your ubuntu installation.

if you like kubuntu, then just get it [http://www.kubuntu.org/](http://www.kubuntu.org/)

backup all your data and install it the pure way without a conflicting ubuntu desktop!

---

### Post by markthekdeguy on 2011-02-07
agreed with above ..  if 

sudo apt-get install kubuntu-desktop

doesn't work, you could try either

sudo apt-get install kde-full 

sudo apt-get install kde-minimal

these will install a more (or less) complete KDE,
but some problems with this may well be :

a)
Synaptic wont pop up a dialogue box when it asks which
login manager you want to use. it will just sit there when 
applying changes, you have to click the 'details' checkbox
then you will see a mini terminal-window asking you which
login manager you prefer, either GDM  (Gnome) or KDM (KDE)
- either will work, but if you're going KDE ...

b)
There will be Gnome apps probably running, even when
you've logged into KDE.  not a deal breaker, but may decrease
performance from these unwanted background processes.

c)
Pulseaudio may well be running :confused:

d)
Possibly GTK apps may look fugly, whereas Kubuntu (proper) installs
a 'wrapper' which forces all GTK stuff to look like a KDE app.
- it works beautifully too. add  the QTCurve themes all round, you've got a
seriously gorgeous desktop btw :p

hope this helps. have fun !

---

### Post by vincix on 2011-02-08
> **markthekdeguy said:**
> agreed with above ..  if 

sudo apt-get install kubuntu-desktop

doesn't work, you could try either

sudo apt-get install kde-full 

sudo apt-get install kde-minimal

these will install a more (or less) complete KDE,
but some problems with this may well be :

a)
Synaptic wont pop up a dialogue box when it asks which
login manager you want to use. it will just sit there when 
applying changes, you have to click the 'details' checkbox
then you will see a mini terminal-window asking you which
login manager you prefer, either GDM  (Gnome) or KDM (KDE)
- either will work, but if you're going KDE ...

b)
There will be Gnome apps probably running, even when
you've logged into KDE.  not a deal breaker, but may decrease
performance from these unwanted background processes.

c)
Pulseaudio may well be running :confused:

d)
Possibly GTK apps may look fugly, whereas Kubuntu (proper) installs
a 'wrapper' which forces all GTK stuff to look like a KDE app.
- it works beautifully too. add  the QTCurve themes all round, you've got a
seriously gorgeous desktop btw :p

hope this helps. have fun !


Hello,

I've made this exact mistake and my Ubuntu boots up (now the screen with the four dots is Kubuntu on a blue background) and my xserver doesn't start. I do have access to my consoles though. 
Is there a way to reverse it? To return to the old the basic desktop ubuntu and make it exactly as it was?

Thanks

---

### Post by wizard10000 on 2011-02-08
> **markthekdeguy said:**
> b)
There will be Gnome apps probably running, even when
you've logged into KDE. not a deal breaker, but may decrease
performance from these unwanted background processes.

Probably not, as autostart processes are different for KDE and GNOME.  There may be some *services* running, but there shouldn't be any GNOME apps running in KDE unless they've been configured to autostart *in* KDE.

> **markthekdeguy said:**
> d)
Possibly GTK apps may look fugly, whereas Kubuntu (proper) installs
a 'wrapper' which forces all GTK stuff to look like a KDE app.
- it works beautifully too. add  the QTCurve themes all round, you've got a
seriously gorgeous desktop btw :p

Installing kde-config-gtk, kde-style-qtcurve, kwin-style-qtcurve and gtk2engines-qtcurve will solve this.  I believe all are part of kubuntu-desktop.

I transitioned from GNOME to KDE two years ago and did it by installing kubuntu-desktop.  Next upgrade I did a clean install of KDE but I had both DE installed for a couple months to make sure I could do what I needed to do while transitioning to KDE.

---

### Post by markthekdeguy on 2011-02-12
when i say 'apps' i use the term broadly to illustrate the difference between a Ubuntu install with added Kubuntu-desktop, as compared to a vanilla Kubuntu install as a point of interest, as this seemed like a valid and useful point to make to the original poster

but as the OP didn't ask for the distinction between apps, daemons, userspace, KIO, 'services' modules or anything like that, it was deemed unneeded info and serves to possibly confuse the issue.

and no, installing those qtcurve engines alone doesn't install the
gtk2-engines-qtcurve.rc.sh and make it auto run the script,
at least, not on any kubuntu-desktop etc  i've ever added to ubuntu.
there are however gtk based autostarts in there automagically added
which aren't there on a vanilla kubuntu install.

---

