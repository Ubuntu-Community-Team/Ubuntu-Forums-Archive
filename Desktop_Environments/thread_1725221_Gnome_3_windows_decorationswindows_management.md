---
title: "Gnome 3 windows decorations/windows management?"
date: 2011-04-09
forum: Desktop Environments
---

### Post by Deadboy420 on 2011-04-09
I just installed Gnome 3 shell on Ubuntu 11.04 natty and everything seems to look fine except my windows decorations.  May be something simple I'm missing. Please see screenshot:

[IMG]http://img807.imageshack.us/i/screenshotkc.png/[/IMG]

---

### Post by irv on 2011-04-09
Gnome 3 is quite new and ubuntu 11.04 is still beta, You might have to wait unit the 28th of April and see if the final release fixes it. I haven't try either yet but I have installed Gnome 3 but haven't activated it you. I am on the road and I want to wait until I get home to do this. I am still running 10.10 and I want to see if it will work with this version.

---

### Post by Deadboy420 on 2011-04-09
I was on 10.10 too, but from what I had read Gnome 3 seems to have better compatibility with 11.04 -- even though it's still in beta. 

It just seems that this is a relatively simple problem but I can find nowhere in Gnome a settings option for windows decorations.

---

### Post by irv on 2011-04-09
> **Deadboy420 said:**
> I was on 10.10 too, but from what I had read Gnome 3 seems to have better compatibility with 11.04 -- even though it's still in beta. 

It just seems that this is a relatively simple problem but I can find nowhere in Gnome a settings option for windows decorations.
Like I said I am not using it, but does it use compiz or Metacity? Also is there a way to pick different Themes?

---

### Post by Deadboy420 on 2011-04-09
"GNOME shell uses Mutter, a compositing window manager based on the Metacity window manager, and the Clutter toolkit to provide visual effects and hardware acceleration."

> Also is there a way to pick different Themes? 	

Not that I'm aware of. There is a tweak tool (Gnome3 Tweak Tool) but it doesn't touch windows decorations.
[]("http://en.wikipedia.org/wiki/GNOME_Shell#cite_note-4")

---

### Post by Deadboy420 on 2011-04-10
UPDATE:  I was able to figure out how to change window borders by:

**1) going to: [http://gnome-shell.deviantart.com/gallery/29533997](http://gnome-shell.deviantart.com/gallery/29533997)  **
[B]2) chosing a new theme
3) download and copy the extracted theme folder into /home/*my username*/.themes/      (if there is no ".themes" folder, create one)
4) then opening[/B] [B][I][B]gconf-editor (Alt + F2)
[/B][/I][/B]5) [I][B]Navigating to desktop > gnome > shell > windows
6) On the right side where theme value, enter name of the new theme folder
7)  Reboot 

Now, it's looking good!  I think it may have been an error when upgrading to Gnome 3, I didn't successfully get the offical theme package or one of it's dependencies. I'm still looking into it.
[/B][/I]

---

### Post by Deadboy420 on 2011-04-10
I finally _completely_ fixed my Gnome 3 installation. I started browsing through the gnome 3 packages via Synaptic, and noticed that gnome-themes, gnome-theme-standard, and a few similar weren't installed. Hmmm :rolleyes:   I thought... can't hurt to try.  So I installed every gnome-theme package i could find and.... voila!! \\:D/The default Adwaita theme appeared just like it should've on the first boot. 

I don't know if this was just a fluke thing, not having those packages installed from the start, but I just thought I'd share in case anyone else is having similar problems with Gnome 3 on 11.04 not looking the way it should. 

*P.S.   You may get an error about installing gnome-theme or gnome-theme-standard.  If so, you may have to remove gnome-accessibility-theme first, or whichever package is causing the error. Then install gnome-theme-standard

Cheers! :D

---

### Post by morgue on 2011-04-12
The one that's supposed to fix this issue is gnome-themes-standard
but I don't have it in my packages :(

Any suggestions?

Can you please check what repo you have it on?

---

### Post by irv on 2011-04-12
> **morgue said:**
> The one that's supposed to fix this issue is gnome-themes-standard
but I don't have it in my packages :(

Any suggestions?

Can you please check what repo you have it on?

Do a search for gnome-themes-extras. I am not sure what the PPA is.

---

### Post by morgue on 2011-04-13
> **irv said:**
> Do a search for gnome-themes-extras. I am not sure what the PPA is.

