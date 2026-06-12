---
title: "[SOLVED] Why did they chose to put fspot into Gnome?"
date: 2007-05-29
forum: Desktop Environments
---

### Post by siddartha on 2007-05-29
I mean it is quite feature slim and it is partially broken.

Does this mean Gnome is becoming just what de Icaza and Novell want to? Just like with Evolution which needed years to work like what was envisioned probably this would have the same fate of being pushed just because it is a clone of another Windows app. Back when Evolution was started using Outlook was a big problem with Wine was a problem. But now when Picasa does about the same thing with less bugs why push this project? Just to show people that mono is a good way to align to Microsoft tech?

Normally they should have let g-thumbs alone as it does its job quite well and quite fast and for more functions people could run digikam. Besides picasa upload there is nothing I can think of that digikam doesn't have and fspot has it. The other way around the list is long.

Don't get me wrong. I do like Gnome and I have been using it for some years now, but the app selection is getting worse year by year and at the same speed I have to adopt kde apps. For xxx's sake inkscape is one major app using the gtk toolkit with no good contender from what I know and that's about it. Projects like Opera or OpenOffice don't rely on either one.

So, back to the main question: why did they push mono and apps like fspot in the main distribution?

Cheers,
Sidd

---

### Post by RafG on 2007-05-29
The difference is somewhat academic, but F-Spot is not an [official GNOME application]("http://en.wikipedia.org/wiki/List_of_GNOME_applications") (why couldn't I find such a list on gnome.org, BTW?).

Which Digikam features do you miss in F-Spot? I have never used DIgikam, so I don't even know what I'm missing :-)

---

### Post by tht00 on 2007-05-29
I'm not sure quite what you're getting at.  You're never going to be able to tweak a distro (or window manager) to everyone's liking, especially when it comes to pre-bundled apps.

If you don't like them, don't use them or even uninstall them.  By being included, you aren't being forced to use them -- just ignore them and go on your way.


> **siddartha said:**
>  But now when Picasa does about the same thing with less bugs why push this project? Just to show people that mono is a good way to align to Microsoft tech?

?

Are you asking why F-spot is supported when there is a 'better' app (Picasa) out there?  There are a variety of reasons for this.  Mainly, Ubuntu's philosophy is to include free (open source) applications, keeping closed/proprietary software to an absolute minimum.  If I'm not mistaken, Picasa is a closed-source Google app. 


> **siddartha said:**
> Normally they should have let g-thumbs alone as it does its job quite well and quite fast and for more functions people could run digikam. Besides picasa upload there is nothing I can think of that digikam doesn't have and fspot has it. The other way around the list is long.

I'm not understanding what you're saying here at all.

> **siddartha said:**
> Don't get me wrong. I do like Gnome and I have been using it for some years now, but the app selection is getting worse year by year and at the same speed I have to adopt kde apps. For xxx's sake inkscape is one major app using the gtk toolkit with no good contender from what I know and that's about it. Projects like Opera or OpenOffice don't rely on either one.

Again, no one is forcing you to use anything.  If you find some KDE apps work for you better, *then use them*.  Linux is about choice.  Bundling of different apps (either by the DE or distros) isn't going to affect your freedom of choosing and running the software you like.

Besides, Opera is based on the QT library and OpenOffice is based on GTK.

> **siddartha said:**
> So, back to the main question: why did they push mono and apps like fspot in the main distribution?

Why not?  We could look at the extremes of bundling nothing or bundling everything, but all in all, I think you'd find Ubuntu to be a good middle-ground, having enough to be a usable desktop for most people while staying fairly light on it's feet.

---

### Post by siddartha on 2007-05-29
No, it is not a Gnome application but it is chosen by Ubuntu.

The darn thing can't even import all pictures in a directory and the already shortened list isn't completely uploaded. On my system it is also slower than its counterpart although Picasa is using wine.

My point is they should have kept fspot out of reach as it is a poor excuse for anything IMHO. It clones another app - just like Evolution being a copy won't make it better and it will be just a few steps away from the original. It isn't fast enough and surely eats more resources. Also the offered tools are inferior to comparable software - XnView or Digikam.

Trying to keep proprietary software is a worthy cause but just replacing them with just another project instead of working on making a few better is wrong. It goes against other free software as well. So the Gnome team took off the mplayer and a few builds I checked from the Ubuntu repository are broken and they put Totem (official software for Gnome) which is so easy to use it's unusable with something like two or three sound cards active in the same system.

What features does digikam has? Well you can tweak the IPTC and Exif of a picture, you have a better range of easy tools in case you don't want to mess with Gimp, it is a real picture manager as you can import not only from some directory but also from a scanner or right from your screen, etc.

