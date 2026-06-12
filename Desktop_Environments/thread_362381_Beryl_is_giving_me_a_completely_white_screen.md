---
title: "Beryl is giving me a completely white screen"
date: 2007-02-15
forum: Desktop Environments
---

### Post by BladeOfAnduril on 2007-02-15
Hello,

I just installed the latest updates for Beryl.  The last set of updates broke it, but this new set has it working again... sort of.  Beryl loads up, but the screen stays completely white.  All I can see is the mouse.  I can flip the cube, and see that, but once the transparency from that fades, it goes back to white.  Does anyone know how to fix this??? I can't so anything in Beryl with it like that.  Thanks.

---

### Post by panti19 on 2007-02-15
hey. i have the same problem with a fresh install of the latest beryl.
notify me if you get any solutions:)

---

### Post by meggo on 2007-02-15
my friend and I are both having this problem, his with a fresh install, and mine with an upgrade.

---

### Post by divague on 2007-02-15
I had the same problem, and i found this post that worked for me, but i just prefered to downgrade to version 1.999.2 unitl the final version comes out.

[http://forum.beryl-project.org/viewtopic.php?f=36&t=3756](http://forum.beryl-project.org/viewtopic.php?f=36&t=3756)

hope it helps.

---

### Post by panti19 on 2007-02-15
thanks for the solution, but it didn't work for me..

how do i downgrade?:)

---

### Post by divague on 2007-02-15
Open synaptic package manager, search for beryl, press ctrl+e and select version 0.1.99.2
you have to do this for beryl, beryl-core, beryl-manager, beryl-plugins, beryl-plugins-data, beryl-settings, beryl-settings-binding, libberyldecoration0 and libberylsettings0

---

### Post by dro0g on 2007-02-15
> **divague said:**
> I had the same problem, and i found this post that worked for me, but i just prefered to downgrade to version 1.999.2 unitl the final version comes out.

