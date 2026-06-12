---
title: "I want mini install, but original Ubuntu GTK look with Openbox"
date: 2012-12-17
forum: Desktop Environments
---

### Post by zgemba on 2012-12-17
Hello,

I used ubuntu mini CD to to console install because I don't want to many software on my PC, and want Openbox as my WM.

After CLI I installed x.org and after that openbox, firefox and thunar. I did this before on older ubuntu releases and faced the same problem. GTK apps look ugly in openbox and some apps have missing icons.

Before I used lxappearance, but it seems messed up in 12.10 so I installed various gnome parts till I ended up installing all ubuntu-desktop which installed million other apps I don't want and bloated the system.

The GTK apps now have nice look in Openbox but the system is bloated. I am going to reinstall everything again, but I didn't figure out what part of gnome fixed the look and feel of GTK apps.

I tried several gtk theme switchers, installed various themes and icons packs but they all do their work buggy in 12.10.

Is there a way to have a nice polished look&feel of default ubuntu installation, but just with CLI + Xorg + Openbox. As I see it, ubuntu now uses GTK3 and I need to choose GTK3 and GTK2 compatible theme and icons.

I really like the default once that come with ubuntu, could you help me to get them in Openbox.

TIA,
Zgemba.

---

### Post by zgemba on 2012-12-17
The closest to the solution that I could come is gtk3-engines-unico (is this the 12.10 default theme/engine, does it cover also gtk2 applications and should I install murine theme/engine or whatever and do customization separately fot GTK3 and GTK2 apps).

---

### Post by ibjsb4 on 2012-12-17
> I really like the default once that come with ubuntu, could you help me to get them in Openbox.

Using the mini.iso and installing minimal classic with metacity, the default theme is "Adwaita".

[ATTACH]228797[/ATTACH]

---

### Post by zgemba on 2012-12-17
> **ibjsb4 said:**
> Using the mini.iso and installing minimal classic with metacity, the default theme is "Adwaita".

[ATTACH]228797[/ATTACH]

Did you manage to do it on 12.10?

---

### Post by ibjsb4 on 2012-12-17
> **zgemba said:**
> Did you manage to do it on 12.10?

I run 12o4.  But wouldn't it be the same?

---

### Post by zgemba on 2012-12-17
> **ibjsb4 said:**
> I run 12o4.  But wouldn't it be the same?

I did the 12.10 mini install, and now I'm trying to have a nice GTK theme (GTK2 and 3 compatible) for GTK apps. But no matter what I do apps still have that ugly default grey theme.

I installed xorg/openbox and after that theme engines and couple of themes. I used lxappearance and all gnome theme switchers that I could find but no luck.

This process worked flawless on 12.04. I just don't want to install all gnome components, I'm trying to do this with smallest possible requirements.

Maybe I'm missing something. I'll try it virtually with Arch or Debian.

---

### Post by ibjsb4 on 2012-12-17
Gnome-color-chooser use to be a wonderful tool, but didn't work very good last time I tried it in 12o4.  Maybe the PPA would work better and give you the results your looking for.

