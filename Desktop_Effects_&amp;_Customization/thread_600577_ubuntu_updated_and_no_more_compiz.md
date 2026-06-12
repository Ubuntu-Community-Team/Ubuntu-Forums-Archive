---
title: "ubuntu updated and no more compiz"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by salvadorveiga on 2007-11-02
Well the update manager icon was flashing so i just installed the new updates and now i have no compiz... well i do have i think but it's like basic compiz since there is no wobbly windows or anything... my previous settings are gone...and if i try to go to CCSM it doesn't do anything... this is what appears when i type "compiz --replace":
```
salvador@quarto-salvador:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5960 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator


```

that's it... what else can I do to have compiz normal again ? thanks

---

### Post by Zorael on 2007-11-02
```
$ glxinfo | grep rendering
```

Also, what does starting ccsm from a terminal output?

---

### Post by amphet on 2007-11-02
I have the same problem after today's updates

```

yeyo@mushroom:~$ glxinfo | grep rendering
direct rendering: Yes

```

---

### Post by jonray74 on 2007-11-02
I think you need to install the XGL server by doing:

sudo apt-get install xserver-xgl

cause it says Checking XGL: not present

hope that helps

:)

---

### Post by salvadorveiga on 2007-11-02
well i didnt have the xgl server before and it worked just fine... at least i think i didn't have since compiz worked out of the box...all i did was install the CCSM and 3D windows plugin... but after today's updates (which had some compiz updates in it - I checked) it doesn't work... I believe it's working somethings because whenever i open an application the zoom effects are there aswell the Wall Plugin, and also if I click Super+Mouse I can get the Zoom to work so I guess compiz is working at some extent... anything else is not working... i'll try your tips when i get to my computer thanks

---

### Post by Zorael on 2007-11-02
If all else fails, try completely removing and reinstalling. Just make sure you don't have any weird repositories that might screw things up.

```
$ sudo apt-get update
$ sudo apt-get **purge** compiz* libcompiz* libdeco* emerald* libemerald*
```

---

### Post by amphet on 2007-11-02
> **Zorael said:**
> If all else fails, try completely removing and reinstalling. Just make sure you don't have any weird repositories that might screw things up.

```
$ sudo apt-get update
$ sudo apt-get **purge** compiz* libcompiz* libdeco* emerald* libemerald*
```

that worked for me, thanks.

---

### Post by salvadorveiga on 2007-11-02
> **amphet said:**
> that worked for me, thanks.

