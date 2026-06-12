---
title: "kubuntu-desktop vs kde?"
date: 2005-12-26
forum: General Help
---

### Post by Hrodebert on 2005-12-26
Whats the difference?
I haven't used Kde in years and I "upgraded" Ubuntu to Kubuntu a couple of days ago.
Now, I have read some comments about how Kde on other distros is, hmm.. different.
Some say it's better. Some even say that the Kubuntu devs have crippled Kde.
And then I realised that some Konqueror menus were missing.
So, I'm beginning to wonder.. What else is hidden or missing?

Is it possible to remove all kubuntu-* and install the bare kde package and then have a clean nonsimplified Kde?
If not, how do I revert back to the original kde settings? Will deleting everything in .kde help?
Also.. checking the kubuntu-default-settings package shows that it contains a LOT of config files. So not counting eyecandy and the crippled Konqueror profiles, what else does it do? What else does it "simplify"? Do I have to edit every config file the default-settings package installed by hand to get a fully functional Kde?

I like Kubuntu, and I don't mind some custom distro-settings.
But to simplify and hide functionality with a default-settings package without having an original-settings package is almost like censorship.. and don't get me started on that.
Censorship is bad, mmkay.

Thanks.

---

### Post by xtacocorex on 2005-12-26
I don't think that KDE is crippled on Kubuntu. I came from Fedora/RedHat (Gnome based) so KDE on those distros might have limited functionality, but I couldn't tell.

The only thing I miss is the right click service menu for refresh.

If you are worried, you could remove all traces of KDE and download the sources and build it yourself which will take quite a while.

---

### Post by strikeforce on 2005-12-27
I find kubuntu-desktop better than kde due to better fonts and the like however thats probably my inability to change things and kubuntu's default looking better than me knowing what to do.

You can remove kubuntu-desktop then manually installing the kde files however I don't recommend it.  I came from ubuntu and then installed kde manually so I know it works.

---

### Post by aysiu on 2005-12-28
I prefer KDE to Kubuntu-desktop.

It didn't take me long to figure out the main differences. Kubuntu-desktop:
1. Has annoying *huge* mouseovers on panel buttons
2. Has no wizard to ask you whether you prefer Windows, Mac, or Linux settings.
3. Has fewer applications

That's pretty much it.

---

### Post by asimon on 2005-12-28
[QUOTE=aysiu]1. Has annoying *huge* mouseovers on panel buttons
[/quote]
These are the exact same tooltips as in vanilla KDE. Kubuntu didn't change these. The new tooltips are from upstream and I like them, they look nice and the blend-in effect looks good too. If you want you can disable them in the "Configure Panel..." dialog. Note that the new tooltips are an upstream change, not a kubuntu speciality.

[QUOTE=aysiu]
2. Has no wizard to ask you whether you prefer Windows, Mac, or Linux settings.[/quote]
Many people think that this wizard is a bad idea usability wise. Anyway you can make all changes in the kcontrol or system settings, thus no functionality is lost.

[QUOTE=aysiu]
3. Has fewer applications
[/quote]
kubuntu-desktop is supposed to install a reasonable complete standard kde desktop. In this context it makes sense to not install every possible KDE application, i.e. stuff like kpovmodeler or ten different kinds of media players and text editors. It also has to fit with the rest of the system on a single CD. Everything not included in kubuntu-desktop can be installed later if one wants.

---

### Post by aysiu on 2005-12-28
[QUOTE=asimon]These are the exact same tooltips as in vanilla KDE. Kubuntu didn't change these. The new tooltips are from upstream and I like them, they look nice and the blend-in effect looks good too. If you want you can disable them in the "Configure Panel..." dialog. Note that the new tooltips are an upstream change, not a kubuntu speciality.[/quote] Actually, tooltips and the huge mouseover balloons are two *different* options. Kubuntu defaults to the huge mouseover balloons. KDE defaults to regular (small) tooltips.

