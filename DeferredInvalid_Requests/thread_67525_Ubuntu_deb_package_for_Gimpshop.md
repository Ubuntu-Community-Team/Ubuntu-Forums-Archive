---
title: "Ubuntu deb package for Gimpshop"
date: 2005-09-20
forum: Deferred/Invalid Requests
---

### Post by Blue1k on 2005-09-20
After spending some compiling gimpshop from source I made a deb package. The install worked perfectly on my system (Hoary i386 kernel).

Can anyone host this for me?

..oh yah. If it doesn't work for you, you can't come over to my house and punch me in the face. This is my first package but it appears to work fine :-P


**Moved to Backports/Requests for assessment -- KB**

---

### Post by rdwtux on 2005-10-10
Did you ever post the .DEB file?  I'd like to use it

---

### Post by bored2k on 2005-10-10
You can let others test it uploading it to rapidshare.de .

---

### Post by aetheist on 2005-10-12
You'd be a star if you could upload that.. o.o

---

### Post by Blue1k on 2005-10-14
[QUOTE=aetheist]You'd be a star if you could upload that.. o.o[/QUOTE]


LOL..I'll do it this weekend.

BTW the package won't install in Kubuntu..only Ubuntu...I tried :(

---

### Post by Blue1k on 2005-10-16
Ok, the link is:

[http://rapidshare.de/files/6367769/gimp-2.2.8_2.2.8-1_i386.deb.html]("http://rapidshare.de/files/6367769/gimp-2.2.8_2.2.8-1_i386.deb.html")

The package includes gimp with the gimp-shop interface (photoshop)
The package will only work in Ubuntu Breezy and Hoary (not Kubuntu) 

Cheers! :)

---

### Post by Stormy Eyes on 2005-10-21
What good is this? When I downloaded and installed Gimpshop, I thought it would make the GIMP a single-window app.

---

### Post by rdwtux on 2005-10-21
i thought so too.. i couldnt' see much difference so i removed it.

---

### Post by Blue1k on 2005-10-22
Look at the menu structure.. When you open up a file it will have the same layout as Photoshop. 

Sheesh:rolleyes:

---

### Post by Blue1k on 2005-10-22
I made one for Kubuntu Breezy as well. Just make sure to install regular gimp first. :) [http://rapidshare.de/files/6628116/gimp-2.2.8_kubuntu.deb.html]("http://rapidshare.de/files/6628116/gimp-2.2.8_kubuntu.deb.html")

---

### Post by JohnGalt on 2005-11-02
How do I install? I've been wanting to use the gimpshop, thanks

---

### Post by aysiu on 2005-11-02
I installed it with the .rpm with the alien command. I think it was something like ```
sudo alien -i gimpbyme.rpm
``` I, too, found nothing special about it, though. It doesn't look like Photoshop at all. It looks like GIMP.

---

### Post by One2 on 2005-11-06
>  I, too, found nothing special about it, though. It doesn't look like Photoshop at all. It looks like GIMP.
Some menues and the names for certain tools changed that´ s all... I am kind of dissapointed with gimpshop.

---

### Post by jdong on 2005-11-09
cool :)

---

### Post by rdwtux on 2005-11-09
so the question is, is this an official/proper package of the gimpshop project or just a recreation of the menu structure in by an individual?

i have installed gimpshop on windows and although it does look more like gimp than photoshop, it is much different than this package.

---

### Post by jdong on 2005-11-11
DEFERRED for now, until Backports requests are sorted though -- then, I'll take a look for Extras inclusion.

---

### Post by quietglow on 2005-11-23
Just for the heck of it, Photoshop isn't a "single window app" on all platforms! In fact, on the platform on which is originated (mac os), it continues to have lots of windows. I think the point of this project was to make Photoshop pros feel a little more comfy with the GIMP, not make it look like Windows container.

---

### Post by _jB on 2005-12-03
Ye, sure still looks like the old gimp, but I still like it :)

I still prefer if it was a single window app, but for now I just do it like this.
[LIST]
[*]1. Select an unused workspace
[*]2. Load up TheGimp (duh) and select File>New>Some size
[*]3. Right Click toolsbars and set "On Top"
[*]4. Center image window and "Maximize window"
[/LIST]
There You have it, a "single window app" :P

Still not 100% photoshopish, but for now,  it'll do :)

---

