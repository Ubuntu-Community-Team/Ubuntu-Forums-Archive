---
title: "Menu item missing in Lubuntu"
date: 2011-09-01
forum: Desktop Environments
---

### Post by peyre on 2011-09-01
On my Lubuntu box, after I installed Wine (I use the beta version), it placed a Wine category in my main menu (between Sound & Video and System Tools).  Yesterday I was working with Starcraft, trying to get it to run in Wine more efficiently by trying different settings--so I was going into that menu frequently.  Somewhere along the way I must have pushed a wrong button or done something I shouldn't with the mouse or something, and now it's disappeared.  It doesn't seem to have moved to a submenu somewhere; it's just gone.  Anyone know how to get it back?

I've tried reinstalling Wine over the top.  I've tried removing it, then installing the non-beta version, but the Wine menu didn't come back.  I then removed the non-beta Wine, installed the beta Wine, and still it didn't come back.

I could try a Complete Removal of Wine, but I hate to reinstall all my Windows software over again just for this Wine menu.  Anyone have any ideas?

---

### Post by whatthefunk on 2011-09-03
Got to /usr/share/applications and find the wine.desktop file.  Copy it and paste it here.

---

### Post by peyre on 2011-09-03
Ah, cool!  Here it is:
```
[Desktop Entry]
Type=Application
Name=Wine Windows Program Loader
Name[cs]=Zavad&#283;&#269; program&#367; pro Wine
Name[de]=Wine Windows-Programmstarter
Name[es]=Wine Cargador de programas de Windows
Name[lt]=Wine Windows program&#371; paleidykl&#279;
Name[nl]=Wine Windows programmalader
Name[sv]=Wine Windows Programstartare
Name[ro]=Wine - Înc&#259;rc&#259;torul de programe Windows
Name[ru]=Wine - &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1095;&#1080;&#1082; Windows &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1084;
Name[uk]=Wine - &#1079;&#1072;&#1074;&#1072;&#1085;&#1090;&#1072;&#1078;&#1091;&#1074;&#1072;&#1095; Windows &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;
Name[fr]=Wine - Chargeur de programmes Windows
Name[ca]=Wine - Carregador d'aplicacions del Windows
Name[pt]=Carregador de aplicativos Windows Wine
Name[pt_br]=Carregador de aplicativos Windows Wine
Name[it]=Wine Carica Programmi Windows
Name[da]=Wine, Programstarter til Windows-programmer
Name[nb]=Wine - for kjøring av Windows-programmer
Name[nn]=Wine - for køyring av Windows-program
Name[sr]=Wine - &#1076;&#1080;&#1079;&#1072;&#1095; Windows &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1072;
Name[sr@latin]=Wine - diza&#269; Windows programa
Name[hr]=Wine - diza&#269; Windows programa
Name[he]=Wine — &#1502;&#1512;&#1497;&#1509; &#1514;&#1499;&#1504;&#1497;&#1493;&#1514; Windows
Exec=wine start /unix %f
MimeType=application/x-ms-dos-executable;application/x-msi;application/x-win-lnk;application/x-ms-shortcut;
Icon=wine
NoDisplay=true
StartupNotify=true
Categories=Main
GenericName=Wine

```

---

### Post by whatthefunk on 2011-09-03
Change NoDisplay to false.  Does that work?

---

### Post by peyre on 2011-09-03
> **whatthefunk said:**
> Change NoDisplay to false.  Does that work?

No!  Funny, you'd think it would.  I modified it with sudo then rebooted to make sure it would take effect.  The menu was still missing.  I went back and reopened wine.desktop to make sure it showed NoDisplay=false, and it did.

---

### Post by kerry_s on 2011-09-03
Check ~/.local/share/applications

---

### Post by peyre on 2011-09-04
For what exactly?

---

### Post by whatthefunk on 2011-09-04
There might be another .desktop file in there.  Go to ~/.local/share/applications to see if there is a wine file there.  If it says NoDisplay=true, change it to false and see if that takes care of it.  If there is no wine file there, you might want to try to copy the file from /usr/share/applications into ~/.local/share/applications to see if you can get the local settings to override the global problem.

