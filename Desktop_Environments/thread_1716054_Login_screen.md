---
title: "Login screen"
date: 2011-03-27
forum: Desktop Environments
---

### Post by Inygknok on 2011-03-27
So I've been trying to search for a theme for my login screen in Ubuntu Maverick.  I've found a few themes that are very attractive but they usually have some detail that I find intrusive or unattractive.  FOr example this one:

[http://gnome-look.org/content/show.php/Debian+Future?content=114987](http://gnome-look.org/content/show.php/Debian+Future?content=114987)

Changing the wallpaper it has is simple, but I would like to remove the "Welcome" message it has.  Maybe just make it display the PC name and a symbol next to it (perhaps the Ubuntu 10.10 red circle symbol?).  It's an idea.  There's also a great looking Iron Man login screen I found on the website but it has never allowed me to download it; it's pretty much the only one I wouldn't modify at all.

So can anyone guide me into how I would go about editing this theme or making one from scratch?  I'm very intrigued in learning if it's not a 10 in a 1-10 difficulty rating.  Most of the threads I've run into are old and one of them even forced me into having to re-install Ubuntu all over again after it wouldn't boot up at all.  I really rather ask and have someone guide me than getting frustrated again (and not being able to convince my girlfriend to install it on her laptop so she'll stop getting viruses in Win7).

---

### Post by galacticaboy on 2011-03-27
I tired this at one point, I got the wallpaper changed but everything else I could not. From what I have read and understand is that in the newest version of Ubuntu they have disabled all ability to change the login theme. The only things you can personalize it the logo, the wallpaper, and your user picture, that is it. Keep searching though, there has to be a way!

---

### Post by Inygknok on 2011-03-27
Maybe diving into one of the themes and editing each thing manually?  If that can be done and someone guides me through the process (to know what each file does) then I really wouldn't mind trying it out and posting results.  I've been at this for 2 days now.  Used Ubuntu Tweaks but that only allows you to change the wallpaper and icon (no interface). 

GDM2Setup won't download in Maverick at all.

---

### Post by Krytarik on 2011-03-27
I hate to destroy your hopes about being able to do more comprehensive modifications to the login screen, but see my earlier post regarding that:
[http://ubuntuforums.org/showthread.php?p=10468340](http://ubuntuforums.org/showthread.php?p=10468340)

Greetings.

---

### Post by Copper Bezel on 2011-03-28
I don't understand. Did the Debian Future theme apply and do what it says on the box? If so, it's just a .xml document and some indexed .pngs. He could edit any part of that freely. The welcome message would just be a string of text in the xml.

I've never tried this personally - I'm just using the Crunchybranch login screen from Gnome-Look, although I did change the panel and login window theme to Orta using GDM2 Setup.

---

### Post by Inygknok on 2011-03-28
> **Copper Bezel said:**
> I don't understand. Did the Debian Future theme apply and do what it says on the box? If so, it's just a .xml document and some indexed .pngs. He could edit any part of that freely. The welcome message would just be a string of text in the xml.

I've never tried this personally - I'm just using the Crunchybranch login screen from Gnome-Look, although I did change the panel and login window theme to Orta using GDM2 Setup.

GDM2 won't install on Maverick though  :/

I'm going to download the Debian Future theme now and I'll let you know what happens.

---

### Post by Copper Bezel on 2011-03-28
Cool.

I have no idea how I got GDM2 Setup installed on my machine. I'm most definitely using Maverick, and I'm pretty sure I installed it after I upgraded. It apparently has the ability to bork your login settings on Ubuntu, which sounds rather serious, although I haven't seen it happen. It overwrites your login settings with the wrong cases (but running the normal Login Window settings manager afterward fixes them.)

Installing it *did* disallow Ubuntu Tweak to change the computer icon in GDM Setup, and it can't be changed in GDM2, and for whatever reason, it fixated on the Xubuntu mouse head logo, so that I eventually had to search my system for all images with "Xubuntu" in the path and overwrite it with the logo I wanted.

Maybe GDM2 isn't actually a very good solution. Let's see what happens with that theme. = )

---

### Post by Inygknok on 2011-03-28
I searched a bit more and ran across this:
[http://ubuntuforums.org/showpost.php?p=10316888&postcount=2](http://ubuntuforums.org/showpost.php?p=10316888&postcount=2)

[http://ubuntuforums.org/showthread.php?t=1572705](http://ubuntuforums.org/showthread.php?t=1572705)

[http://ubuntuforums.org/showthread.php?p=10605710#post10605710](http://ubuntuforums.org/showthread.php?p=10605710#post10605710)


Apparently, one method is to downgrade to an older GDM version.  Another way is just to use in unison both GDM2setup and Ubuntu Tweak.  Downgrading the GDM is something I'd rather not do as I'm way too new to know what to do if I mess something up.  I already have Ubuntu Tweak and played around with it a bit, but can't find anything about how to install GDM2setup on Maverick.  I'll keep looking.

I downloaded the theme by the way, but all I can find via Google search on how to install themes is either methods in older Ubuntu releases or using GDM2 along with Ubuntu Tweak.

Anybody else got any idea how to get GDM2setup to install on Maverick?

---

### Post by Copper Bezel on 2011-03-28
My GDM is 2.30.5-0ubuntu4. That's the most recent version for Maverick at packages.ubuntu.com. My GDM2 Setup is [this]("http://pypi.python.org/pypi/gdm2setup/0.5.3-karmic") one, and it's only supported through Lucid but still works.

---

### Post by Inygknok on 2011-03-28
Oooooh, looks like I'll finally have the chance to sit down and learn how to compile from source.  Thanks for the incentive.  Let's see how this goes.....

Before I begin, is this a good guide I should follow or should I find a more modern one?

[http://ubuntuforums.org/showthread.php?t=323939](http://ubuntuforums.org/showthread.php?t=323939)

---

### Post by Copper Bezel on 2011-03-28
I've never had much luck. Does this not work?

```
sudo add-apt-repository ppa:gdm2setup/gdm2setup
sudo apt-get update
sudo apt-get install python-gdm2setup
```

---

### Post by Inygknok on 2011-03-28
> **Copper Bezel said:**
> I've never had much luck. Does this not work?

```
sudo add-apt-repository ppa:gdm2setup/gdm2setup
sudo apt-get update
sudo apt-get install python-gdm2setup
```

Nope.  Fails to fetch.

---

### Post by Krytarik on 2011-03-28
If you really feel the need to install/use GDM2Setup, just download it from here and install it manually with GDebi:
[https://launchpad.net/~gdm2setup/+archive/gdm2setup/+buildjob/1571217]("https://launchpad.net/%7Egdm2setup/+archive/gdm2setup/+buildjob/1571217")

You could also manually add the Lucid repo to your sources, but since the developer apparently ceased its development anyway, it wouldn't really make sense.

---

### Post by Inygknok on 2011-03-28
> **Krytarik said:**
> If you really feel the need to install/use GDM2Setup, just download it from here and install it manually with GDebi:
[https://launchpad.net/~gdm2setup/+archive/gdm2setup/+buildjob/1571217]("https://launchpad.net/%7Egdm2setup/+archive/gdm2setup/+buildjob/1571217")

You could also manually add the Lucid repo to your sources, but since the developer apparently ceased its development anyway, it wouldn't really make sense.
Will that work just fine with 64-bit Maverick?

Also, pardon my ignorance but what's GDebi?

---

### Post by Krytarik on 2011-03-28
> **Inygknok said:**
> Will that work just fine with 64-bit Maverick?

Also, pardon my ignorance but what's GDebi?
LOL:D Does it work fine *at all*?!

I guess there is no difference if you install it to the 32 or 64 bit version of Ubuntu.

If you want to try it, click at the download link, then simply choose "Open with GDebi".
[https://help.ubuntu.com/community/InstallingSoftware#Using%20GDebi%20to%20install%20packages]("https://help.ubuntu.com/community/InstallingSoftware#Using%20GDebi%20to%20install%20packages")

Why don't you just follow the guide I posted earlier, it lets you change everything (what is possible), you don't need to install another app, and it doesn't screw up your GDM config.

---

### Post by Copper Bezel on 2011-03-28
> LOL :D Does it work fine at *all*?!

Yeah, I mentioned the case-switching and the XFCE fixation, right? = ) But to be fair, my login window is pretty *now*. It has Orta and ponies.

But yeah, if it's not going to work on 64 bit (I'm on 32) GDebi won't allow it to be installed at all.

---

### Post by Inygknok on 2011-03-28
I'm following Krytarik's guide at the moment.  I'm new to Linux so I'm triple checking every single instruction.  So far so good.  I patted myself on the back for changing the Grub splash screen.  Thanks for the help so far guys!  I'll keep working on this for a bit longer and tomorrow night and let you guys know how it goes.

Help in these forums really is top notch.  I can honestly say that people who give up on Linux and go back to Windows (heavy gamers and heavy-duty gfx designers excluded) either just don't follow instructions or want everything handed to them on a diamond platter.  I'm not saying this is a 1 on a 1-10 difficulty scale, but if people find this overly complicated, I'd like to see the expression on their faces after being told to take apart and reassemble an entire transmission.

---

### Post by Krytarik on 2011-03-28
> **Inygknok said:**
> 
Help in these forums really is top notch.  I can honestly say that people who give up on Linux and go back to Windows (heavy gamers and heavy-duty gfx designers excluded) either just don't follow instructions or want everything handed to them on a diamond platter.  I'm not saying this is a 1 on a 1-10 difficulty scale, but if people find this overly complicated, I'd like to see the expression on their faces after being told to take apart and reassemble an entire transmission.
+1 for that. I'm under the impression that the majority of users, that happens to be Windows users, are either not willing or able to invest the slightest bit of brain activity to switch to another OS. They are paying for that with
1.) money
2.) dependence on a single vendor
3.) being an easy target of malware
4.) lag of customizability
5.) certain lag of stability
6.) ignorance of what the OS does
7.) inability to gain knowledge about that