---

### Post by tht00 on 2007-05-30
> **siddartha said:**
> No, it is not a Gnome application but it is chosen by Ubuntu.

The darn thing can't even import all pictures in a directory and the already shortened list isn't completely uploaded. On my system it is also slower than its counterpart although Picasa is using wine.

Looks like there is a Linux version of Picasa.  Besides, Wine causes little/no slowdown if everything is working correctly.

> **siddartha said:**
> My point is they should have kept fspot out of reach 

"Out of reach" would restrict the freedom Linux stands for. ;)

> **siddartha said:**
> as it is a poor excuse for anything IMHO.

An opinion.  A valid opinion, perhaps, but surely, at least some people have had good experiences with it.

> **siddartha said:**
>  It clones another app - just like Evolution being a copy won't make it better and it will be just a few steps away from the original.

I don't see anything _wrong_ with clones -- when the application they are mimicking are good to start with.  Evolution copying Outlook is not necessarily bad when that functionality is non-existent for Linux.

> **siddartha said:**
> It isn't fast enough and surely eats more resources. Also the offered tools are inferior to comparable software - XnView or Digikam.

Ok.  Now we're getting somewhere.

Digikam is a KDE app, which would be impossible to put on the Ubuntu CD because of the KDE library that is required with it.  You'd have to dump other packages just to get Digikam on there.  Not going to happen.

XnView, which doesn't appear to be in the repos for some reason, is an X11 application.  Plus, it is closed-source.

While they both may be good, Ubuntu seems to prefer a "polished" look over an "unpolished" look with more usability.  The other apps, while I'm sure are good, just aren't meant for Ubuntu -- because of cd-size restrictions, Ubuntu philosophy, and Ubuntu's polished look.


Look, here's the thing.  I don't have any problems with how Ubuntu has pre-packaged software.  It is all removable if you don't want it, and you can always install your own software as you see fit.  I use Ubuntu as my primary OS because of how well it works for me, not because of what was packaged with it.

We could start the same battle over default media players too.  When it all boils down, Ubuntu has to pick _something_, and if you don't like it (no-one will like everything), change it yourself.

---

### Post by siddartha on 2007-10-16
Solved the problem: just get in synaptics and remove the darn thing with all its dependencies. Than search mono and check if it in use by another app. If not remove that too.

---

### Post by Steveway on 2007-10-16
If you want an alternative to F-spot then try Jbrout.
Jbrout only supports Jpegs, for the moment, and it is not as featurefull as F-Spot, but it works pretty fast and uses less memory.
And as a side note; Jbrout is written in Python, yay!

---

### Post by siddartha on 2007-10-16
I will give it a try. IMHO python is a better and more elegant solution to java or mono if you set aside politics.

---

### Post by Erunno on 2007-10-16
> **tht00 said:**
> Besides, Opera is based on the QT library and OpenOffice is based on GTK.

Wrong on both accounts. Opera uses an inhouse toolkit for the most part with some exceptions like printing where they use Qt (and only under Linux). OpenOffice.org uses its own toolkit as well but features wrappers for Qt and GTK+ for some slight visual integration (icons, widget style).

---

### Post by Paulr-55 on 2007-11-20
I have been using Ubuntu for a year, every release since Dapper, and I have never been able to get Fspot to work. It used to crash on start-up now in Gutsy it acts like it is importing my photos but when it's done -- no photos, no nuthin, no error message.

This thing comes pre-installed on Ubuntu?

---

### Post by babuu on 2007-11-20
I have imported all of my photos into F-spot without problems, and I really like the simplicity of it. F-spot may have crashed once or twice but thats ok, the price you pay when you run Linux.

---

### Post by writser on 2007-11-20
> **siddartha said:**
> I will give it a try. IMHO python is a better and more elegant solution to java or mono if you set aside politics.
This statement is utterly retarded, especially in this context. Why is an image viewer in Python better than one in Java? Judge applications on their performance, features and usability, not on the language in which they are written.

---

### Post by rsambuca on 2007-11-20
> **writser said:**
> This statement is utterly retarded, especially in this context. Why is an image viewer in Python better than one in Java? Judge applications on their performance, features and usability, not on the language in which they are written.

Other than the use of the very politically incorrect word, I agree with the sentiment.

---

### Post by siddartha on 2007-11-23
> **writser said:**
> This statement is utterly retarded, especially in this context. Why is an image viewer in Python better than one in Java? Judge applications on their performance, features and usability, not on the language in which they are written.

Sorry. My mistake. Instead of IMHO I should have spelled in my retarded oppinion.

---

