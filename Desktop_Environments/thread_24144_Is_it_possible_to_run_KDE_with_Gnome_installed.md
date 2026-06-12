---
title: "Is it possible to run KDE with Gnome installed?"
date: 2005-04-05
forum: Desktop Environments
---

### Post by Francisco on 2005-04-05
Hi,

  I wanted to know if it was possible to install and use KDE as my desktop system, but I still want to keep "GDM" to login into ubuntu.

 How can I install KDE for ubuntu? apt-get install kde isn't the one...

Thanks :)

---

### Post by bored2k on 2005-04-05
[QUOTE=Francisco]Hi,

  I wanted to know if it was possible to install and use KDE as my desktop system, but I still want to keep "GDM" to login into ubuntu.

 How can I install KDE for ubuntu? apt-get install kde isn't the one...

Thanks :)[/QUOTE]
 sudo apt-get install kubuntu-desktop.

and yes you can keep your pretty gdm.

---

### Post by Francisco on 2005-04-05
[QUOTE=bored2k]sudo apt-get install kubuntu-desktop.

and yes you can keep your pretty gdm.[/QUOTE]

root@ubuntu:/home/francisco # apt-get install kubuntu-desktop
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package kubuntu-desktop
root@ubuntu:/home/francisco # apt-get install kubuntu
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package kubuntu
root@ubuntu:/home/francisco # apt-get install kubuntu


 did apt-get update and didn't worked either

---

### Post by SamH on 2005-04-05
I have KDE working via the Synaptic installer.  I just checked the boxes for the KDE stuff I wanted and ran it.  I can switch back and forth easily at the login.  

I'm experimenting a lot with Hoary RC.  Once the release comes out I'll do a clean install, probably witout KDE (except maybe K3B).

---

### Post by Xian on 2005-04-05
Francisco, you will most likely have to update your repos to Hoary in order to install the kubuntu packages.

---

### Post by Francisco on 2005-04-05
[QUOTE=Xian]Francisco, you will most likely have to update your repos to Hoary in order to install the kubuntu packages.[/QUOTE]

 Doing that now :)

---

### Post by dbott67 on 2005-04-06
[QUOTE=SamH]I have KDE working via the Synaptic installer.  I just checked the boxes for the KDE stuff I wanted and ran it.  I can switch back and forth easily at the login. [/QUOTE]

I have also used Synaptic to download & install KDE, IceWM and Fluxbox.  I just went into the SETTINGS | REPOSITORIES section of Synaptic and checked the additional repositories.

I am able to switch without any problems between Gnome, KDE, IceWM and Fluxbox.  The ubuntu splash/login screen remained, although I have since changed the graphical greeter to one of the others (Happy Gnome) using the "Login Screen Setup" utility.  I was never able to use the utility to get the graphical greeter to change, although I did find the config file & edited it by hand.  It was well-commented so it was easy to figure out which lines to edit.

I have also changed the splash screen using the "Configuration Editor" in system tools ( / apps --> gnome-session --> options --> splash_image ).

Plenty of fun!

-Dave

PS - btw, using Warty 4.10

---

### Post by lorap on 2005-04-06
hi friend!
of course you can get kdesktop installed with no harm.
you even can instal applications built for kde and run them in gnome environment.
most of them'd work fine.like cd burning tool K3B.
have a nice day.
pavel

---

### Post by Francisco on 2005-04-06
Hi,

 Yeah, I was told to get Hoary and then install kubuntu-desktop thru APT and it works like a charm now :)

Thanks all!

---

### Post by az on 2005-04-06
[QUOTE=dbott67]I have also used Synaptic to download & install KDE, IceWM and Fluxbox.  I just went into the SETTINGS | REPOSITORIES section of Synaptic and checked the additional repositories.

I am able to switch without any problems between Gnome, KDE, IceWM and Fluxbox.  The ubuntu splash/login screen remained, although I have since changed the graphical greeter to one of the others (Happy Gnome) using the "Login Screen Setup" utility.  I was never able to use the utility to get the graphical greeter to change, although I did find the config file & edited it by hand.  It was well-commented so it was easy to figure out which lines to edit.

I have also changed the splash screen using the "Configuration Editor" in system tools ( / apps --> gnome-session --> options --> splash_image ).

Plenty of fun!

-Dave

PS - btw, using Warty 4.10[/QUOTE]

