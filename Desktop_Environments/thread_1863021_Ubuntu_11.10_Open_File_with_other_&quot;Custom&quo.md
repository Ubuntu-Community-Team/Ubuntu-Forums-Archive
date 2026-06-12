---
title: "Ubuntu 11.10 Open File with other &quot;Custom&quot;  Application"
date: 2011-10-17
forum: Desktop Environments
---

### Post by cookacounty on 2011-10-17
OK, so whoever decided to remove the feature to use any application to open a file was a bonehead.

I have a text file called ocean.ocn that I want to open with nedit.....this was easily changed until now. I can't seem to find an easy way to do this, any suggestions?

I feel like I need to vent my frustration with ubuntu 11.10, making what used to be an easy task complicated. I have already had to spend several hours to get my computer back to where it was. If it wasn't for evolution supporting exchange sever 2010 I never would use this version. Am I the only one that thinks Maverick was awesome and simply improving the applications inside it was all that was needed?

Thanks,
Aaron

---

### Post by mc4man on 2011-10-17
fairly easy - nedit's .desktop is missing something to allow it to be shown in the r. click context menu

```
gksudo gedit /usr/share/applications/nedit.desktop
```
find the Exec= line & add a %f to end, leave a space between nedit & %f - ignore the untitled document 1 that also opens - close it without saving, do save the nedit.desktop
```
[Desktop Entry]
Version=1.0
Name=NEdit
[COLOR="Blue"]Exec=nedit %f[/COLOR]
Icon=Nedit
Terminal=false
Type=Application
Categories=Motif;Utility;TextTools;
GenericName=Text editor
GenericName[en]=Text editor
GenericName[nl]=Tekst verwerker
```
Then you'll find it by right clicking on your file > open with > other applications
After that it will be shown directly in the r. click menu

If you wish to set nedit as default for all text files then use the right click > **Properties** > open with instead

---

### Post by Gingalone on 2011-10-28
I have the same problem (on ubuntu 11.10 with XFCE) I appended %f to the exec line in the .desktop related file and that does not work. (not even after rebooting).
And in the "open with another application" window beside the "Show other applications" button there is only a "find applications online" option (and not a button for manual search among the applications installed in the system (as there was in older versions of ubuntu).
What can I do? :confused:

Thanks!

---

### Post by Orvar on 2011-11-03
[QUOTE=mc4man;11357219]fairly easy - nedit's .desktop is missing something to allow it to be shown in the r. click context menu

```
gksudo gedit /usr/share/applications/nedit.desktop
```
find the Exec= line & add a %f to end, leave a space between nedit & %f - ignore the untitled document 1 that also opens - close it without saving, do save the nedit.desktop...

Well, I ran into the same problem, but with DOSBOX.
I have an old special CAD software that runs on DOS, and until 11.10 I have just ticked DOSBOX in the "open with" dialog.
I installed DOSBox and I can open the DOS window without problem, so the program works. But it doesn´t show up in the Openwith-list or Other programs-list.
I opened the dosbox settings in usr/share/applications the way you suggest, but then the dosbox file is... totally empty! No line to add the %f to. 
So, please, is there anyone who can help me put DOSBOX in the "open with" or/and "other programs" list?

Sorry, I was too quick...
I didn´t write dosbox.*desktop*...
When I did the code was there, I added the %f and saved the file. 
And now IT WORKS!!! 
***THANKS A LOT! ***

But I still consider this a bug. If I install a program, I probably want to use it... And if I like it, I probably want it to automatically open the corresponding files i click on. So... why are Gimp, E.book reader, K3b and a lot of other programs automatically added to the list, but not DOSBox? 
It was installed in exactly the same manner (using the Ubuntu sofware center). It is an annoying inconsistency that was not there before 11.10. Hope the Ubuntu team fixes this.
However... Thanks again for your help!

---

### Post by gtgrover on 2011-11-04
I agree that this is an annoying change/lack.

I liked that in the older versions you could choose your application with a command line box that includes browsing to the application.

THANKS for the directions on editing the /usr/share/applications desktop files.  At least this is one way to get them to show up in the list of applications.  It worked like magic.  Great tip.

Now I can manually make sure the applications I need, do show up in the list.

I'd suggest trying to see if there is a dosbox.desktop file in the directory /usr/share/applications.  If you see the format of the others you might be able to make a template for dosbox, that is if there isn't something already there.

1. cd to the directory /usr/share/applications
2. use 'grep -i dosbox *'  this will search for the name dosbox ignoring case.
3. if it's not there make one  from one of the smaller ones. 
4. I used sol.destop and copied it to my own fake app to test.
5. Don't forget the %f, this shows that the application can be passed a file name, it has to be there to show up in the list.

sudo cp sol.desktop fake.destop
gksudo gedit fake.desktop

fake.desktop
```
[Desktop Entry]
Name=Fake Application Test
Comment=Do some fake stuff
Exec=/bin/bash %f
Icon=gnome-aisleriot
Terminal=true
Type=Application
Categories=GNOME;GTK;Game;CardGame;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=aisleriot
X-GNOME-Bugzilla-Component=Zwischenlager
X-GNOME-Bugzilla-Version=3.2.1
StartupNotify=true
X-HildonDesk-ShowInToolbar=true
X-Osso-Service=org.gnome.Games.AisleRiot
X-Osso-Type=application/x-executable
X-Ubuntu-Gettext-Domain=aisleriot
```
This worked for me.  Fake application with the sol icon showed up in the list of applications.

I set the Terminal=true here so I'd see some results. /bin/bash needs to be replaced with the real dosbox executable, and Terminal=false would probably be the choice.

You'll have to find the icon you want.

---

### Post by snecci on 2011-11-26
Waw, great job.... Something that was pretty fast to do now takes a lot of time and gets more complicated. That is exactly the way OS's should evolve....

Sorry, but I am really not able to see the reason behind this kind of changes.... Many times I have the feeling that we are moving backwards. Can it be that some designers/developers are trying to make open source world "explode" from the inside?

And for those who might defend this partial solutions, I may tell you that for a long time I had a very old computer that could not run hd videos, and the only way I could play my flipcam made videos (from a user friendly interface) was using a custom execution command that would open mplayer with lots of options like frameskipping and more ;)

