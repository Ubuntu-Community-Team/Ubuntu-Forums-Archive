---
title: "For those that experience frequent Konqueror crashes"
date: 2005-04-11
forum: Desktop Environments
---

### Post by denzilla on 2005-04-11
Please go here, verify that the backtrace is the same as yours and place a vote for the bug I submitted. Its still unconfirmed and its been days since I filed it. 

[http://bugs.kde.org/show_bug.cgi?id=103400](http://bugs.kde.org/show_bug.cgi?id=103400)

Thanks :)

---

### Post by dermotti on 2005-04-11
I think you should load up another distro with kde 3,4 first and test,

I loaded up Slax live cd with xorg and kde 3.4 and didnt se the issue

---

### Post by denzilla on 2005-04-11
I thought of that, but I see no other way to draw attention to the problem. Is there an official kubuntu bug report page? My underclocked brain might've missed it ;)

---

### Post by Ironi on 2005-04-11
I'm not experiencing any of the weird Konqueror issues discussed recently. However, I'm using a mix of hoary packages with Debian unstable & experimental packages. My guess is that the crash problem at least may not be directly related to KDE.

BTW, it looks like your backtraces aren't going to be very helpful to the KDE developers (no debug symbols). I recommend recompiling kdebase (and perhaps other packages) with debug symbols. For kdebase, this *should* work (sorry, not tested):

```
sudo apt-get build-dep kdebase
sudo apt-get install fakeroot

FOLDER="/tmp/kdebuild" # change to suit
mkdir "$FOLDER"; cd "$FOLDER"
apt-get source kdebase

cd kdebase-3.4.0/
perl -pi -e "s/--with-hal$/--with-hal --enable-debug/" debian/rules
fakeroot debian/rules binary
ls -l ../*.deb
echo sudo dpkg -i ../*.deb # remove the echo to install the packages
```

---

### Post by denzilla on 2005-04-11
What is the point of backtrace logs if key components aren't enabled!?

---

### Post by dermotti on 2005-04-11
Well, i think this is a Kubuntu Issue, i would hope the devs would rebuild kde and catch the bug. 

Im assuming everyone who is running the latest kubuntu is getting this bug.

---

### Post by Ironi on 2005-04-11
[QUOTE=denzilla]
What is the point of backtrace logs if key components aren't enabled!?
[/QUOTE]
Debugging symbols bloat the binaries and generally make the code run considerably slower. KDE's backtrace functionality just gives you whatever it can (from gdb apparently), without trying to determine whether or not debugging symbols are present. When they aren't present, the backtraces usually aren't too helpful; perhaps the developers should include some kind of notice to that effect, and a link explaining how to remedy the situation.

---

### Post by Manny C on 2005-04-11
Looks like someone has reported the bug to Ubuntu (and thus Kubuntu) people. Bug is confirmed...it seems that the bug can be removed if the navigation side panel is closed.