---

### Post by peyre on 2011-09-05
Ah ok!  I've copied wine.desktop to ~/.local/share/applications, and set NoDisplay to false, then rebooted.  It's still not appearing.  Weird!

---

### Post by whatthefunk on 2011-09-05
You could try to get it displayed somewhere else in the menu by replacing
```
Categories=Main
```
with
```
Categories=GNOME;Application;Utility;
```

This should get it to display in the Applications sub-menu.

---

### Post by peyre on 2011-09-08
That doesn't appear to have done anything (I made the change in both /usr... and ~/.local...).

Uh...Applications submenu?  I don't have one.  Did you mean Accessories?  The Wine Windows Program Loader shows in there (not sure if it was there before), but nothing else re. Wine.

---

### Post by amjjawad on 2011-09-10
> **peyre said:**
> That doesn't appear to have done anything (I made the change in both /usr... and ~/.local...).

Uh...Applications submenu?  I don't have one.  Did you mean Accessories?  The Wine Windows Program Loader shows in there (not sure if it was there before), but nothing else re. Wine.

There is NO Applications menu nor sub menu in Lubuntu or LXDE.
You are right.

Try this:

```
Categories=Settings;DesktopSettings 
```

---

### Post by peyre on 2011-09-15
> **amjjawad said:**
> There is NO Applications menu nor sub menu in Lubuntu or LXDE.
You are right.

Try this:

```
Categories=Settings;DesktopSettings 
```

Thanks!  Sorry about the delay getting back, but life intervened there for a bit.  Ok, I've set that in both files, but the Wine menu still doesn't appear.  Strange.

---

### Post by amjjawad on 2011-09-16
> **peyre said:**
> Thanks!  Sorry about the delay getting back, but life intervened there for a bit.  Ok, I've set that in both files, but the Wine menu still doesn't appear.  Strange.

You welcome and never mind about the delay. Real Life keeps is so busy.

I'm sorry to ask such a question but are you looking in all the menus? Accessories, etc?

---

### Post by amjjawad on 2011-09-16
I don't like Wine and don't need to use it but I have installed it just to help you :)

```
[Desktop Entry]
Type=Application
Name=Wine Windows Program Loader
Name[cs]=Zavad&#283;&#269; program&#367; pro Wine
Name[de]=Wine Windows-Programmstarter
Name[es]=Wine Cargador de programas de Windows
Name[lt]=Wine Windows program&#371; paleidykl&#279;
Name[nl]=Wine Windows programmalader
Name[sv]=Wine Windows Programstartare
Name[ro]=Wine - Înc&#259;rc&#259;torul de programe Windows
Name[ru]=Wine - &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1095;&#1080;&#1082; Windows &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1084;
Name[uk]=Wine - &#1079;&#1072;&#1074;&#1072;&#1085;&#1090;&#1072;&#1078;&#1091;&#1074;&#1072;&#1095; Windows &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;
Name[fr]=Wine - Chargeur de programmes Windows
Name[ca]=Wine - Carregador d'aplicacions del Windows
Name[pt]=Carregador de aplicativos Windows Wine
Name[pt_br]=Carregador de aplicativos Windows Wine
Name[it]=Wine Carica Programmi Windows
Name[da]=Wine, Programstarter til Windows-programmer
Name[nb]=Wine - for kjøring av Windows-programmer
Name[nn]=Wine - for køyring av Windows-program
Name[sr]=Wine - &#1076;&#1080;&#1079;&#1072;&#1095; Windows &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1072;
Name[sr@latin]=Wine - diza&#269; Windows programa
Name[hr]=Wine - diza&#269; Windows programa
Name[he]=Wine &#8212; &#1502;&#1512;&#1497;&#1509; &#1514;&#1499;&#1504;&#1497;&#1493;&#1514; Windows
Exec=wine start /unix %f
MimeType=application/x-ms-dos-executable;application/x-msi;application/x-win-lnk;application/x-ms-shortcut;
Icon=wine
**[COLOR=Red]NoDisplay=false[/COLOR]**
StartupNotify=true
[COLOR=Red]**Categories=Settings;DesktopSettings**[/COLOR]
```When I did these two little changes in red, I got it on the list. Please check the attached screen shot.