I have the feeling of loosing freedom where I think I should have exactly the opposite one.

---

### Post by khdetw on 2011-12-05
I'm with you Aaron. Whoever removed the ability to manually enter the "open with" application should be sent to purgatory at Microsoft.

---

### Post by edgue on 2011-12-15
> **khdetw said:**
> I'm with you Aaron. Whoever removed the ability to manually enter the "open with" application should be sent to purgatory at Microsoft.

I just ran into the same issue and thought about checking/creating a bug entry at launchpad for this. I gave up after 30 minutes. 

Maybe i am stupid, but I cant think of any good reason to remove this feature.

---

### Post by mhogerheijde on 2011-12-20
This answered my question as well! Thanks a lot. My custom .desktop  for Sublime Text wasn't working, it was missing the %f on the Exec= line.

For others, if you don't have root on the system you're working on: this works just as fine when you put the .desktop file in ~/.local/share/applications/.

I also find it retarded that this function has been removed from the context-menu. I do, however, find the new 'find app on-line' option quite nice.

---

### Post by mike'o on 2011-12-20
> **mhogerheijde said:**
> This answered my question as well! Thanks a lot. My custom .desktop  for Sublime Text wasn't working, it was missing the %f on the Exec= line.

Does not work for me.

I tried to edit a .desktop -file by right clicking it and selecting open with... However there is not even such option available!
It seems that from some places the option is disabled altogether, so no difference if you get your program to the list of available commands or not.

Sucks big time.

---

### Post by willus on 2012-01-08
As a Windows user who just installed the latest Ubuntu, I agree with others that there needs to be a way to navigate to a custom application (gnome-terminal, for instance, for a command-line app?), just like there is in Windows.  I shouldn't have had to find the answer for this in an on-line forum.  Over-simplifying the desktop and taking away options hurts the Ubuntu cause.

---

### Post by tlcstat on 2012-01-30
Greetings,
Had the same problem with gPHPEdit. The solution in post #2 worked perfect. 
Thanks. 

While on the same subject, would you by chance know how to remove multiple entries from that same context menu. Not a big deal, would just like to clean it up a bit.
tlcstat

---

### Post by studiogrynn on 2012-02-15
> While on the same subject, would you by chance know how to remove multiple entries from that same context menu. Not a big deal, would just like to clean it up a bit.

While in the list, right click and select to remove the association.

---

### Post by Redsandro on 2012-06-27
I can **open any image** file with [**_XnViewMP_**]("http://newsgroup.xnview.com/viewtopic.php?f=60&t=26033"), an awesome image viewer better than anything I've seen in Linux.

But, I **_cannot_ open .jpg** with **XnViewMP**. I cannot choose it from the list. What's going on here?

Tried here, not helping: [http://www.ubuntugeek.com/how-to-addremove-applications-from-open-with-window.html](http://www.ubuntugeek.com/how-to-addremove-applications-from-open-with-window.html)

---

### Post by sentey on 2012-10-04
Hi there. First post here, hope I'm not reviving a too old post or sth.

I have a problem. I need to open a .image file with an application I downloaded (squeak). And I don't understand how to create the .desktop file (it does not exist, or otherwise I have not been able to find it) or how to edit it.

I would appreciate any help. Thanks in advance

**Edit: Solved with Ubuntu Tweak.**

---

### Post by cmcanulty on 2012-11-03
I still can't get files to open that I save using firefox deskcut. they have a .desktop extension. I did your hack and I get an open with on other files but not the .deskcut files. I love deskcut but due to this issue it is unusable. All I need to do is set .descut to open with firefox. I HATE that they keep making things harder and less options.

---

### Post by vcell on 2013-07-03
I totally agree, snecci. I used to hawk Ubuntu to Linux wannabe-newbies because it is so easy to transition to. But when someone comes back to me with an issue like this, and I have to open a command line and perform (what appears to them to be) a foreign program language, I see their eyes glaze over with "Dear God What Have I Done!" and conversion back to Windows or OSX may not be far behind.

What a shame. What a stupid ridiculous shame. Especially since this post started in 2011 and it is now 2013 and this is still the case. Nothing has reverted.

---

### Post by Redsandro on 2013-07-04
The annoying simplification that **@cmcanulty** mentions makes Ubuntu more and more not unlike the OSX that **@vcell** mentions and the (former) OSX users love. Canonical is not crazy. For every tech-savvy user that they pi**ss off, they gain 10 new 'dumb' users.

Also, although you have to do abacadabra in the command line, know that most fixable problems, however small infuriating, are unfixable on OSX by the average OSX user. They have to go back to a service point, complain to the developers, or just deal with it.

Furthermore, Ubuntu has been more like a smart-tv since about 12.04 and nobody likes those smart-tv-menus. So if you want to recommend anything to friends who are new to Linux, give them Linux Mint Cinnamon edition.

Linux Mint is Ubuntu "what it should be". All stupid decisions (more and more) are rolled back. No 'political' decisions to hold certain packages back. And Cinnamon is a Gnome-Shell fork "what it should be". Modern, yet normal. No crazy shell or silly unity.

---

