---
title: "[SOLVED] Please help with emerald-themes"
date: 2007-10-15
forum: Desktop Effects &amp; Customization
---

### Post by DuKeS15 on 2007-10-15
First of all I'd like to say thanks to all those of you experienced Ubuntu users who make guide's and how-to's. I'm a first time user of Ubuntu (only on my 4th day of switching from windows xp) and if it wasn't for you all i'd be sooooo lost lol So thanx for the help. 

That being said...i am asking you all for help installing emerald-themes on my PC. At first i tried Ubuntu Feisty Fawn using Wubi to not have to do a complete install and everything worked great on 7.04. I was able to get emerald-themes and beryl running no problem. Now that i switched to 7.10 rc i seem to not be able to install emerald-themes. I try to install through the Synaptic Package Manager and i get this error message when marking for install:

[I]The following packages have unresolvable dependencies.
Make Sure that all required repositories are added and enabled in the preferences.

emerald:
 Depends: libemeraldengine0 but it is not going to be installed
 Depends: libwnck18 (>=2.15.90) but it is not installable
[/I]

How do i go about installing those missing dependencies? Like I mentioned, this is only my 4th day using Ubuntu so i'm not very familiar with how to do most simple things on it yet. I do have beryl working 100%, cube and everything and now the only thing i'd need to be at ease is to be able to install the emerald-themes which i loved when i had 7.04.

Any help is GREATLY appreciated. TIA

DuKeS.

---

### Post by DuKeS15 on 2007-10-15
*bump*

---

### Post by cudaman73 on 2007-10-15
Honestly, since i've never had the problem above, the only thing I can think of is maybe you're missing a repository.

Open up Synaptic (System -> Administration -> Synaptic Package Manager).
Bring up the Repositories page (Settings -> Repositories)
Make sure all of the ones on the 'Ubuntu Software' tab are checked, and all ones on the 'Third-party software' ones are unchecked (unless you specifically need them for something).
Click close, then update your apt-cache ( The reload button top left of window)

Then try and install the package again.

If that doesn't wok, someone with more experience will have to help you. :(

---

### Post by DuKeS15 on 2007-10-16
No that didn't solve my problem cudaman. Thanks for trying to help though :)

I did get it resolved another way, found a post around here that explained how to get the missing dependencies i needed. 

For anyone looking to resolve the same issue i had, this reply by **[kingof1981]("http://http://ubuntuforums.org/showthread.php?t=529813&page=2")** on another thread tells you how to get it working. 

In my case i only added the following two lines to a terminal and it did the trick:

[I][COLOR="Red"]sudo aptitude -y -f install libwnck18 libwnck-common
sudo aptitude -y -f install emerald emerald-themes libemeraldengine0
[/COLOR][/I]

hope that helps someone :)

---

