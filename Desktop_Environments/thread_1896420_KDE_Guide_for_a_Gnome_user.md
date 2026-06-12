---
title: "KDE Guide for a Gnome user?"
date: 2011-12-16
forum: Desktop Environments
---

### Post by ve4cib on 2011-12-16
Hi.  I've been a Gnome (2) user for years, and every time I try using KDE I always seem to get lost configuring it or finding the right application to use to perform some random task with.  I've been using Gnome for so long that I've gotten to the point where the Gnome-compliant HIGs are second-nature to me; every time I want to configure something I know where to look.  Every time I want to do X I know what the name of the application is, where it's located in the menus, and how its menus are laid out.

KDE is obviously different.  And I want to give KDE a fair shakedown using its own applications (e.g. kpackagekit instead of synaptic, kate instead of gedit, etc....) and not rely on the Gnome ones as much.

Does anyone know of a good KDE tutorial written for converts from Gnome?  Or converts from XFCE?  Most KDE tutorials I've found spend a lot of time talking about Linux in general (which is fine, but not what I need).  Even just a table that shows the Gnome application and its equivalent KDE counterpart would be helpful.

---

### Post by mikewhatever on 2011-12-17
I thought the point of having all the options exposed in KDE was to get lost among them, kind of like walking through a maze.

---

### Post by QIII on 2011-12-17
This would be a good place to start:

[http://userbase.kde.org/Tutorials](http://userbase.kde.org/Tutorials)

I used to love GNOME.  Alas.  But KDE came out smokin' with 4.7.

Showing something in X and showing it in Y is often not a good way to learn something that is, in effect, a new language.  You can't speak a new language fluently in terms of vocabulary, metaphor and idiom if you are locked in a direct, literal, "word for word" translation.

Walking through a particular maze might not be fun.  Learning to navigate through mazes is empowering.

---

### Post by cwklinuxguy on 2011-12-17
I've never been a big KDE user, but there is nothing that says it is bad to use the Gnome programs. You said you don't want to rely on them, but if you find them preferable, then just use them.

---

### Post by QIII on 2011-12-17
I would have to agree that there is nothing at all wrong with GNOME apps, no matter what desktop environment you are using -- provided they will work.

I don't think there is any rule writ large that says one MUST use only KDE apps with KDE.

---

### Post by Telengard C64 on 2011-12-17
Klick on the K button in the panel. Klick the help button to open KDE Help Center. There's your guide.  ;)

---

### Post by ve4cib on 2011-12-17
> **QIII said:**
> This would be a good place to start:

[http://userbase.kde.org/Tutorials](http://userbase.kde.org/Tutorials)

Thank-you!  That looks like it should get me started.

I'm a big fan of Gnome2, simply because I've been using it for so long and have all my little scripts and tweaks set up to get it working *just* the way I like.  Alas, Gnome2 is dead, so I'm branching out and trying different things.  I've got XFCE on one computer and I'm probably going to put KDE on another one.

I'm not opposed to using Gnome applications in a different DE, but I'd like to give KDE a fair shakedown using it how it was "intended" to be used first.  But every time I try I always seem to get lazy and give up, and go back to Gnome.

> Showing something in X and showing it in Y is often not a good way to learn something that is, in effect, a new language.  You can't speak a new language fluently in terms of vocabulary, metaphor and idiom if you are locked in a direct, literal, "word for word" translation.

True, but let's face it: KDE and Gnome are both designed to be complete desktop environments for Linux.  They have lots of things in common; basic text editors, web browsers, multimedia players, package managers, etc....  Having a "word for word" translation for those applications is helpful.  Beyond that I'm well aware that a word-for-word translation between KDE's plasma desktop and Gnome2 will be largely meaningless.

---

### Post by Bonster on 2011-12-17
Welcome to KDE lols

And no, try not to mix Gnome and KDE apps, if u dont have too.
Disable KDE junk like Nepomuk Strigi and Akonadi then enjoy =)

---

### Post by ve4cib on 2011-12-18
> **Bonster said:**
> Welcome to KDE lols

And no, try not to mix Gnome and KDE apps, if u dont have too.
Disable KDE junk like Nepomuk Strigi and Akonadi then enjoy =)

