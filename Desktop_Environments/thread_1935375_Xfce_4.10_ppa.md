---
title: "Xfce 4.10 ppa?"
date: 2012-03-04
forum: Desktop Environments
---

### Post by drfox on 2012-03-04
We're about a month away from the new XFCE 4.10 release. Does anyone know if there is a testing PPA for the beta?
Larry

---

### Post by Tiganjero on 2012-03-04
I don't think there is one yet.

Cheers,
George

---

### Post by Noccy on 2012-04-12
Meh, just noticed that xdesktop-settings and the entire xfdesktop4 package was missing on my 11.10 setup, and I can't reinstall it due to dependency problems that would force remove half my system :s 

The most recent ppa for Xfce4 seem to be for natty, which is highly disappointing. Attempted to build it myself, which turned out to be easier said than done. So, I currently can't change the desktop wallpaper or any desktop settings; quite annoying.

Do you think there is any hope for updated packages in the main repository, or a ppa for oneiric/precise any time soon? Or should I try upgrading to 12.04 beta and hope for the best? The package list at [http://packages.ubuntu.com/precise/xfce/](http://packages.ubuntu.com/precise/xfce/) doesn't look too promising :(

---

### Post by drfox on 2012-04-12
Why not just build it? It really wasn't that hard.
I did it and posted it last week:
[http://ubuntuforums.org/showthread.php?t=1951935](http://ubuntuforums.org/showthread.php?t=1951935)

HTH. Larry

---

### Post by Noccy on 2012-04-13
> **drfox said:**
> Why not just build it? It really wasn't that hard.

Thank you :) I should have rtfm about the build order before giving up. However, I was able to build everything up to xfcelibxfce4ui, which builds but doesn't link due to unresolved references;

```
/usr/lib/i386-linux-gnu/libpangocairo-1.0.so: undefined reference to `g_mutex_trylock'
/usr/lib/libxfce4util.so: undefined reference to `g_mutex_unlock'
/usr/lib/libxfce4util.so: undefined reference to `g_mutex_lock'
```

By editing the makefile not to build xfce4-about I was able to make it all the way to exo, where the same problem appears again, and without exo none of the remaining packages will build. 

Did you experience this while building? Google suggests that this belongs to libglib-dev which is properly installed (which is apparent by the fact that it compiles neatly but refuses to link, so it is able to find the headers).

---

### Post by drfox on 2012-04-13
Try configuring again 
./configure
and post your terminal output. If it's too long, post the last 20 or so lines. I think you're probably missing a dependency.
Larry

---

### Post by Noccy on 2012-04-13
> **drfox said:**
> Try configuring again 
./configure
and post your terminal output. If it's too long, post the last 20 or so lines. I think you're probably missing a dependency.
Larry

I don't think it's as much missing dependencies as  my system looking for them in all the wrong places. I built Gimp from source a while ago, and it appears to have installed some overrides somewhere which I am unable to locate. Renaming the old ~/gimp library resulted in this:

[http://pastebin.com/PvwL340t](http://pastebin.com/PvwL340t)

I have been grepping every corner of pkgconfig, looking for symlinks etc but to no avail. And as far as I can recall, I built Gimp without sudo which just makes things even more confusing.

Where could this override be located?

---

### Post by drfox on 2012-04-13
Have you tried purging gimp and reinstalling from the ubuntu repository? Aside from the gimp failure and the [exo-desktop-item-edit] Error 1, your make looks like mine. You could also try posting at forum.xfce.org

Larry

---

### Post by Noccy on 2012-04-14
> **drfox said:**
> Have you tried purging gimp and reinstalling from the ubuntu repository?

I did exactly that and it sorted the problems out allowing me to re-install the xfce4-package and with that xfdesktop :) Seems the reason for it going away in the first place was an incompatible version of glib2 and related libraries in the gimp 2.8rc ppa I was using.

Thanks for the help :) Saved me a system re-install for now. 

Chris

---

### Post by Toz on 2012-04-14
xfce 4.10 pre2 released today!

[[img]http://s15.postimage.org/kz5wm705z/xfce4_10pre2.jpg[/img]](http://postimage.org/image/kz5wm705z/)
(built from git)

---

### Post by drfox on 2012-04-14
> **Toz said:**
> xfce 4.10 pre2 released today!

Thanks! Built and restarted. It's working fine.
Is there an easier way to update than going to terminal and executing 
"./configure && make" and then "sudo make install" 
with each package?
Larry

---

### Post by Toz on 2012-04-14
I'm building from git and am trying to develop a script to automate the process because you're right, its time consuming. 

BTW, does your Settings Manager work? When I bring mine up I don't have any icons - just headings. The individual applets can start up fine and work, its just the settings manager that isn't right.

I am running the latest preview on beta 2 of precise. A double dose of freshness.

---

### Post by drfox on 2012-04-14
> **Toz said:**
> I'm building from git and am trying to develop a script to automate the process because you're right, its time consuming. 

BTW, does your Settings Manager work? When I bring mine up I don't have any icons - just headings. The individual applets can start up fine and work, its just the settings manager that isn't right.

I am running the latest preview on beta 2 of precise. A double dose of freshness.

I'm using precise also. Pioneers are the guys with the arrows in their chests. ;)
Did you download and build thunar-volman? If not, that's probably your settings problem. I made the mistake of overlooking that part of xfce when I first built 4.10 since it's not mentioned in the build instructions.
HTH  Larry

---

### Post by Toz on 2012-04-14
Yes I did. I found out that the problem was a conflict between the installed libexo libs and the newly built ones. Some fancy linking and re-linking of libraries took care of that for me.

I've also had to rebuild xfce4-indicator-plugin to get the indicators working again. Must be related to running it from git. Who's bright idea was that? (Oh yeah, mine). There are multiple daily updates coming out of it.

---

### Post by drfox on 2012-04-14
> **Toz said:**
> Yes I did. I found out that the problem was a conflict between the installed libexo libs and the newly built ones. Some fancy linking and re-linking of libraries took care of that for me.

I've also had to rebuild xfce4-indicator-plugin to get the indicators working again. Must be related to running it from git. Who's bright idea was that? (Oh yeah, mine). There are multiple daily updates coming out of it.

From "Pal Joey," a 1940 musical comedy by Rodgers and Hart:

Do it the hard way and it's easy sailing
Do it the hard way and it's hard to lose
Only the soft way has a chance of failing
You have to choose

git is apparently the "soft" way; building step by step the "hard" (aka PITA) way. The "smart" way will be to wait for the ppa.
Larry

---

### Post by BrokenKingpin on 2012-04-15
I am pretty excited for this new release. Hopefully there is a PPA for 12.04 when the final release it out.

---

### Post by carrozza on 2012-04-16
Ditto as above; for the newbies building from sources is not easy.
I'm pretty happy about Xfce evolution!

Did I read it right that 4.10 will be released just a few days after Precise goes gold? Why didn't they choose an earlier date so that Xubuntu 12.04 could have the most recent Xfce?
Meh...

---

### Post by theos911 on 2012-04-19
You can't rush perfection, or so the saying goes. ;)

IIRC *buntu goes into feature/package lock a month before release, so the entire xfce project would need to be have been moving about a month faster for 4.10 to have had any chance of making it in.

That in mind, I'd rather have an ***LTS* **ship with something tested and stable than something hot off the presses.

---

### Post by mips on 2012-04-30
I think I will be installing this once my xubuntu 12.10 has downloaded (2hrs to go). I got the alternate iso so will do a base install and then give this a bash but I'm very sure I'm gonna be back here later today asking some questions :biggrin:

Which the PPA was populated already, sigh...

---

### Post by mips on 2012-04-30
Just a heads up.

Keep an eye on Lionel Le Folgoc's PPA [https://launchpad.net/~mrpouit/+archive/ppa]("https://launchpad.net/%7Emrpouit/+archive/ppa") he's busy packaging 4.10 final for Debian right now and once he is done he will backport for this PPA. He's one of the Xubuntu contributors and will later move it to [https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10]("https://launchpad.net/%7Exubuntu-dev/+archive/xfce-4.10")

---

### Post by Gaygerbil on 2012-05-01
I'm going through dependency hell trying to build the DE myself and update it with the tar archives, I hope they get the final build released soon into the ppa. It's kinda ridiculous that it's taken them this many days to get it into one. Kinda of like releasing a distro and making users build it themselves for people who wanted it the first week it came out. 

Call me new fashioned but with technology the way it is now, why torture users who don't want to spend 3 to 4 hours staying up and doing this to have the latest distro? And it's obvious they understand how time consuming this activity is, one of the requirments to building the DE on the actual XFCE site is: "Coffee".

---

### Post by mips on 2012-05-01
> **Gaygerbil said:**
> I'm going through dependency hell trying to build the DE myself and update it with the tar archives, I hope they get the final build released soon into the ppa. It's kinda ridiculous that it's taken them this many days to get it into one. Kinda of like releasing a distro and making users build it themselves for people who wanted it the first week it came out. 

Call me new fashioned but with technology the way it is now, why torture users who don't want to spend 3 to 4 hours staying up and doing this to have the latest distro? And it's obvious they understand how time consuming this activity is, one of the requirments to building the DE on the actual XFCE site is: "Coffee".

Exercise some patience, it was only released 2 days ago. These people aren't getting paid to do it and they have other responsibilities as well.

---

### Post by Toz on 2012-05-01
> **Gaygerbil said:**
> I'm going through dependency hell trying to build the DE myself and update it with the tar archives,
What kind of dependency issues are you having? There are a number of dev packages that need to be installed to enable the compilation of the packages, but aside from that, I didn't run into any major dependency issues.

---

### Post by Gaygerbil on 2012-05-02
I understand they're not getting paid, my post was probably a bit off, I had been trying to build it for about 3 hours at the time I posted it. 

The error I'm running into is with Gtk+-2.0, which I thought I already had, I can't figure out what it's talking about that I need.

---

### Post by theos911 on 2012-05-02
I think it is referring to 'gtk+-devel' .

---

### Post by Toz on 2012-05-02
Or libgtk2.0-dev. I built from git. Here is a list of dependencies that I had to install:

xfce4-dev-tools -> intltool libtool libglib2.0-dev
libxfce4util -> gtk-doc-tools
xfconf -> libdbus-1-dev libdbus-glib-1-dev libextutils-depends-perl libextutils-pkgconfig-perl
libxfce4ui -> xserver-xorg-dev libgtk2.0-dev libstartup-notification0-dev
xfce4-panel -> libwnck-dev
thunar -> libgudev-1.0-dev libnotify-dev libexif-dev libpng12-dev libjpeg-dev
xfce4-settings -> libxklavier-dev
tumbler -> libffmpegthumbnailer-dev libgstreamer0.10-dev libgsf-gnome-1-dev libpoppler-glib-dev libopenrawgnome-dev
xfce4-indicator-plugin -> libindicator-dev

---

### Post by Gaygerbil on 2012-05-03
Thank you for the help, I got past the dependencies issue but now I'm running into an error I don't understand myself. 

```
/usr/bin/install: cannot create regular file `/lib/libxfce4ui-1.so.0.0.0': Permission denied
```

I am using 'sudo' to execute the command it still gives me this permission denied error.

EDIT: I think a PPA has been updated with XFCE 4.10...so I guess this doesn't matter now. Lol.

---

### Post by mips on 2012-05-03
> **Gaygerbil said:**
> 
EDIT: I think a PPA has been updated with XFCE 4.10...so I guess this doesn't matter now. Lol.

Patience is a virtue :p

---

### Post by tewth on 2012-05-03
Edit: Nevermind, just saw the thread directing to PPA, used it and everything works now. Here's the link [http://ubuntuforums.org/showthread.php?p=11903278#post11903278](http://ubuntuforums.org/showthread.php?p=11903278#post11903278)

PPA isn't updated yet as far as I can tell...
I managed to get all of the dependencies resolved and get xfce 4.10 compiled... however...
it doesn't seem to work correctly. About Xfce (in the xfce tab) says I have xfce 4.10 running, but as far as I can tell, I'm still on 4.8, window tiling doesn't work, the settings menu isn't in the new style as I've seen in screenshots, etc.
Not sure what I did wrong... compiled it to /opt/xfce4
When I boot into the Xfce session as opposed to my xubuntu session it throws an error upon opening the settings manager
Sigh... I wish I had just patched 4.8 with the tiling update like I did on my old install, it makes the de so much more usable

---

### Post by jefsview on 2012-05-03
it's on the move with the final builds now.

hopefully it'll be completed today or early tomorrow with all of the available panel apps.

:popcorn:

-- Jeff

---

### Post by dentaku65 on 2012-05-04
> **jefsview said:**
> it's on the move with the final builds now.

hopefully it'll be completed today or early tomorrow with all of the available panel apps.

:popcorn:

-- Jeff

Unfortunately the the Action Buttons and Session Menu plugis are not working with 4.10 final (ppa version); plus it is not available xfce4-session too; strange thing, after I've installed the 4.10 on the next update/dist-upgrade the system proposed me to install Unity desktop and all its dependencies :confused:
I've purged the ppa and get back to 4.8 of Precise.

---

### Post by mips on 2012-05-04
> **jefsview said:**
> it's on the move with the final builds now.

hopefully it'll be completed today or early tomorrow with all of the available panel apps.

:popcorn:

-- Jeff

> **dentaku65 said:**
> Unfortunately the the Action Buttons and Session Menu plugis are not working with 4.10 final (ppa version); plus it is not available xfce4-session too; strange thing, after I've installed the 4.10 on the next update/dist-upgrade the system proposed me to install Unity desktop and all its dependencies :confused:
I've purged the ppa and get back to 4.8 of Precise.

AMD64 builds of few critical packages failed due to unmet dependencies which are still queued in Launchpad to be built. Once the critical dependencies are built the failed xfce 4.10 packages will be resubmitted for building and only then will you get a working xfce 4.10 solution.

Earlier today when I spoke to the xfce4 packager he said the dependencies were still 13hrs away from being built after which he would have to resubmit the failed xfce 4.10 packages which could take 2+ days to complete. PPA build servers are slow.

Patience is a virtue ;)