Your girls are cute!

You should try the new XFCE4 in Hoary.  I hate it much less than any other version of xfce I have tried before.

---

### Post by Xian on 2005-04-06
[QUOTE=azz]I hate it much less than any other version of xfce I have tried before.[/QUOTE]
Wow, that is quite a recommendation. :)

---

### Post by Francisco on 2005-04-06
Whats XFCE4?

---

### Post by dbott67 on 2005-04-06
[QUOTE=azz]Your girls are cute![/QUOTE]
Hi Azz,

Thanks!
[QUOTE=azz]You should try the new XFCE4 in Hoary.  I hate it much less than any other version of xfce I have tried before.[/QUOTE]

I just downloaded it and am using it now --- nice.  Thanks for the tip!  :)

How are things in la belle province?  My grandfather came to Canada in 1929 and lived in Montreal until the mid 40's before his job brought him to Ontario.  My dad & his 2 brothers we all born in Montreal.

Take care & thanks for the XFCE tip.

-Dave

Francesco, [XFCE](http://www.xfce.org)  is another desktop GUI, like Gnome, KDE, IceWM and Blackbox/Fluxbox, but it is considered to be a "light weight" Window Manager --- offering better speed and performance for lower end PCs.

---

### Post by gmike on 2005-04-08
can one install xfce through apt-get install xfce?

---

### Post by dbott67 on 2005-04-08
[QUOTE=gmike]can one install xfce through apt-get install xfce?[/QUOTE]
 Hi gmike,

I used Synaptic (the graphical overlay for apt-get) to download xfce4.  I had to add a couple of the other repositories in the SETTINGS | REPOSITORIES menu (or you can uncomment the appropriate lines in the [sources.list ](http://www.ubuntuguide.org/#extrarepositories) file.

From within Synaptic, I did a search for 'xfce' and found the xfce4 listing.  I'm not sure what the actual package name is, but I am guessing it might be:

apt-get install xfce4

I'm not at home right now, so I can't tell you for sure.

-Dave

---

### Post by Datchew on 2005-04-08
hi guys.
been following this thread... 

Am I correct that  XFCE WILL NOT WORK in warty warthog?
That's what i'm running, and learning on, and crashing and screwing up about once a week.

---

### Post by dbott67 on 2005-04-08
[QUOTE=Datchew]hi guys.
been following this thread... 

Am I correct that  XFCE WILL NOT WORK in warty warthog?
That's what i'm running, and learning on, and crashing and screwing up about once a week.[/QUOTE]

I am using Warty Warthog and have installed XFCE4 (I didn't attempt XFCE v3).  I have not had any issues.  I have also installed KDE, IceWM and Fluxbox and all seem to run well.

From my personal viewpoint, Gnome is by far the most intuitive.  KDE looks real nice and Fluxbox is very quick (although most of the apps run slow on my P2-300 that it doesn't really make any difference).

I've been running Ubuntu for 1 month now and I am really enjoying the experience.  I've been spending a lot of time trolling forums, searching for stuff and seeing what issues others have had, but most of the stuff just worked.

-Dave

---

### Post by Datchew on 2005-04-08
awesome. 

thanks much. 
i'll try it from synaptic and see what i can find out. 

if i blow it up, hey, at least hedgehog came out officially today so i can upgrade!

---

### Post by Francisco on 2005-04-08
[QUOTE=Datchew]awesome. 

thanks much. 
i'll try it from synaptic and see what i can find out. 

if i blow it up, hey, at least hedgehog came out officially today so i can upgrade![/QUOTE]
  Thanks dbott67 for the explanation :)

---

### Post by dbott67 on 2005-04-08
[QUOTE=Francisco]Thanks dbott67 for the explanation :)[/QUOTE]

You're welcome.

-Dave

---

### Post by dbott67 on 2005-04-08
[QUOTE=Datchew]awesome. 

thanks much. 
i'll try it from synaptic and see what i can find out. 

if i blow it up, hey, at least hedgehog came out officially today so i can upgrade![/QUOTE]

You're welcome, too! :)

I'm sitting on the fence for the Hedgehog upgrade.  My laptop has been running pretty good with Warty and I've got everything working.  My understanding is that Hedgehog uses the Xorg system, while Warty uses XFree and I haven't had a chance to investigate the impact of upgrading on the other WMs I've got installed (Gnome, KDE, IceWM, Fluxbox & XFCE).  I've also customized the login and the splash screen, although having to redo them would be good practice.

Does anyone know what the impact of upgrading to Hedgehog will have on other WMs?  Also, I'm running an old Toshiba Tecra 8000 with 256 MB RAM & 8 GB Hard Drive, D-Link DWL-650+ Wifi.  Everything seems to work under Warty, so I don't expect any hardware issues.  

-Dave

---

### Post by dbott67 on 2005-04-09
[QUOTE=dbott67]You're welcome, too! :)

I'm sitting on the fence for the Hedgehog upgrade.  My laptop has been running pretty good with Warty and I've got everything working.  My understanding is that Hedgehog uses the Xorg system, while Warty uses XFree and I haven't had a chance to investigate the impact of upgrading on the other WMs I've got installed (Gnome, KDE, IceWM, Fluxbox & XFCE).  I've also customized the login and the splash screen, although having to redo them would be good practice.

Does anyone know what the impact of upgrading to Hedgehog will have on other WMs?  Also, I'm running an old Toshiba Tecra 8000 with 256 MB RAM & 8 GB Hard Drive, D-Link DWL-650+ Wifi.  Everything seems to work under Warty, so I don't expect any hardware issues.  

-Dave[/QUOTE]

I felll off the fence! :)

I ran the upgrade last night.  I started last night about 9 pm, the download (about 510 MB) finished about 10 PM and the installation was not complete by the time I went to bed at 12 am.  This morning the installation was paused waiting for some input as to whether or not to over-write some config settings, and then it took about another 45 minutes or so to complete.

So, be prepared for a lengthy upgrade process from Warty to Hedgehog for slower machines (P2-300 w/ 256 MB RAM).

I haven't checked KDE, IceWM, Fluxbox & XFCE yet, but I'll let you know.

-Dave

UPDATE:

- KDE Works & looks good. The only problem right now is with my sound card.  I had to fiddle around with a config file to getting working in Warty, so I'm sure I'll have to fiddle some more with Hoary to get it going again.
- XFCE has been updated and looks really nice now.  A big improvement over the other version I had installed, although it runs a little slower.
- Fluxbox and IceWM both work & look the same.

- All customizations appear to have been maintained, so it just looks like the sound card is the only issue.

---

### Post by Datchew on 2005-04-09
i'm still having a bit of trouble creating a bootable install cd. 

I downloaded the iso file and burned it to cd... but it won't boot. 

i thought i might have to make the cd "bootable" but i have no idea which template for a bootdisk to use since i'm burning it in windows.

i have it on cd so i'll try burning it again in ubuntu and see if i can find make it bootable. 

any help would be great. 

I'm gonna try xfce4 on warty this afternoon before i wipe and goto hoary.

---

### Post by dbott67 on 2005-04-09
[QUOTE=Datchew]i'm still having a bit of trouble creating a bootable install cd. 

I downloaded the iso file and burned it to cd... but it won't boot. 

i thought i might have to make the cd "bootable" but i have no idea which template for a bootdisk to use since i'm burning it in windows.

i have it on cd so i'll try burning it again in ubuntu and see if i can find make it bootable. 

any help would be great. 

I'm gonna try xfce4 on warty this afternoon before i wipe and goto hoary.[/QUOTE]

What software in Windows do you use to burn CDs?  Typically, there's a special option for buring ISOs rather than just a straight copy of the ISO.  A straight copy (which is what you might have done would create a single file on the CD called 'whatever.iso').  There's generally a setting to "Create CD from IMAGE" and then you would select the ISO file that you downloaded.

The other thing to check is to make sure that your BIOS is set to BOOT FROM CDROM first.

-Dave

---

### Post by Datchew on 2005-04-09
using nero.  it wouldn't let me use the iso file as a boot template. 

anyway, i had it on a cd already so i went to ubuntu wiki

[http://www.ubuntulinux.org/wiki/BurningIsoHowto](http://www.ubuntulinux.org/wiki/BurningIsoHowto)

and burned it through nautilus in ubuntu and it worked like a champ. 
am running it right now. 
I like it... a little more "refined" and organized than warthog. 
Also, I installed xfce4 and am using it right now!!!

i REALLY like how you can choose between gnome and xfce4 when you login at the startup.  reallllllllly like that.  

thanks much for the tips. 

Datchew.

---

