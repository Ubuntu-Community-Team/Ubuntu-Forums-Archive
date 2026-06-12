---
title: "KDM Theme Manager Not Working"
date: 2006-03-09
forum: Desktop Environments
---

### Post by Lexicon on 2006-03-09
Hi all.  Linux/Kubuntu newbie here.


I've got the ubuntu 0.9.8 version of KDM Theme Manager installed, but I can't figure out why it's not working.  When I try to install Theme Manager themes, (.kth files) it gives me the error "The file is not a valid KDM theme archive."  But I'm pretty damned sure it is.  I've tried five different themes from kde-look.org, and for those that require certain window decorations or icons, I've installed those.  But still the error.  I've uninstalled and reinstalled Theme Manager a couple times, using both Adept and the .deb on kde-apps.org,  but still no luck.  Anyone know what's up?

---

### Post by Jucato on 2006-03-09
KDM Themes are responsible for how your KDM login screen (the one that asks you for your username and password) looks. KDM Theme Manager is found in KControl > System Administration.

KDE Theme Manager (.kth) is responsible for how your whole desktop looks. The KDE Theme Manager is found in KControl or System Settings. 

Two different things. Two different theme files. Yeah, sometimes the names get confusing. :D

---

### Post by Lexicon on 2006-03-09
Okay, I'm a really big newbie, because I still can't find what I'm looking for.  "KDM Theme Manager" is under "System Administration" in "System Settings".  Not only that, but when I check out a screenshot for "KDM Theme Manager" and its windowbar says "KDE Control Module."  So where do I go for what I want (the thing to install .kth files)? I can't find anything else to do what I want.

Sorry for being such a huge n00b.

---

### Post by aysiu on 2006-03-09
Press Alt-F2 and type ```
kcontrol
``` The first thing you see at the top should be Appearance and Themes. Expand that. Then you should see something that says "theme manager" toward the bottom of that expanded menu. That's where you install the *.kth themes you downloaded from kde-look.org

KDM is, as was stated before, for the login screen (where you type your username and password to get into Kubuntu). Those have separate themes that I don't believe can be installed graphically. The KDM themes get stored in /usr/share/apps/kdm/themes

---

### Post by Lexicon on 2006-03-09
Thank you very much aysiu (and Fenyx, even though I was too dumb to understand your instructions).  It seems kind of strange to have most of the settings available through the "System Settings" menu in K Menu, but some only accessible through kcontrol, which requires explaining to a complete newbie to understand.  Is it that only officially-sanctioned KDE controls can go in the "System Settings" section?

Again, thanks.

---

### Post by aysiu on 2006-03-09
I hate System Settings.

There's no shortcut to KControl in the new Kubuntu, but it's still there, and I still use it. KControl is easier to use (I prefer trees to buttons for settings) and has more settings available.

Just use KControl.

---

### Post by m.musashi on 2006-03-09
[QUOTE=aysiu]There's no shortcut to KControl in the new Kubuntu[/QUOTE]
I'm sure you know this but for any newbies you can add it to the kmenu. I put it right under "system settings" on the main menu.

---

### Post by Jucato on 2006-03-09
Or you could also do this:
1. Right click on any blank area of the panel/taskbar to launch the "Configure Panel" option
2. Go to the "Menus" option, probably 3rd from the top
3. Then in the Optional Menus checklist, enable the "Settings" checkbox
4. Click Apply, then OK

This will add a Settings menu group in K Menu for easy access to either KControl or the individual KControl modules.

