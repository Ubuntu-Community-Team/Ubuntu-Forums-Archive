---
title: "Transparent Gnome tray icons have white background!"
date: 2010-03-12
forum: Desktop Environments
---

### Post by auh2o on 2010-03-12
This is how my Firestarter and Pidgin icons appear in the tray against a panel using an image background, even though the icons are transparent. What can be done to fix this? According to **[this]("http://ubuntuforums.org/showthread.php?t=86602")** five year old thread, GTK libraries didn't support transparency in the tray area back then, but surely this must've been fixed by now? There are even some links to bugfixes in that very thread, but I'm hesitant to apply something that old. What to do?[URL="http://ubuntuforums.org/showthread.php?t=86602"]
[/URL]

---

### Post by auh2o on 2010-03-13
Bump.

Here it is treated like a Pidgin bug, and is still not fixed:

[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/447548](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/447548)

But as evident, Firestarter has the same problem, and so does VLC. Deluge or Transmission however, do not. Neither does Gnome Do. So might it be program specific after all, and not any longer a GTK problem, as it was 5 years ago? This problem is showing up with too many programs though, so you think developers would have taken note.

What other programs do you know who have the same problem?

---

### Post by Tikkyca on 2010-03-13
I think thats because of that theme if not then icons are not transparent it happens sometimes to me like in limewire or vuze,but in other programs it doesn't happen at all.

---

### Post by auh2o on 2010-03-13
The icons do indeed have transparent backgrounds, I have verified this. You can do so yourself by having a look at for example the Pidgin icons in /usr/share/pixmaps/pidgin/tray in Gimp, should you have them installed.

And it's not a theme, I have simply set the panel to display a background image - and it doesn't matter what image, either. The problem persists. Likewise if I choose a solid color background.

No, the only way I can get the icons to blend in is to use the system theme. That is the color around the icons, that very light gray. Which again leads me to believe it's a Gnome related problem. Somehow, Gnome can't properly handle the transparency of these icons, although it can handle others.

---

### Post by auh2o on 2010-03-16
Well, here's another thread from 4 years ago, lamenting the white color around the Firestarter icon.

[http://ubuntuforums.org/showthread.php?t=108316](http://ubuntuforums.org/showthread.php?t=108316)

The "solution" in that thread? Paint the area around the icon black to blend with the black panel that guy was using.

Seriously, how can this seemingly simple problem have been around for so long without a fix? There are endless bug reports on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/403135](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/403135)

And it IS a theme problem, not an application problem. All themes included by default in Karmic gives several icons either white or black backgrounds. But apparently, the problem disappears with some of the Lucid themes (though not the one applied by default):

[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/403135/comments/80](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/403135/comments/80)

Screenshot included at link.

So after 5 years of this problem, it may finally go away if you upgrade to Lucid and choose the right theme? That's it? No other solution?

---

### Post by auh2o on 2010-04-01
Am I really the only one still bothered by this in 9.10?

---

### Post by bornagainpenguin on 2010-04-02
> **auh2o said:**
> Am I really the only one still bothered by this in 9.10?

Hardly!  But other than complaining about it, what can we do about it?  Strangely enough this wasn't an issue at all for me under Hardy...

--bornagainpenguin

---

### Post by darkshines87 on 2010-04-03
Hi,

I recently switched my gnome panel look to a cool semi transparent background image and got rid of this notification icon (that letter thing). Then I activated the Pidgin tray icon and was shocked to see that the transparency didn't work. Even after restarting and switching around the panel looks it didn't change.

I couldn't find any solution to this, although I want one badly! :D

@ auh2o you are not the only one, this has to be fixed easily, considering that the icon image has transparency information and the fusion and transmission icons have a transparent background.

plz someone fix this! ](*,)

---

### Post by Spike-X on 2010-04-17
> **auh2o said:**
> Am I really the only one still bothered by this in 9.10?
No. No, you're not.

*grumble*

---