what's the purge command for ?

 I just removed everything related to compiz and I also removed the xserver-xgl (I didn't have it at first) because it made my computer TOO SLOW ... I am now running only on metacity but on my way to install compiz... Should I just install compiz and the dependencies will install automatically ?

---

### Post by Zorael on 2007-11-02
Purge works like remove, only it also removes configuration files. This does not include files stored in the Gnome/KDE Backend, or in configuration files in your home directory, so your Compiz profile - for instance - will not be removed. It's equavilent to the 'complete removal' option in Synaptic.

As for installing Compiz, it depends on what window manager you're using. The compiz package has compiz-core, compiz-plugins, compiz-gnome, compiz-fusion-plugins-main, compiz-fusion-plugins-extra, and libcompizconfig0 as its dependencies.

Obviously, if you're running KDE, you don't need compiz-gnome, in which case you're better off picking the packages one by one and **including compiz-kde**.

Furthermore, there *are* some Compiz-related packages not included in the compiz bundle. For instance, the settings manager!

Ubuntu/Gnome:
```
$ sudo apt-get install compiz compizconfig-settings-manager compiz-extra compiz-bcop
```
Kubuntu/KDE:
```
$ sudo apt-get install compiz-core compiz-plugins compiz-fusion* compizconfig-settings-manager compiz-extra compiz-bcop compiz-kde libcompizconfig0
```

Likely specifying some of those packages would be redundant, as they're at some level dependent of eachother, but meh.

If you want Emerald ontop of that, just install it normally.

But again, mind your repositories, especially if you upgraded. You'll want to take extra care to make sure the Compiz/Emerald you're installing is the one from the official repositories. The other ones might work, but then again, they might not. And if you're on the official ones, we can (sort of/sometimes/once in a blue moon) help.

---

### Post by salvadorveiga on 2007-11-02
> **Zorael said:**
> Purge works like remove, only it also removes configuration files. This does not include files stored in the Gnome/KDE Backend, or in configuration files in your home directory, so your Compiz profile - for instance - will not be removed. It's equavilent to the 'complete removal' option in Synaptic.

As for installing Compiz, it depends on what window manager you're using. The compiz package has compiz-core, compiz-plugins, compiz-gnome, compiz-fusion-plugins-main, compiz-fusion-plugins-extra, and libcompizconfig0 as its dependencies.

Obviously, if you're running KDE, you don't need compiz-gnome, in which case you're better off picking the packages one by one and **including compiz-kde**.

Furthermore, there *are* some Compiz-related packages not included in the compiz bundle. For instance, the settings manager!

Ubuntu/Gnome:
```
$ sudo apt-get install compiz compizconfig-settings-manager compiz-extra compiz-bcop
```
Kubuntu/KDE:
```
$ sudo apt-get install compiz-core compiz-plugins compiz-fusion* compizconfig-settings-manager compiz-extra compiz-bcop compiz-kde libcompizconfig0
```

Likely specifying some of those packages would be redundant, as they're at some level dependent of eachother, but meh.

If you want Emerald ontop of that, just install it normally.

But again, mind your repositories, especially if you upgraded. You'll want to take extra care to make sure the Compiz/Emerald you're installing is the one from the official repositories. The other ones might work, but then again, they might not. And if you're on the official ones, we can (sort of/sometimes/once in a blue moon) help.

yes i'm installing from the official repos... they have ubuntu symbols next to them on synaptic... anyways I removed and installed compiz again.... everything regarding compiz was removed and i installed it again and the problem persists... Like before some plugins are working as ZOOM, WALL PLUGIN, ANIMATIONS, since I can use them through key shortcuts... but the CCSM still remains I have no access this is what I get when doing CCSM from terminal

```
salvador@quarto-salvador:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
salvador@quarto-salvador:~$ 

```

any ideas what this would be ?thanks

---

### Post by salvadorveiga on 2007-11-02
Solved... got it working again... i guess it was some config files that got behind from the removal so I just deleted everything... and it is working now...

by the way, my firefox fonts are too small what can I do? I already unchecked "allow websites to use their fonts" my firefox configuration is pretty much the same as firefox in windows but still there are some fonts too small like the one I am writing right now... it's small, and it looks "broken" as if some pixels were missing... I already messes around on Appearance Fonts but it seems to have no effect on firefox... is it some configuration under "ABOUT:CONFIG" ? if so can someone help me out...

thank you

---

### Post by mrmiserable on 2007-11-02
also check /usr/bin/compiz for whitelist and add fglrx if you use ati 8.42.3 driver

---

### Post by Ragnar Bocephus on 2007-11-02
> **mrmiserable said:**
> also check /usr/bin/compiz for whitelist and add fglrx if you use ati 8.42.3 driver

This worked for me.  Apparently the update restored /usr/bin/compiz to the original, so both fglrx and my card were blacklisted again.  Simple enough fix.  Thanks for the tip!

---

### Post by salvadorveiga on 2007-11-03
> **mrmiserable said:**
> also check /usr/bin/compiz for whitelist and add fglrx if you use ati 8.42.3 driver

i'm not using proprietary drivers from ATI..though I have one question... I have a Radeon 9200 128 MB, should I download the ATI driver or stick with the Open Source "radeon" instead ?

i think I have the open source one... how can i check which one I have '

---

### Post by eg0n on 2007-11-03
After the last update I had a different problem. I think that compiz is running ok but everything is TOO slow. I used synaptic manager to completely remove it and then reinstall it again but nothing changed.  I 've turned off any visual effects but still I notice the same problem. Any ideas for what's wrong?

---

### Post by pienose on 2007-11-03
I am having the same problem, compiz updated and stoped working. I have tried removing all the compiz and emerald pacages, then reinstalling but all to no avail. Help!

---

### Post by dentaku65 on 2007-11-03
> **salvadorveiga said:**
> 
```
salvador@quarto-salvador:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
salvador@quarto-salvador:~$ 

```

any ideas what this would be ?thanks

Try:
```
sudo rm /usr/bin/ccsm
```

then:
```
sudo apt-get install --reinstall compizconfig-settings-manager
```

then from the console try again:
```
ccsm
```

---

### Post by Neo4 on 2007-11-04
after the update my compiz stopped working too!

I have the new driver installed
composite and aiglx enabled on the xorg.conf file
whitelisted fglrx on the compiz-manager but when I run conpiz it says:

compiz
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

i don't want xgl i want to run compiz from aiglx...
any idea?

thanks
_________________

---

### Post by features on 2007-11-04
> **mrmiserable said:**
> also check /usr/bin/compiz for whitelist and add fglrx if you use ati 8.42.3 driver


That solution also worked for me :)  Sneaky sneaky...

---

### Post by mrmiserable on 2007-11-04
neo4

compiz
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

just do this in terminal