Greetings.

---

### Post by Inygknok on 2011-03-28
I'm having a slight problem in one of the guides:
[http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html](http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html)

I managed to change the wallpaper and text colors just fine.  I kept reading and tried to change the text fonts.  I got a new font and installed it correctly (checked with Gedit and OPenOffice).  I put it in /.fonts/ but once I try to navigate to it via the Terminal, it won't show up.  I can view the font files just fine with Nautilus, but no go with the Terminal.

I thought this was an error of sorts so just proceeded with the instructions given in the rest of the guide to change fonts, but now the wallpaper disappeared and the Grub menu has the original, big and blocky look.

---

### Post by Krytarik on 2011-03-28
You don't see the font file when you run this command?:
```
ls -al ~/.fonts
```Please post the contents of
- "/boot/grub/grub.cfg"
- "/etc/default/grub"
- "/etc/grub.d/05_debian_theme"
In code-tags please, the #-button in the editor.

Also, please note the path to your splash image file.

---

### Post by Inygknok on 2011-03-29
Finally able to sit down in front of the pc.  Just noticed that to get the actual directory I had to type "~/.fonts" and then tab complete instead of "/.fonts".

Now I'm stuck at another section of the guide though.  Where it says:

[B]2) Open your terminal and run the grub-mkfont command,
[/B]```
sudo grub-mkfont --output=/boot/grub/zekton.pf2 --size=14 /usr/share/fonts/truetype/ttf-larabie/zektondo.ttf             
```The font I want is called orbitron-medium.ttf, so I replaced the above code as the following:
```
sudo grub-mkfont --output=/boot/grub/orbitron-medium.pf2 --size=14 /home/thestig/.fonts/orbitron-medium.ttf
```

