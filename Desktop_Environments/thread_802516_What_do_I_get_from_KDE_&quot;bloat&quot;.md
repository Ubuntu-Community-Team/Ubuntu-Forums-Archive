---
title: "What do I get from KDE &quot;bloat&quot;?"
date: 2008-05-21
forum: Desktop Environments
---

### Post by Palu on 2008-05-21
:popcorn:

Hello! From all benchmarks and articles I read, it seems KDE has a larger memory and CPU footprint. My computer can handle that fine. Since I doubt a project as big as KDE is simply suffering from poor efficiency, I was wondering what I get from that "bloat". I guess bloat is a bad word, but since I can handle higher demands, I think I could like it. Is there something it can do graphically which you'd have to do in the terminal in Gnome? Is it more customizeable? Are icons or some other basic thing configureable with more options?

To me KDE is much less pretty than Gnome (I like smaller icons in Gnome and don't like all the boxes in KDE or the look of the desktop switcher thingie), but eventually I need to learn more aobut customizing both desktops, so I think that's a non-issue.

Finally (and most importantly), how do I install KDE on my current Ubuntu install? Afterwards, how will I switch between them? Will there be an interface kind of like Grub but instead for the Window managers? Will I be disadvantaged having both installed (assume I'm not concerned about space on my hard drive but am concerned about processing demands and somewhat concerned about memory)? Is it better to make a different install of the OS?

---

### Post by Nythain on 2008-05-21
what you get is a completely different look... and some really great apps *cough*amarok*cough*konqueror*cough*k3b*cough*

ok, but seriously... i havent benchmarked it much myself, but most of kde's "bloat" is in the software from what i've gathered... i've heard many say that kde itself runs lighter than gnome itself... but like i said i havent done any official benchmarks personally.

as for customization, thats iffy... there's a lot that each can do that the others cant... and theres a lot that easier to find/do in kde than in gnome. on the outside, kde is easier to configure with the use of kcontrol... on teh inside gnome is easier to design for because it gives the users more control over the independant aspects of the desktop environment and window manager...

the easiest way to install kde is
sudo apt-get install kubuntu-desktop
i wont say its the best way, because that will install kde, and the kitchen sink, but its the quickest easiest way to start exploring the potential of kde...

switching between the two is easy... at some point the kubuntu-desktop install might want to install kdm, if it does, it should ask if you want to use kdm or your current gdm, id stick with gdm if its familiar to you... either way, from now on, when you log out and back in, or reboot or whatever there will be an option under "sessions" or "session type" or whatever in either GDM or KDM to choose if you want to load Gnome or KDE

personally, i love kde... if i wasnt a minimalist running an X + Fluxbox install, i would be running kde... but wich one is better is all personal prefrence and has been the start of many holy wars

---

### Post by Palu on 2008-05-21
My biggest difficulty is that most comparison threads are "which is better?" in style. I want to know the actual differences like "In Gnome you can change xyz file and it can control all blah blah aspects, where in KDE..." I haven't found a lot, and my experience is so limited, that I've had a lot of trouble finding differences--especially since I sometimes get completely stuck in KDE (my comfort zone is almost all inside Gnome).

Oh, and I think I have Amarok installed under Gnome... that's possible, right? I use Rythmbox and am not on my own PC for a little bit, so I can't remember offhand.

---

### Post by DMK62 on 2008-05-21
They tend to differ in that Gnome usually has one gui in one place to change something on your system whereas in KDE you can access that from different areas. Kcontrol will give you acess to most of the settings and System Settings will give you that but to a lesser degree. When it comes to applications written for KDE their configurations settings are almost always under the Settings menu in the application. 

Some settings in Gnome are right up front and some take some digging to find. KDE tends to give you them all up front.

Most apps written for gnome and kde will work on both systems. Just that extra libraries have to be installed. Performance is sometimes affected.

In my opinion, it comes down to a matter of personal preference. 

Dale

---

### Post by GeneralZod on 2008-05-22
> **Palu said:**
> :popcorn:

Hello! From all benchmarks and articles I read, it seems KDE has a larger memory and CPU footprint.

Than GNOME, you mean? Only fractionally - the difference is barely worth considering:

[http://ktown.kde.org/~seli/memory/desktop_benchmark.html](http://ktown.kde.org/~seli/memory/desktop_benchmark.html)

[http://spooky-possum.org/cgi-bin/pyblosxom.cgi/kdevsgnome.html](http://spooky-possum.org/cgi-bin/pyblosxom.cgi/kdevsgnome.html)

---

### Post by Zorael on 2008-05-22
KDE and Gnome are pretty much on the same step as footprint is concerned, with KDE being lighter and faster in some tests, and likely not in others. The step down to lighter environments such as Xfce is much larger.

I like to quote [this](http://mail.gnome.org/archives/usability/2005-December/msg00021.html) since I'm a bad and shallow person.
> On Tue, 13 Dec 2005, Till Kamppeter wrote:
> 
> Frederic told that the options from the PPD file are intentionally mot
> listed in the printing dialog, the usability team of GNOME was against
> listing these options. They clutter the dialog and can be more confusing
> than useful to the user.

I personally just encourage people to switch to KDE.

This "users are idiots, and are confused by functionality" mentality of 
Gnome is a disease. If you think your users are idiots, only idiots will 
use it. I don't use Gnome, because in striving to be simple, it has long 
since reached the point where it simply doesn't do what I need it to do.

Please, just tell people to use KDE. 

		Linus
End advice is to use what you like best. KDE is more fleshed-out with GUI ways of changing a lot of settings (the "bloat"), whereas with Gnome you need to delve into gconf files to get some stuff done (the "user-friendly and minimalistic approach", "what you see is what you need"). Etc etc.


edit: If you don't want to install the whole kubuntu-desktop package, with the default applications and whatnot, just grab [FONT="Courier New"]kdebase-bin[/FONT] for KDE3 and [FONT="Courier New"]kde4-core[/FONT] for KDE4. (Don't judge KDE on KDE4 just yet, though. It still has some way to go in many areas.)

They will pull necessary dependencies and get you a skeletal installation of the relevant environment.

---

### Post by Palu on 2008-05-22
Thanks Zor~... your answer is closest to what I'm looking for. I really don't care what takes the most memory since I have a machine with 2 GB, but now I know where to look for differences--that is, configuration. Slowly I will learn how to use KDE. :)

---

### Post by peterroots on 2008-05-23
I would go along with the two main themes here - KDE/Gnome do things differently and it is largely a matter of preference which you go for.  KDE does seem to give more configuration options than Gnome but would argue this is more a matter of preference than Gnome developers assuming the users are idiots!
Having said that I like KDE3 but at a first look at KDE4 I think it seems to have swung more to the simplistic way of taking away options although the new Dolphin is much nicer than the one in Kubuntu7.10.

---