> 
Many people think that this wizard is a bad idea usability wise. Anyway you can make all changes in the kcontrol or system settings, thus no functionality is lost. I prefer the wizard. With one or two clicks, I can get KDE a lot closer to how I like it.

> 
kubuntu-desktop is supposed to install a reasonable complete standard kde desktop. In this context it makes sense to not install every possible KDE application, i.e. stuff like kpovmodeler or ten different kinds of media players and text editors. It also has to fit with the rest of the system on a single CD. Everything not included in kubuntu-desktop can be installed later if one wants. Of course kubuntu-desktop can be tweaked to be like KDE, and KDE can be tweaked to be like kubuntu-desktop. The differences I was referring to are the *defaults*, and I prefer the KDE defaults. Personal preference--that's it.

---

### Post by asimon on 2005-12-28
[QUOTE=aysiu]Actually, tooltips and the huge mouseover balloons are two *different* options. Kubuntu defaults to the huge mouseover balloons. KDE defaults to regular (small) tooltips.[/quote]
Oops, you're right. I thought the old tooltips were replaced by the new effect.

[QUOTE=aysiu]
The differences I was referring to are the *defaults*, and I prefer the KDE defaults. Personal preference--that's it.[/QUOTE]
Yes, I neither like the default look of kubuntu-desktop nor of upstream KDE. There is just no way to please everyone with default preferences.

---

### Post by getaceres on 2005-12-28
The only thing I'm missing are some Konqueror menu entries that's missing in Kubuntu:
1) Tools->Search... So I can search for a file in a directory.
2) Window menu, so I can show the right panel or the integrated console in the konqueror window.

---

### Post by ibook-linux on 2005-12-28
I have never run KDE by itself or through kubuntu so I am unsure of the differences but if it is really bothering you just remove it and try fresh.
You proabably know the commands but for others reading I will post them.

sudo apt-get uninstall kubuntu-desktop
to remove the kubuntu KDE version then just:
sudo apt-get install kde-core

after that you can install what you want and ignore the rest for KDE.
If you really don't like that you can always reinstall the kubuntu desktop.

---

### Post by Adrian on 2005-12-28
[QUOTE=ibook-linux]sudo apt-get uninstall kubuntu-desktop
to remove the kubuntu KDE version then just:
sudo apt-get install kde-core
[/QUOTE]

Unfortunately, it's not that easy since kubuntu-desktop is a meta-package. Check this thread:
[http://www.ubuntuforums.org/showthread.php?t=96048](http://www.ubuntuforums.org/showthread.php?t=96048)

Also, it can be nice to delete everything in the ~/.kde folder to remove previous configuration settings (if that is desired, of course).

---

### Post by Lord Illidan on 2005-12-28
What about KDE 3.5 which you can get from the KDE breezy repos? Has that got limited functionality too? I like it...better and faster than SUSE's KDE..

---

### Post by Hrodebert on 2005-12-29
3.5 is also cripp.. simplified.
I don't like to call it crippled because I understand why they did the way they did. But it's still annoying..
One quick fix here [http://www.ubuntuforums.org/showthread.php?t=77114](http://www.ubuntuforums.org/showthread.php?t=77114)

cp /usr/share/apps/konqueror/konqueror-orig.rc ~/.kde/share/apps/konqueror/konqueror.rc
cp /usr/share/apps/konqueror/profiles/* ~/.kde/share/apps/konqueror/profiles/

---

### Post by christmasisland on 2006-02-21
From the Kubuntu FAQ:

[http://www.kubuntu.org/faq.php#konqueror](http://www.kubuntu.org/faq.php#konqueror)

sudo rm -r /usr/share/kubuntu-default-settings/kde-profile/default/share/apps/konqueror
sudo cp /usr/share/apps/konqueror/konqueror-orig.rc /usr/share/apps/konqueror/konqueror.rc

I'm wondering, there use to be (I thought) a way to left click in a search bar on any webpage to add a keyword search ... it's not there now.  Can I get it back (if it was there)?

---