However, as you can see, "Wine" has its own entry anyway.

---

### Post by whatthefunk on 2011-09-16
From this thread:
[http://ubuntuforums.org/showthread.php?t=1845073](http://ubuntuforums.org/showthread.php?t=1845073)

Force the regeneration of the menu by deleting the files in ~/.cache/menus/  Then restart the panel with
```
lxpanelctl restart
```

---

### Post by peyre on 2011-09-21
Strange.  I've made sure wine.desktop shows both those lines in red, in both locations, and I've run lxpanelctl restart as root, but still no Wine section appears...even after a reboot.

You know, it's a shame that LXDE is so lame re. shortcuts.  In Xubuntu I'd just create Desktop shortcuts to winecfg etc. and call it done, but that doesn't really work in Lubuntu.

---

### Post by amjjawad on 2011-09-21
> **peyre said:**
> Strange.  I've made sure wine.desktop shows both those lines in red, in both locations, and I've run lxpanelctl restart as root, but still no Wine section appears...even after a reboot.

Have you considered to re-install Wine?

> You know, **it's a shame that LXDE is so lame re. shortcuts.**  In Xubuntu I'd just create Desktop shortcuts to winecfg etc. and call it done, but that doesn't really work in Lubuntu.You wouldn't call it "so lame" when LXDE makes your ancient Laptop or PC breathes new life while other DE can not. You wouldn't call it "so lame" when LXDE makes your machine runs much faster than anything else. Nothing is prefect my friend. If there is ONLY ONE "perfect" Software/OS in the world, there will be NO need to have more than 300 active Linux Distributions over there, not to mention the other OS (Windows, Mac, etc).

Not to be harsh or rude but let's don't forget the fact that "nothing is prefect" and let's not forget the other advantages in LXDE :)

LXDE, if you don't know, still not stable and version 1 still not yet released. However, it's very promising, otherwise Lubuntu wouldn't be an official variant and it wouldn't be in a better rank than Xubuntu and Kubuntu on Distrowatch ;)

---

### Post by whatthefunk on 2011-09-21
Have you tried to copy the wine.desktop file to /home/user/desktop?  That should put it on the desktop.

---

### Post by peyre on 2011-09-21
> **amjjawad said:**
> Have you considered to re-install Wine?

Let's see...
> **peyre said:**
> I've tried reinstalling Wine over the top.  I've tried removing it, then installing the non-beta version, but the Wine menu didn't come back.  I then removed the non-beta Wine, installed the beta Wine, and still it didn't come back.
Now I could remove it altogether and reinstall from scratch.  I just hesitate to go back and reinstall all my Windows software again.  Then again, 11.10 is only a month away--it might resolve itself with an upgrade.

> **amjjawad said:**
> You wouldn't call it "so lame" when LXDE makes your ancient Laptop or PC breathes new life while other DE can not. You wouldn't call it "so lame" when LXDE makes your machine runs much faster than anything else.

XFCE would breathe new life into a laptop like this too; it's just that LXDE does it better.  Lubuntu has some very good features, but its support for shortcuts is--yes--lame by comparison with the other lightweight distro I use.  I'm not unhappy with Lubuntu overall; I'm just pointing out one of its shortcomings (as I see them).

> **amjjawad said:**
> Not to be harsh or rude but let's don't forget the fact that "nothing is prefect" and let's not forget the other advantages in LXDE :)

Not forgotten.  I'm not about to toss LXDE; I'm just carping about something that was bothering me at the time.

---

### Post by amjjawad on 2011-09-21
> **peyre said:**
> Now I could remove it altogether and reinstall from scratch.  I just hesitate to go back and reinstall all my Windows software again.  
I was actually talking about removing it and re-install it again from scratch but you might lose your programs, etc.

> Then again, 11.10 is only a month away-- **it might resolve itself with an upgrade**.

Only if it's a bug IMHO.