What are Nepomuk Strigi and Akonadi?  I've never even heard of those.

---

### Post by Telengard C64 on 2011-12-18
> **ve4cib said:**
> What are Nepomuk Strigi and Akonadi?  I've never even heard of those.

Some crappy daemon to index all the files on your system for apparently no good reason. Much more trouble to understand and configure than it's worth. Gobbles resources like there's no tomorrow.

[example](http://kubuntuforums.net/forums/index.php?topic=3119674.msg281410#msg281410)

If you ever want to find a file just use **kfind** on the desktop, or else **locate** or **find** in Konsole.

Anyone who really knows what this junk is or how to make it do something useful, feel free to rebut me.

**_EDIT_**
[http://www.linuxquestions.org/questions/slackware-14/strigi-nepomuk-akonadi-796167/](http://www.linuxquestions.org/questions/slackware-14/strigi-nepomuk-akonadi-796167/)

---

### Post by davdo2004 on 2011-12-18
> **bonster said:**
> welcome to kde lols

disable kde junk like nepomuk strigi and akonadi then enjoy =)

+1

---

### Post by QIII on 2011-12-18
I think nepomuk, strigi and akonadi are cpu stress tests ...:lol:

---

### Post by Asraniel on 2011-12-18
by the way, the have been mostly fixed for kde 4.8. There was a fundraiser going on to improve them. I could not test it yet, but many that did reported that you don't notice the cpu usage anymore and that its actually usefull now. On kde 4.7 i have it deactivated, but for 4.8 i will try it again :)

---

### Post by VanillaMozilla on 2011-12-20
KDE and Gnome applications work fine together.  I have several KDE apps on Gnome because they're better than the Gnome apps.  I don't see why the reverse wouldn't work well.  But I'm not entirely sure whether Gnome 3 will sabotage the Gnome apps.

---

### Post by Alejandro Nova on 2012-01-02
If you still believe Akonadi and Nepomuk are CPU and HDD torture tests, you need KDE 4.8. Wait for it, or install it; there are many tangible improvements (check for Akonadi 1.6.90 too). 

In fact, they are so tangible that we can say there's finally a night-and-day difference between KDE 4.7 (or earlier) and KDE 4.8. They basically rewrote the Akonadi-Nepomuk bridge, replaced hand tuned SQL queries by automatically generated queries. As a result, performance improved, system load was decreased dramatically and there are no  memory leaks anymore.

---

### Post by cwklinuxguy on 2012-01-04
> **VanillaMozilla said:**
> KDE and Gnome applications work fine together.  I have several KDE apps on Gnome because they're better than the Gnome apps.  I don't see why the reverse wouldn't work well.  But I'm not entirely sure whether Gnome 3 will sabotage the Gnome apps.

Indeed true. ANY Linux app will run on ANY desktop environment assuming dependencies (and system requirements) are met. Rhythmbox will run on KDE, Konquerer will run on Gnome, and so on. You can mix apps as much as you want. It's up to you.

---

### Post by perspectoff on 2012-02-14
KubuntuGuide:

[http://ubuntuguide.org/wiki/Kubuntuguide](http://ubuntuguide.org/wiki/Kubuntuguide)

This guide has side by side tips for Ubuntu and Kubuntu, including overlaps. Answers a lot of your questions.

---

### Post by hildenbrandsteven on 2012-02-14
[http://docs.kde.org/](http://docs.kde.org/) -- Just read up on any app you're curious about. But, the best way to learn something is just to do it. So mess around with KDE, you'll learn it quick. You have to force it to be your main DE though, don't switch back to gnome just to complete some tasks you're more comfortable with.

---