### Post by andoni on 2010-04-22
I hope it gets fixed in Lucid (I don't think so though...).

---

### Post by victor9098 on 2010-04-23
Problem still in Lucid, I have been to the Firestarter website to file a bug, but there bugzilla link is broken. It is the small details like this that make the difference, especially if it is starting you in the face all the time

---

### Post by MisterLambda on 2010-04-24
I can reproduce this in openSUSE, another distro, so it's an upstream problem with either GNOME or the app devs.

---

### Post by auh2o on 2010-05-01
As for the Pidgin tray icon, it is FIXED in the updated version included in 10.04 (yay!)

But Firestarter still suffers from this problem, as does VLC, and the Mail Notification applet (package name: mail-notification). These are the ones I've discovered, but there might very well be more.

> **MisterLambda said:**
> I can reproduce this in openSUSE, another  distro, so it's an upstream problem with either GNOME or the app  devs.

My bet would be the latter, seeing as how this was reported as a Pidgin bug on Launchpad and subsequently fixed by the Pidgin devs. Funny thing is, I don't remember the version of VLC that shipped with 9.10 having this problem. But I don't recall 100%.

---

### Post by Neovos on 2010-05-01
I too am quite annoyed by this. This is 10.4 Lucid for crying out loud, everything should be perfect by now! ....right?

I was trying to isolate the problem and tried something as you can see in my screenshot below: Icons on the gnome bar itself? they respect transparencies. The same icons in the notification area? not so much. I think the notification applet itself is a better place to start looking for this then the gnome bar. Anyone familiar with the source packages for that applet or where to find them? Time to start hacking!

---

### Post by Spike-X on 2010-05-01
The only way I've found to work around this is to use AWN just as a tray/notification area, shrunk down and off to one corner.

But Neovos is right, this really should have been sorted by now.

---

### Post by aryzing on 2010-05-05
> **auh2o said:**
> Funny thing is, I don't remember the version of VLC that shipped with 9.10 having this problem. But I don't recall 100%.

I don't either.

---

### Post by Spike-X on 2010-05-06
It seems this problem has been fixed for the Pidgin tray icons, but not for Gmail-notify or VLC. I've worked around this by using a different mail notifier and disabling the VLC tray icon, but again, this really should have been sorted by now. 

Maybe Mark Shuttleworth's design team could have a look at this when they're not too busy cluttering up the top window bar with a bunch of crap?

---

### Post by DomesDKG on 2010-05-06
wish they would, I'd be much more interested in a fix to this than windicators for the time being

---

### Post by jibanez on 2010-05-07
Unfortunately, this behavior is still present in Lucid.

---

### Post by Neovos on 2010-05-07
not surprisingly, this problem is an epic. Here are some of the more informative bugs reports:

[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/403135](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/403135)
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1818471.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1818471.html)

I think though, after reading up on it, that no one is really into fixing it because of how Canonical plans to do away with the entire notification tray anyway. So their diverting resources into that instead I guess? 