I get the following message:
[I]```
Unknown gsub feature 0x73616c74 (salt)
Unknown gsub feature 0x736d6370 (smcp)
Unknown gsub feature 0x73733031 (ss01)
Unknown gsub feature 0x73733032 (ss02)
Unknown gsub feature 0x73733033 (ss03)
```


What you requested:
[/I]```
thestig@DEATHSTAR:~$ ls -al /boot/grub/grub.cfg
-r--r--r-- 1 root root 5115 2011-03-28 18:36 /boot/grub/grub.cfg
thestig@DEATHSTAR:~$ ls -al /etc/default/grub
-rw-r--r-- 1 root root 1185 2011-03-28 18:35 /etc/default/grub
thestig@DEATHSTAR:~$ ls -al /etc/grub.d/05_debian_theme
-rwxr-xr-x 1 root root 1471 2011-03-28 17:15 /etc/grub.d/05_debian_theme

```

The splash image for the grub menu is in the "/usr/share/images/grub/" directory.

---

### Post by Krytarik on 2011-03-29
1.) Regardless of the errors, it might be that the font file will work, just try it.

2.) I requested the **contents** of those files, because you said that everything is back to the default, and obviously I can't help troubleshooting without any details.

---

### Post by Inygknok on 2011-03-29
I went ahead and finished the process like you said to try it out.  It worked  :)