Have you tried to search for similar issue here: [www.googlubuntu.com](www.googlubuntu.com) ?

> XFCE would breathe new life into a laptop like this too; it's just that LXDE does it better.  Lubuntu has some very good features, but its support for shortcuts is--yes--lame by comparison with the other lightweight distro I use.  I'm not unhappy with Lubuntu overall; I'm just pointing out one of its shortcomings (as I see them).
Appreciate that and thanks for your opinion. Our point of view may vary but at the end, I guess we both like LXDE :)

> Not forgotten.  I'm not about to toss LXDE; I'm just carping about something that was bothering me at the time.
Ok, and I'm sorry if I was a bit harsh/rude :)

I'll try to read your thread again and try to produce the same issue and will let you know if I got some updates. I installed Wine just to help you with your thread. I don't ever use it.

---

### Post by peyre on 2011-09-22
> **whatthefunk said:**
> Have you tried to copy the wine.desktop file to /home/user/desktop?  That should put it on the desktop.

Yes, that worked--though it installs the "Wine Windows Program Loader" icon to the Desktop.  That icon shows in my Preferences menu already; what I'm looking for is the whole Wine menu I used to have just beneath Sound & Video.  Thanks though.

---

### Post by peyre on 2011-09-22
> **amjjawad said:**
> I was actually talking about removing it and re-install it again from scratch but you might lose your programs, etc.

Ah, ok!  Yes, that is a definite option to try.  I may go ahead and do that.

> **amjjawad said:**
> Only if it's a bug IMHO.

Actually, I've seen upgrades fix little issues I was having that were like this, where a configuration got goofed up somewhere I couldn't track down.  So it's possible, though I wouldn't lay money on it--but of course, with Ubuntu there's no money involved.  \\:D/

> **amjjawad said:**
> Have you tried to search for similar issue here: [www.googlubuntu.com](www.googlubuntu.com) ?

No--but I may do that too.

> **amjjawad said:**
> Appreciate that and thanks for your opinion. Our point of view may vary but at the end, I guess we both like LXDE :)

Agreed.  It's a nice DE.

> **amjjawad said:**
> Ok, and I'm sorry if I was a bit harsh/rude :)

I'll try to read your thread again and try to produce the same issue and will let you know if I got some updates. I installed Wine just to help you with your thread. I don't ever use it.

That's ok--I may actually have responded harshly/rudely myself.  Yesterday was kind of an ugly day at the office, which has done bad things for my mood... I may have approached the petulant "You're not helping meeeeee!" attitude Linux folks sometimes get from newbies.  Thanks for taking the time and effort to attack the issue with me.  I do wish I could remember what key combination or whatever it was that caused that menu to disappear.  In the end it won't be a big hairy deal if I can't work this out.

---

### Post by amjjawad on 2011-09-22
> **peyre said:**
> Ah, ok!  Yes, that is a definite option to try.  I may go ahead and do that.

I'm afraid that's the only option. However, I suggest to go through your configuration files (.desktop) and check the syntax, etc. Two days ago, I was testing a new shortcut and I messed up my **lubuntu-rc.xml** file then I figured out how to fix it and I got rid from an error message I had after logging to Lubuntu. 

> Actually, I've seen upgrades fix little issues I was having that were like this, where a configuration got goofed up somewhere I couldn't track down.  So it's possible, though I wouldn't lay money on it--but of course, with Ubuntu there's no money involved.  \\:D/

Perhaps it's possible and perhaps it's not ;)

>  No--but I may do that too.
[www.googlubuntu.com](www.googlubuntu.com) is very helpful.


>  Agreed.  It's a nice DE.
+1


> That's ok--I may actually have responded harshly/rudely myself.  Yesterday was kind of an ugly day at the office, which has done bad things for my mood... I may have approached the petulant "You're not helping meeeeee!" attitude Linux folks sometimes get from newbies.  Thanks for taking the time and effort to attack the issue with me.
Oh come on, never mind ... we all do that and pass through the same (even though I'm jobless) so totally understood :) 

You welcome :)