[http://design.canonical.com/2010/04/notification-area/](http://design.canonical.com/2010/04/notification-area/)
[https://wiki.ubuntu.com/CustomStatusMenuDesignGuidelines](https://wiki.ubuntu.com/CustomStatusMenuDesignGuidelines)

Still quite annoying but I'm all for a revamp of the notification tray. I've always hated it since windows 95 but it's so hard to wrap ones head around an outside the box alternative.

---

### Post by victor9098 on 2010-05-07
> **Neovos said:**
>  Still quite annoying but I'm all for a revamp of the notification tray. I've always hated it since windows 95 but it's so hard to wrap ones head around an outside the box alternative.

I agree, I am sure at the UDS when all this is laid out development will effectively end on existing system tray icons. That and since 10.04 is an LTS nothing will change until the next LTS for those that stick with it. I tried the gnome global menu a while back, but thought it was rather pointless as OpenOffice and Firefox do not work with it (not GTK) and I use them all the time. How they solve this for the netbook in 10.10 and desktop in 11.04 and am looking forward to see. Anything that removes clutter and streamlines the interface I generally support.

I have looked on Gnome-Look for alternative icons that may fix this problem, but that is still a messy workaround and have not had much success.

---

### Post by Tryfon on 2010-05-15
This bug has really got to be fixed. I have checkgmail in my startup and its ugly face has been staring at me all the freaking time since I don't even remember which version of Ubuntu!

I don't think I can take it for too long more. Show some mercy and somebody fix it pleeeaaase...

---

### Post by Tryfon on 2010-05-15
Fixed for CheckGmail, HOORRAYYY!!!!

You just need to run the command ```
checkgmail -update
``` and make sure to respond with a capital 'Y' when asked to confirm!

---

### Post by Ubuntnux on 2010-05-15
Didn't work for me...

---

### Post by Neovos on 2010-05-15
> **Tryfon said:**
> You just need to run the command ```
checkgmail -update
``` and make sure to respond with a capital 'Y' when asked to confirm!

This issue is so weird. I want to think that the applet itself is causing it, yet it seems that the individual programs can do something to their own icons that can then fix it. VLC fixed itself and gmail in this case fixed itself too. Anyone know of any cases where it fixed, then reverted back? or maybe we can dig around the source/icons/changelogs of those programs where it was fixed and see if they changed anything?

---

### Post by oarion7 on 2010-05-26
> **Ubuntnux said:**
> Didn't work for me...


Ditto...


You would think, even if this isn't the highest priority, that you wouldn't want to release an operating system whose default GUI had obvious glitches in it...:confused:

---

### Post by lunatico on 2010-06-10
This simply keeps me away from darker themes, which I like a lot, but unfortunately can't use.

---

### Post by grindboy on 2010-06-11
I got the same issue with the default theme for 10.04 so I've changed to the same theme I used in 9.10 (Shiki-Colours). In 9.10 there were no problems. Not even with Tweetdeck (Adobe Air) or Spotify (WINE) now in 10.04 using the same theme I'm getting the white background showing for both these apps.

How come we still don't know whats causing this? I can understand that Canonical is unwilling to fix it if they are phasing out the notification area all together but I get the impression from posts that this has been a bug for eons. Why wasn't it fixed back when the notification was going to be used for forseeable future?

---

### Post by tondo1 on 2010-06-15
hi
i also had that problem but i solved it by installing truecrypt. i dont know how that help but it works. i tried in ubuntu 9.10 and 10.04 and works in both!!!

---

### Post by lunatico on 2010-06-15
> **tondo1 said:**
> hi
i also had that problem but i solved it by installing truecrypt. i dont know how that help but it works. i tried in ubuntu 9.10 and 10.04 and works in both!!!

How did you installed that? I don't see a truecrypt package on the repositories.

---

### Post by tondo1 on 2010-06-18
UTFG :D
you can download truecrypt from their official website
it is for both 32 and 64 bit OS
you can try it but i really dont know how truecrypt can affect transparency of icons :D

---

### Post by Cadeyrn on 2010-06-23
It didn't work for me. Oh, and some more apps that have the glitch are Desktop Drapes and the Steam tray icon when running through Wine 1.2-rc4.

---

### Post by Spike-X on 2010-06-24
I've gone back to running a non-transparent panel. Problem solved!

---

### Post by eats7 on 2010-06-25
banshee also has this problem. i am on lucid

---

### Post by jesuisbenjamin on 2010-06-25
> **Neovos said:**
> I too am quite annoyed by this. This is 10.4 Lucid for crying out loud, everything should be perfect by now! ....right?

I was trying to isolate the problem and tried something as you can see in my screenshot below: Icons on the gnome bar itself? they respect transparencies. The same icons in the notification area? not so much. I think the notification applet itself is a better place to start looking for this then the gnome bar. Anyone familiar with the source packages for that applet or where to find them? Time to start hacking!

another thread on notification applet found the packages.
[http://ubuntuforums.org/showpost.php?p=9510000&postcount=44](http://ubuntuforums.org/showpost.php?p=9510000&postcount=44)

---

### Post by bornagainpenguin on 2010-07-24
> **Tryfon said:**
> Fixed for CheckGmail, HOORRAYYY!!!!

You just need to run the command ```
checkgmail -update
``` and make sure to respond with a capital 'Y' when asked to confirm!

You get best results with this by doing a change to root before updating.

```
sudo su
```

Then run the above command, being sure to type "Y" when it asks if you want to do an update.  The application will then launch--just close it out, that is root's version of the program.  Cancel out of the password request also.  Now exit the terminal to log out of your root account.

```
exit
```

Then start the application from the application menu as usual, the icon in the tray should work as expected and in accordance to the rest of the system.

Hope that helps.

--bornagainpenguin

---

### Post by Neovos on 2010-07-25
> **jesuisbenjamin said:**
> another thread on notification applet found the packages.
[http://ubuntuforums.org/showpost.php?p=9510000&postcount=44](http://ubuntuforums.org/showpost.php?p=9510000&postcount=44)

Thanks Jesuis, I'll have to check that out when I get a chance. 

Another interesting set of behaviors (and why I further think it is not program specific at all, but all within the applet itself) is exemplified in the pictures below. I first had true-crypt running which showed the white border issue. But upon starting Destroy Twitter 2, the true-crypt icon fixed itself and now just the DT2 icon had the white border. I tried starting another one just to see if the problem was just occurring on the "newest" icon but it was to no avail; it occurred on both of the newest ones. So I can't really find a way to replicate it for sure, but I'm pretty confident that different versions of icons aren't the core of the problem even though they may fix it at times.

---

### Post by jerrykenny on 2010-07-25
Also seemed to be a problem with nvidia graphics cards and transparency.

The terminal for instance would display white text on a white background.

Wonderfull.

So the simplest kludge was just to turn off the tranparency. prefences. appearance, desktop effects i think.

---

### Post by Tryfon on 2010-07-25
where exactly is this transparency option located? I'd like to try it with skype.

---

### Post by K. Hendrik on 2010-07-30
I got this problem with VLC, TweetDeck and TV-Browser

---

### Post by seb_42 on 2010-07-30
Hello !

I'm on Lucid, and I have also this problem (I can see it with VLC or the Network Manager).

I post to notice that :

 - I have a nVidia 7600 card (maybe this is related to the way transparency is handled with nvidia cards ?)

 - the "white" color correspond to the color indicated in system->preferences->appearance->theme->customize...->Colors->Window_ Background. (I'm translated from Ubuntu in French, maybe the names are slightly different)

---

### Post by haydoni on 2010-07-30
I see this with open office (systray quickstarter), vlc (kind of pointless - but now seems to be default behaviour), spotify (under wine). The "show desktop" icon exhibits similar, but apparently intentional, behaviour...

Pretty crazy that the Gnome "bug", if that's what it is, is 5 years old!

---

### Post by Marctwo on 2010-07-30
If those in charge are planning to replace this intuitive systray interface with the clunky app indicator then all this is great for them as users will at least appreciate the nice looking icons...

This didn't really bother me but I do use the systray in AWN as I intend to ditch the buggy gnome panels and their randomly disappearing applets anyway.

---

### Post by seb_42 on 2010-07-31
Back after some tests. I'm more and more convinced that the problem is related to nvidia drivers...

I'm in dual screen and I've realized that, in my configuration, whatever driver I use (96, 173, or current (ie 195) ), the problem only appears when Xinerama is enabled !

There is no longer the "white background bug" when Xinerama is disabled, even in dual screen. In my case, I do need Xinerama, so I prefer having this "bug" than disabling Xinerama, but maybe you should consider disabling it, if it's too annoying ;) (or at least to know if there is the same behavior with your configuration)

---

### Post by G_u_s on 2010-07-31
My card is Intel...

---

### Post by seb_42 on 2010-07-31
Ok, so we can only conclude it's a really weird bug xD

I think it is the way Gnome handle transparency that is the problem. Sometimes, it computes itself the colors, and sometimes asks the graphic card. And maybe this decision depends on a lot of complex factors, that's why some apparently unrelated modifications can affect the behavior. :/

---

### Post by Marctwo on 2010-07-31
In my limited experience, this is only an issue with the systray applet in the gnome-panels.  Icons elsewhere on the panels may be subject to other bugs but they at least preserve their transparency.  Icons in systray applets on other docks/panels also preserve their transparency.  This has really obvious implications...

---

### Post by seb_42 on 2010-07-31
Hello all ! I'm very very happy :D

Problem solved ! (well, in my configuration, at least. Hope that would work for you too)

I've downloaded the source code of the notification-area-applet (the one that has the background bug, part of the gnome-panel package) and the source code of the new indicator-applet, that has a correct background.

I compared both, try a lot of modifications without success, but finally succeeded in having something working ! (Even if finally, I didn't used any code from the working applet... I've just commented some code, I don't really understand how, but it seems to work xD)

Try this and give some feedback :

1) Right click on the notification area (the "systray", as it is erroneously called) and remove it from the panel.

2) VERY IMPORTANT : create a backup of a file you'll modify later :
```
cd /usr/lib/gnome-panel
sudo cp notification-area-applet notification-area-applet.bak
```

3) Download the attachment

4) Replace the file /usr/lib/gnome-panel/notification-area-applet by the one in the archive you've downloaded in 3)

5) Rigth-click on your panel, select Add..., and add a "Notification area". If the bug is corrected, it's finished !! If a problem occurs (which would be the case, in my opinion...), remove the newly added applet (if any), and continue to next step.

6) You'll have to compile yourself the package fixed. Don't worry, it isn't (too much) complicated : just follow the following steps