---

### Post by mr_pouit on 2012-05-05
> **dentaku65 said:**
> Unfortunately the the Action Buttons and Session Menu plugis are not working with 4.10 final (ppa version); plus it is not available xfce4-session too; strange thing, after I've installed the 4.10 on the next update/dist-upgrade the system proposed me to install Unity desktop and all its dependencies :confused:
I've purged the ppa and get back to 4.8 of Precise.

"Session Menu" plugin (= xfsm-logout-plugin) has been dropped from xfce4-session >= 4.9.x anyway. Xfce4-panel should take care of the migration and replace it with one of its own plugins.

And as written above, some packages are still missing on amd64 (e.g. xfce4-panel, thunar, xfdesktop, xfce4-settings), it's not a good idea to upgrade right now.

---

### Post by dentaku65 on 2012-05-06
> **mr_pouit said:**
> "Session Menu" plugin (= xfsm-logout-plugin) has been dropped from xfce4-session >= 4.9.x anyway. Xfce4-panel should take care of the migration and replace it with one of its own plugins.

And as written above, some packages are still missing on amd64 (e.g. xfce4-panel, thunar, xfdesktop, xfce4-settings), it's not a good idea to upgrade right now.

Hi mr_pouit,
thx for the info. I'm using the 3bit version of 4.10; after the updating I see these packages kept back:
```
xfce4-appfinder xfce4-session
```
If the "xfsm-logout-plugin" is still present on "Add new items..." this means that we have to wait the new xfce4-session package?

