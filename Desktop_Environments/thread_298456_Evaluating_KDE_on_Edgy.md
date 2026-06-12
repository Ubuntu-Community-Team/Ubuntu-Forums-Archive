---
title: "Evaluating KDE on Edgy"
date: 2006-11-12
forum: Desktop Environments
---

### Post by allanlewis on 2006-11-12
Hi,

I recently installed Edgy after having used Dapper for about 6 months and was wondering what I need to do in order to try out KDE as a desktop environment while still keeping Gnome. I know I can install the "kubuntu-desktop" package (see [this thread]("http://ubuntuforums.org/showthread.php?t=103073&highlight=ubuntu+kde+test")) but this seems rather a lot of space to use (and a lot to download) just for an evaluation.

What would I get by installing "kdebase" or one of the other "kde..." packages? (although not "kde" itself as that takes ~500MB)

Basically, what is the minimum I need to install in order to try out KDE alongside Gnome?

---

### Post by Velotix on 2006-11-12
To get KDE apps to work in GNOME, you only need the key KDE libraries. Unfortunately, that's not what you're after.

KDE is a self-contained desktop environment, so if you want to test out KDE itself, **you have to install the whole thing**. No ifs, ands or buts.

You have three options: *kde-core*, *kubuntu-desktop* or don't bother.

You seem concerned about the size - are you worried specifically about the size of the package you need to download (in which case it's actually under 200MB as I recall) or the size of KDE (which is admittedly pretty hefty but still smaller than 500MB - I think it's closer to 400MB)?

---

### Post by allanlewis on 2006-11-12
> **Velotix said:**
> <snip>
You have three options: *kde-core*, *kubuntu-desktop* or don't bother.
<snip>
So what would be the difference between installing those two packages?

---

### Post by Velotix on 2006-11-12
The difference? *kde-core* is an untouched distribution of KDE: it's identical to the one you can download from the KDE website. If you want to explicitly try KDE as opposed to the *Ubuntu version* of KDE, then *kde-core* is probably what you want.

*kubuntu-desktop*, however, is the only difference between Kubuntu and Ubuntu. Ubuntu and Kubuntu are the same except for the package that sits on top and runs the pretty GUI (graphical user interface; desktop). Kubuntu is therefore full of stuff recommended by the Ubuntu development team and is more likely to work properly with your Ubuntu installation without any additional modifications. The price you pay for this is that Kubuntu is somewhat slower than vanilla KDE (apparently; I'm still trying Kubuntu from what was originally a Xubuntu install - and loving everything except the increased RAM usage).

Go with what suits your needs best - I'd say in your case you probably want *kde-core*, but it's up to you.

---

### Post by allanlewis on 2006-11-13
Thanks for the explanation - I guess what I meant by "trying KDE" was "trying kubuntu". I didn't realise that the kde used in kubuntu was so heavily customised, so I think I'd better try installing kubuntu - presumably this won't break my existing Gnome/Edgy installation?

---

### Post by TheWizzard on 2006-11-13
> **allanlewis said:**
> Thanks for the explanation - I guess what I meant by "trying KDE" was "trying kubuntu". I didn't realise that the kde used in kubuntu was so heavily customised, so I think I'd better try installing kubuntu - presumably this won't break my existing Gnome/Edgy installation?

gnome and kde should run fine together. but switching back and forth a lot may cause small problems. in other words: 
> Some people ask me why I have separate boots for KDE and Gnome. Theoretically you can have both desktop environments on one installation, but I've found that that clutters things up and sometimes (rarely) makes things malfunction. I just like my installations clean. [http://www.psychocats.net/essays/kdevsgnome](http://www.psychocats.net/essays/kdevsgnome)


if you just want to look what kde looks like i think you're pretty save. make sure you use aptitude instead of apt-get. here's a guide:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

