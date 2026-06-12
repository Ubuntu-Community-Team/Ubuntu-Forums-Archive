---
title: "How do I install KDE 4.0 b3 in Kubuntu 7.10  (the easy way)?"
date: 2007-10-19
forum: Desktop Environments
---

### Post by RipRapRob on 2007-10-19
As the title of this thread says:

[B]I'm running Kubuntu 7.10 and would like to install KDE 4.0 newest beta the easiest way.
[/B]
I've tried installing using the Adept Manager (I'm to much of a Linux-noob to try compiling anything myself) by selecting most packages with the KDE4 prefix (most packages wthout the "-dev" suffix).

 After downloading a LOT of packages I got an error message saying "The application Adept Updater (dept_updater) crashed and caused the signal 11 (SIGSEGV)".

And the backtrace says something like: "This backtrace appears to be of no use. This is probably because you rpackages are built in a way which prevents creation of proper backtraces, or the stack frame was seriously corrupted in the crash."

I can't seem to get around this problem - I get more or less the same error every time I try to start the Adept Updater, but thats OK: I'll reinstall Kubuntu, while waiting for your help :KS I'm just mentioning this, to show you I've tried installing KDE 4.0  before shouting 'help' :rolleyes:

So the problem I'm hoping someone of you can help me with is 'just' this:

[B]I really would like to try the KDE 4.0 beta 3: Is there an easy way or a step by step guide for installing KDE 4 in Kubuntu 7.10?
[/B]
I've only managed to find guides for K/Ubuntu 7.4, but under 7.10 I expect to be able to install without having to use the command line (yes, I'm that kind of user :-\") 

Thanks in advance for your help!

Regards
Rob (mentally preparing for the wrath of those who think noobs should stay the hell away from beta stuff)

(English is not my first language, so I apologize for any spelling and grammar errors)

---

### Post by RipRapRob on 2007-10-19
Solved the problem with the Adept Manager (sudo dpkg --configure -a), so I think I saved myself a reinstall :)

But still needs help with installing KDE 4...

---

### Post by RipRapRob on 2007-10-19
I've tried following the instructions on [http://kubuntu.org/announcements/kde4-beta3.php](http://kubuntu.org/announcements/kde4-beta3.php) but KDE 4 does not show up as an option on my Login-menu :(

I've tried restarting both X and my PC, but to no avail :(

---

### Post by id12586 on 2007-10-21
I am also interested  on that.

One important thing is whether Kde3 + kde4 can actually "live" together or we are talking only for a full upgrade..

---

### Post by midnightracer on 2007-10-21
I just started using kubuntu a couple of days ago and I still cannot figure out how to get my sound to work, so I was hoping maybe an upgrade to kde 4 beta 3 may make it a little easier to figure out. Anyway, I was also looking on kubuntu's website to do this upgrade to use kde 4 completely and throw 3 out the window. You say the instructions on kubuntu.com didnt help? I'm too afraid to try cause I do not want to screw anything up. Especially cause I am a noob and a half.

---

### Post by btdown on 2007-10-21
[http://kubuntu.org/announcements/kde4-beta3.php](http://kubuntu.org/announcements/kde4-beta3.php)

---

### Post by GeneralZod on 2007-10-21
> **midnightracer said:**
> I just started using kubuntu a couple of days ago and I still cannot figure out how to get my sound to work, so I was hoping maybe an upgrade to kde 4 beta 3 may make it a little easier to figure out. Anyway, I was also looking on kubuntu's website to do this upgrade to use kde 4 completely and throw 3 out the window.

KDE4 is not at the stage where it is better than KDE3 yet (in fact, it is significantly worse), and likely won't be until KDE4.1 or so is released.  Sticking with KDE3 is by far the best option :)

---

### Post by midnightracer on 2007-10-21
> **GeneralZod said:**
> KDE4 is not at the stage where it is better than KDE3 yet (in fact, it is significantly worse), and likely won't be until KDE4.1 or so is released.  Sticking with KDE3 is by far the best option :)

Ok, thanks for the heads up. As a noob I will definitely stay away from 4 until its ready. Do you know when the stable version is likely to be released?

---

### Post by GeneralZod on 2007-10-21
> **midnightracer said:**
> Ok, thanks for the heads up. As a noob I will definitely stay away from 4 until its ready. Do you know when the stable version is likely to be released?

KDE4.0 should, if all goes to plan, be released around 11th December.  Even then, though, it will likely be of Beta-quality, alas :(

---

### Post by LuisAugusto on 2007-10-23
> **GeneralZod said:**
> KDE4 is not at the stage where it is better than KDE3 yet (in fact, it is significantly worse), and likely won't be until KDE4.1 or so is released.  Sticking with KDE3 is by far the best option :)

It is true that KDE 4.1 will not be the best option, but I do not think that KDE 4.0 will be worst than KDE 3.5, basely I already find pretty much everything to be better. The only thing lacking a lot is Plasma, but since it is the only piece that have not going freeze, I believe it would give a average desktop experience.

> **GeneralZod said:**
> KDE4.0 should, if all goes to plan, be released around 11th December.  Even then, though, it will likely be of Beta-quality, alas :(

That is not true, most of KDE already passed  beta quality, they are almost RC quality, however, again, people guide themself looking just at Plasma.

KDE 4.0 will be a nice release, it will be lacking some details (as klipper and kprint), but it will have everything you need, from file management to compiz like effects, indeed, it will not be as stable as 3.5, but for most users it will be enough.

Just my 2 cents.

---

### Post by bmorency on 2007-10-23
> **btdown said:**
> [http://kubuntu.org/announcements/kde4-beta3.php](http://kubuntu.org/announcements/kde4-beta3.php)

I followed the instruction at that site but when it says

"To run it as a full session copy /usr/lib/kde4/share/apps/kdm/sessions/kde.desktop to /usr/share/xsessions/kde4.desktop"

i get an error saying

"cp: cannot stat `/usr/lib/kde4/share/apps/kdm/sessions/kde.desktop': No such file or directory"

I checked and i do not have a session directory under /usr/lib/kde4/share/apps/kdm/
only a pics directory.

these instructions worked when i tried it under fiesty instead of gutsy and using kde 4 beta 2.

---

### Post by Nergar on 2007-10-25
> **bmorency said:**
> I followed the instruction at that site but when it says

"To run it as a full session copy /usr/lib/kde4/share/apps/kdm/sessions/kde.desktop to /usr/share/xsessions/kde4.desktop"

i get an error saying

"cp: cannot stat `/usr/lib/kde4/share/apps/kdm/sessions/kde.desktop': No such file or directory"

I checked and i do not have a session directory under /usr/lib/kde4/share/apps/kdm/
only a pics directory.

these instructions worked when i tried it under fiesty instead of gutsy and using kde 4 beta 2.

Same thing here any help would be appreciated

---

### Post by LuisAugusto on 2007-10-26
Oh, just as a side note, Kubuntu KDE 4 Packages suck, you'll get better results compiling, or using another distro with KDE 4 pre-compiled packages (OpenSUSE, Mandriva, etc)

---

### Post by hotweiss on 2007-11-21
Try following these instructions:

[http://babelfish.altavista.com/babelfish/tr?lp=it_en&url=http%3A//www.tuxmind.altervista.org/%3Fp%3D484](http://babelfish.altavista.com/babelfish/tr?lp=it_en&url=http%3A//www.tuxmind.altervista.org/%3Fp%3D484)

---