7) Download the necessary packages :
```
sudo apt-get install dpkg libgtk2.0-dev liborbit2-dev libbonoboui2-dev libgnome-desktop-dev libwnck-dev libgconf2-dev libgconf2.0-cil-dev libdbus-glib-1-dev libcanberra-gtk-dev librsvg2-dev libgweather-dev
```

8 ) download the source code of gnome-panel 
```
sudo apt-get source gnome-panel
```

9) Go to the directory of the sources :
```
cd ~/gnome-panel-2.30.2/
```

10) Configure your future compilation :
```
sudo ./configure
```

11) If "./configure" tells you that some packages are missing, install them. I've tried to be exhaustive on step 8 ), but maybe I failed xD. The packages to install have always a name like libXXXX-dev. Go back to step 10), until it works ;)

12) Replace the applets/notification-area/na-tray-child.c file by the one on the attachment.

13) Compile all
```
sudo make
```

14) Install the new notification area
```
cd applets/notification-area
sudo make install
```

15) Put it in the good place (don't understand why it isn't already the case...)
```
sudo cp /usr/local/libexec/notification-area-applet /usr/lib/gnome-panel/notification-area-applet
```

16) Same as step 5)

Hope this will work for you !

---

### Post by hegomir on 2010-08-06
Thank you! The above solution worked for me! And it only took a second! It just worked after replacing notification-area-applet (a.k.a. the 6th step way). 

