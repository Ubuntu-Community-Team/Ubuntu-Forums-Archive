---
title: "No icons for KDE apps running on gnome"
date: 2007-06-23
forum: Desktop Environments
---

### Post by rdoolen on 2007-06-23
I have Ubuntu 7.04(Feisty). The icons on my KDE apps  are gone ( Amarok, digikam, k3b etc). I just see an icon that looks like a page or a piece of paper. 

On other accounts on the same machine, the icons are fine. I assume the problem is in my account set-up, in the way gnome deals with KDE apps. Some .KDE folder I would guess.

Come someone point me in the right direction?

I had installed, and later removed, KDE from my install. I think I messed it up at that time.

Thanks

---

### Post by {spitFire} on 2007-06-23
IMO, the icons are fetched from pre-defined locations like 
  * ~/.icons
  * /usr/share/icons
  * /usr/share/pixmaps

and when Gnome can't find an icon associated with an app, it loads the default icon, which in your case seems to be a piece of paper or whatever!  I think it is the problem with your current icon theme! Load some other icon theme (either from the defaults installed or from more sexy ones from [www.gnome-look.org](www.gnome-look.org)), and the apps should get their icons back.

---

### Post by rdoolen on 2007-06-23
Thanks for your help, but I don't think this is it. The problem apps use KDE icons. So, in principle you are correct, but the locations you listed aren't the ones I am looking for.

---

### Post by Magnentius on 2007-06-24
I have this problem too, see this thread: [http://ubuntuforums.org/showthread.php?t=482939]("http://ubuntuforums.org/showthread.php?t=482939")

As you can see in this image, when you install kubuntu-desktop from ubuntu and then run a kde session, it looks like this:

[IMG]http://pixsup.com/uploads/8be0a9594a.jpg[/IMG]

---

### Post by rdoolen on 2007-06-24
Actually, my problem is when I run the KDE app in a gnome session.

I would bet our issues are similar.

What happens when you run a gnome session?

---

### Post by Magnentius on 2007-06-24
The same happens as with you. I only tried to install KDE to see if that would solve the problem (it didn't), but I normally use gnome. You write that other accounts on the same pc do show their KDE icons. I have three computers with Ubuntu, but they all miss their icons. I will try to set up some new accounts to see if they have their icons.

---

### Post by Magnentius on 2007-06-25
Ok, I tried to create a new account to see if this solves the problem but it doesn't work either. I've made another screenshot, now from gnome running the KDE apps Kate and K3b:

[IMG]http://Pixsup.com/uploads/a478a6a67b.jpg[/IMG]

Does anybody know what the problem could be?

---

### Post by bailout on 2007-06-25
If you search you will see lots of similar posts. Someone needs to file a bug report if it hasn't already been done.

---

### Post by Magnentius on 2007-06-25
I searched many posts, but most of the were about the icons in the panel ('system tray' in M$), but not about this. I will bug report it then I guess.

---

### Post by Magnentius on 2007-06-25
I've submitted a bug report at [https://bugs.launchpad.net/ubuntu/+bug/122117]("https://bugs.launchpad.net/ubuntu/+bug/122117")

---

### Post by rdoolen on 2007-06-25
I have made some progress on my issues.

I installed Kcontrol from KDE. This allowed me to set the default KDE icons to be something other than "Gnome" fonts. This made my KDE apps look fine.

There still is something not right in the way my KDE apps are configured. Amarok is set to use custom fonts, yet it seems to only be using the KDE defaults. Again, I am guessing this is in some config file for KDE, but for now I am declaring victory, for my my issue.

I'll continue to investigate and post anything useful I find.

Thanks to everyone!

---

### Post by Magnentius on 2007-06-26
This works for me too, kate works perfectly now, except for the slow startup. Thanks!

---

### Post by zozobra on 2008-02-10
This worked for me as well.

---