[https://bugzilla.ubuntu.com/show_bug.cgi?id=8009](https://bugzilla.ubuntu.com/show_bug.cgi?id=8009)

---

### Post by dermotti on 2005-04-12
Ill give it a run on my test box and see how it works

---

### Post by Skaman on 2005-04-12
i'm experiencing this crappy crashes....
but not only in konqueror,in kopete kaffeine and a lot of ather applications too....

it seems like "random crashy system" O_o That's unbeelievable!!!

I updated to kubuntu from kubuntu and then uninstalled the gtk packages......
do u think i can solve the problem with a fresh install....or the problems will keep goin on? :?

---

### Post by !nkubus on 2005-04-13
I went to support the bug, so i hope a fix will be near.

the bug sometime duplicate the view of normal files not just hidden ones (that's spooky)

---

### Post by denzilla on 2005-04-13
Yes, I've noticed that too. Also, sometimes after you delete a file, the image is still there till you hit refresh.

---

### Post by Skaman on 2005-04-15
is unbelievable....i crash even in contrrol center superkaramba kdetv and kuser.....this is  [-X  good...... ](*,)

---

### Post by Valavien on 2005-04-16
The problem I have is that whenever I open the Control Center or Open Konqueror it just freezes.  I can still move the mouse but that's it.  Can't issue any commands with the keyboard.

---

### Post by devil28 on 2005-04-16
[QUOTE=Valavien]The problem I have is that whenever I open the Control Center or Open Konqueror it just freezes.  I can still move the mouse but that's it.  Can't issue any commands with the keyboard.[/QUOTE]
 for me these crashes make the system almost unusable at the moment. frequent crashen in most kde-related apps. kaffeine crashes as soon as I try to open a file an so do all other players. also the other stuff like konq and kcontrol. 
i sure hope this gets fixed real ´soon or Im back to mepis. strange enough I havnt been getting any upgrades at all since the first install. the first one was quite big, but none thereafter. update does okay though. do you guys get upgrades?

---

### Post by Valavien on 2005-04-16
I don't seem to get any files either when using update either.

---

### Post by netsharc on 2005-04-20
[QUOTE=Valavien]The problem I have is that whenever I open the Control Center or Open Konqueror it just freezes.  I can still move the mouse but that's it.  Can't issue any commands with the keyboard.[/QUOTE]

Happens to me too, Valavien. After trying and trying, I figured it happens when Control Center or Konqueror tries to render HTML with images. When you open either program it (tries to) open an HTML "welcome page". But the system would still be accessible through SSH, my method of testing was, going root in a Konsole and then typing sleep 20 && kill -9 `pidof X` .. this gives me 20 second to try and figure out the source of the crash, and when the system hangs, X will be killed so I can login again.

Pretty annoying, it worked for the first 2 boots/2 days, and I wonder what's causing it.

---

### Post by Valavien on 2005-04-20
I actually found the answer for my problem in another thread.  

In your sudo gedit /etc/X11/xorg.conf file you unfortunately have to turn off render accell
	Option 		"RenderAccel" 		"false"

So that means no pretty window effects :(
I think the bug is being worked on.

---

### Post by ltmon on 2005-04-20
[QUOTE=Valavien]I actually found the answer for my problem in another thread.  

In your sudo gedit /etc/X11/xorg.conf file you unfortunately have to turn off render accell
	Option 		"RenderAccel" 		"false"

So that means no pretty window effects :(
I think the bug is being worked on.[/QUOTE]

I can confirm that.  

My perfectly stable Kubuntu (3 weeks of heavy usage without a crash) went exactly as you described as soon as I tried to enable the composite extension and renderaccel.

L.

---

### Post by Ironi on 2005-04-21
[QUOTE=Valavien]The problem I have is that whenever I open the Control Center or Open Konqueror it just freezes.  I can still move the mouse but that's it.  Can't issue any commands with the keyboard.[/QUOTE]
The "active mouse pointer freeze" has been happening to a lot of people (even users of other DEs and WMs, I believe). So far, no one has found the actual cause of the problem. It's been attributed to Xorg, KDE, RenderAccel, Composite, the video card BIOS, the system BIOS, nVidia's proprietary driver... gah. At this point, I'm just happy that I figured out a way to stop it from happening with RenderAccel and Composite enabled.

Anyways, you can read more about it at the following links:
[http://www.nvnews.net/vbulletin/showthread.php?t=31858](http://www.nvnews.net/vbulletin/showthread.php?t=31858)
[http://www.nvnews.net/vbulletin/showthread.php?t=47502](http://www.nvnews.net/vbulletin/showthread.php?t=47502)
[http://www.nvnews.net/vbulletin/showthread.php?t=49117](http://www.nvnews.net/vbulletin/showthread.php?t=49117)

A few "solutions" that I've collected:
[http://www.nvnews.net/vbulletin/showpost.php?p=587740](http://www.nvnews.net/vbulletin/showpost.php?p=587740)

---

### Post by xenfasa on 2005-04-21
[QUOTE=Valavien]I actually found the answer for my problem in another thread.  

In your sudo gedit /etc/X11/xorg.conf file you unfortunately have to turn off render accell
	Option 		"RenderAccel" 		"false"

So that means no pretty window effects :(
I think the bug is being worked on.[/QUOTE]

I don't have this in my xorg.conf and I still get frequent crashing running kubuntu?

Can anything else be causing this?

---

### Post by !nkubus on 2005-04-21
Well i dit an upgrade tday and look at the packages that are upgraded:

```

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  libavcodeccvs libpostproc0 mplayer-386 transcode
The following packages will be upgraded:
  kdelibs-bin kdelibs-data kdelibs4 kdelibs4-dev
4 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 18.5MB of archives.


```

hope it's gonna fix Konqueror problems :)


EDIT:

No chances here here the error i get after the upgrade:
```

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  libavcodeccvs libpostproc0 mplayer-386 transcode
The following packages will be upgraded:
  kdelibs-bin kdelibs-data kdelibs4 kdelibs4-dev
4 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 18.5MB of archives.


```

anybody else?

---

### Post by !nkubus on 2005-04-21
Opps there a post about it .

sorry

---

### Post by quigonjim on 2005-04-22
Linux newbie here migrating from SuSE.  When I installed Kubuntu (the second time, the first time I was getting the instabilities and knew less about it), I did the following steps:  Enable universe, upgrade to 686 kernel, installed Nvidia drivers, full upgrade of entire system.  All using apt-get.  When I rebooted, after my Kubuntu login I got a KDE setup screen letting me choose themes etc.  I have the KDE 3.4 default wallpaper on the desktop too.  Seems quite stable.  :)
I hope this is useful to someone.
Thanks!

---

### Post by FISH on 2005-04-23
I had the konqueror crashes as well, so I used Gentoo file manager, and it worked great. I noticed this in the beta and the official release of kubuntu, so I reformatted and installed vanilla Ubuntu which has no noticeable problems

---

### Post by neilius on 2005-05-01
I thought I'd chime in on this one, Konqueror is just not wanting to play, randomly crashing and doing the duplicate icons thing. Does anyone know if this is being worked on? I heard that any upgrades to KDE won't be included until the next release of Kubuntu. Say it ain't so! :(

Regards,

Neil.

---

### Post by escuchamezz on 2005-05-01
so much for being more stable than windows xp...  :---)

---

### Post by Ainvar on 2005-05-01
Yes this makes me a sad panda, but I have faith and hope in the ubuntu/kubuntu teams along with the rest of the linux community in finding and fixing the issue causing this.

I will do the xorg.conf fix when I boot back into ubuntu and load up kde and see what it does on my end. I am also one of the ones having this issue but thought it was due to my ati x300 laptop video card, but then I botted to gnome and it runs smooth and slick (not a gnome fan though).

---

### Post by Gezzer on 2005-05-02
[QUOTE=neilius]I thought I'd chime in on this one, Konqueror is just not wanting to play, randomly crashing and doing the duplicate icons thing. Does anyone know if this is being worked on? I heard that any upgrades to KDE won't be included until the next release of Kubuntu. Say it ain't so! :(

Regards,

Neil.[/QUOTE]

i was having a similar problem with konqueror so i swapped it for Nautilus as my file manager
no more crashes  :smile:  ...

---

### Post by senectus on 2005-06-07
anyone know why there's been no updates on this?

[https://bugzilla.ubuntu.com/show_bug.cgi?id=8009](https://bugzilla.ubuntu.com/show_bug.cgi?id=8009)

It makes like in KDE Uber annoying.

---

### Post by dejitarob on 2005-06-08
> it seems that the bug can be removed if the navigation side panel is closed.This worked for me. After I updated to 3.4.1, I put the nav side panel back and I haven't had a crash or double icons since.

[QUOTE=neilius] I heard that any upgrades to KDE won't be included until the next release of Kubuntu. Say it ain't so! :([/QUOTE]Add 'deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main' to /etc/apt/sources.list and then sudo aptitude update & upgrade.

---

### Post by senectus on 2005-06-08
[QUOTE=dejitarob]Add 'deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main' to /etc/apt/sources.list and then sudo aptitude update & upgrade.[/QUOTE]

so why does kubuntu have it's own repository ?
This strikes me as a bit silly/dangerous/wasteful...

---

### Post by dejitarob on 2005-06-08
Because Ubuntu's policy is to save all major updates, except for security related, for the next official release which will be Breezy. But since JRiddell contributes to KDE he simply packaged them since he's nice I guess. All this is already discussed in the [KDE 3.4.1 release thread](http://ubuntuforums.org/showthread.php?t=38405). Please use the search. Thanks!

---

### Post by senectus on 2005-06-08
[QUOTE=dejitarob]Because Ubuntu's policy is to save all major updates, except for security related, for the next official release which will be Breezy. But since JRiddell contributes to KDE he simply packaged them since he's nice I guess. All this is already discussed in the [KDE 3.4.1 release thread](http://ubuntuforums.org/showthread.php?t=38405). Please use the search. Thanks![/QUOTE]

Hmm I see, perhaps there needs to be a "severity" rating for "non-security" related updates.. so that pretty permanent fixes such as Konq crashing as often as this bug does can be fixed.
The issue seemed to be very wide spread and pretty destructive to usability.

---

### Post by dejitarob on 2005-06-09
I would agree with you. I just was repeating what I read earlier from a mod in that thread. I guess the policy stems from focusing more on the new releases instead of the old ones. Yet in this case, if its already been packaged by a dev I don't understand why it's simply not uploaded into the official ubuntu repos.

---

### Post by senectus on 2005-06-09
[QUOTE=dejitarob]I would agree with you. I just was repeating what I read earlier from a mod in that thread. I guess the policy stems from focusing more on the new releases instead of the old ones. Yet in this case, if its already been packaged by a dev I don't understand why it's simply not uploaded into the official ubuntu repos.[/QUOTE]
Probably due to testing and cross testing requirements..
Thanks for the help btw..

---

### Post by davidgypsy on 2005-07-11
Very helpful thread! Now I know it's not just me! ;-)

---

### Post by -DarkMind- on 2005-07-11
konqueror crash in my machine too...

but not appear any message  :-?

---

### Post by senectus on 2005-07-11
[QUOTE=-DarkMind-]konqueror crash in my machine too...

but not appear any message  :-?[/QUOTE]

Add 'deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main' to /etc/apt/sources.list and then sudo aptitude update & upgrade.

---

### Post by z_pod on 2005-07-11
[QUOTE=senectus]Add 'deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main' to /etc/apt/sources.list and then sudo aptitude update & upgrade.[/QUOTE]
 Hi,

I had the same problem. What I did was to reinstall kubuntu hoary from scratch, to add kde3.4.1 reps to sources.list and to upgrade kde.... no more crashes or errors....

Same thing I did to get rid of a number of crashes in koffice 1.3.5 (now I'm happily running 1.4)

Regards

---