Thank you so much!

Oh, and I'm using lucid lynx, with ati 56xx series.

---

### Post by G_u_s on 2010-08-07
> **seb_42 said:**
> Hello all ! I'm very very happy :D

Problem solved ! (well, in my configuration, at least. Hope that would work for you too)

[...]

Try this and give some feedback :

[...]

Hope this will work for you !

Well, friend, it did indeed work! I had to do the whole procedure, and add extra dependencies, but as far as I can tell, the bug is gone (I've tested with VLC, I can't remember what the other problematic programs were, silly me).

Many thanks, maybe you should submit your .c to the development team, and/or ask this tutorial to be cited in a FAQ somewhere.

Again, many thanks for taking the time to do this =)

---

### Post by jorux on 2010-08-08
Amazing!
 It works.

---

### Post by Tryfon on 2010-08-08
You should definitely submit your bug fix to Canonical. It is crucial.

---

### Post by seb_42 on 2010-08-08
I've reported this as a comment/attachment on 

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/403135?comments=all](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/403135?comments=all)

However, as I've said in the comment, this fix is very "dirty". It seems only to work, in my case, for the default theme. Is this the same for you ?

---

### Post by hegomir on 2010-08-11
Yeah, I can confirm it.

Since I update my Ambiance theme to the new maverick meerkat look, the fix stopped working. :/

Oh, well.

---

### Post by lfruiz on 2010-08-12
Wow, thank you so much. Works excellent.

---

### Post by lsdrew on 2010-08-14
Thanks for the patch. Worked perfectly.

---

### Post by jamessimo on 2010-08-15
Hey guys! I want to try this patch, but on step 4 were I swap the applet for the fixed one, I cannot because of permissions (Never had to change system files before).

How do you replace the notification-area-applet? I assume through terminal because I have root access there.

---

### Post by Southernlights on 2010-08-23
I'm not sure how it compares with the fix given earlier by [seb_42]("http://ubuntuforums.org/member.php?u=1121548") but bug #403135 
([https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/403135](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/403135)) 
on launchpad I think is also about the same problem.  There is a lot going on in that thread
 but reply #175 ([https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/403135]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/403135/comments/175")
[/comments/175]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/403135/comments/175")) by Konstantinos Natsakis also gives a fix which just involves
replacing two packages (gnome-panel and gnome-panel-data) and restarting the Gnome 
panel and bonobo-activation-server (I'm not sure what this is). 


It fixed the problem for me after a restart.  Was so happy when it worked :mrgreen:

---

### Post by Marogian on 2010-09-03
> **jamessimo said:**
> Hey guys! I want to try this patch, but on step 4 were I swap the applet for the fixed one, I cannot because of permissions (Never had to change system files before).

How do you replace the notification-area-applet? I assume through terminal because I have root access there.

Extract the backup to your desktop and do something like:
```
sudo cp ~/Desktop/notification-area-applet /usr/lib/gnome-panel/notification-area-applet
```

---

### Post by jamessimo on 2010-09-06
> **Marogian said:**
> Extract the backup to your desktop and do something like:
```
sudo cp ~/Desktop/notification-area-applet /usr/lib/gnome-panel/notification-area-applet
```

Thanks for the reply! ill try it out tonight!

---

### Post by lunatico on 2010-09-06
> **seb_42 said:**
> 
5) Rigth-click on your panel, select Add..., and add a "Notification area". If the bug is corrected, it's finished !! If a problem occurs (which would be the case, in my opinion...), remove the newly added applet (if any), and continue to next step.