### Post by MetalMusicAddict on 2005-12-03
I just want GIMP to minimize all windows if I minimize the main one. My pet pev.

Blue1k. Your avatar is straight out of a "Down and dirty tricks" book for Photoshop. :)

---

### Post by kperkins on 2005-12-04
[QUOTE=MetalMusicAddict]I just want GIMP to minimize all windows if I minimize the main one. My pet pev.

Blue1k. Your avatar is straight out of a "Down and dirty tricks" book for Photoshop. :)[/QUOTE]
There's an option to do this in the development version (2.3.5 is the newest) called transient dock.  It's a little buggy, and may not be able to work correctly with all window managers, but it's what you're looking for, and I installed 2.3.5 on my system with no problems, using the source from gimp.org. (I probably had to install some dependencies, but I don't remeber what they were right off the top of my head.
As far a gimpshop--I've never seen any real advantage to it over regular gimp. (and menus have changed some int the dev version, also--still not the same as PS, but why do people care so much anyways, it's not PS it's Gimp.)

---

### Post by MetalMusicAddict on 2005-12-05
[QUOTE=kperkins]There's an option to do this in the development version (2.3.5 is the newest) called transient dock.  It's a little buggy, and may not be able to work correctly with all window managers, but it's what you're looking for, and I installed 2.3.5 on my system with no problems, using the source from gimp.org. (I probably had to install some dependencies, but I don't remeber what they were right off the top of my head.
As far a gimpshop--I've never seen any real advantage to it over regular gimp. (and menus have changed some int the dev version, also--still not the same as PS, **but why do people care so much anyways, it's not PS it's Gimp**.)[/QUOTE]
I think its because it looks so close. Their is some steps taken by its devs to make PS people more at home ie: ps-menurc but I think people should learn a little more. I can get away from PS because I dropped down money for it so I cant just flush it. I will one day. 

I want to start a site for Ubuntu artist types to help them/me with creating in Ubuntu. Focus on some of the bigger apps. GIMP, Inkscape... Maybe 3D apps. Does that sound nuts? Something like CreativeUbuntu.org?

---

### Post by quietglow on 2005-12-05
(trying to take my mind off this laptop annoyance)

I think that's a fantastic idea, and one I'd very much like to help out with. I've been thinking of trying to do something with organizing all the linux/ubuntu photography helps. I have a bunch of tweaks I use (RAW thumnailing in Nautilis etc.) that I use and I'm sure many others have em' as well. Are you going to make an Ubuntu team?

---

### Post by Owdy on 2005-12-13
Exellent! Thank you! :D

---

### Post by cmlal on 2005-12-18
[QUOTE=MetalMusicAddict]I want to start a site for Ubuntu artist types to help them/me with creating in Ubuntu. Focus on some of the bigger apps. GIMP, Inkscape... Maybe 3D apps. Does that sound nuts? Something like CreativeUbuntu.org?[/QUOTE]

That sounds fantastic! As a person who used to spend a lot of time with Photoshop I feel a little lost in my new Ubuntu environment.

(I've been running Photoshop with the CrossOver trial software but unfortunally it was buggy as hell.)

---

### Post by funkyade on 2006-03-06
Is this .deb still available? 2.2.10 anyone?

Tried getting it from RapidShare but just gets in a loop with a failed request...

Have the source, but would prefer a .deb if possible.

PS in response to the hosting request, I can host the files for free (funkyfish.net) so long as I can get hold of the .debs...!

hth

---

### Post by e2k on 2006-03-09
[QUOTE=funkyade]Tried getting it from RapidShare but just gets in a loop with a failed request...[/QUOTE]
It worked for me just now.. Try again, and if it doesn't work PM me with your email and I'll send it to you :cool:

---

### Post by zodwallop on 2006-06-29
Does anyone know if this is the most recent .deb package for GIMPShop?  I wasn't able to find one for the most recent version, 2.2.11.

---

### Post by mzm2000 on 2006-07-07
Hi all,

Just found gimpshop 2.2.11 deb package available for download here.
[http://linux.suramya.com/tutorials/Install_GIMPShop/]("http://linux.suramya.com/tutorials/Install_GIMPShop/")

Some notes:
[LIST]
[*]You need to uninstall gimp before you install gimpshop. try:  ```
apt-get remove gimp
``` and / or ```
apt-get remove gimp-data
``` to remove gimp if u have it installed.
[*]I needed to satisfy dependency libgimpprint1 before i could install. ```
apt-get install libgimpprint1
```
[*]The cant seem to find where the menu.xml file is and spits out an error.. ```
Failed to open file '/home/suramya/Temp/GimpShop/gimpshop//share/gimp/2.0/menus/image-menu.xml'
``` ive contacted the author and he is very helpful. I will re-post with his suggestions here.
[/LIST]
Ive attached a screencap of the current setup with error messages .. anyone else know whats going on here?

---

### Post by giuliastro on 2006-07-15
Same error here. Any workarounds?

---

### Post by giuliastro on 2006-07-16
I managed to create a checkinstall deb file with latest compiled version of Gimpshop.
You can find packages [here]("http://www.4shared.com/dir/592434/a2bc9508/gimpshop.html"). You might need to install the included *libgimpprint1* and install XML parser by using: **cpan -i XML::Parser**. I am not that sure wether this is mandatory or not, please let me know. Uninstall Gimp before installing!

[[IMG]http://img96.imageshack.us/img96/2249/schermatari1.th.png[/IMG]](http://img96.imageshack.us/my.php?image=schermatari1.png)

---

### Post by marcusg on 2006-07-30
using the package worked fine for me on Ubuntu 6.06
thanks alot.

---

### Post by megamads on 2006-08-04
I had trouble using the .deb package from the Suramyasite, getting the same xml-errors as described by mzm2000.

Using giuliastro's build however, everythings is dandy! Thanks alot :)

---

### Post by SamuelDr on 2006-08-04
wow, giuliastro's works really well!!!

would it run only on ubuntu, or would it run under any debian?

---

### Post by GadgetsGuy on 2006-09-19
I clicked on every .deb link in this thread and they all seem to have been removed?  :(

---

### Post by czer323 on 2006-09-20
I found a direct link to 2.2.11:
[http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb](http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb)

Uninstalled gimp and gimp-data.  Installing GimpShop.  It didn't put a link in my applications>Graphics menu bar, but no biggy.

Running "gimp" from a command line or adding it to a launcher works just fine for me.  Everything looks great.

---

### Post by SeanIM on 2006-10-27
Do you really need to uninstall Gimp and reinstall to get Gimpshop to load?

Reason I ask is that I let the package manager install the .deb file from the plasticbugs location and now when I start Gimp I get the Gimpshop intro...

Admittedly I'm no Gimp pro so I'm having a hard time figuring out what exactly may have changed.

Thanks.

---

### Post by synaptyx on 2006-10-27
> **giuliastro said:**
> I managed to create a checkinstall deb file with latest compiled version of Gimpshop.
You can find packages [here]("http://www.4shared.com/dir/592434/a2bc9508/gimpshop.html"). You might need to install the included *libgimpprint1* and install XML parser by using: **cpan -i XML::Parser**. I am not that sure wether this is mandatory or not, please let me know. Uninstall Gimp before installing!Thanks for that giuliastro! It worked perfectly on my Dapper Drake Kubuntu install. And for us inexperienced users, I found this way to put an icon on your desktop...

Run these commands (you may have to put "sudo" before them):```
ln -s /usr/local/bin/gimp-2.2 /usr/bin/gimpshop
ln -s /usr/local/bin/gimp-remote-2.2 /usr/bin/gimpshop-remote
```

Now for elementary stuff for the real n00bs (like me)...

Add a desktop icon:

a) Right click anywhere in the desktop and select: Create New > File > Link To Aplication
b) In the "General" tab write the name of the application (should be GIMPshop)
c) Click in the "square" icon to customize it, and, by selecting "Other Icons", choose Gnome-Gimp as your application icon.
d) Select the "Application" tab and write gimpshop in the "Command" space.

Want it on the Graphics menu? No problemo:

a) Click 'K' button
b) Right click 'Graphics' menu
c) Click 'Edit Menu'
d) Drag your shiny new 'Gimpshop' icon onto the 'Graphics' menu
e) Click 'Save' (floppy disc icon) and you're done :D