> I do wish I could remember what key combination or whatever it was that caused that menu to disappear.  In the end it won't be a big hairy deal if I can't work this out.
You know? nothing better than these issues whether it's huge or not. After all, you can't learn how to fix unless you break. I know it's not your fault as you didn't do it purposely but IMHO, this is the best approach of learning. 

Keep us updated in case you'll find something and I'll keep searching too whenever I get some extra free time :)

---

### Post by peyre on 2011-10-04
Well that's depressing.  I've done a Complete Removal of Wine in Synaptic, deleted the .wine folder, and deleted whatever wine config files I could find.  Then I rebooted, reinstalled Wine, and started reinstalling my apps.  Still no Wine menu!

It's not a big deal really, but it would have been nice.  Again, maybe 11.10 will make a difference...maybe.  In the meantime, I've created some basic scripts on the Desktop that open winecfg and the uninstaller.  That'll do the job, just less elegantly.  Thanks for taking the time to assist me on this, guys.

---

### Post by amjjawad on 2011-10-04
> **peyre said:**
> Well that's depressing.  I've done a Complete Removal of Wine in Synaptic, deleted the .wine folder, and deleted whatever wine config files I could find.  Then I rebooted, reinstalled Wine, and started reinstalling my apps.  Still no Wine menu!

That's weird indeed. There must be something so simple we are missing here.

> Again, maybe 11.10 will make a difference...maybe.  

Maybe Yes, maybe Not :)

[qoute]Thanks for taking the time to assist me on this, guys.[/QUOTE]

You welcome and sorry if I couldn't help you much!

---

### Post by peyre on 2011-10-04
> **amjjawad said:**
> That's weird indeed. There must be something so simple we are missing here.

Yeah, that's what I'm thinking.  It's probably something really small and simple, but without knowing what it is, there's just about no way to find it out.

> Maybe Yes, maybe Not :)

Yep.  But, considering there's no Wine menu at all--meaning I can't open my Windows apps from the Desktop without creating special scripts (and ugly ones, since I can't use the appropriate icons)...I might just reinstall Lubuntu from scratch with 11.10.  It's just my *secondary* machine anyway.

> You welcome and sorry if I couldn't help you much!

Not to worry.  It wasn't for lack of trying.

---

### Post by amjjawad on 2011-10-05
I always think about complicated ways to fix something then I realize the solution is so much easy and could be done with one or two steps. Yes, if you don't know what are you looking for is definitely hard but interesting at the same time :)

One needs to learn how to fix broken things without re-installing all over again but sometimes, that probably your only way.

If it's your secondary machine, try to learn how to fix it and if you see no point of doing that, then re-install.

I'll wait for Lubuntu 11.10 too and I think I'll get rid of all the other distribution
[LIST]
[*][]("http://us.mg2.mail.yahoo.com/dc/launch#")
[/LIST]
s on my machine and install Lubuntu ONLY :D

---

### Post by whatthefunk on 2011-10-05
Have you tried to locate strange .desktop files?  If youve reinstalled wine and it still isnt showing up, my guess is that there is a local .desktop file that is overriding other ones.

```
locate wine.desktop
```

---

### Post by amjjawad on 2011-10-05
> **whatthefunk said:**
> Have you tried to locate strange .desktop files?  If youve reinstalled wine and it still isnt showing up, my guess is that there is a local .desktop file that is overriding other ones.

```
locate wine.desktop
```

I think it should be here:

/usr/share/applications/wine.desktop

---

### Post by whatthefunk on 2011-10-06
> **amjjawad said:**
> I think it should be here:

/usr/share/applications/wine.desktop

Yes, there is one there, but there is also probably a local one that may be overriding the global settings set in the applications one.

---

### Post by amjjawad on 2011-10-06
> **whatthefunk said:**
> Yes, there is one there, but there is also probably a local one that may be overriding the global settings set in the applications one.

For me, that was the only one but hope the OP will find anything else that could causing this weird issue.

:)

---

### Post by peyre on 2011-10-06
I see it in the following locations:

