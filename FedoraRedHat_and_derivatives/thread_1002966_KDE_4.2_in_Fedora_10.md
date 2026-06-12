---
title: "KDE 4.2 in Fedora 10?"
date: 2008-12-05
forum: Fedora/RedHat and derivatives
---

### Post by DeadSuperHero on 2008-12-05
Hey, everyone.

I switched to Fedora 10 "Cambridge" a couple days ago, and I absolutely love it.

However, I was wondering: are there available binary packages for KDE 4.2 for Fedora yet? Although 4.1 is quite useable, the 4.2 SVN build I had in Ubuntu was very smooth. (Albeit flawed, as the mixture of Gnome, KDE 4.1, and KDE 4.2 tended to make PulseAudio an angry beast.)

In any case, what's the best way of going about getting the latest SVN for Fedora? Do I just simply take the time out to compile everything, or should I just simply wait a little longer for the MoTU to put up packages from Project Neon?

I tried looking into Rawhide's repo, but it's really a confusing jumble. I had to do a reinstall as I mistakenly thought that updating all packages to Rawhide would give me the desired effect. (Wrong, for me.)

Just curious, though.


On the OTHER hand, is it more worthwhile to just wait the extra month or two for the offical KDE builds to be adopted into the offical Fedora repos?

---

### Post by YeOK on 2008-12-06
There are a few places to get packages before they appear in the main repos. 

First, you could simple enable the updates-testing repo. Although, I'm not sure if KDE has arrived there yet. You could also go and download the .src.rpm packages from Koji (the Fedora build system). You will need the src.rpm packages because I think KDE 4.2 has only appeared as a Fedora 11 (Rawhide) package. Rebuilding will be the best option.

Link: [Koji]("http://koji.fedoraproject.org/koji/index")

The last option would be to upgrade to Rawhide. That's not a great idea at the moment though, its very early in Fedora 11's life cycle.

I'm sorry I can't give you a detailed guide, but rebuilding KDE isn't something I've done. I use Gnome. Your best option would be to ask over at the Fedora Forums. Someone there will be able to help you.

Link: [Fedora Forums]("http://www.fedoraforum.org/?")

---

### Post by KhaaL on 2008-12-12
I'd like to know this aswell. I'm also curious on how well KDE4 is supported in fedora, is it better than ubuntu (or maybe even as good as opensuse?)

---

### Post by jteb on 2008-12-12
Well, I'm running rawhide (f11) since f10 came out. I can tell you KDE 4.2 is in there and it did run really well up to a few days ago. kdelibs has been updated to 4.1.82, although the other packages haven't yet. 

as long as you stick to the 4.1.80 packages you'll be alright and it even runs remarkably well actually.

Regards,
Jan

---