tia

---

### Post by mr_pouit on 2012-05-06
You should upgrade them, it will remove xfce4-utils (deprecated with Xfce 4.10). If you see xfsm-logout-plugin, that means you're still using xfce4-session 4.8.x.

---

### Post by dentaku65 on 2012-05-06
> **mr_pouit said:**
> You should upgrade them, it will remove xfce4-utils (deprecated with Xfce 4.10). If you see xfsm-logout-plugin, that means you're still using xfce4-session 4.8.x.

I supposed yes, I still using xfce4-session 4.8 because the package has been kept back when I upgraded the version via your PPA

Ops solved: removing xfce4-utils, the xfce4-session has been updated!

---

### Post by mips on 2012-05-06
The PPA works fine now for those that wanna try 4.10.

I'm now running 4.10

---

### Post by c-shadow on 2012-05-06
What would be suggested way to upgrade to final 4.10?
Both apt-get upgrade and dist-upgrade are leaving kept back packages.
Currently I have installed rc version from mrpouit's PPA.

EDIT: kept back packages are only on stock ubuntu xfce 4.8 
rc 4.10 upgraded without a problem :-)

---

### Post by jefsview on 2012-05-06
> **mips said:**
> The PPA works fine now for those that wanna try 4.10.

I'm now running 4.10

