---
title: "[ How To] Installing Screenlets"
date: 2008-02-04
forum: Desktop Effects &amp; Customization
---

### Post by jryprt on 2008-02-04
[COLOR="Red"]**EDIT:  Older Versions 0.0.10   SCREENLETS **[/COLOR]   The new Screenlets New Bzr 0.0.12 I found it buggy.
**_[COLOR="Red"]If you get Errors Please make a new Thread & Post the Errors someone will help I do not know how to troubleshoot Screenlets Thank You[/COLOR]_**

The OLD way of Ubuntu installation:

            Go to System -> Administration -> Synaptic Package Manager and open up Settings -> Repositories. In the tab 'Third-Party Software' press the 'Add' button. 
            In the dialog window enter one of these lines: 
            deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) edgy screenlets 
            deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) feisty screenlets 
            deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) gutsy screenlets 
            depending on your version of Ubuntu. Close Synaptic Package Manager. 
            Then press alt+F2 and in the dialog enter: 
            wget [http://download.tuxfamily.org/screenlets/hendrikkaju.gpg](http://download.tuxfamily.org/screenlets/hendrikkaju.gpg) -O- | sudo apt-key add - 
            After pressing the 'reload' button in the Synaptic Package Manager you should find the package named 'screenlets' (not Bzr 0.0.12) in the :::list. Mark it for installation and apply!
[B][U][COLOR="Red"]If you get errors after "sudo apt-get update"  use [This repository](http://hendrik.kaju.pri.ee/ubuntu/)
[/COLOR][/U][/B]
Go To System ->Preferences &#8211;> Screenlets  choose the screenlet you want click launch/add (you can choose Auto start on login)

3rd party screenlets or Gnome-Look.org  screenlets you need to Manually install.

1. Make .screenlets directory. In the Terminal ```
mkdir -p ~/.screenlets
```
2. Download .tar.gz to your Desktop 
3. Right click the .tar.gz & hit Extract Here
4. Open home directory , then hit Ctrl+h to see hidden folders
 look for .screenlets folder open it.
5. Drag or copy the .tar.gz into the .screenlets folder.

Go To System ->Preferences &#8211;> Screenlets  choose the screenlet you want click launch/add (you can choose Auto start on login)

3rd party screenlets [Here](http://www.screenlets.org/index.php/Category:UserScreenlets)

Gnome-Look.org  screenlets [Here]( http://www.gnome-look.org/index.php?xcontentmode=6700&PHPSESSID=6b2bd26304210ffc06cfdc857f45367c)

**_[COLOR="Red"]Please post a message after to bump it to the top for others to see in case they want it too.[/COLOR]_**

---

### Post by ayoli on 2008-02-04
Does it install the last version of screenlet 0.0.12 I saw here ; [http://ubuntuforums.org/showthread.php?t=672548](http://ubuntuforums.org/showthread.php?t=672548) ?

---

### Post by jryprt on 2008-02-04
> **ayoli said:**
> Does it install the last version of screenlet 0.0.12 I saw here ; [http://ubuntuforums.org/showthread.php?t=672548](http://ubuntuforums.org/showthread.php?t=672548) ?

The Synaptic Package Manager said its is.

---

### Post by ayoli on 2008-02-04
> **jryprt said:**
> The Synaptic Package Manager said its is.

ok, thank you for this info.

---

### Post by jryprt on 2008-02-05
I Edited the post the new one was buggy for me , the old one works fine.

---

### Post by ayoli on 2008-02-05
Maybe this official package of screenlets 0.12 is more stable than the one in the tuxfamily repos from the first post.
Found in this thread [http://forum.compiz-fusion.org/showthread.php?t=6889](http://forum.compiz-fusion.org/showthread.php?t=6889) section ubuntu 2b.
The instructions also said to remove first the old screenlets stuff.

---

### Post by jryprt on 2008-02-05
> **ayoli said:**
> Maybe this official package of screenlets 0.12 is more stable than the one in the tuxfamily repos from the first post.
Found in this thread [http://forum.compiz-fusion.org/showthread.php?t=6889](http://forum.compiz-fusion.org/showthread.php?t=6889) section ubuntu 2b.
The instructions also said to remove first the old screenlets stuff.

I tried 2 diff. guides both said to remove all the stuff , I did but still buggy for me so I removed all the stuff again used the older one its stable , some if not all the new screenlets are in the 3rd party or gnome-look.org

---

### Post by spyder850 on 2008-02-08
thanks guys! this thread really helped getting my widgets up and running.

Thanks again!:)

---

### Post by crazyjake on 2008-03-14
BAH!!!

i am relatively new to Linux so forgive me for being stupid...

when i update the third party resources in Synaptic and hit Reload, this message comes up after it "downloads" the packages.

[http://download.tuxfamily.org/screenlets/dists/gutsy/screenlets/binary-i386/Packages.gz:](http://download.tuxfamily.org/screenlets/dists/gutsy/screenlets/binary-i386/Packages.gz:) 404 Not Found

when i went to go investigate the site the screenlet directory was modified "2008-Feb-09 11:10:04"

did they take this down? and if so, is there another one i can use? :confused:

thanks

---

### Post by ayoli on 2008-03-14
> **crazyjake said:**
> BAH!!!

i am relatively new to Linux so forgive me for being stupid...

when i update the third party resources in Synaptic and hit Reload, this message comes up after it "downloads" the packages.

[http://download.tuxfamily.org/screenlets/dists/gutsy/screenlets/binary-i386/Packages.gz:](http://download.tuxfamily.org/screenlets/dists/gutsy/screenlets/binary-i386/Packages.gz:) 404 Not Found

when i went to go investigate the site the screenlet directory was modified "2008-Feb-09 11:10:04"

did they take this down? and if so, is there another one i can use? :confused:

thanks
you may want to try this one : [http://www.getdeb.net/release.php?id=2128](http://www.getdeb.net/release.php?id=2128)

---

### Post by crazyjake on 2008-03-14
AWESOME!!!!!! :KS

that worked perfectly!! after a little fiddling i got my wallpaperclock to work! thanks man!

---

### Post by ayoli on 2008-03-14
> **crazyjake said:**
> AWESOME!!!!!! :KS

that worked perfectly!! after a little fiddling i got my wallpaperclock to work! thanks man!

you're most welcome :)

---

### Post by WFGeppetto on 2008-03-19
Well, this all looks simple enough, and I know I had it working on an earlier install, but the repository doesn't seem to be working right now.

I double, and triple checked the line, I don't see how I could have gotten it wrong, but when I 'reload', it says that the "following repository was not found" and lists the screenlets repository.

When I open Software Resources, and edit the line, this is the URL, copied and pasted from my Sources:

> [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets)
That is exactly as it appears.  Is there something wrong with my source line, or is the repository down at the moment?

---

### Post by ayoli on 2008-03-19
> **WFGeppetto said:**
> Well, this all looks simple enough, and I know I had it working on an earlier install, but the repository doesn't seem to be working right now.

I double, and triple checked the line, I don't see how I could have gotten it wrong, but when I 'reload', it says that the "following repository was not found" and lists the screenlets repository.

When I open Software Resources, and edit the line, this is the URL, copied and pasted from my Sources:


That is exactly as it appears.  Is there something wrong with my source line, or is the repository down at the moment?

This repos is doown, latest screenlet package can be found here :
[http://www.getdeb.net/release.php?id=2309](http://www.getdeb.net/release.php?id=2309)

---

### Post by WFGeppetto on 2008-03-20
Ah, thank you very much!

---

### Post by wootah on 2008-05-29
Older thread, newer repos (?)
```
deb http://ppa.launchpad.net/gilir/ubuntu gutsy main universe
```

EDIT: Linky -> ([http://forum.compiz-fusion.org/showthread.php?t=6889](http://forum.compiz-fusion.org/showthread.php?t=6889))

---

