---
title: "UbuntuStudio theme has changed? it's totally black now..."
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by icest0rm on 2007-10-18
Hi, I've just upgraded my feisty to gutsy but noticed that my UbuntuStudio theme changed.

Now the Gnome-panel it's totally black when before it was grey-black

Also window borders and decoration are different.

Here you will find 2 pictures explaining the differences, don't bother about icons or wallpaper, i'm just speaking only of UbuntuStudio Theme for window borders and gnome panel

old way:

[[IMG]http://img142.imageshack.us/img142/8899/ubuntustudioip7.th.png[/IMG]](http://img142.imageshack.us/my.php?image=ubuntustudioip7.png)

new way:

[[IMG]http://img505.imageshack.us/img505/564/schermatauq6.th.png[/IMG]](http://img505.imageshack.us/my.php?image=schermatauq6.png)

Do you know if the theme has changed on new packages? Or is there something wrong with me?
thanks

---

### Post by por100pre1 on 2007-10-18
That's the new theme, nothing's wrong there.

---

### Post by todd_freeride on 2007-10-18
where did you get ubuntu studio 7.1? just by doing the upgrade thing? I'm a studio user on 7.04

---

### Post by rafaelcapanema on 2007-10-18
Same here. I'm really disappointed.
It used to be my favorite theme, now it's just... not good. The whole new artwork is extremely ugly (wallpapers, splash screen etc. etc. etc.)

I wish I could roll back to the previous version.

---

### Post by blackbeard on 2007-10-18
It is fairly easy to make the panel look like it did in feisty and there is a ubuntustudio theme for emerald on gnome-look.

you just have to have the right .png files in the right places.

I am having trouble finding out how to install the feisty usplash screen or the login screen. I just did a fresh install, and i was not aware of the theme change until i rebooted and could not believe my eyes. If anyone has any idea where to find the usplash package or anything like that, i would be really thankful.

---

### Post by icest0rm on 2007-10-19
> **blackbeard said:**
> It is fairly easy to make the panel look like it did in feisty and there is a ubuntustudio theme for emerald on gnome-look.

you just have to have the right .png files in the right places.

ok I've installed that emerald theme but it isn't really like the old UbuntuStudio theme....that was nicer....anyway I'm still missing the right panel.png for having the same old panel....what a shame, that old UbuntuStudio theme was perfect....now I don't like it, apart from login screen/wallpaper or what else...just only the gnome-panel and window borders...:(

> I am having trouble finding out how to install the feisty usplash screen or the login screen..
login screen:
[http://www.gnome-look.org/content/show.php/UbuntuStudio+GDM?content=58047](http://www.gnome-look.org/content/show.php/UbuntuStudio+GDM?content=58047)

---

### Post by rafaelcapanema on 2007-10-19
Is the Ubuntu Studio artwork team listening?

---

### Post by rafaelcapanema on 2007-10-19
Hey, take a look at what I've just found on [http://ubuntustudio.org/downloads](http://ubuntustudio.org/downloads) !!!!

[I]Fun Stuff

    * Feisty Artwork .deb. - This package contains all the artwork from our Feisty release. It WILL NOT set it for you. It simply puts it in place.[/I]

Sweet!!!! Can someone download and test it? I'm at work right now, on Windows XP.

---

### Post by icest0rm on 2007-10-19
> **rafaelcapanema said:**
> Hey, take a look at what I've just found on [http://ubuntustudio.org/downloads](http://ubuntustudio.org/downloads) !!!!

[I]Fun Stuff

    * Feisty Artwork .deb. - This package contains all the artwork from our Feisty release. It WILL NOT set it for you. It simply puts it in place.[/I]

Sweet!!!! Can someone download and test it? I'm at work right now, on Windows XP.

ok the panel.png is the old one....
didn't installed, just checked the img for that..

---

### Post by Disillusion on 2007-10-19
> **rafaelcapanema said:**
> Hey, take a look at what I've just found on [http://ubuntustudio.org/downloads](http://ubuntustudio.org/downloads) !!!!

[I]Fun Stuff

    * Feisty Artwork .deb. - This package contains all the artwork from our Feisty release. It WILL NOT set it for you. It simply puts it in place.[/I]

Sweet!!!! Can someone download and test it? I'm at work right now, on Windows XP.

Good find, it puts the window decorations and the icons back, but not the gnome panel look. Maybe the art for it is in there and it just doesn't apply it properly. If anyone figures it out, let me know. The windows look weird with the all black panels.

---

### Post by FakeOutdoorsman on 2007-10-19
The new theme is totally ugly and disappointing.

---

### Post by icest0rm on 2007-10-19
> **Disillusion said:**
> Good find, it puts the window decorations and the icons back, but not the gnome panel look. Maybe the art for it is in there and it just doesn't apply it properly. If anyone figures it out, let me know. The windows look weird with the all black panels.

just apply panel.png as background panel to gnome-panel and it will get as it was..maybe you need to set it up on index.theme if not present..

---

### Post by Disillusion on 2007-10-19
> **icest0rm said:**
> just apply panel.png as background panel to gnome-panel and it will get as it was..maybe you need to set it up on index.theme if not present..

Ok, but where is this file?

---

### Post by D-EJ915 on 2007-10-19
[http://dej915.serveftp.com/host/UbuntuStudio/gtk-2.0/panel/panel.png](http://dej915.serveftp.com/host/UbuntuStudio/gtk-2.0/panel/panel.png)

---

### Post by erkkir on 2007-10-19
I dont understand, ubuntu studio used to be the good-looking ubuntu. The first shock was the login screen with the new ubuntu studio artwork. This must be a joke... 

Anyway for me the black panel is fine, it looks good, there are also nice new desktop backgrounds. But the login and logout screen with the new ubuntu studio "logo"... You must be kidding :(

Before I was really proud of my ubuntu-studio although the theme doesnt work perfectly with some programs (buttons in firefox are quite awful and for many programs the theme is too dark).

I was waiting for something different...

---

### Post by FakeOutdoorsman on 2007-10-19
To get the UbuntuStudio Feisty gradient back:
```

sudo rm /usr/share/themes/UbuntuStudio/gtk-2.0/panel/panel.png
wget http://dej915.serveftp.com/host/UbuntuStudio/gtk-2.0/panel/panel.png
sudo cp panel.png /usr/share/themes/UbuntuStudio/gtk-2.0/panel/

```

Reload Gnome with crtl + alt + backspace.

To get the Feisty GDM theme:
1. Get the theme from [gnome-look.org]("http://www.gnome-look.org/content/show.php/UbuntuStudio+GDM?content=58047") [thanks to icest0rm]
2. System -> Administration -> Login Window -> Local -> + Add -> Choose downloaded theme file.

---

### Post by por100pre1 on 2007-10-19
> **rafaelcapanema said:**
> Hey, take a look at what I've just found on [http://ubuntustudio.org/downloads](http://ubuntustudio.org/downloads) !!!!

[I]Fun Stuff

    * Feisty Artwork .deb. - This package contains all the artwork from our Feisty release. It WILL NOT set it for you. It simply puts it in place.[/I]

Sweet!!!! Can someone download and test it? I'm at work right now, on Windows XP.

Nice! :)

---

### Post by rafaelcapanema on 2007-10-19
Just installed it. Works like a charm, including the panel!

Before installing the .deb, try removing the repository line (if any) and all the ubuntustudio-related packages. That's what I did.

Good luck!

---

### Post by MetalMusicAddict on 2007-10-20
> **rafaelcapanema said:**
> Is the Ubuntu Studio artwork team listening?

Yes, but we don't care. ;) Gloss is dead.

---

### Post by rdeckard on 2007-10-22
Then guess what? 

YOU'RE FIRED.

You've got the wrong attitude for this project. Get lost.

The success of any project is based on it's responsiveness to public demand, this one is no different.
IF you think gloss is dead, then that's your own illusion. The rest of us like the old theme better, so quit acting like Bush & co.

:mad:

---

### Post by MetalMusicAddict on 2007-10-22
> **rdeckard said:**
> Then guess what? 

YOU'RE FIRED.

You've got the wrong attitude for this project. Get lost.

The success of any project is based on it's responsiveness to public demand, this one is no different.
IF you think gloss is dead, then that's your own illusion. The rest of us like the old theme better, so quit acting like Bush & co.

:mad:

LOL!!!

Guess what kid, I'm the Donald here. ;) The gloss is dead because I said so. Use the old theme if you wish. We made it easy to access.

The success of this project revolves around me. Trust me. Without me, it would die. Just the unfortunate truth of the matter.

Use gloss if you like (with your 6 posts), we're gonna stop being compared to Vista. ;)

---

### Post by ZOMGxuan on 2007-10-27
Well then Damn.

Damn, damn, damn, damn, damn.

Just try not to make Hardy look too dull. Completely black panels is dull. Maybe you could add little paint splashes to go with the whole punk thing. At least the Hardy logo looks better.

---

### Post by vemon on 2007-12-31
At least please change the login screen :) Don't mean to be rude but it currently (US Hardy Alpha 2) looks like "my first gimp experiment".

Is the US theme in Alpha 2 really final or just a "placeholder" for the final graphics?

---

### Post by XP-FREAK on 2007-12-31
@icest0rm

How did you get the information how many files are in a folder / how large is a file below the destkop icons?

---