Yup. After step 5 it was fixed... on a machine that was previously upgraded from 9.10 so that might make a difference. I shall try with another 10.04 that was installed fresh.

It does concern me that you say you don't know what fixed it... I hope nothing else breaks under the hood!

But thanks anyway!

---

### Post by jamessimo on 2010-09-08
> **Marogian said:**
> Extract the backup to your desktop and do something like:
```
sudo cp ~/Desktop/notification-area-applet /usr/lib/gnome-panel/notification-area-applet
```

Worked! Had to change cp to mv but it worked!! 

I can confirm this also works with wine applications in the notification area (Spotify, Steam ect)

---

### Post by seb_42 on 2010-09-08
> **lunatico said:**
> 
It does concern me that you say you don't know what fixed it... I hope nothing else breaks under the hood!

Don't panic, the only thing I've done is commented out some code in a "if ... then ... else if .... then ... else if .... then ..." to force one of the cases.

It only forces the way transparency is handle in the notification area applet (can't change anything else on the system), and the only thing I don't understand is, to be simple, "why forcing the use of this transparency mode resolve the problem ?"

Thanks for your replies anyway, I'm happy my work helps other people :)

---

### Post by lunatico on 2010-09-09
> **seb_42 said:**
> Don't panic, the only thing I've done is commented out some code in a "if ... then ... else if .... then ... else if .... then ..." to force one of the cases.

It only forces the way transparency is handle in the notification area applet (can't change anything else on the system), and the only thing I don't understand is, to be simple, "why forcing the use of this transparency mode resolve the problem ?"

Thanks for your replies anyway, I'm happy my work helps other people :)

Yeah no panic... nothing has crashed anyway so safe fix it is. Cheers!

---

### Post by taavi on 2010-10-06
After upgrade to 10.10-rc my Sonata icon has white background. Maybe fixed in official, but maybe not...

Icons are transparent pngs and this is git install. If this does matter.

---

### Post by cypresstwist on 2010-10-12
Same problem here with Sonata.

---

### Post by Tares on 2010-10-15
It was fixed in 10.04 and its back in 10.10 :/

---

### Post by Shpongle on 2010-10-22
This is a joke seriously , 5 years...  its the little things like this that turn people off .  Paper cut candidate here .  /rant .      @ seb thanks for the fix

---

### Post by kjekse on 2010-10-23
Damn, I couldn't use the fix. Got problems when doing make.
I had all packages I needed as well.

---

### Post by int0x80 on 2010-10-27
Awaiting for bugfix... :(

---

### Post by int0x80 on 2010-11-02
[http://web.archiveorange.com/archive/v/NUQmuXe5EMkAUaryr32X](http://web.archiveorange.com/archive/v/NUQmuXe5EMkAUaryr32X)

[http://web.archiveorange.com/archive/v/NUQmugLWAmyUm7aprEmq](http://web.archiveorange.com/archive/v/NUQmugLWAmyUm7aprEmq)

This workaround seems to work, I didn't try yet...

---

### Post by joslin on 2010-11-10
Comment #187 from this launchpad bug resolved any issues I was having:

[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/403135]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/403135")

Thanks.

---

### Post by lunatico on 2011-05-11
> **joslin said:**
> Comment #187 from this launchpad bug resolved any issues I was having:

[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/403135]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/403135")

Thanks.

Thanks!

Have used this on 10.04 and Linux Mint 10 and it works.

---

### Post by mwillams73 on 2011-06-04
Thank You!!!!!!! That worked even on my live usb with persistance lol, It begs the question though if it's that simple a whole 2 seconds, why hasnt the devs just patched this? anyways thanks for this!!!!!!

---

### Post by apuertas on 2011-07-04
> **seb_42 said:**
> Hello all ! I'm very very happy :D

Problem solved !
[...]
Hope this will work for you !

Good Job!!
In elementaryOS works perfectly!!

Thank you so much!  :D

---

### Post by XTREEM|RAGE on 2012-02-11
Does any one know if this works for 11.10? Don't want to break anything because it's an "old" fix.

I have troubles with truecrypt having a white background.

---