I have this one installed. Still no Adwaita theme :(

---

### Post by JamesPKing on 2011-04-13
I also have this same problem. I have tried changing the gconf-editor to a theme in my /.theme/ folder but still when I load up I get the 'old-fashioned' window decorations... I have tried multiple different themes to try and get this to work; unfortunately I am without success. 

When I try to install 'gnome-theme-extras' I just receive the error: E: /var/cache/apt/archives/gnome-themes-extras_2.22.0-3_all.deb: trying to overwrite '/usr/share/themes/Unity/index.theme', which is also in package unity-theme 0.2ubuntu1

I am using Ubuntu 11.04, which is where that Unity conflict probably arises from, anyone got a fix?

---

### Post by morgue on 2011-04-13
Well according to this
[http://www.ubuntuupdates.org/ppa/gnome_3?dist=natty#](http://www.ubuntuupdates.org/ppa/gnome_3?dist=natty#)

It's on ppa:gnome3-team/gnome3 but it says Natty (11.04), I'm on 10.10. Weird that I have to upgrade, specially since people have been able to get it working on 10.10.

---

### Post by linux_wannabe on 2011-04-13
> **JamesPKing said:**
> I also have this same problem. I have tried changing the gconf-editor to a theme in my /.theme/ folder but still when I load up I get the 'old-fashioned' window decorations... I have tried multiple different themes to try and get this to work; unfortunately I am without success. 

When I try to install 'gnome-theme-extras' I just receive the error: E: /var/cache/apt/archives/gnome-themes-extras_2.22.0-3_all.deb: trying to overwrite '/usr/share/themes/Unity/index.theme', which is also in package unity-theme 0.2ubuntu1

I am using Ubuntu 11.04, which is where that Unity conflict probably arises from, anyone got a fix?
I had a similar problem after installing Gnome3 on Ubuntu 11.04.  When I tried to install the "gnome-themes-standard" package, it said there was an error trying to overwrite a theme in the "highcontrast" theme (can't remember the exact one).  In synaptic, I selected the conflicting package for removal and "gnome-themes-standard" for installation and Walla! when I rebooted it was working!  I don't think the "gnome-themes-extras" package will be critical... try just installed the "standard" package.

---

### Post by JamesPKing on 2011-04-13
> **linux_wannabe said:**
> I had a similar problem after installing Gnome3 on Ubuntu 11.04.  When I tried to install the "gnome-themes-standard" package, it said there was an error trying to overwrite a theme in the "highcontrast" theme (can't remember the exact one).  In synaptic, I selected the conflicting package for removal and "gnome-themes-standard" for installation and Walla! when I rebooted it was working!  I don't think the "gnome-themes-extras" package will be critical... try just installed the "standard" package.

Thanks for that, it now works.

To fix:

```
sudo apt-get purge gnome-accessibility-themes
```
```
sudo apt-get install gnome-themes-standard
```

---

### Post by morgue on 2011-04-13
> **JamesPKing said:**
> Thanks for that, it now works.

To fix:

```
sudo apt-get purge gnome-accessibility-themes
```
```
sudo apt-get install gnome-themes-standard
```

I get
Unable to locate package gnome-themes-standard

---

### Post by CsG_kieran_2 on 2011-04-13
> **JamesPKing said:**
> Thanks for that, it now works.

To fix:

```
sudo apt-get purge gnome-accessibility-themes
```
```
sudo apt-get install gnome-themes-standard
```

I get;

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Whats wrong here?

---

### Post by Krytarik on 2011-04-14
> **CsG_kieran_2 said:**
> I get;

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Whats wrong here?
You have most probably another package manager running at the same time, for example Synaptic.

---

### Post by reebomber on 2011-04-14
> **JamesPKing said:**
> Thanks for that, it now works.

To fix:

```
sudo apt-get purge gnome-accessibility-themes
```
```
sudo apt-get install gnome-themes-standard
```
this worked for me :-)

---

### Post by promet on 2011-04-16
> **Deadboy420 said:**
> I just installed Gnome 3 shell on Ubuntu 11.04 natty and everything seems to look fine except my windows decorations.  May be something simple I'm missing. Please see screenshot:

[IMG]http://img807.imageshack.us/i/screenshotkc.png/[/IMG]

Hello Deadboy420,

Thanks for the instructions. I've followed them and tried to change my theme, but the desktop keeps defaulting to Adwaita. I'm looking into the theme folders and they seem to have subfolders.

The unzipped "Before_Dawn" Theme (the one I manually entered into gconf-editor, as you described) folder has a subfolder titled "metacity-1" which has all of the image files etc. for the theme.

Should these files be copied up into the "root" folder to be seen by the system do you think? How is the folder for the theme you successfully installed structured, does it have subfolders like I described, or are the theme files in the "root" of the theme-named folder. If that makes sense...

Any thoughts would be greatly appreciated, and thanks again, to all you guys, for the informative posts!

cheers

---

### Post by Deadboy420 on 2011-04-19
@promet

Literally all I did was place the full, unzipped "Before_Dawn" folder inside my ".themes" folder as described previously in post #6. I made no other modifications to the folder or copies elsewhere.

You won't already have a ".themes" folder in your /home/username/ by default, so make sure to create one and put the extracted "Before_Dawn" folder in there. That's the only place you need to put the new theme. The only other suggestion I can add is to make sure the theme name you type in gconf-editor is exactly how it's spelled/formated in the .themes folder (ie. "before dawn vs. "Before_Dawn") . 

Also, this is only to change the _windows borders_. Use the Gnome-Tweak-Tool if you want to change gtk theme. 

Are you on 11.04 or 10.10??

---

### Post by thebigredone on 2011-04-20
Thanks guys. Was fighting with this and now it's fixed. :D

---

### Post by pswartout on 2011-04-25
Works a treat - many thanks :)

---

### Post by kjano on 2011-05-14
have the same problem and /usr/lib/gnome-session/gnome-session-check-accelerated; echo $? returns 0 but i cannot even change themes using gnome-tweak-tool anymore. everything was working fine with gnome 3 and themes some days ago but now it is broken.

installing lxappearance does not change anything for me.

sudo apt-get purge gnome-accessibility-themes
sudo apt-get install gnome-themes-standard
also does not help

I also get the message User theme extension not enabled in the tweak tool.

---

### Post by kjano on 2011-05-16
the new gnome 3 ppa update today fixed the problem....and now 10h later it is broken again... :(

---

### Post by rdnetto on 2011-05-30
Thanks for that, 'sudo apt-get install gnome-themes-standard' fixed it for me. It's amazing how many people are neglecting to mention that with the instructions for install gnome-shell.

---

### Post by sonicb00m on 2011-08-03
This fixed my problem too but i had to reinstall gnome-shell and then do alt-f2 , r

---