THanks a lot for helping me out.  Got any other nifty guides to customize other things?  For example, the desktop environment.  My girlfriend hates to have "APplications Places System" at the top.

---

### Post by Copper Bezel on 2011-03-29
That part you can actually change by right-clicking the menu, selecting Remove from Panel, and then right-clicking where it was, selecting "Add to Panel," and selecting the Gnome Menu, which operates a bit more like a Windows Start menu, from the list. 

If you want to use an alternate Main Menu or make even more dramatic changes to the interface, there are tutorials for that, too, as the Gnome Panels are very customizable; you might want to look into installing GnoMenu, which is an auto-populating, searchable menu quite a bit like the one in Windows 7. Personally, I use an alternative panel called Avant Window Navigator in place of the Gnome panels.

> +1 for that. I'm under the impression that the majority of users, that happens to be Windows users, are either not willing or able to invest the slightest bit of brain activity to switch to another OS. 

Linux users also tend to have a hobbyist sensibility that Windows users don't necessarily have, which makes this sort of thing fun in a way it isn't to most Windows users. Of course the system's customizability and its tendency to teach the user a bit of computer science along the way seem to encourage that.

---

### Post by Krytarik on 2011-03-29
Cool that it worked!
> **Copper Bezel said:**
> That part you can actually change by right-clicking the menu, selecting Remove from Panel, and then right-clicking where it was, selecting "Add to Panel," and selecting the Gnome Menu, which operates a bit more like a Windows Start menu, from the list. 
Actually those is called "Main Menu". It's quite nice, not the Windows style like GnoMenu has. However I still prefer the default menus, because I access them quite often, and don't want to add another submenu layer.
> **Copper Bezel said:**
> If you want to use an alternate Main Menu or make even more dramatic changes to the interface, there are tutorials for that, too, as the Gnome Panels are very customizable; you might want to look into installing GnoMenu, which is an auto-populating, searchable menu quite a bit like the one in Windows 7.
See here: [http://www.ubuntugeek.com/gnomenu-consolidated-menu-for-gnome.html](http://www.ubuntugeek.com/gnomenu-consolidated-menu-for-gnome.html)

---

### Post by Copper Bezel on 2011-03-29
Oh, I agree - I very much like having a Places menu to pull up a shortcut location (usually my Dropbox or the sort of catchall folder I use for whatever I'm doing at the moment.) Sorry about the mistake with the name of the regular menu.

---

### Post by Inygknok on 2011-03-29
Thanks guys :)

I'll be looking into those links once I get back home.  I'm going to sit my gf down and have her give this a shot and finally judge on how simple it is in reality.

This all feels like the first time I was taught how to work on an engine, without the grease.

---

### Post by Inygknok on 2011-03-30
After sitting down, I thought I'd like to share something else I ran into for other users that have recently migrated to Ubuntu from Win7.

[http://gnome-look.org/content/show.php/DockbarX?content=101604](http://gnome-look.org/content/show.php/DockbarX?content=101604)

It takes a bit to set up (in terms of time), but once you do, it gives you a dockbar extremely similar to Win7's with better customizations.  And this is just after about 4-5 days of using Ubuntu.  Imagine what you could learn after just a month, and then some.

---

### Post by Krytarik on 2011-03-30
Although this is obviously a bit off the original topic (not to mention the previous Grub thing), you should check this out, regarding DockbarX and Avant Window Navigator (AWN):
[http://ubuntuforums.org/showthread.php?t=1685924](http://ubuntuforums.org/showthread.php?t=1685924)
[http://ubuntuforums.org/showthread.php?t=1714111](http://ubuntuforums.org/showthread.php?t=1714111)

And maybe also this:
[http://ubuntuforums.org/showthread.php?t=1715155](http://ubuntuforums.org/showthread.php?t=1715155)

---

