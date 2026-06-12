---
title: "Window bar (not panel!) in 12.04 classic desktop disappers occasionally"
date: 2013-01-03
forum: Desktop Environments
---

### Post by chkstate on 2013-01-03
I recently upgraded form 11.04 to 12.04 x64. Unity is a pain to me so I am working in gnome fallback/classic mode, but now I am experiencing a strange gnome behaviour of which I do not know if it is a bug or a feature I do not understand.

The program menu bar of windows with controls for close/maximize/minimize (not the gnome-panel!) is occasionally (maybe twice a day) disappearing as if I was using Unity. Most of the time I am expecting this in Mozilla or Thunderbird but I assume this is due to the fact that this are my mostly used applications. Only restarting an application brings back the controls. I checked CompizConfig where WindowDecoration is enabled.

Searching the forums on this topic either gives me results dealing with the gnome-panel or the window bar disappearance in Unity. But what is the matter with this behaviour in gnome classic mode?  

You will find a screenshot attached which shows a Thinderbird window with missing controls as well as a Firefox window nearby were everything is fine. 

[http://img255.imageshack.us/img255/9513/screenshotmenubarerror.png](http://img255.imageshack.us/img255/9513/screenshotmenubarerror.png)

---

### Post by cmcanulty on 2013-01-03
+1

---

### Post by ibjsb4 on 2013-01-03
Try a different theme, see if that gets you anywhere.

---

### Post by cmcanulty on 2013-01-03
no theme change isn't a fix

---

### Post by ibjsb4 on 2013-01-03
> **cmcanulty said:**
> +1

> **cmcanulty said:**
> no theme change isn't a fix

Care to elaborate?

---

### Post by cmcanulty on 2013-01-03
It has happened to me in classic also and I ended up reinstalling. I am just wondering if there is a similar command to use in 12.04 classic. I did a bunch of searches before I reinstalled, but nothing worked.

---

### Post by kansasnoob on 2013-01-04
The first thing I can think of is to see if it effects both the standard Gnome Classic session and also the Gnome Classic (no effects) session:

[ATTACH]229544[/ATTACH]

The standard classic session uses the Compiz window manager whereas the classic (no effects) session uses the Metacity window manager.

I've had no problems using Metacity per this method:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

Compiz seems to be problematic, I assume because of *hard-wired* settings associated with Unity, but I've never really cared for Compiz - thus I've not bothered learning much about it ;)

The second thing that comes to mind is the theme being used. Here again your mileage may vary if using Compiz but with Metacity I've had trouble with the Clearwaita theme from two different sources but I've had good luck with the Zukitwo themes:

[http://ubuntuforums.org/showpost.php?p=11993655&postcount=70](http://ubuntuforums.org/showpost.php?p=11993655&postcount=70)

Note: You'll see that I began there with a couple of possibilities for restoring a "default" theme and a list of commands for determining what the existing theme is.

The third thing that comes to mind, and I doubt this is the case but it's worth a look, you may or may not find that you need to disable the Firefox and/or Thunderbird global menu add-ons. To do so in Firefox just go to Tools > Add-ons > Global Menu Bar integration and select Disable. You'll then be prompted to restart Firefox. I don't use Thunderbird so I can't be sure of the specific procedure with it, but I'd think it's similar.

Hope this helps :D

---

### Post by cmcanulty on 2013-01-04
I use the clearlooks also and have the global menu disabled. Now since reinstalling it hasn't happened again so I can't try the fixes. But it is clearly a bug that crops up now and then with several people.Thanks

---

### Post by kansasnoob on 2013-01-04
> **cmcanulty said:**
> I use the clearlooks also and have the global menu disabled. Now since reinstalling it hasn't happened again so I can't try the fixes. But it is clearly a bug that crops up now and then with several people.Thanks

There is no clearlooks theme for gnome 3, so I can only guess that you're using clearwaita which has always caused me problems.

And you don't even mention which session you're using. I know the Compiz session is problematic ;)

---

### Post by cmcanulty on 2013-01-04
I am using ubuntu 12.04 classic no effects with the clearlooks-phenix-master

---

### Post by kansasnoob on 2013-01-04
> **cmcanulty said:**
> I am using ubuntu 12.04 classic no effects with the clearlooks-phenix-master

Then I suggest trying another theme :)

---

### Post by cmcanulty on 2013-01-04
as I said that doesn't fix problem

---

### Post by kansasnoob on 2013-01-04
> **cmcanulty said:**
> as I said that doesn't fix problem

I'm clueless then :confused:

I'm running that setup on over 30 PC's with a wide variety of hardware and I'm having no trouble.

Could you post a link to that theme so I can do some testing with it?

---

### Post by cmcanulty on 2013-01-05
[http://gnome-look.org/content/show.php/Clearlooks-Phenix?content=145210]("http://gnome-look.org/content/show.php/Clearlooks-Phenix?content=145210")

thanks!

---

### Post by kansasnoob on 2013-01-05
> **cmcanulty said:**
> [http://gnome-look.org/content/show.php/Clearlooks-Phenix?content=145210]("http://gnome-look.org/content/show.php/Clearlooks-Phenix?content=145210")

thanks!

It may take me a couple of weeks so be patient ;)

---

### Post by kansasnoob on 2013-01-05
Just a quick BTW ;)

I was curious about the README in that .zip download so I first determined which version I needed. I checked and 'libgtk-3-0' is version 3.4.2 so I downloaded "Clearlooks-Phenix 2".

Immediately after doing so all of the clutter on my desktop disappeared ........... that is it was suddenly hidden, and I had to reboot before the clutter reappeared properly. To me that in itself is a harbinger of doom :(

I've never seen anything like that happen before, at least not since I started using Ubuntu in 2007. So I really am reluctant to try and install the packages from that source.

Why would downloading a .zip cause any problems even w/o being opened to read?

---