sudo gedit /usr/bin/compiz
password
you should see this on line 54

 
# Driver whitelist
WHITELIST="nvidia intel ati radeon i810"

change to this

# Driver whitelist
WHITELIST="nvidia intel ati radeon fglrx i810"

restart compiz

hope this helps

---

### Post by Zaneyard on 2007-11-04
I am having a problem where I cannot start Compiz either
It worked on the live CD but once i got everything updated on my HDD it gives me this error when I goto Visual Effects in the appearance preferences box and click anything other than none "The Compisite Extension is not available."
I am using my prop. drivers for my Radeon X300

---

### Post by Zaneyard on 2007-11-04
I just restarted and it worked.
I think it had something to do with my session. I remember my curser turning into an x for a moment during startup when it flickers back when I had feisty on my computer.
though I did do a combination of the commands on the first page of this post, they may or may not have helped
I mostly uninstalled it and reinstalled it so if that helps.

---

### Post by Neo4 on 2007-11-04
> **mrmiserable said:**
> neo4

compiz
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

just do this in terminal

sudo gedit /usr/bin/compiz
password
you should see this on line 54

 
# Driver whitelist
WHITELIST="nvidia intel ati radeon i810"

change to this

# Driver whitelist
WHITELIST="nvidia intel ati radeon fglrx i810"

restart compiz

hope this helps


already done that with no sucess =/
and in the /etc/xdg/compiz/compiz-manager if I have more whithelisted cards after fglrx this is what happen when do compiz --replace:

compiz --replace
/etc/xdg/compiz/compiz-manager: 7: nvidia: not found
Checking for Xgl: not present. 
Blacklisted PCIID '1002:5653' found 
aborting and using fallback: /usr/bin/metacity 

this driver really sucks! so far so bad!

---

### Post by Forlong on 2007-11-04
> **Neo4 said:**
> I have the new driver installed
composite and aiglx enabled on the xorg.conf file
whitelisted fglrx on the compiz-manager but when I run conpiz it says:

compiz
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

i don't want xgl i want to run compiz from aiglx...
any idea?
See the last step [here](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support)

Do _not_ mess with /usr/bin/compiz

---

### Post by Neo4 on 2007-11-04
that worked! thanks
should I edit the /usr/bin/compiz and remove the fglrx from the withelist?

but why I have to do this now? before this update all worked fine =/

btw compiz is still slow =/

---

### Post by mick222 on 2007-11-04
H

---

### Post by salvadorveiga on 2007-11-04
> **Neo4 said:**
> that worked! thanks
should I edit the /usr/bin/compiz and remove the fglrx from the withelist?

but why I have to do this now? before this update all worked fine =/

btw compiz is still slow =/

i don't think is slow mine is quite fast... and my computer is like 4 years old and at the time I bought it my graphics card was the cheapest I could find from the market... I have a radeon 9200, but I did notice on my first installation if I ever get the ATI drivers compiz was too damn slow... and some other user here told me to install xserver-xgl and it made the computer too slow also... just make sure to stick with the OSS driver and don't install anything else... let it be like you first installed your OS (i am taking as granted that you have an ATI)

MY COMPIZ IS NOW WORKING... all i did was mark "Remove completely" in synaptic so all the config files would be deleted too... then i just reinstalled them and it works like a charm... only thing that doesn't work is the WATER PLUGIN but I never managed to work that ever... every distro I installed it's been the only plugin I can't make it work...

---

### Post by Neo4 on 2007-11-04
salvadorveiga are you portuguese? i bet you are because of your name. i'm too =)
well mine is slow with this new ati driver...
before that with xgl with worked like a charm.
i have an x700 so isn't her fault

compiz is a litle slow with this new ati driver.
and on glxgears with compiz i only loose 100fps (4800 without compiz)
but with compiz on the image of the gears sometimes have some scratches and othertimes disapear like just 0.1seconds!

this aiglx from ati still has much to do!

hugs

---

### Post by salvadorveiga on 2007-11-05
yes i am indeed portuguese eehheh... new user to linux and loving it... I don't know if your graphic card is supported by the OSS driver but you might give it a chance... you sound a lot more experienced in ~Linux than me I don't even know if i'm running AIGLX or XGL ... I just now mine works... if in order to use XGL we need to have installed the package xserver-xgl then I'm not using it... A user here in this thread recommended me to install it when compiz wasn't working after the update and it made the computer really slow as if I were on a Remote connection, so I uninstalled it and continued with whatever it's working on my cmputer...

my opinio for you is to get rid of the ATI official drivers I don't think they're too good yet, and if your card is supported by OSS driver then stick with it... like I said my computer isn't a big deal and compiz is running  really fast and smooth... it's a joy watching it work

---

