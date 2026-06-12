---
title: "[kubuntu] What Is Better For ME ??"
date: 2008-05-14
forum: Desktop Environments
---

### Post by abedqader on 2008-05-14
I want to use ubuntu or kubuntu for personal us eand some php-asp programming what is better ????

i have hp pavilion dv4000 ??

---

### Post by NightwishFan on 2008-05-14
Personally I like a KDE desktop. If you like GUI configuration and simpler customization, then go with KDE. If you like strong defaults and simpler interfaces go with Gnome. (Overly simplified, but that is the main reason I use Kubuntu).

---

### Post by MONODA on 2008-05-14
i would go with kubuntu.

---

### Post by p_quarles on 2008-05-14
Given the criteria you list, there is absolutely no way of suggesting one over the other. They will both be perfectly good for personal use and light development.

The *only* thing I would say here is that KDE has a very nice web development IDE called Quanta+. It's the most featureful Linux web IDE, but consequently has more features than most individual developers would find themselves using. Screem and Bluefish are two Gnome applications that are also both very good, but have fewer features.

In any case, KDE applications can be run in Gnome, and vice versa, so there's really no point in basing the decision on a single application. Give the live disks for both distributions a try and see which feels better to you.

---

### Post by sunstriker on 2008-05-14
for asp, I think you should use Visual Studio...Because you need windows to run it (not taken apache-mono into account)
For php, I use Eclipse with a php plugin, it's the best I ever used. It parses your code and has IntelliSense / autocomplete.
for ubuntu/kubunt. It just doesn't matter. a program will work just as good in kde as in gnome. You can install both kde and gnome via apt-get. For example install ubuntu and install kde via synapti or apt.
```
 sudo apt-get install kde4
```

Or the opposite: install kubuntu and install gnome. Then you can pick which one to use on the login screen and try them both.

---

### Post by NightwishFan on 2008-05-14
I would advise kde3.5 until july when kde4.1 is out.

---

### Post by Zorael on 2008-05-14
What you like best is best for you, I'd say. There's nothing barring anyone from running Qt (KDE) apps when in Gnome, though they may look a bit funky. As for GTK+ (Gnome) apps in KDE, the only thing you'll notice is that file dialogs (open/save/etc) have a different look and different bookmarks than normal KDE ones do. As well as some other inconsistencies, like toolbars (file, edit, etc).

Burn both as live cds, boot them up one after another, decide which you want and install. If you change your mind later, you can remove one and install the other without wiping your system.

---

### Post by NightwishFan on 2008-05-14
Just now I got my Kubuntu cd in the mail. :D

---

### Post by Xiong Chiamiov on 2008-05-15
> **sunstriker said:**
> For example install ubuntu and install kde via synapti or apt.
```
 sudo apt-get install kde4
```


Oh God, no, please don't.

As far as Desktop Environments (DEs), it doesn't really matter - it's a preference thing.  Try 'em both and see what you like more.

As far as coding, I'm pretty sure you're not going to be able to run asp locally on your box.  Besides, who'd learn the language of the devil when you have PHP? :P
I didn't really like Quanta (too much WYSIWYG crap taking up my screenspace), and I can't stand Eclipse's interface (I switched out of using it for Java, even though I love its auto-completion and many other nice features), so I use Komodo Edit.  It has tabs, code folding, projects, and remote file editing over FTP.

---

### Post by NightwishFan on 2008-05-15
Good luck. About trying the live cds I do recommend that. Please ask if you have any specific questions about any environment.

---

### Post by jdunn on 2008-05-15
> **abedqader said:**
> I want to use ubuntu or kubuntu for personal us eand some php-asp programming what is better ????

i have hp pavilion dv4000 ??

Its just a matter of personal preference.  One is not "better" than the other.

---

### Post by CharlieM on 2008-05-16
If you want to run .Net code locally in ubuntu you should look at mono. I know there is some support for asp.net but I am not really sure how complete it is as I have never used it.

My company writes C Sharp code mostly. We deploy our server apps to FreeBSD or Ubuntu Servers running Mono. For web development we tend to use Apache Tapestry which is Java based and so can deployed on any thing. 

In terms of IDEs Eclipse is very good but it does take a lot of getting used to. If you are writting .Net code then MonoDevelop quite good although fairly new and still lacking a few featrures. 

Either way they will all run in Gnome or KDE so that choice is completely up to you. As others have said, try out the live CDs see which one you prefer. Personally I use Gnome as its interface seem a lot Cleaner/Simpler.

Hope that helps

Charlie M

---

### Post by VMC on 2008-05-16
I'm going to try both. I download ubuntu. I'm using that for right now. I have ordered kbuntu in the mail. When that arrives I will put that one on another system and try it out. I perfer KDE over Gnome. Only for the fact board games look better. KDE has a more polished look, Gnome board games look like something out of the past, say Windows 3.1 look and feel. I have no reason why, it just does. I'm not sure which one is fast. I did install the new Fedora9 and it look a lot longer to fully boot up and it's KDE 3.5 interface was awful. Strange but I think it was the dark colors. So in the end I will try both ubuntu/kubuntu.

---

### Post by predator41464 on 2008-05-16
> **sunstriker said:**
> for asp, I think you should use Visual Studio...Because you need windows to run it (not taken apache-mono into account)
For php, I use Eclipse with a php plugin, it's the best I ever used. It parses your code and has IntelliSense / autocomplete.
for ubuntu/kubunt. It just doesn't matter. a program will work just as good in kde as in gnome. You can install both kde and gnome via apt-get. For example install ubuntu and install kde via synapti or apt.
```
 sudo apt-get install kde4
```

Or the opposite: install kubuntu and install gnome. Then you can pick which one to use on the login screen and try them both.

[COLOR="RoyalBlue"]hello .I did load up kde with this  sudo apt-get install kde4 how can I uninstall it or how can I go back.to use only ubuntu gnome .:popcorn:am new at this .[/COLOR]

---

### Post by chritianpettet on 2008-05-16
maybe this will work
sudo apt-get remove kde4

---

### Post by NightwishFan on 2008-05-16
You needed to use aptitude install not apt-get to install meta packages, or else it is hard to remove them. If you used KDE instead of kubuntu-desktop to remove it you will have to uncheck all the packages manually I believe.

---