[https://launchpad.net/gnome-color-chooser](https://launchpad.net/gnome-color-chooser)

---

### Post by zgemba on 2012-12-17
> **ibjsb4 said:**
> Gnome-color-chooser use to be a wonderful tool, but didn't work very good last time I tried it in 12o4.  Maybe the PPA would work better and give you the results your looking for.

[https://launchpad.net/gnome-color-chooser](https://launchpad.net/gnome-color-chooser)

Nope, doesn't work.

Does anyone know how to install a console line minimal ubuntu installation, then xorg with any manager other than gnome and then to apply GTK theme for apps.

---

### Post by LarsKongo on 2012-12-17
```
sudo apt-get install --no-install-recommends light-themes
```
Also include any icon theme you would like to use there. (Like ubuntu-mono for example.)

Then:
```
nano ~/.config/gtk-3.0/settings.ini
```

And add this:
```
[Settings]
gtk-theme-name = Ambiance *(or any other theme you like.)*
gtk-fallback-icon-theme = *Your preferred icon theme*
gtk-font-name = *Your preferred font*
```
You may have to log out and in/restart x or openbox for changes to take effect.

---

### Post by Krex on 2012-12-17
I actually registered on the forums just now to ask about this issue.

The solution proposed above works fine for apps that use GTK3, but GTK2 apps (firefox, for instance) still get the default openbox (or fluxbox) grey buttons. I have tried using gnome-settings-daemon, lxappearance, gtk-theme-switcher and gtk-chtheme, all with various problems and the same lack of result. I've googled this and experimented for several days, and it's becoming quite frustrating. Any clues or help would be appreciated.

---

### Post by zgemba on 2012-12-18
> **Krex said:**
> The solution proposed above works fine for apps that use GTK3, but GTK2 apps (firefox, for instance) still get the default openbox (or fluxbox) grey buttons. I have tried using gnome-settings-daemon, lxappearance, gtk-theme-switcher and gtk-chtheme, all with various problems and the same lack of result. I've googled this and experimented for several days, and it's becoming quite frustrating. Any clues or help would be appreciated.

Dear Krex, I am so glad that I am not the only one with the same problem. I just booted my virtual machine (12.04_LTS - 32bit). The same procedure that worked flawless there isn't working on my new machine (12.10 - 64bit). On 12.04 I just used lxappearance and I could change themes, icons, fonts. ~/.gtkrc-2.0 and ~/.config/.gtkrc-3.0 were created automatically and everything was looking great under openbox.

Now on 12.10 I can't seem to get it done using all theme-managers (lxappearance, switch2, gtk-chtheme, gnome-settings-daemon...). I installed all theme engines but none of them did the job.

Now I'm learning to write my custom gtk themes just to have nice looking GTK apps under openbox. (as I wrote previously - I don't want bloated system, I just install xorg and openbox and want to theme GTK apps)

---

### Post by zgemba on 2012-12-18
I found a solution for my problem, and as always it's the best solution - learn more about it and do it manually.

I found a theme that has support for both gtk2 and gtk3, installed only required engines for that theme, fonts and icons and wrote or copied required config files to right places.

These GTK theme switcher/helpers don't do it properly.

---

### Post by Krex on 2012-12-18
> **zgemba said:**
> I found a solution for my problem, and as always it's the best solution - learn more about it and do it manually.

I found a theme that has support for both gtk2 and gtk3, installed only required engines for that theme, fonts and icons and wrote or copied required config files to right places.

These GTK theme switcher/helpers don't do it properly.

I decided to edit the config file myself with a guide I found - and it STILL doesn't work. Highly frustrating. It's as if fluxbox/openbox (problem persists in both these window managers) doesn't even read the .gtkrc-2.0. Bothersome, to say the least.

---

### Post by zgemba on 2012-12-18
> **Krex said:**
> I decided to edit the config file myself with a guide I found - and it STILL doesn't work. Highly frustrating. It's as if fluxbox/openbox (problem persists in both these window managers) doesn't even read the .gtkrc-2.0. Bothersome, to say the least.

First, ubuntu isn't really Openbox friendly in my experience. I would recommend you read this guide because it helped me a lot to understand GTK:
[ARCH linux GTK wiki]("https://wiki.archlinux.org/index.php/GTK%2B")

Then you need to find GTK 3.6 themes that have GTK2 & GTK3 theme included, for example Adwaita X Dark. Here's a link with 8 GTK themes compatible with GTK 3.6:

[8 GTK 3.6 compatible themes]("http://www.webupd8.org/2012/11/8-gtk-36-compatible-themes-available-in.html")

You need to install theme engines if the theme you want requires it (a good starting point would be to install gtk2-engines-murrine, gtk-engine-unico and gtk2-engines-pixbuf packages). Review the readme file that comes with the theme you want.

Then you need to place the themes config files in your home directory (the themes will mainly be installed in your /usr/share/themes folder). You need to copy the gtk3 config file from the themes folder to ~/.config/gtk-3.0/settings.ini and gtk2-rc to ~/.gtkrc-2.0. You can find in the first link I posted how these 2 config files should look like.

I'll post tomorrow details how I did it, I'm at win machine now.

---

### Post by Krex on 2012-12-19
> **zgemba said:**
> First, ubuntu isn't really Openbox friendly in my experience. I would recommend you read this guide because it helped me a lot to understand GTK:
[ARCH linux GTK wiki]("https://wiki.archlinux.org/index.php/GTK%2B")

Then you need to find GTK 3.6 themes that have GTK2 & GTK3 theme included, for example Adwaita X Dark. Here's a link with 8 GTK themes compatible with GTK 3.6:

[8 GTK 3.6 compatible themes]("http://www.webupd8.org/2012/11/8-gtk-36-compatible-themes-available-in.html")

You need to install theme engines if the theme you want requires it (a good starting point would be to install gtk2-engines-murrine, gtk-engine-unico and gtk2-engines-pixbuf packages). Review the readme file that comes with the theme you want.

Then you need to place the themes config files in your home directory (the themes will mainly be installed in your /usr/share/themes folder). You need to copy the gtk3 config file from the themes folder to ~/.config/gtk-3.0/settings.ini and gtk2-rc to ~/.gtkrc-2.0. You can find in the first link I posted how these 2 config files should look like.

I'll post tomorrow details how I did it, I'm at win machine now.

Well, I've now done these things and a lot of other things. I just can't get GTK2 to work - even with your described method, only the GTK3 apps show the themes.

I installed lubuntu with the minimal install - this uses openbox. Then all GTK themes showed up just fine. Then when I started an openbox session, GTK2 once again didn't work. This really baffles me - I really can't understand where the problem is, as both the sessions share the exact same configuration files. LXappearance works fine in the LXDE  session, but does nothing in the openbox session.

I'm really stuck here - does anyone have any idea?

---

### Post by zgemba on 2012-12-20
> **Krex said:**
> Well, I've now done these things and a lot of other things. I just can't get GTK2 to work - even with your described method, only the GTK3 apps show the themes.

I installed lubuntu with the minimal install - this uses openbox. Then all GTK themes showed up just fine. Then when I started an openbox session, GTK2 once again didn't work. This really baffles me - I really can't understand where the problem is, as both the sessions share the exact same configuration files. LXappearance works fine in the LXDE  session, but does nothing in the openbox session.

I'm really stuck here - does anyone have any idea?

Did you make sure you are using theme with both GTK2 and GTK3 styles. Don't use lxappearance or gnome-tweak-tool, they don't work for me either in 12.10 under openbox.

Can you name one gtk2 and one gtk3 application you are using on your system. What theme did you choose (is it gtk3.6 compatible and does it have gtk2 theme also), did you installed it on /usr/share/themes, are you working as a root user or regular user.

Do you have ~/.gtkrc-2.0 file and what's in it. Do you have ~/gtk-3.0/settings.ini file and what's in it.

Make sure you have all required engines that theme requires, and additional stuff like librsvg...

I'm just doing a new CLI from a 12.10 X64 mini cd to debloat my system, and am just going to install xorg and openbox and manually set the look, and if it all goes well I'll post you the steps that I've done.

---

### Post by andrew.46 on 2012-12-25
My own needs are very simple and I my ~/.gtkrc-2.0 is as follows:

```

gtk-icon-theme-name = "Tango"
gtk-fallback-icon-theme = "Tango"
gtk-theme-name = "Clearlooks"
gtk-font-name = "DejaVu Sans 10"

```

but I am not that fussed with good looks :)

---