Are you using 32 bit or 64?

Might wait for the migration to the dev ppa, to make certain the amd64 are all built.

Thanks for all the info.

-- Jeff

---

### Post by mips on 2012-05-07
> **jefsview said:**
> Are you using 32 bit or 64?

Might wait for the migration to the dev ppa, to make certain the amd64 are all built.

Thanks for all the info.

-- Jeff

64-bit, all the 64 bit stuff has completed building.

---

### Post by jefsview on 2012-05-07
Thanks. I wasn't certain.

After I added the ppa again (I switched from vanilla Xubuntu to Voyager), 3 items were still held back, including xfce-settings and xfce-sessions. 

thanks for the info.

-- Jeff

---

### Post by neu5eeCh on 2012-05-07
> **jefsview said:**
> Thanks. I wasn't certain.

After I added the ppa again (I switched from vanilla Xubuntu to Voyager), 3 items were still held back, including xfce-settings and xfce-sessions. 

thanks for the info.

-- Jeff

Voyager is lovely. Xubuntu could stand to take a few ideas for Voyager. I also installed it and am using it.  I don't know why Xubuntu feels compelled to offer such a stick-in-the-mud aesthetic.

---

### Post by jefsview on 2012-05-07
> **VTPoet said:**
> Voyager is lovely. Xubuntu could stand to take a few ideas for Voyager. I also installed it and am using it.  I don't know why Xubuntu feels compelled to offer such a stick-in-the-mud aesthetic.

Yes, it's really lovely. Even though I deleted Awn and synapse, I love the number of different conkys they have, and a nice assortment of pre-configured Thunar scripts (even though I had to rename them in English). It is a bit heavier than vanilla Xubuntu, but it also has a wider selection of default tweaks and customization that raises the elegance factor.

I'll be upgrading Xfce to 4.10 before I head out to work this afternoon. Looking forward to the new deskbar!

-- Jeff

---

### Post by jefsview on 2012-05-07
All right, the upgrade went well.

Some items didn't work at first with just an in-place upgrade of installed components. Then I went into Synaptic and looked over options, and, duh -- I forgot to install the Xfce 4 meta package. That upgraded the previous held packages and now all works as expected.

-- Jeff

---

### Post by mexicanseaf00d on 2012-05-21
Anyone having problems with **indicator-messages**? To be precise, no icon change on new mail in Thunderbird? It does recognise when TB is running and is able to start it.

---

