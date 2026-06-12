---
title: "XFCE looks so basic, want to make it like Xubuntu screenshot!"
date: 2014-08-27
forum: Desktop Environments
---

### Post by kamhagh on 2014-08-27
my XFCE is so basic and looks like win98, ! i want to make it like this:
[IMG]http://xubuntu.org/wp-content/uploads/2011/09/trusty_whiskermenu.png[/IMG]

how can i make it like this, i searched net , i couldn't find what to do ! i just did sudo apt-get install xfce4!

sorry ! but i couldn't figure it out :(

---

### Post by slickymaster on 2014-08-27
As Whiskermenu is now the default menu in Xubuntu, you can swap out the old application menu with it. Just right click the top panel and navigate to Panel > Add New Items, then select &#8220;Whisker Menu&#8221; and click &#8220;Add&#8221;.
After that, and to remove the old application menu, just right click on its icon and choose the &#8220;Remove&#8221; option.

---

### Post by kamhagh on 2014-08-27
thanks :) im gonna change color too so it looks good+ let me google that wallpaper it looks cool :) thanks

i will also try to make window colors same :)

---

### Post by slickymaster on 2014-08-27
> **kamhagh said:**
> thanks :) im gonna change color too so it looks good+ let me google that wallpaper it looks cool :) thanks

i will also try to make window colors same :)

That is the default wallpaper for Xubuntu, you already have it in your system in the **/usr/share/xfce4/backdrops/** directory.

---

### Post by kamhagh on 2014-08-27
theres no folder name backdrops, i have ubuntu, i installed it with apt-get install xfce4 if that helps!

---

### Post by sisco311 on 2014-08-27
If you don't mind installing some extra packages, then you could install xubuntu-default-settings, which contains the default settings for Xubuntu. It will also install the xubuntu-artwork package which contains the Xubuntu themes and artwork. Once installed, you can select Xubuntu session at the login screen.


For a full Xubuntu experience, you will have to install xubuntu-desktop, a meta-package which  depends on all of the packages in the Xubuntu desktop system, including abiword, bluez, evince, gimp, mousepad, pidgin, xchat and much more.

---

### Post by kamhagh on 2014-08-27
i might put it to download tonight, when i installed a kubuntu-desktop package it made my whole system like i installed kubuntu ! even the splash screen and ect, so i tought its better not to do that, but for my fathers laptop im downloading xubuntu to see if it can run it(i heard its lightweight!) if i liked it there i will get it for mine own pc, its smooth and cool :D i kinda like it :) (im downloading i326 one, It's for my fathers laptop, its a slow stupid 32bit vaio VGN-P530N ! , if i liked it simply i get xubuntu-desktop!)

edit: its so small, im downloading the [COLOR=#000000]xubuntu-default-settings![/COLOR]

---

### Post by kamhagh on 2014-08-27
ok i did it,i still have applications menu ! and the top bar isn't transparent so it the bottom, im doing it manually now ! also i have applications menu

and theres no item names [COLOR=#000000]Whisker![/COLOR]

---

### Post by sisco311 on 2014-08-27
After installing the package, did you log out and select Xubuntu session at the login screen?

---

### Post by kamhagh on 2014-08-27
woops, i tought i did,i did it now, i have app meny and non transparent top panel let me reset setting and do it !

still no whisk let me reboot

---

### Post by sisco311 on 2014-08-27
Oh, for the whisker menu you have to install xfce4-whiskermenu-plugin.

---

### Post by kamhagh on 2014-08-27
i will just get the xubuntu-desktop, i got the splash screen anyway :S is it revertable without deleting the whole xubuntu i downloaded?!

---

### Post by sisco311 on 2014-08-27
To select the graphical splash screen, run:
```

sudo update-alternatives --config default.plymouth

```

The text based splash screen will only show when graphics is not available. You can set the default one with:
```

sudo update-alternatives --config text.plymouth

```

After changing the splash screen you have to update the initramfs:
```

sudo update-initramfs -u

```

---

### Post by kamhagh on 2014-08-27
thanks a lot :D i love this now, i didn't realize the top was transparent :D now everything fine expect i accidentally removed launch bar :D i didn't need it anyway, i will make one myself if i needed it!

i will google a plugin for showing network status, and also which workspace i am on!

---

### Post by kamhagh on 2014-08-28
this is awesome ! im looking xfce as my everday DE :D but anyway, my adventure isn't over yet :D im gonna try other stuff :P

---

### Post by kamhagh on 2014-08-28
i dont want to make another thread for this, but:( i kinda screwed my themes again

i loged into KDE to try something, i went back and saw all my apps now have KDE theme in XFCE ! so i went and deleted .KDE folder and still it was there after some google search i did some stuff, and rebooted , now my XFCE was like, white, not the default theme, i tried many thigns its still like that, the theme is different it bothers me because text doesn't match the theme ! and it looks stupid

also my unity is white now :S my old apps look diffrent ! how can i restore All my DE settings to default ?:(

edit: my kde is also now white and has blue shade, the wallpaper is now debian icon !

edit: i fixed it by re entering KDE and restoring the old setting and going to unity this time only deleting the .gtrc-2.0 file ! if anyone has same probem this fixed it and now everything looks awesome like always xD

---

### Post by lintuxer on 2014-10-14
**Hi kamhagh,**

I think what you want to do is this:
[http://www.slideshare.net/LinuxThemer/xubuntu-with-a-pure-debian-base-from-scratch](http://www.slideshare.net/LinuxThemer/xubuntu-with-a-pure-debian-base-from-scratch)

---