@Lexicon: "System Settings" is a Kubuntu project, not a KDE one. The official "sanction" control center for KDE is KControl. I hate it too, as well as the Adept package manager. (well, not really hate, considering these are just babies in terms of development. You can't hate babies right?)

EDIT: KDM themes CAN be installed graphically, IF you have the KDM Theme Manager installed. As a clue, KDM Themes will usually come in .tar.gz files. While KTH (KDE Themes) will come in .kth files (or .kth inside .tar.gz). Take note that to install/remove/change the KDM themes, you have to hit the Administrator Mode button.

---

### Post by m.musashi on 2006-03-09
[QUOTE=Fenyx]Or you could also do this:
1. Right click on any blank area of the panel/taskbar to launch the "Configure Panel" option
2. Go to the "Menus" option, probably 3rd from the top
3. Then in the Optional Menus checklist, enable the "Settings" checkbox
4. Click Apply, then OK

This will add a Settings menu group in K Menu for easy access to either KControl or the individual KControl modules.

@Lexicon: "System Settings" is a Kubuntu project, not a KDE one. The official "sanction" control center for KDE is KControl. I hate it too, as well as the Adept package manager. (well, not really hate, considering these are just babies in terms of development. You can't hate babies right?)

EDIT: KDM themes CAN be installed graphically, IF you have the KDM Theme Manager installed. As a clue, KDM Themes will usually come in .tar.gz files. While KTH (KDE Themes) will come in .kth files (or .kth inside .tar.gz). Take note that to install/remove/change the KDM themes, you have to hit the Administrator Mode button.[/QUOTE]
Thanks. That's even better. And thanks for the instructions. I guess I should remember help isn't help if you don't give the steps.

---

### Post by m.musashi on 2006-03-09
Looking over this thread again and I'm confused. Which one is KDM theme manager? I can find a theme manager in KControl but I thought that was the kth files (KDE themes as you said). So where is the KDM theme manager? Do you have to add it? How? Can anyone explain the difference and reasons for using one over the other.  Aysiu says he hates system settings, Fenyx doesn't like KControl (or did I misunderstand). I'm trying to hijack or anything. I'm just starting to play with KDE and making it look cool is the first thing. Thanks.

More on topic, the OP mentioned the theme-manager themes on kde-look. Those are for the theme manager in system settings, right? Or is that the same as the one in KControl? Where can you find themes for KDM Theme Manager?

---

### Post by m.musashi on 2006-03-09
Looking over this thread again and I'm confused. Which one is KDM theme manager? I can find a theme manager in KControl but I thought that was the kth files (KDE themes as you said). So where is the KDM theme manager? Do you have to add it? How? Can anyone explain the difference and reasons for using one over the other.  Aysiu says he hates system settings, Fenyx doesn't like KControl (or did I misunderstand). I'm trying to hijack or anything. I'm just starting to play with KDE and making it look cool is the first thing. Thanks.

More on topic, the OP mentioned the theme-manager themes on kde-look. Those are for the theme manager in system settings, right? Or is that the same as the one in KControl? Where can you find themes for KDM Theme Manager?

---

### Post by aysiu on 2006-03-09
[QUOTE=Fenyx]
EDIT: KDM themes CAN be installed graphically, IF you have the KDM Theme Manager installed.[/QUOTE] How do you install the KDM theme manager? Is that in the repositories?

---

### Post by Jucato on 2006-03-09
Um... I got mine from KDE-Apps.
[http://www.kde-apps.org/content/show.php?content=33231]("http://www.kde-apps.org/content/show.php?content=33231")
Scroll a bit down, and there's a deb for Kubuntu.

EDIT: I just checked, there a new version of kdmtheme here:
[http://www.kde-apps.org/content/show.php?content=34690&PHPSESSID=9fed92bf3b237e828b7d23f495514c39]("http://www.kde-apps.org/content/show.php?content=34690&PHPSESSID=9fed92bf3b237e828b7d23f495514c39") But I haven't tested this one yet.

---

### Post by aysiu on 2006-03-09
Thanks for the link, Fenyx.

I'm actually cool with just putting stuff in /usr/share/apps/kdm/themes manually, but it's good to know for the future, just in case.

---

### Post by Jucato on 2006-03-09
[QUOTE=m.musashi]Looking over this thread again and I'm confused. Which one is KDM theme manager? I can find a theme manager in KControl but I thought that was the kth files (KDE themes as you said). So where is the KDM theme manager? Do you have to add it? How? Can anyone explain the difference and reasons for using one over the other.  Aysiu says he hates system settings, Fenyx doesn't like KControl (or did I misunderstand). I'm trying to hijack or anything. I'm just starting to play with KDE and making it look cool is the first thing. Thanks.

More on topic, the OP mentioned the theme-manager themes on kde-look. Those are for the theme manager in system settings, right? Or is that the same as the one in KControl? Where can you find themes for KDM Theme Manager?[/QUOTE]

Sorry I didn't see this earlier, before I posted my reply to aysiu. Ok, here goes:
1. The KDM Theme Manager is an app that you have to install by downloading the .deb from the link I posted (it's not in the repositories). BUT, like aysiu said, you can change KDM themes manually, by copying the downloaded themes to /usr/share/apps/kdm/theme. I'm just not sure how you can activate them. the KDM Theme Manager app provides a nice GUI for doing this.

2. KDM themes can be downloaded from KDE-Look.org. They have their own section. 

3. Actually, I hate System Settings, along with Adept, the 2 Kubuntu projects. I feel they are still too immature to be included as the default for the distro. Especially Adept, which can ruin your system if you are not careful. But this is something the devs have decided, so my opinion basically doesn't matter. (Btw, the Adept in the Dapper Live CD is even worse! It's like only geeks will be able to understand and use it) Unfortunately, KPackage (the official KDE package manager) doesn't offer the same power as Synaptic.

4. The Theme-Manager section in KDE-Look is indeed for the KControl Theme Manager module. It comes in .kth files (or a .kth file inside .tar.gz files).

Hope these clears things up a bit.

---

### Post by aysiu on 2006-03-09
[QUOTE=Fenyx]
BUT, like aysiu said, you can change KDM themes manually, by copying the downloaded themes to /usr/share/apps/kdm/theme. I'm just not sure how you can activate them.[/quote] The graphical way is probably "better," at least for the OP. Just for the record, though, you activate it by editing /etc/kde3/kdm/kdmrc and changing the line that says /usr/share/apps/kdm/themes/kubuntu to /usr/share/apps/kdm/themes/name_of_new_theme

> 
3. Actually, I hate System Settings, along with Adept, the 2 Kubuntu projects. I feel they are still too immature to be included as the default for the distro. Especially Adept, which can ruin your system if you are not careful. But this is something the devs have decided, so my opinion basically doesn't matter. (Btw, the Adept in the Dapper Live CD is even worse! It's like only geeks will be able to understand and use it) Unfortunately, KPackage (the official KDE package manager) doesn't offer the same power as Synaptic. Amen. First thing I do when installing Kubuntu is change System Settings back to Control Center and then replace Adept with Synaptic Package Manager.

---

### Post by m.musashi on 2006-03-10
[QUOTE=aysiu] Amen. First thing I do when installing Kubuntu is change System Settings back to Control Center and then replace Adept with Synaptic Package Manager.[/QUOTE]
Yeah, I'm new(er) to the KDE side and I noticed that updates are run by Adept. I figured it was the same as synaptic or whater runs updates on the gnome side. If it's problematic how can I switch it? Thanks.

---

### Post by aysiu on 2006-03-10
Go to KMenu > System > Konsole and type ```
sudo apt-get update
sudo apt-get remove adept
sudo apt-get install synaptic
```

---

### Post by Jucato on 2006-03-10
[QUOTE=m.musashi]Yeah, I'm new(er) to the KDE side and I noticed that updates are run by Adept. I figured it was the same as synaptic or whater runs updates on the gnome side. If it's problematic how can I switch it? Thanks.[/QUOTE]

Um... what exactly do you mean? If you are looking for a "Fetch Updates" counterpart in Synaptic, it's the "Reload" button. These updates your repositories and is equivalent to ```
sudo apt-get update
```.

But I guess that's not what you mean, right? :D
Anyway, Adept isn't as problematic as it is unintuitive. The biggest problems that users have with it is that it doesn't prompt you on the changes that you are about to make. The only way you are informed of any changes is either through the status bar or by clicking preview changes, both of which are not good ways of informing users about changes that will affect your system.

---

### Post by m.musashi on 2006-03-10
[QUOTE=aysiu]Go to KMenu > System > Konsole and type ```
sudo apt-get update
sudo apt-get remove adept
sudo apt-get install synaptic
```[/QUOTE]
apt-get or aptitde (ala another thread:)).

Will that also activate synaptic to monitor updates or do I have to do something else? Run it? Make it a auto start program or something.

This may be a dumb question but isn't synaptic already installed on the gnome side? I see gnome apps in my kde menu and kde apps in gnome. I thought gnome an kde were just fronts for ubuntu but that behind the scenes it was the same ubuntu/linux. Am I not getting something?

---

### Post by aysiu on 2006-03-10
Oh, if you already have Gnome, then Synaptic should be installed.
I don't know about updates, because I usually get rid of the notifier.

---

### Post by m.musashi on 2006-03-10
[QUOTE=Fenyx]Um... what exactly do you mean? If you are looking for a "Fetch Updates" counterpart in Synaptic, it's the "Reload" button. These updates your repositories and is equivalent to ```
sudo apt-get update
```.

But I guess that's not what you mean, right? :D
Anyway, Adept isn't as problematic as it is unintuitive. The biggest problems that users have with it is that it doesn't prompt you on the changes that you are about to make. The only way you are informed of any changes is either through the status bar or by clicking preview changes, both of which are not good ways of informing users about changes that will affect your system.[/QUOTE]
Okay, I'm getting confused - even more so:). In gnome I get a little notice that I have new updates. I click it and then can review and install them. In kde I get a little red light. I click it and can install the updates but it's the adept package. When I right click it is say "about adept" or something. Will Aysiu's steps not take it away and put the gnome/synaptic version in its place? I'm actually using dapper but that shouldn't really matter, should it?

BTW, my apologies to the OP. I didn't mean to totally hijack your thread. It just kind of drifted that way. I hope your original question was well answered and that maybe this similar but somewhat off topic tangent is useful to you.

---

### Post by Jucato on 2006-03-10
Hmm... this will be a rather long discussion. but anyway:

1. aptitude is a front-end (that is, something that offers a user interface) to apt-get, so you could use either. heck, you can even use Adept to install Synaptic. Of course, you can't use Adept to uninstall Adept.

2. If you installed kubuntu/kde over an ubuntu installation, Synaptic should already be there. You can check by pressing Alt+F2 (Run command) and typing in "synaptic" (without the quotes). If it runs, then it's installed. You might have initial permission problems, since Synaptic needs to be run w/ administrator privileges, so it needs a kdesu (or gksudo if you're in GNOME) to run it.

3. GNOME and KDE are what we call Desktop Environments. They are responsible for making sure that the apps that you installed play nicely with each other. In short, they are responsible for INTEGRATION, that is, integrating each and every part of the operating system. Now beneath all these, is the Linux kernel, which is the common denominator in all Linux distributions (although they use different release versions, depending on what was available during development). GNOME is the default DE (desktop environment) for Ubuntu, while KDE is the default for Kubuntu (Xfce is for Xubuntu). Of course you're free to install one over the other and mix and match. That is, if you have the bandwidth to download all the needed files. If you don't, then you could hook up with aysiu's latest project, the Ubuntu add-on CD's (shameless plug :D)

---

### Post by m.musashi on 2006-03-10
Cool, thanks for the info. It's starting to make sense. I'm still not clear, though, on how to get synaptic to take over the automatic updates on the kde side - at least without running it manually from time to time. I guess that isn't so bad. Still, I kind of like getting a notice when there are updates available.

---

### Post by Lexicon on 2006-03-10
[QUOTE=m.musashi]BTW, my apologies to the OP. I didn't mean to totally hijack your thread. It just kind of drifted that way. I hope your original question was well answered and that maybe this similar but somewhat off topic tangent is useful to you.[/QUOTE]

My original question was fully answered, and yes, your tangent is useful to me, since I tried Ubuntu earlier and liked the way Synaptic worked better than Adept, so perhaps I'll switch it, knowing that I can (I had just figured Adept was Kubuntu-only and Synaptic was Ubuntu-only).  I may switch it, that is, if I can actually get KDE working again (see my other thread)!

---

### Post by m.musashi on 2006-03-10
[QUOTE=Lexicon]My original question was fully answered, and yes, your tangent is useful to me, since I tried Ubuntu earlier and liked the way Synaptic worked better than Adept, so perhaps I'll switch it, knowing that I can (I had just figured Adept was Kubuntu-only and Synaptic was Ubuntu-only).  I may switch it, that is, if I can actually get KDE working again (see my other thread)![/QUOTE]
Thanks for letting me know. I'm pretty new to the whole forum thing and haven't fully internalized the etiquette. It's hard though when you come across a useful thread but some piece isn't addressed and then one small question leads to another and so on...

What other thread are you refering to?

---

### Post by Lexicon on 2006-03-10
[QUOTE=m.musashi]What other thread are you refering to?[/QUOTE]

"Big Problem This Time" - should be right near the top of the list.

---

### Post by Jucato on 2006-03-10
Btw, Synaptic isn't an Ubuntu-only program. It's also used by Debian and some other Debian-based GNOME distros.

Now I'll go check your other thread :D

---

### Post by gallatin on 2006-03-15
Just wanted to post a thanks to everyone who responded to the KDE themes vs. KDM themes issue. I was having the same problem earlier today, and I think you've provided my answer for me. I'm on a windows box at work at the moment, but I think I'll have some success when I get back to my linux box later today.

Thanks for the patient instructions and advice, it's much appreciated!

---

### Post by lunamystry on 2007-10-10
I can't use my KDEtheme manager (If that is what it is). I click administrator mode but it does not apply whatever theme I have selected. In the log in screen it uses the KDE settings. How do I change that, using graphic interface and through terminal if possible.

---

### Post by lunamystry on 2007-10-10
thought a picture may be useful

---

### Post by The Recorder on 2007-10-11
A later version of KDM Theme Manager - Version:  1.2.1 - is available, which might correct the problem of theme not changing.

[https://sourceforge.net/project/showfiles.php?group_id=204883](https://sourceforge.net/project/showfiles.php?group_id=204883)

See: [http://www.kde-apps.org/content/show.php/KDM+Theme+Manager?content=22120&PHPSESSID=a55e2a359f82fc760104a7c42a64541f](http://www.kde-apps.org/content/show.php/KDM+Theme+Manager?content=22120&PHPSESSID=a55e2a359f82fc760104a7c42a64541f)
for description of update.

Also, make sure that your /etc/kde3/kdm/kdmrc file has the line:

UseTheme=true

... in the same section as the "Theme=/usr/share/apps/kdm/themes/kubuntu" line. Mine did not, and I couldn't get any login but the "boxed" one.  If the above update doesn't work, you will have to edit the "Theme=......." line each time that you want to change your theme.

Hope this helps...

---

### Post by Zorael on 2007-10-17
> **The Recorder said:**
> Also, make sure that your /etc/kde3/kdm/kdmrc file has the line:

UseTheme=true

... in the same section as the "Theme=/usr/share/apps/kdm/themes/kubuntu" line. Mine did not, and I couldn't get any login but the "boxed" one.  If the above update doesn't work, you will have to edit the "Theme=......." line each time that you want to change your theme.

Hope this helps...

This did it for me. :) Awesome, many thanks.

---

### Post by sk0rp10 on 2007-10-21
New version of KDM theme manager correclty reads current theme from configuration file /etc/kde3/kdm/kdmrc but still fails to update it on theme change. 

so... still broken , only manual theme change work as now (gutsy, 21/10/07)

---

### Post by myoungf1 on 2007-10-23
I have noticed that when launching the KDM Theme Manager and then clicking on the Administrator button that the password dialogue box does not come up.  Before I would need to enter my Admin passwork and then click okay but now all it does after I hit the Admin button is it goes directly to the main theme changer screen without prompting for a password.

---

### Post by oobuntoo on 2007-10-26
I have the same problem. I really like to change my KDM theme without having to manually doing it.

---

### Post by aysiu on 2007-10-26
Does Alt-F2 and ```
kdesu kcontrol
``` help get around the *Administrator Mode* issue?

---

### Post by oobuntoo on 2007-10-26
The problem is not that I can't use KDM Theme Manager under System Administration in Kcontrol. It's just that the KDM Theme Manager under Gutsy simply does not work. I can install new KDM themes and they would all show up. But when I select a new theme and click "Apply" then log out, KDM still use the default one.

---

### Post by myoungf1 on 2007-10-26
> **aysiu said:**
> Does Alt-F2 and ```
kdesu kcontrol
``` help get around the *Administrator Mode* issue?

No, it still does not write to the proper file.  I did the command and changed the theme and then hit apply.  I then closed the window and got an error message asking if the changes that I made were to be applied and then hit the apply button again.  I then redid the command and voila the changes were not made.

---

### Post by myoungf1 on 2007-10-26
Here is the output from a terminal when starting the kcontrol module hopefully this will help someone.

Error: "/var/tmp/kdecache-myoungf1" is owned by uid 1000 instead of uid 0.
ERROR: Communication problem with kcontrol, it probably crashed.
myoungf1@myoungf1-desktop:~$ Error: "/tmp/ksocket-myoungf1" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-myoungf1" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-myoungf1" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-myoungf1" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-myoungf1" is owned by uid 1000 instead of uid 0.
kcontrol: Loading themes... ( /usr/share/apps/kdm/themes/ )
kcontrol: Looking for /usr/share/apps/kdm/themes/bioBagatir-login/KdmGreeterTheme.desktop
kcontrol: Looking for /usr/share/apps/kdm/themes/bioBagatir-login/GdmGreeterTheme.desktop
kcontrol: Adding theme bioBagatir Theme
kcontrol: Looking for /usr/share/apps/kdm/themes/circles/KdmGreeterTheme.desktop
kcontrol: Looking for /usr/share/apps/kdm/themes/circles/GdmGreeterTheme.desktop
kcontrol: Adding theme Circles
kcontrol: Looking for /usr/share/apps/kdm/themes/Debian/KdmGreeterTheme.desktop
kcontrol: Looking for /usr/share/apps/kdm/themes/Debian/GdmGreeterTheme.desktop
kcontrol: Adding theme Debian
kcontrol: Looking for /usr/share/apps/kdm/themes/debian-edu/KdmGreeterTheme.desktop
kcontrol: Looking for /usr/share/apps/kdm/themes/debian-edu/GdmGreeterTheme.desktop
kcontrol: Adding theme Debian Edu O1
kcontrol: Looking for /usr/share/apps/kdm/themes/KDM RED/KdmGreeterTheme.desktop
kcontrol: Looking for /usr/share/apps/kdm/themes/KDM RED/GdmGreeterTheme.desktop
kcontrol: Adding theme KDM RED
kcontrol: Looking for /usr/share/apps/kdm/themes/Krystal/KdmGreeterTheme.desktop
kcontrol: Looking for /usr/share/apps/kdm/themes/Krystal/GdmGreeterTheme.desktop
kcontrol: Adding theme Krystal
kcontrol: Looking for /usr/share/apps/kdm/themes/kubuntu/KdmGreeterTheme.desktop
kcontrol: Looking for /usr/share/apps/kdm/themes/kubuntu/GdmGreeterTheme.desktop
kcontrol: Adding theme Kubuntu O2
kcontrol: Looking for /usr/share/apps/kdm/themes/kubuntu-no-userlist/KdmGreeterTheme.desktop
kcontrol: Looking for /usr/share/apps/kdm/themes/kubuntu-no-userlist/GdmGreeterTheme.desktop
kcontrol: Adding theme Kubuntu O2 - No Userlist
kcontrol: Looking for /usr/share/apps/kdm/themes/Linux Passion/KdmGreeterTheme.desktop
kcontrol: Adding theme Linux Passion
kcontrol: Looking for /usr/share/apps/kdm/themes/Satanic/KdmGreeterTheme.desktop
kcontrol: Looking for /usr/share/apps/kdm/themes/Satanic/GdmGreeterTheme.desktop
kcontrol: Adding theme Kubuntu Satanic Edition
kcontrol: Looking for /usr/share/apps/kdm/themes/SE-Baphomet/KdmGreeterTheme.desktop
kcontrol: Looking for /usr/share/apps/kdm/themes/SE-Baphomet/GdmGreeterTheme.desktop
kcontrol: Adding theme Kubuntu SE Baphomet
kcontrol: Looking for /usr/share/apps/kdm/themes/SE-Bat/KdmGreeterTheme.desktop
kcontrol: Looking for /usr/share/apps/kdm/themes/SE-Bat/GdmGreeterTheme.desktop
kcontrol: Adding theme Kubuntu SE Bat
kcontrol: Looking for /usr/share/apps/kdm/themes/SE-Glass/KdmGreeterTheme.desktop
kcontrol: Looking for /usr/share/apps/kdm/themes/SE-Glass/GdmGreeterTheme.desktop
kcontrol: Adding theme Kubuntu SE Glass
kcontrol: Looking for /usr/share/apps/kdm/themes/true-nature/KdmGreeterTheme.desktop
kcontrol: Adding theme True Nature
kcontrol: Loading... ( /etc/kde3/kdm/kdmrc )
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image

myoungf1@myoungf1-desktop:~$ sudo kcontrol
Error: "/var/tmp/kdecache-myoungf1" is owned by uid 1000 instead of uid 0.
ERROR: Communication problem with kcontrol, it probably crashed.
myoungf1@myoungf1-desktop:~$ Error: "/tmp/ksocket-myoungf1" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-myoungf1" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-myoungf1" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-myoungf1" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-myoungf1" is owned by uid 1000 instead of uid 0.
kcontrol: Loading themes... ( /usr/share/apps/kdm/themes/ )
kcontrol: Looking for /usr/share/apps/kdm/themes/bioBagatir-login/KdmGreeterTheme.desktop
kcontrol: Looking for /usr/share/apps/kdm/themes/bioBagatir-login/GdmGreeterTheme.desktop
kcontrol: Adding theme bioBagatir Theme
kcontrol: Looking for /usr/share/apps/kdm/themes/circles/KdmGreeterTheme.desktop
kcontrol: Looking for /usr/share/apps/kdm/themes/circles/GdmGreeterTheme.desktop
kcontrol: Adding theme Circles

---

### Post by ComplexNumber on 2007-12-02
mine doesn't change the theme either no matter what i do ](*,).


EDIT
> **The Recorder said:**
> A later version of KDM Theme Manager - Version: 1.2.1 - is available, which might correct the problem of theme not changing.

[https://sourceforge.net/project/showfiles.php?group_id=204883](https://sourceforge.net/project/showfiles.php?group_id=204883)

See: [http://www.kde-apps.org/content/show.php/KDM+Theme+Manager?content=22120&PHPSESSID=a55e2a359f82fc760104a7c42a64541f](http://www.kde-apps.org/content/show.php/KDM+Theme+Manager?content=22120&PHPSESSID=a55e2a359f82fc760104a7c42a64541f)
for description of update.

Also, make sure that your /etc/kde3/kdm/kdmrc file has the line:

** UseTheme=true**

** ... in the same section as the "Theme=/usr/share/apps/kdm/themes/kubuntu" line. Mine did not, and I couldn't get any login but the "boxed" one. If the above update doesn't work, you will have to edit the "Theme=......." line each time that you want to change your theme.**

Hope this helps...
nice one! that worked :).
it's still a bit crap though...having to manually edit a system file to get a theme to show up.

---

### Post by Snowhog on 2008-06-15
> **The Recorder said:**
> A later version of KDM Theme Also, make sure that your /etc/kde3/kdm/kdmrc file has the line:

UseTheme=true

... in the same section as the "Theme=/usr/share/apps/kdm/themes/kubuntu" line. Mine did not, and I couldn't get any login but the "boxed" one.  If the above update doesn't work, you will have to edit the "Theme=......." line each time that you want to change your theme.

Hope this helps...

Man did it ever! I just have to say THANK YOU, THANK YOU, THANK YOU!! I had made a change to the wallpaper used in my default theme. That was good until I installed the *kdmtheme* package. When I restarted my PC, I had the new wallpaper background, but not the greeter I expected!

Again, thank you for the 'spot on' solution.

---