---

### Post by gkoshra on 2006-11-02
Hi, i'm very new at this and really want to use gimp for my photo stuff. I am a heavy user of photoshop and am really interested in gimpshop.

So, will this work on Xubuntu? I really like xfce.

Thanks.

---

### Post by Djainette on 2006-12-14
Hello all.

I'm interested in gimpshop but several points seem weird to me. 
I know that the original program is a Mac application, and that the linux binary is made from its source code. But isn't it a problem, in order to keep an up-to-date gimp ? 
Gimp uninstallation is required to install Gimpshop. What if many users share the same machine ? Maybe some would want the original gimp, and maybe others would rather use gimpshop.

Gimpshop is released with the GPL licence. So would it be possible to turn it into a gimp extension ? So that gimp may still be updated without gimpshop being "late", and so that users may switch between gimp and gimpshop ?
like : intalling gimpshop on top of gimp (like a GUI on a command tool)
and then switch by using two differents executables...

---

### Post by jehnx on 2006-12-14
I've got a .deb available to download now of 2.2.11 up at [www.GIMPshop.com](http://www.gimpshop.com/).  Also source files and other such resources.  :)

---

### Post by binklespup on 2006-12-21
You guys could use a bittorent tracker to host your apps, demonoid has a fair amount of linux stuff,
[http://www.demonoid.com/files/]("http://www.demonoid.com/files/")

---

### Post by thechanklybore on 2007-01-05
> **Djainette said:**
> Hello all.

I'm interested in gimpshop but several points seem weird to me. 
I know that the original program is a Mac application, and that the linux binary is made from its source code. But isn't it a problem, in order to keep an up-to-date gimp ? 
Gimp uninstallation is required to install Gimpshop. What if many users share the same machine ? Maybe some would want the original gimp, and maybe others would rather use gimpshop.

Gimpshop is released with the GPL licence. So would it be possible to turn it into a gimp extension ? So that gimp may still be updated without gimpshop being "late", and so that users may switch between gimp and gimpshop ?
like : intalling gimpshop on top of gimp (like a GUI on a command tool)
and then switch by using two differents executables...


Eh? Gimp was never originally a Mac application - what gave you that idea? It's been Linux first all the way. 

Unfortunately as far as I'm aware Gimp doesn't allow you to change the interface from extensions and/or plugins - so the answer is no you can't do this.

---

### Post by medievalmutt on 2007-01-05
> **thechanklybore said:**
> Eh? Gimp was never originally a Mac application - what gave you that idea? It's been Linux first all the way. 

I suppose he means "gimpshop" was originally made for the Mac (because the author's a Mac user).

---

### Post by Djainette on 2007-01-07
> **medievalmutt said:**
> I suppose he means "gimpshop" was originally made for the Mac (because the author's a Mac user).
Yes, that's what I meant.

---

### Post by MrDetermination on 2007-03-10
2.2.11 on a fresy edgy install: dependency is not satisfiable: libgimpprint1

---

### Post by wxnker on 2007-03-11
Had the same problem with the former deb package - 2.2.11.

This works:
[http://www.plasticbugs.com/blogimg/g....11-1_i386.deb](http://www.plasticbugs.com/blogimg/g....11-1_i386.deb)

---

### Post by RobbieCrash on 2007-05-06
That link does not work.

---

### Post by mlitty on 2007-05-16
Here's another site with instructions and a deb package that seems to work well on Feisty Fawn (7.04).  It says that it's for Xubuntu, but I installed it with no problem on Ubuntu, and I suspect it will install on any compatible derivative.

[http://www.packetmonster.net/gimp_shop_install_on_xubuntu]("http://www.packetmonster.net/gimp_shop_install_on_xubuntu")


I hope this helps.
~mlitty

---

### Post by sweeney276 on 2007-05-29
Some people here have misunderstood the purpose of GIMPshop. The GIMP already includes most of the functionality of Photoshop, but for somebody used to using Photoshop, this functionality is sometimes hard to find, hence GIMPshop.

It is merely a restructuring of menus and a renaming of certain functions so that people used to Photoshop will find their way around the GIMP more easily.  It is not, and is not intended to be, a clone of Photoshop.

Personally, I have found The GIMP all I need for my photographic needs, but it is a program that needs to be learnt how to use.  I find GIMPshop most useful when "converting" instructions in photography magazines that are meant to be for Photoshop; its not perfect but it does help.  However, for maximum use of The GIMP you need to get a good book on The GIMP and learn how to use it as a stand alone program, but GIMPshop can be looked upon as an interface which makes the conversion from Photoshop to The GIMP much easier.

After all, The GIMP is the de facto standard for Linux and FOSS image editing, so if you want to use Photoshop get a Windows box, but to help you on the road to getting complete mastery of The GIMP, GIMPshop can help.

---

### Post by Larkshall on 2007-08-16
My biggest problem with the Gimp is that it doesn't include a "Smart Erase" like the MS Digital Image suite 10. Perhaps that would be a better improvement than changes to the GUI. It doesn't seem to have a "Clone" tool either.

---

### Post by bogolisk on 2007-08-16
> **Larkshall said:**
> My biggest problem with the Gimp is that it doesn't include a "Smart Erase" like the MS Digital Image suite 10.


Would you mind explain what that tool suppose to do? (just curious) Gimpers are not necessary familiar with PS and even less with MS Digital Image suite 10. My wild guess right now is you can probably do the same thing with layers and painting on the mask.

> Perhaps that would be a better improvement than changes to the GUI. It doesn't seem to have a "Clone" tool either.

I use gimp-2.3.18 (gutsy source package rebuilt on feisty) and it has "clone", "heal", "air-brush", etc.

---

### Post by bogolisk on 2007-08-16
> **sweeney276 said:**
> Some people here have misunderstood the purpose of GIMPshop. The GIMP already includes most of the functionality of Photoshop, but for somebody used to using Photoshop, this functionality is sometimes hard to find, hence GIMPshop.

It is merely a restructuring of menus and a renaming of certain functions so that people used to Photoshop will find their way around the GIMP more easily.  It is not, and is not intended to be, a clone of Photoshop.

Personally, I have found The GIMP all I need for my photographic needs, but it is a program that needs to be learnt how to use.  I find GIMPshop most useful when "converting" instructions in photography magazines that are meant to be for Photoshop; its not perfect but it does help.  However, for maximum use of The GIMP you need to get a good book on The GIMP and learn how to use it as a stand alone program, but GIMPshop can be looked upon as an interface which makes the conversion from Photoshop to The GIMP much easier.

After all, The GIMP is the de facto standard for Linux and FOSS image editing, so if you want to use Photoshop get a Windows box, but to help you on the road to getting complete mastery of The GIMP, GIMPshop can help.

I do agree with the above. However, "gimpshop" is kind of a forbidden word on the gimp mail-lists.

[https://lists.xcf.berkeley.edu/lists...ly/010449.html](https://lists.xcf.berkeley.edu/lists...ly/010449.html)
> ...It's a forked version and the person who did that fork refuses to work with the GIMP developers...
[http://wiki.gimp.org/gimp/GimpShop](http://wiki.gimp.org/gimp/GimpShop)
> ...Support for GIMPshop must come from the GIMPshop developers. Please avoid asking questions specific to GIMPshop on the GIMP mailing lists, because the differences between both programs usually cause a lot of confusion...

I'm not saying not to use gimpshop, but just don't ask gimpshop questions on gimp lists.

---

### Post by Chudilo on 2007-08-21
I downloaded it from [http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb]("http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb")

It installed using "gdebi"
no missing packages.

---

### Post by xyverz on 2007-09-04
Ergh.  I posted the link before I saw the latest reply.  You can ignore this post.  *sigh*

--X...

---

### Post by geovino on 2007-09-14
I just installed gimpshop 2.2.11 from the Plastic Bugs site. It installed OK but when I go to Gimp it opens with a Gimpshop splash screen then goes to Gimp. Gimpshop is not listed in the menu and typing gimpshop as a command line does nothing. How would I open it? or how do I uninstall it?

---

### Post by jackatothemon on 2007-09-17
You, Blue1k are a wonderful man, I was looking for a way to install that easliy for a very long time. :)

---

### Post by MeanderingCode on 2007-10-17
> **geovino said:**
> I just installed gimpshop 2.2.11 from the Plastic Bugs site. It installed OK but when I go to Gimp it opens with a Gimpshop splash screen then goes to Gimp. Gimpshop is not listed in the menu and typing gimpshop as a command line does nothing. How would I open it? or how do I uninstall it?

```
gimp
```
on the command line.

I'm running Xubuntu Feisty, installed via gdebi with .deb from the rapidshare link on gimpshop.com (404 on mirror.suramya).  runs from cli just fine. 

I, however, cannot find it in the XFCE Menu.  The Gimp has always shown up under Graphics.

Anyone else noticing this or know a way to help XFCE along?

Thanks.

---

### Post by icodeme on 2008-11-03
Thanx for the file :)

---