[http://forum.beryl-project.org/viewtopic.php?f=36&t=3756](http://forum.beryl-project.org/viewtopic.php?f=36&t=3756)

hope it helps.

The fix in that link worked for me, thanks!

---

### Post by bob9000 on 2007-02-16
Hi! I had the same problem, so I installed the absolute latest version from the CVS repositories, I added this one to sources.list:
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

and it did the trick, everything worked beautifully. I hear there could be some problems with plugins in this version, but I assume if they've got this worked out in a weeks time when 0.2 comes out all that should be fixed, in the meantime, this should get you up and running.

Rock On

---

### Post by jtuchscherer on 2007-02-20
I had the same problem. I didn't downgrade to the beryl version.
But I solved it by starting beryl in the terminal:
```
beryl-xgl --use-copy
```

I have an ATI graphic card and use the proprietary ATI driver (8.33.6).

---

### Post by paleocybernetic.net on 2007-02-21
**for users running beryl/xgl on ubuntu edgy who are getting the white screen problem and who want to downgrade but have been wrestling with synaptic:**

i have also had the white screen problem when installing beryl-0.2.0+svn20070219 from debs. the beryl-xgl --use-copy also worked for me, but as others have noted, it runs slower. i didn't find this performance hit acceptable, so i tried to downgrade as others have done (to 0.1.4). i've been having a tough time synaptic to force install previous versions because of the weird dependency complexities between beryl and emerald that i encountered.

i solved the problem by completely removing the beryl and emerald packages in synaptic, and then i went to the svn repository a la http and downloaded the debs for version 0.1.5 (edgy) manually:

[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/)

in here are all the 0.1.5 debs for beryl and emerald. note these are specific svn revisions, and they work together. there are other (some newer) svn revisions for 0.1.5 (at [http://download.tuxfamily.org/3v1deb/pool/edgy/beryl-svn/)](http://download.tuxfamily.org/3v1deb/pool/edgy/beryl-svn/)), but i found that you will _probably_ encounter weird python errors specific to beryl-settings.

when installing these debs, you need to do it in a specific order, because of dependencies, and even then, it will give your 'unconfigured' errors. this is ok, you can configure them afterwards. these are the 0.1.5 packaged i installed using dpkg -i

[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-core_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-core_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-dbus_0.1.5+svn20070108-r2517+3v1ubuntu5_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-dbus_0.1.5+svn20070108-r2517+3v1ubuntu5_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-manager_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-manager_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-plugins_0.1.5+svn20070117-r2765+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-plugins_0.1.5+svn20070117-r2765+3v1ubuntu0_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-plugins-data_0.1.5+svn20070117-r2765+3v1ubuntu0_all.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-plugins-data_0.1.5+svn20070117-r2765+3v1ubuntu0_all.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-plugins-nonfree_0.1.5+svn20070117-r2765+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-plugins-nonfree_0.1.5+svn20070117-r2765+3v1ubuntu0_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-settings_0.1.5+svn20070116-r2739+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-settings_0.1.5+svn20070116-r2739+3v1ubuntu0_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-settings-bindings_0.1.5+svn20070115-r2671+3v1ubuntu1_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-settings-bindings_0.1.5+svn20070115-r2671+3v1ubuntu1_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/emerald_0.1.5+svn20070116-r2710+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/emerald_0.1.5+svn20070116-r2710+3v1ubuntu0_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/libberyldecoration0_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/libberyldecoration0_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/libberylsettings0_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/libberylsettings0_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/libemeraldengine0_0.1.5+svn20070116-r2710+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/libemeraldengine0_0.1.5+svn20070116-r2710+3v1ubuntu0_i386.deb)

the order you install them with dpkg is important, as there will be configuration errors. i think i installed the libs first, and then the beryl-* packages, then emerald, then beryl. i ran dpkg --configure -a after every config error message. i also ran it after attempting to install all the debs, as well as dpkg -i *.deb (reinstall all the debs) for good measure.

it seems beryl-0.1.5 runs well and without any crazy white screens.

---

### Post by db9s on 2007-02-21
> **jtuchscherer said:**
> I had the same problem. I didn't downgrade to the beryl version.
But I solved it by starting beryl in the terminal:
```
beryl-xgl --use-copy
```

I have an ATI graphic card and use the proprietary ATI driver (8.33.6).
:popcorn: :KS 

WOW THAT WORKED !!!!! Can you please please explain the logic behind that command? 
This could be the lifesaver for these crappy svn versions!

---

### Post by herbster on 2007-02-21
> **paleocybernetic.net said:**
> **for users running beryl/xgl on ubuntu edgy who are getting the white screen problem and who want to downgrade but have been wrestling with synaptic:**

i have also had the white screen problem when installing beryl-0.2.0+svn20070219 from debs. the beryl-xgl --use-copy also worked for me, but as others have noted, it runs slower. i didn't find this performance hit acceptable, so i tried to downgrade as others have done (to 0.1.4). i've been having a tough time synaptic to force install previous versions because of the weird dependency complexities between beryl and emerald that i encountered.

i solved the problem by completely removing the beryl and emerald packages in synaptic, and then i went to the svn repository a la http and downloaded the debs for version 0.1.5 (edgy) manually:

[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/)

in here are all the 0.1.5 debs for beryl and emerald. note these are specific svn revisions, and they work together. there are other (some newer) svn revisions for 0.1.5 (at [http://download.tuxfamily.org/3v1deb/pool/edgy/beryl-svn/)](http://download.tuxfamily.org/3v1deb/pool/edgy/beryl-svn/)), but i found that you will _probably_ encounter weird python errors specific to beryl-settings.

when installing these debs, you need to do it in a specific order, because of dependencies, and even then, it will give your 'unconfigured' errors. this is ok, you can configure them afterwards. these are the 0.1.5 packaged i installed using dpkg -i

[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-core_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-core_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-dbus_0.1.5+svn20070108-r2517+3v1ubuntu5_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-dbus_0.1.5+svn20070108-r2517+3v1ubuntu5_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-manager_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-manager_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-plugins_0.1.5+svn20070117-r2765+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-plugins_0.1.5+svn20070117-r2765+3v1ubuntu0_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-plugins-data_0.1.5+svn20070117-r2765+3v1ubuntu0_all.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-plugins-data_0.1.5+svn20070117-r2765+3v1ubuntu0_all.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-plugins-nonfree_0.1.5+svn20070117-r2765+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-plugins-nonfree_0.1.5+svn20070117-r2765+3v1ubuntu0_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-settings_0.1.5+svn20070116-r2739+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-settings_0.1.5+svn20070116-r2739+3v1ubuntu0_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-settings-bindings_0.1.5+svn20070115-r2671+3v1ubuntu1_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/beryl-settings-bindings_0.1.5+svn20070115-r2671+3v1ubuntu1_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/emerald_0.1.5+svn20070116-r2710+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/emerald_0.1.5+svn20070116-r2710+3v1ubuntu0_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/libberyldecoration0_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/libberyldecoration0_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/libberylsettings0_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/libberylsettings0_0.1.5+svn20070117-r2769+3v1ubuntu0_i386.deb)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/libemeraldengine0_0.1.5+svn20070116-r2710+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/libemeraldengine0_0.1.5+svn20070116-r2710+3v1ubuntu0_i386.deb)

the order you install them with dpkg is important, as there will be configuration errors. i think i installed the libs first, and then the beryl-* packages, then emerald, then beryl. i ran dpkg --configure -a after every config error message. i also ran it after attempting to install all the debs, as well as dpkg -i *.deb (reinstall all the debs) for good measure.

it seems beryl-0.1.5 runs well and without any crazy white screens.


Oh my goodness!!!!!! i have been trying to get XGL and Beryl to work for a week now and after 4 bad installs (and subsequent REINSTALLS of UBUNTU! :() this is the guide that worked PERFECTLY! I'm in my XGL Session right now having loads of fun setting Beryl up!! Thanks man!!!!!!!!!!!!!!! :) :) :)

---

### Post by shinynew on 2007-02-21
"WOW THAT WORKED !!!!! Can you please please explain the logic behind that command?
This could be the lifesaver for these crappy svn versions!"

That simply changes the way that beryl gets/posts the textures for the windows (not sure which) I personally saw a HUGE drop in performance using this, but it really does work. (this can also be set in the settings, just look for something that says use copy.)
When it screws up just hit alt+ctrl+F1 to get to a terminal then type in: 
```

killall beryl-xgl
or
killall beryl
```
Then go to the beryl-manager and change the settings.

---

### Post by Melcar on 2007-02-22
So it's not only me then.  Excellent, I guess.  Hopefully a real fix will be available soon.  Strange that this does not happen to me in OpenSuse.

---

### Post by db9s on 2007-02-22
New updates today, and THEY STILL DIDN'T FIX IT !! :confused:

do they even know how everyone is being effed up?? 
everytime an update comes, i thought it would be a fix, but no it still screws up.

---

### Post by dro0g on 2007-02-22
I just switched to using running LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl

(from the bottom of this thread: [http://forum.beryl-project.org/viewtopic.php?f=36&t=3057&start=70](http://forum.beryl-project.org/viewtopic.php?f=36&t=3057&start=70))

That fixed the white screen problem and performance is MUCH better than using beryl-xgl --use-copy.

---

### Post by chalewa on 2007-02-22
> **dro0g said:**
> I just switched to using running LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl

(from the bottom of this thread: [http://forum.beryl-project.org/viewtopic.php?f=36&t=3057&start=70](http://forum.beryl-project.org/viewtopic.php?f=36&t=3057&start=70))

That fixed the white screen problem and performance is MUCH better than using beryl-xgl --use-copy.



this also worked for me

---

### Post by Jaydude765 on 2007-02-22
I just want to note that paleocybernetic.net's method worked for me as well. Thanks very much, I hope the beryl guys sort this issue out for new releases :)

---

### Post by rjz35 on 2007-02-22
it does work with the LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl
but i don not want to load it like this cause i do not know how to make work automatic when restarting in to xgl.
I use my ubuntu for daily work and don't want it to be an  effort working with it. a pitty must say caus i liked it.

---

### Post by Melcar on 2007-02-22
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl does not work for me.  Oh well, back to Suse for the time being (Beryl does work there, to bad it kills nearly all my default key bindings for some reason).

---

### Post by dasunst3r on 2007-02-22
Copy and paste the following, then save it as /etc/apt/preferences:
```
Package: beryl
Pin: version 0.1.99.2*
Pin-Priority: 1001

Package: beryl-core
Pin: version 0.1.99.2*
Pin-Priority: 1001

Package: beryl-manager
Pin: version 0.1.99.2*
Pin-Priority: 1001

Package: beryl-plugins
Pin: version 0.1.99.2*
Pin-Priority: 1001

Package: beryl-plugins-data
Pin: version 0.1.99.2*
Pin-Priority: 1001

Package: beryl-settings
Pin: version 0.1.99.2*
Pin-Priority: 1001

Package: beryl-settings-bindings
Pin: version 0.1.99.2*
Pin-Priority: 1001

Package: emerald
Pin: version 0.1.99.2*
Pin-Priority: 1001

Package: libberyldecoration0
Pin: version 0.1.99.2*
Pin-Priority: 1001

Package: libberylsettings0
Pin: version 0.1.99.2*
Pin-Priority: 1001

Package: libemeraldengine0
Pin: version 0.1.99.2*
Pin-Priority: 1001

Package: emerald-themes
Pin: version 0.1.99.2*
Pin-Priority: 1001
```

If you have already installed Beryl, you should completely remove beryl and reinstall it.

---

### Post by tripleZero on 2007-02-22
I used to have the white screen problem on my edgy comp.  i tried the downgrading thing and that didnt work.  I got my beryl to work by uninstalling beryl and xgl.  I then installed beryl with AIGLX, using the instructions from the beryl wiki site.  after that everything works perfectly.  which leads me to believe that the problem is with xgl.  i also read somewhere that AIGLX is less buggy then xgl, for me that proved to be true.  

just thought i'd give guys another option, because once you get it workin its all worth it.

---

### Post by nachotronics on 2007-02-23
Here's a solution I got from _[**Forlong's** post in the beryl forums]("http://forum.beryl-project.org/viewtopic.php?f=43&t=70&st=0&sk=t&sd=a&start=330")_[SIZE="3"]** it consists in downgrading to the last working version from Treviños svn repository. **[/SIZE]

1. Uninstall Beryl completely
```
sudo apt-get remove 'beryl*'
```

2. Remove the SVN-repository (or any other Beryl-repo) so it won't update, till the next tested working version comes out
```
sudo gedit /etc/apt/sources.list
```
Then comment every beryl related line by adding # at the beggining, in my case they looked like this:
```
# deb http://ubuntu.beryl-project.org edgy main
# deb-src http://ubuntu.beryl-project.org edgy main
# deb http://www.beerorkid.com/compiz edgy main-edgy
# deb http://media.blutkind.org/xgl edgy main (latest: beryl 0.1.1)
# deb http://beryl.xglusers.de/ edgy main (latest: beryl 0.1.4; no aquamarine)
# deb http://download.tuxfamily.org/3v1deb edgy beryl-svn ( bleeding edge beryl development, use with care )
```

3. Look for these packages in /var/cache/apt/archives/

beryl_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
beryl-core_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
beryl-manager_0.2.0+svn20070213-r4019+3v1ubuntu0_i386.deb
beryl-plugins_0.2.0+svn20070218-r4130+3v1ubuntu0_i386.deb
beryl-plugins-data_0.2.0+svn20070218-r4130+3v1ubuntu0_all.deb
beryl-settings_0.2.0+svn20070218-r4140+3v1ubuntu0_i386.deb
beryl-settings-bindings_0.2.0+svn20070201-r3550+3v1ubuntu0_i386.deb
emerald_0.2.0+svn20070208-r3810+3v1ubuntu0_i386.deb
libberyldecoration0_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
libberylsettings0_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
libemeraldengine0_0.2.0+svn20070208-r3810+3v1ubuntu0_i386.deb

also optional: emerald-themes_0.2.0+svn20070126-r3229+3v1ubuntu0_all.deb

Or download them from _[**Treviños** svn repository]("http://download.tuxfamily.org/3v1deb/pool/edgy/beryl-svn/")_ or just [_**get the entire set at once from rapidshare -> beryl-svn.tar.gz**_]("http://rapidshare.com/files/17958701/beryl-svn.tar.gz.html")

4. Copy them to another folder e.g. beryl-svn on your desktop

5. Open a terminal and go to that directory
```
cd ~/Desktop/beryl-svn
```

6. Install all packages of that folder:
```
sudo dpkg -i *.deb
```

7. Start beryl by running
```
beryl-manager
```

8. Enjoy\\:D/

---

### Post by dcherryholmes on 2007-03-01
I fixed the problem by forcing the rendering path to Copy in beryl-manager-->advanced options (and also taking a performance hit).  But does anyone know when xgl will be fixed?  Is it being worked on?  I'm just a little surprised that this bug has persisted for so long.

---

### Post by banditti on 2007-03-01
I am really surprised this hasn't been fixed yet.  sigh

---

### Post by Melcar on 2007-03-03
For me using the SVN repos fixed the white cube, but it gave me other issues and it would sometimes crash.  A similar thread to this in the Beryl forums exists (it's not only us after all) but no one has offered a solution besides downgrading.

---

### Post by Lafie on 2007-03-03
Nevermind all this and all

Edit: Useless command

---

### Post by Ares2 on 2007-03-06
I got a question that may sound stupid but, I've read about every post and I tried some of the suggestions given but I got this question to ask.

How do you guys modify ur settings if you cant even log on the computer, i mean, i did boot in terminal mode but how can i even run beryl in terminal mode. I dont seem to get it, i uninstalled beryl and im still getting that white screen and I cant seem to figure whats wrong. I wanted to edit my startup programs, but yet, i havent figured out how to do so in console.

Would someone help me out :s

---

### Post by Gapert on 2007-03-06
I've had difficulties with beryl white screen too. The newest SVN repos didn't help, and I don't like the idea of downgrading at all. So I installed Compiz and worked with it for a few days, not being totally satisfied.
So I took one more shot at trying Beryl... and it works!

**My system:**
- Ati 200M
- Fgrlx driver
- XGL

I checked the SVN versions and it looks like the latest SVN is from yesterday. So I installed it, and it works without any problems (yet). I'm working on it for about 3 hours now.

So, try downloading the latest SVN again and see if it works for you.

Let me know if it works for you guys too.

P.S.
With Compiz my XGL uses about 50% proc. time constantly, with Beryl that's only 20%...

---

### Post by crack on 2007-03-06
its working, they have fixed it, thank u very much :guitar:

---

### Post by Ares2 on 2007-03-06
I did uninstall beryl and when i tried reinstalling it, i was still getting that white screen, any help?

---

### Post by banditti on 2007-03-07
There were some recent updates, that after installed, everything worked again for me?

Are you current on your updates?

---

### Post by Nigel_C on 2007-03-14
The Xgl xserver package was updated yesterday. This fixed the issue for me (200M + fglrx + Beryl on AMD64 Feisty).

Regards,

Nigel

---

### Post by divdude on 2007-03-14
I had exactly same problem. But after I did complete upgrade(apt-get install upgrade). The problem was solved. After kernel upgrade i had to reinstall my nvidia drivers though. But it
has become REALLY EASY due to a nifty tool called envy.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Now beryl works like a charm.

---

### Post by Xamindar on 2007-03-28
Where are the svn repositories?

---

### Post by stickperson on 2007-04-20
I just installed Beryl and I'm gettin the white screen.  I'm using Ubuntu 7.04.  How do I tell what kind of card I have?  I tried these steps but nothing seems to be workin.

---

### Post by ColinIam on 2007-07-21
Gahhh.  I got rid of the white screen thing by going "Advanced Beryl Options > Rendering Path > Copy" but now I've got something a bit different.  The animations are completely laggy and as soon as I move a window or click anywhere it starts doing this thing:
[Click here for the screenshot.]("http://img292.imageshack.us/img292/8075/screenshot1ib7.png")

It will stop if I go "Select Window Manager >Metacity (Gnome Window Manager)" but if I select "Quit" then the strange effect doesn't go away and the Beryl logo stays up there, but behaves as though nothing is there at all.

---

### Post by chumchum on 2007-12-16
Hello all
At the moment NONE of this advice is working for me :( and I have to forcibly turn off the PC manually but is there a way to go back to the standard desktop using keyboard shortcuts or something so I can try all the solutions without having to reboot each time just because they didn't work for me.
Thanks in advance

---

