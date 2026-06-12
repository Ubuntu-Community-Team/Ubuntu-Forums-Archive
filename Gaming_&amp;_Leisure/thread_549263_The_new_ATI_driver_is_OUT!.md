---
title: "The new ATI driver is OUT!"
date: 2007-09-12
forum: Gaming &amp; Leisure
---

### Post by Hooloovooloo on 2007-09-12
Get it here!
[http://www2.ati.com/drivers/linux/ati-driver-installer-8.41.7-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-8.41.7-x86.x86_64.run)

More info:
[http://wiki.cchtml.com/index.php/8.41](http://wiki.cchtml.com/index.php/8.41)

Sorry, this is all i could find so far.

EDIT:
I was thinking a little and i figures some of you may wonder what this thread is doing in the gaming forum. Wouldn't it fit better somewhere else?
The way i see it - no. ATI have said themselves that this driver is not to recomend for other users than those who use the r600 chip, _however_ this driver gives one helluva boost for 3d rendering.
That means i don't think that you should install it unless you know what you are doing and want to use it to get better performance in games. Otherwise wait for the next driver coming out next month which will probably be a lot more stable. It will also include support for a lot mor video cards _and_... AIGLX support!

I hope you get my point. Don't install unless you really want to and know how to do it.

---

### Post by tatrefthekiller on 2007-09-12
Doesn't work for me :
Install with --buildpkg.
X700 Pro mobility
Ubuntu Feisty all up to date.

I got this :

fglrx Incompatible kernel module detected HW accelerated OpenGL will not work.
fglrx : QS connection has not been initialized.

---

### Post by Hooloovooloo on 2007-09-12
> **tatrefthekiller said:**
> Doesn't work for me :
Install with --buildpkg.
X700 Pro mobility
Ubuntu Feisty all up to date.

I got this :

fglrx Incompatible kernel module detected HW accelerated OpenGL will not work.
fglrx : QS connection has not been initialized.

Hmm... Follow this guide, but replace the filenames with the one of the current driver. Worked excellent for me.

---

### Post by pheonixind on 2007-09-12
I think I may wait for this until it's a bit more tested out.  Is this the new open driver or the proprietary one?

---

### Post by tatrefthekiller on 2007-09-12
I'll try again more carefully. What's your video card ? Do you see some performance improvements ?
Take a look at this : [http://www.x.org/docs/AMD/](http://www.x.org/docs/AMD/)

---

### Post by hikaricore on 2007-09-12
> **pheonixind said:**
> I think I may wait for this until it's a bit more tested out.  Is this the new open driver or the proprietary one?

If you'd look where it is... ati.com

---

### Post by tolstoyboy on 2007-09-12
i've been checking the ati website...and they don't show the new driver posted....

---

### Post by hikaricore on 2007-09-12
It's possible they havn't announce it publicly yet.  *shrug*

---

### Post by Sparckus on 2007-09-12
Only shows up if you select a 2xxx series card for driver download, they also say that people with cards other than 2xxx shouldnt install it because of stability issues.

:/

---

### Post by Hooloovooloo on 2007-09-12
> **tatrefthekiller said:**
> I'll try again more carefully. What's your video card ? Do you see some performance improvements ?
Take a look at this : [http://www.x.org/docs/AMD/](http://www.x.org/docs/AMD/)

Huge improvements. I don't think anyone playing games on ubuntu should care that ATI doesn't recomend it. My FPS in Savage was more than doubled.

---

### Post by tolstoyboy on 2007-09-12
I think this article should clarify a few things; many of us are waiting for 8.42...this should be the release that stirs the water more than 8.41. It will provide support for many of the cards we use in notebooks...

[http://www.phoronix.com/scan.php?page=article&item=827&num=1](http://www.phoronix.com/scan.php?page=article&item=827&num=1)

---

### Post by KushMaster on 2007-09-12
I have a ATI Radion 1300x , will this new driver release apply to my video card ? Should i d/l the driver ?

---

### Post by Hooloovooloo on 2007-09-12
> **KushMaster said:**
> I have a ATI Radion 1300x , will this new driver release apply to my video card ? Should i d/l the driver ?

It will apply to your video card, yes. I think you should download it if you feel that you need more speed while playing games and are comfortable with installing and possibly fixing anything that may go wrong.

---

### Post by Kowalski_GT-R on 2007-09-12
Hi all,

I'm following this instructions here: [https://help.ubuntu.com/community/InstallingRunPackage](https://help.ubuntu.com/community/InstallingRunPackage)

but installer says I must run the installer as 
superuser

what am I missing here?

---

### Post by hardyn on 2007-09-12
has anybody applied for a package exception with gutsy?

This seems like something that should be in the gutsy release.

cheers.

---

### Post by garnie on 2007-09-12
> **Kowalski_GT-R said:**
> Hi all,

I'm following this instructions here: [https://help.ubuntu.com/community/InstallingRunPackage](https://help.ubuntu.com/community/InstallingRunPackage)

but installer says I must run the installer as 
superuser

what am I missing here?

you need to do as super user aka sudo 

so run in a terminal like this 

sudo sh "ati-driver"

and it should work

---

### Post by Kowalski_GT-R on 2007-09-12
> **garnie said:**
> you need to do as super user aka sudo 

so run in a terminal like this 

sudo sh "ati-driver"

and it should work


mmmmhhh.....not quite clear.

I get the Sudo part , then do I have to cd to the directory I put the file in?

thanks

---

### Post by srozzman on 2007-09-12
no, you have to cd there 1st, then sudo sh "filename" 

anyway... i tried installing these on my computer... big failure.... watch out if you have a x1650pro.

Cant boot x, i did "sudo aticonfig --initial -f" etc.  then i saw it thinks im using an intel driver.. gotta check that out later.

---

### Post by Sparckus on 2007-09-12
Ive got an X1600, same thing happened.

Removed driver, X still wouldnt start, uninstalled then reinstalled fglrx with apt-get then X started again :o

8.42 for us then lol

---

### Post by Kowalski_GT-R on 2007-09-12
> **srozzman said:**
> no, you have to cd there 1st, then sudo sh "filename" 

anyway... i tried installing these on my computer... big failure.... watch out if you have a x1650pro.

Cant boot x, i did "sudo aticonfig --initial -f" etc.  then i saw it thinks im using an intel driver.. gotta check that out later.

thanks for the info!

Andre

---

### Post by dynamethod on 2007-09-12
im running a ATI X800 XT 256mb, and the new driver doesnt make a hell of a difference, infact kinda glitchy, really really minor glitches like mouse over go's a little odd shape, apart from that nothing special

still cant run compiz-fusion with it :S

---

### Post by Ferrat on 2007-09-12
> **dynamethod said:**
> im running a ATI X800 XT 256mb, and the new driver doesnt make a hell of a difference, infact kinda glitchy, really really minor glitches like mouse over go's a little odd shape, apart from that nothing special

still cant run compiz-fusion with it :S

compiz will be in the 8.42 release probably that has been said almost from the get go, I got some issues but the FPS on glxgears has gone up like 70% for me, altho wine doesn't find the 3d acc. so reinstalling that and testing again

---

### Post by srozzman on 2007-09-12
just reinstalled my linux, and now the new driver installed, though i cannot open CCC.  However, i have not yet tried to aticonfig, because i am afraid of another failure

---

### Post by quadomatic on 2007-09-12
Anyone with an X850 PRO VIVO PCI-Express try this driver?

I want to try it, but I'm afraid of the instability issues.

---

### Post by Burkey on 2007-09-12
I ran some tests before and after the new driver.. I am seeing a 30% boost in performance on my laptop.  ATi X1400 video card and Core Duo CPU.

I also notice a lot of changes in extensions including support for a WGL extension for buffer swap control.  This is a bit of a gaming related extension change.  Sadly I still see no support for YUV textures and really hope ATi adds that.  This is available in the MAC drivers so no reason for linux to not have it btw.

I am very happy!  It made OpenArena VERY smooth as well as my own OpenGL apps.  Looking forward to whats next with ATi/AMD.  big thnkas to AMD, you guys rock.

Also, the CCC works fine for me, not that it matters since it has nothing useful in there really.  Maybe some more polish will go into that as well as some features.

hope to test WoW under both Wine and Cedega with it over the weekend.

---

### Post by dan_linder on 2007-09-13
> **tatrefthekiller said:**
> 
I got this :
fglrx Incompatible kernel module detected HW accelerated OpenGL will not work.
fglrx : QS connection has not been initialized.

I was getting that too.  Try this:
1: Become root / superuser:
```
sudo -i
```
2: Backup your existing /etc/X11/xorg.conf:
```
cd /etc/X11/
cp xorg.conf xorg.conf.orig
```
3: Re-run the ATI configuration utility with the "--initial" option:
```
aticonfig --initial 
```
For some reason my hand-tuned xorg.conf file had something in it that the new ATI driver didn't like.

Dan

---

### Post by xdarkday on 2007-09-13
woot

---

### Post by tatrefthekiller on 2007-09-13
Thanks, I didn't do the aticonfig --initial, because last time, it broke my xorg.conf.
Now it works :
radeon : 2000 fps / 40% proc use
fglrx 8.41 : 4000 fps / 100% proc use.

I don't know if it's better or not...

---

### Post by Golyadkin on 2007-09-13
> **Sparckus said:**
> Ive got an X1600, same thing happened.

Removed driver, X still wouldnt start, uninstalled then reinstalled fglrx with apt-get then X started again :o

8.42 for us then lol


I have the same error with an X1650XT, can't start X at all. Will now go and try removing this driver.


Dan's steps didn't help. The X server still can't boot, with the same error.

***How can I remove this package?***

---

### Post by Sparckus on 2007-09-13
> **Golyadkin said:**
> I have the same error with an X1650XT, can't start X at all. Will now go and try removing this driver.


Dan's steps didn't help. The X server still can't boot, with the same error.

***How can I remove this package?***


Im at work, cant remember exactly but try

cd /usr/share/ati
ls and look for fgrlx uninstaller
sudo sh it
apt-get remove the xorg driver
apt-get install the xorg driver
startx

thats what i did to get it working, cant remember the exact file/package names but just to an apt-cache search for fglrx

---

### Post by Kowalski_GT-R on 2007-09-13
> **srozzman said:**
> 
anyway... i tried installing these on my computer... big failure.... watch out if you have a x1650pro.

Cant boot x

same for me,

X screwed up big time.....

---

### Post by cmat on 2007-09-13
I'm waiting for the packages to be out in the repos before I install them. I wonder I fi can get compiz-fusion working on my laptop now.

---

### Post by misfitpierce on 2007-09-13
Guess i'll just wait till its officially released for my card on site or just wait for 8.42. Either way :)

---

### Post by Slamtotten on 2007-09-17
Hey everyone

I am getting an error message when i try to install this driver.
I have Feisty, up-to-date and an mobility x600 card.

Here is the error output.
```
Generating package: Ubuntu/feisty
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.41.7-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 8.41.7-1
 debian/rules build
echo "Using architecture: i386"
Using architecture: i386
if [ -f /tmp/fglrx.n13964/debian/control.template ]; then \
                cat /tmp/fglrx.n13964/debian/control.template > /tmp/fglrx.n13964/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.n13964/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/feisty/" /tmp/fglrx.n13964/debian/driver.$i > \
              /tmp/fglrx.n13964/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.n13964/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.n13964/debian/10fglrx.template > /tmp/fglrx.n13964/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.n13964/debian/fglrx.default ]; then \
          mv /tmp/fglrx.n13964/debian/fglrx.default /tmp/fglrx.n13964/debian/fglrx; \
        fi
dh_testdir
make: dh_testdir: Command not found
make: *** [configure] Error 127
Removing temporary directory: fglrx-install.k13885

```

i have tried this with both --buildpkg Ubuntu/feisty and Ubuntu/7.04 (I honestly don't know the difference, and im probably in over my head trying to do this)
but any help would be greatly appreciated.

Thank you.

---

### Post by Jadephyre on 2007-09-19
this driver is supposedly ONLY for the x2000 Series of ATI Cards... all others are bound to run into Problems.
Read the News on Phoronix some time... all the Info is there.
All other Cards will get their support back with the 8.42 Version.
So, if you have anything below a 2000 Series Card, stay with the 8.40 or lower.

---

### Post by MadMan2k on 2007-09-19
> **Slamtotten said:**
> 
i have tried this with both --buildpkg Ubuntu/feisty and Ubuntu/7.04 (I honestly don't know the difference, and im probably in over my head trying to do this)
but any help would be greatly appreciated.

Thank you.

apt-get install debhelper

---

