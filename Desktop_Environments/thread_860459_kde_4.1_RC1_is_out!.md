---
title: "kde 4.1 RC1 is out!"
date: 2008-07-15
forum: Desktop Environments
---

### Post by Naegling23 on 2008-07-15
I keep trying to like kde4.

Its getting better, but the kde4.1 beta2 was still buggy as all heck.  

Is this one any better, or should I still hold out?  Post your thoughts and comments on it.

---

### Post by jlacroix on 2008-07-15
I noticed and reported three bugs after installing it, however it may be because not all of the required packages are updated yet. I recommend to stay away from RC1 until tomorrow, by then everything should be in the repos. (Every time I think it's fully updated, another ten or so packages appear).

---

### Post by Rbust0 on 2008-07-16
I agree completely.  I spent most of the evening in a dependency hell and still can't get plasma to not crash on me after upgrading earlier today.

Wait a day or so, hopefully everything in the repos will be updated to what it needs be tomorrow sometime.

---

### Post by silverpig on 2008-07-16
It seems to work okay for me. I was really looking forward to kwin's cube plugin but it's not there for me... maybe it wasn't updated yet.

---

### Post by jlacroix on 2008-07-16
I know that kdeplasma-addons isn't in the repos yet.

I filed a bug about the plasma crashes, and the reason for the crashes was that I had the kdeplasmoids package installed which isn't used anymore, they are not binary compatible per Aaron Seigo. The replacement is kdeplasma-addons. So if you have those old playground/kdeplasmoids packages installed, remove them and install kdeplasma-addons when it becomes available and that should fix the crashes if you are experiencing any.

---

### Post by GeneralZod on 2008-07-16
> **silverpig said:**
> It seems to work okay for me. I was really looking forward to kwin's cube plugin but it's not there for me... maybe it wasn't updated yet.

The cube plugin won't be part of 4.1 as it missed the feature freeze.

---

### Post by silverpig on 2008-07-16
> **GeneralZod said:**
> The cube plugin won't be part of 4.1 as it missed the feature freeze.

Ahh, thanks. It's the only thing I'm really missing right now.

---

### Post by stevebakerj on 2008-07-16
> **jlacroix said:**
> I know that kdeplasma-addons isn't in the repos yet.

I filed a bug about the plasma crashes, and the reason for the crashes was that I had the kdeplasmoids package installed which isn't used anymore, they are not binary compatible per Aaron Seigo. The replacement is kdeplasma-addons. So if you have those old playground/kdeplasmoids packages installed, remove them and install kdeplasma-addons when it becomes available and that should fix the crashes if you are experiencing any.

What is the Bug no.

I'm having the same problem myself but removing kdeplasmoids doesn't seem to be the fix for me.

---

### Post by jlacroix on 2008-07-16
> **stevebakerj said:**
> What is the Bug no.

I'm having the same problem myself but removing kdeplasmoids doesn't seem to be the fix for me.

You need to remove all previous packages, such as playground or kdeplasmoids **AND** install kdeplasma-addons, which isn't in the repositories yet. Without installing kdeplasma-addons there won't be a difference as far as I've been able to tell.

Regardless, the bug I reported is below, see if it matches your crashes and if not post a new bug:

[http://bugs.kde.org/show_bug.cgi?id=166666](http://bugs.kde.org/show_bug.cgi?id=166666)

---

### Post by GeneralZod on 2008-07-16
> **silverpig said:**
> Ahh, thanks. It's the only thing I'm really missing right now.

Maybe it will appear on kde-apps.org before 4.2 - you never know :) It was merged into KDE4 trunk yesterday, so all being well, it will be in 4.2, at least.

---

### Post by inktomi7 on 2008-07-16
I updated yesterday evening and when I log in I get a terminal window in the upper left corner. I tried to login in XFCE and I'm getting the same.

The only visible problem is that kde-icons-oxygen is not being installed for some reason. I tried to remove kdeplasmoids as suggested but it's not possible because first it tries to install kde-icons-oxygen but stops because it says *broken pipe*. Anyone got this problem?

---

### Post by stevebakerj on 2008-07-16
> **jlacroix said:**
> You need to remove all previous packages, such as playground or kdeplasmoids **AND** install kdeplasma-addons, which isn't in the repositories yet. Without installing kdeplasma-addons there won't be a difference as far as I've been able to tell.

Regardless, the bug I reported is below, see if it matches your crashes and if not post a new bug:

[http://bugs.kde.org/show_bug.cgi?id=166666](http://bugs.kde.org/show_bug.cgi?id=166666)

I removed kdeplasmoids, kdeplasmoids-data & kdeplasmoids-libs4, I killed plasma. I then removed plasma-appletsrc from /home/uname/.kde4/share/config, restarted plasma and now plasma loads on startup. Will await kdeplasma-addons.

kdeplasma-addons now in the repos :biggrin:

---

### Post by t_k on 2008-07-16
KDM won't start anymore :(

[https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/248773](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/248773)

***cannot open theme file @@@tobereplacedbydesktopbase@@@***

---

### Post by silverpig on 2008-07-16
> **t_k said:**
> KDM won't start anymore :(

[https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/248773](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/248773)

***cannot open theme file @@@tobereplacedbydesktopbase@@@***

I get the same thing. I was kinda stuck until I fell back onto GDM.

---

### Post by Derviansoul on 2008-07-16
Hello

Everything works fine for me, i can finally resize and move panel around and so, phonon crashes at the startup all the time,giving me an annoying message, desktop grid won't still work properly with my dual monitor. it's allot more stable than before, but not there yet.
But what caused some disappoint to me, was the fact that kde4 it's getting chunky and slow, allot slow than at it's very first version 4.0:(, did anyone notice the same?
It's getting there but still not quite there yet for me:).
regards

---

### Post by RabidDawgr on 2008-07-16
Maybe I should warn those that use nvidia graphics.

Due to some performance problems with nvidia cards in 8000/9000 series especially, kde 4.1 will feel really quite slow. This will be for resizing windows, plasma (and most of all folderview), and in some cases scrolling. 

setting this 
```

nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1 
```

might mitigate the slowness somewhat but it wont conclusively fix it. (note that glyph cache is for 8 series and above, while ipp works for 7 series too).

also those with laptops might consider turning off powermizer (warning: could lead to overheating)

---

### Post by t_k on 2008-07-16
I used the whole day to get the system up and running again.

Found some stuff in these threads:
[http://kubuntuforums.net/forums/index.php?topic=3096121.0](http://kubuntuforums.net/forums/index.php?topic=3096121.0)
[http://kubuntuforums.net/forums/index.php?topic=3095395.msg135525#msg135525](http://kubuntuforums.net/forums/index.php?topic=3095395.msg135525#msg135525)

I then could get KDM up and running again, but when i logged in the ATI Catalyst 8.6 drivers was all buggered up and i got a black screen only.

I found a backup of the xorg.conf file and used that one. I then had to force the 8.6 drivers with: sudo aticonfig --initial -f
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1 (i have no idea why the ATI drivers buggered out)

Then i forced an sudo apt-get update, sudo apt-get upgrade to overwrite KDM and i now have the lovely new login window and the system up and running again at RC1! :)

---

### Post by TheUnabeefer on 2008-07-16
I removed and then reinstalled all of kde4 and then started with a fresh .kde4 directory (mine was a mess from all my fiddling with things before I settled on how I like things, so it seemed a good idea) and it works wonderfully for me.  Sure, it was a bit extreme and I doubt I had to do all of that, but I wanted to try RC1 fresh, without any old prefs messing anything up.

I still find KDE4 to be much more Compiz friendly than even Gnome is, btw.

---

### Post by Rbust0 on 2008-07-18
> **inktomi7 said:**
> I updated yesterday evening and when I log in I get a terminal window in the upper left corner. I tried to login in XFCE and I'm getting the same.

The only visible problem is that kde-icons-oxygen is not being installed for some reason. I tried to remove kdeplasmoids as suggested but it's not possible because first it tries to install kde-icons-oxygen but stops because it says *broken pipe*. Anyone got this problem?

Check the output again.  I had to remove the kdepim-kde4 package as there was an issue between the two of them.

[QUOTE=stevebakerj]I removed kdeplasmoids, kdeplasmoids-data & kdeplasmoids-libs4, I killed plasma. I then removed plasma-appletsrc from /home/uname/.kde4/share/config, restarted plasma and now plasma loads on startup. Will await kdeplasma-addons.[/QUOTE]

I've discovered plasma will crash whenever it trys to load any plasmoid that is no longer compatible with it.  In my case, it was the weather plasmoid I obtained from kde-look.org that kept causing my error.  After I removed plasma-appletsrc (Hence telling plasma not to load that plasmoid anymore), it worked just fine.  Hope this helps.

---