/home/leon/.local/share/applications/wine.desktop
/usr/share/app-install/desktop/q4wine.desktop
/usr/share/app-install/desktop/wine.desktop
/usr/share/applications/wine.desktop

---

### Post by amjjawad on 2011-10-07
> **peyre said:**
> I see it in the following locations:

/home/leon/.local/share/applications/wine.desktop
/usr/share/app-install/desktop/q4wine.desktop
/usr/share/app-install/desktop/wine.desktop
/usr/share/applications/wine.desktop

Then try to manually remove these files and install wine again or remove all except the last one:

```
 /usr/share/applications/wine.desktop
```
You don't have to re-install IMHO in case you'll remove all but this one.

---

### Post by amjjawad on 2011-10-07
The content of : [B]/usr/share/applications/wine.deskto 
[/B]
```
[Desktop Entry]
Type=Application
Name=Wine Windows Program Loader
Name[cs]=Zavad&#283;&#269; program&#367; pro Wine
Name[de]=Wine Windows-Programmstarter
Name[es]=Wine Cargador de programas de Windows
Name[lt]=Wine Windows program&#371; paleidykl&#279;
Name[nl]=Wine Windows programmalader
Name[sv]=Wine Windows Programstartare
Name[ro]=Wine - Înc&#259;rc&#259;torul de programe Windows
Name[ru]=Wine - &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1095;&#1080;&#1082; Windows &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1084;
Name[uk]=Wine - &#1079;&#1072;&#1074;&#1072;&#1085;&#1090;&#1072;&#1078;&#1091;&#1074;&#1072;&#1095; Windows &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;
Name[fr]=Wine - Chargeur de programmes Windows
Name[ca]=Wine - Carregador d'aplicacions del Windows
Name[pt]=Carregador de aplicativos Windows Wine
Name[pt_br]=Carregador de aplicativos Windows Wine
Name[it]=Wine Carica Programmi Windows
Name[da]=Wine, Programstarter til Windows-programmer
Name[nb]=Wine - for kjøring av Windows-programmer
Name[nn]=Wine - for køyring av Windows-program
Name[sr]=Wine - &#1076;&#1080;&#1079;&#1072;&#1095; Windows &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1072;
Name[sr@latin]=Wine - diza&#269; Windows programa
Name[hr]=Wine - diza&#269; Windows programa
Name[he]=Wine — &#1502;&#1512;&#1497;&#1509; &#1514;&#1499;&#1504;&#1497;&#1493;&#1514; Windows
Exec=wine start /unix %f
MimeType=application/x-ms-dos-executable;application/x-msi;application/x-win-lnk;application/x-ms-shortcut;
Icon=wine
NoDisplay=false
StartupNotify=true
Categories=Settings;DesktopSettings

```

---

### Post by whatthefunk on 2011-10-07
Do they all look the same?  Try deleting all but the one in /usr/share/applications.

---

### Post by peyre on 2011-10-09
Good idea!  I deleted all those files, then did a Complete Removal in Synaptic, then reinstalled...but the Wine menu didn't come back.  Looks like we're back to waiting for Thursday.  And that's ok; a reinstall from scratch might do this old machine some good anyway.

---

### Post by amjjawad on 2011-10-09
> **peyre said:**
> Good idea!  I deleted all those files, then did a Complete Removal in Synaptic, then reinstalled...but the Wine menu didn't come back.  Looks like we're back to waiting for Thursday.  And that's ok; a reinstall from scratch might do this old machine some good anyway.

I'm out of ideas and have nothing to add except let's wait for the coming release :)

---

### Post by zer010 on 2012-05-12
This might be an "old" thread, but this issue is still alive and kickin. It seemed to be resolved with a trick in 11.10, but that's no longer available in 12.04.
In 11.10, I could change the DE login option to LXDE vs Lubuntu, but as stated, that's no longer an option.  Any suggestions on this matter seeing that this thread seems to have gone by the wayside?

---

### Post by zer010 on 2012-05-13
I seem to have fixed my issue. I found the .desktop files in /usr/share/applications.  Then I just copied those to ~/.local/share/applications, logged out and when I logged in, the menu items were there. Hope this helps others.

---

