---
title: "Clearlooks theme fails to apply to some apps"
date: 2012-06-03
forum: Desktop Environments
---

### Post by troutrou on 2012-06-03
Hi there,

After 10 years of using Gnome I have finally given it up, wiped Ubuntu 11.10 and replaced it with XUbuntu 12.04. So I am having to learn my way around XFCE. Spent a couple days exploring it and fiddling with it to customize its appeareance and behaviour. Overall I just love it and intend to stick with it over Gnome3 (even the "classic" mode hardly cuts it), but I have one big major issue with it, which I just can't figure out by myself: when I select the Clearlooks theme, somehow half of the applications fail to apply it ! I mean I would eventually understand if it completely failed to apply, but how comes it works perfectly with half of the apps, and fails with the other half, leaving the Desktop in a "Hybrid" state ? All these apps are equal to me.. just regular mainstream XFCE or Gnome apps, that never posed a problem in the past.

Examples of apps that refuse to apply Clearlooks:

The Calculator
Hardware Driver "Manager"
"Web" / Epiphany
Abiword
Synaptic
Update Manager
Network Connections
All of the games
Character map
Rhythmbox
Transmission
Simple Scan
Evince / Document Viewer
Pulse Audio Volume Control 
Startup Disk Creator
Time and Date
Users and Groups
Ubuntu Software Centre

I am really puzzled by this weird problem. All I am sure of, is that it's not due to some mess with old config files or conflict with previous Ubuntu or DE installs, because I wiped the / partition when installing, and although I didn't wipe my Home/ Data partition for obvious reasons, I tried a "clean"/guest session, as well as the Live CD session, as well as an install in a Virtual Machine, and all exhibit the same problem.

I checked the FAQ on XUbuntu's website, as well as the archives of the XUbuntu mailing list, but no sign of this problem... so I am hoping this means it OUGHT to work.

Any ideas ? :-/


--
Vince

---

### Post by Toz on 2012-06-03
Clearlooks is a gtk2-only theme. Many of the apps have been ported to gtk3. To get the best visual appearance for those apps, you should look at using a gtk3 theme. The default Greybird theme is a gtk3 theme. 

Newlooks is a ported version of clearlooks that supports gtk3. Link here: [http://gnome-look.org/CONTENT/content-files/126920-Newlooks_0.98.tar.gz]("http://gnome-look.org/CONTENT/content-files/126920-Newlooks_0.98.tar.gz").

Note that neither Clearlooks or Newlooks contain a window manager (xfwm4) theme.

---

### Post by troutrou on 2012-06-04
Thanks for your reply, it is enlightening indeed.

- I somehow thought that XFCE was still using Gtk2
- I supposed Gkt3 would be compatible with Gtk2 themes in order not to break billions of dekstops over the world
- I assumed that applications didn't need to be rewritten and that some kind of compatibility layer was arranged.

So this means XFCE is neitehr Gtk2 nor Gtk3, it only and all depends on every particular app, what a mess... since many apps will probably never be ported to Gtk3 due to lack of support.

- the tarball you gave me doesn't solve my problem: all the apps taht were broken before, still don't work: they now display a different theme (which I don't recognize), but still don't display the intended theme.

- it display the "raw" Clearlooks, whereas I was using the "Gilouche" variant of the Clearlooks themes, but Newlooks doesn't apply my Gilouche settings :-/

So I had a look in the tarball and it seems it's actually not a Gtk3 ort of Clearlooks, actually it's not even an engine, but just a variation of another theme engine apparently called "Adwaita" (whatever that is). 

So I guess this means the clearlooks ENGINE has not been ported to Gtk3, so my Gilouche theme will nevr work again.

OR... does that mean that the gtk2 ENGINES are still useable for Gtk3 themes, and that only the themes files (such as the one you sent to me, which goes in ~/.themes or /usr/share/themes  need to be modified in order to work with Gtk3 stuff ?

I am confused.... :-/

If someone can shed some light on this. If the engine don't need to be rewritten, then that's cool, it means only the theme needs to be ported, so maybe Gilouche will be ported one day.

In all this mess of bad news, I found at least one encoureaging thing:

You pointed me to Gnome-look.org (which I had forgottent about, I only thought of checking Gnome Art, which does not have any Gtk3 themes), which appear to carry many Gtk3 themes, so maybe I can find something I like. Also, it appears some of them offer both a Gtk3 theme AND an accompanying, similar looking Gtk2 theme, so that all apps looks the same.. great, THAT would solve my problem ! :-)

---

### Post by nomodeset on 2012-06-04
I think you have to realize that Xfce is **not** Xubuntu. How about replacing or even removing all GNOME/GTK3 applications?

---

### Post by troutrou on 2012-06-04
I apologize in advance, but I don't understand what you are trying to say ? (maybe I am stupid).

- Xfce is not Xubuntu ? What do you mean ? XUbuntu offers XFCE as the DE, a DE needs to be part of a distro in order to work (Ubuntu or whatever, XFCE itself doesn't care and doesn't even know about it, it's not relevant)

- Removing all Gnome/Gtk3 apps ? Here again I don't understand. Do you imply that Gtk3 apps are Gnome apps ?! Gtk has nothing to do with Gnome. Gnome just so happens to be based on Gtk, so does XFCE. They are just two DEs that both chose to use Gtk. Gtk apps are not more "gnome" than they are "XFCE". They are just "Gtk".
"Gnome" apps works just as well on XFCE as they do on XFCE, and that's why I like XFCE: it's a Gtk based DE, meaning I can use "Gnome" apps without using Gnome (since I don't like it anymore).

Or did you mean to not use Gtk3 apps, and stick to Gtk2 apps ? I don't think that's what you meant though, because obviously it's a little strange... if Gtk moved from 2 to 3, so will all the apps, at least the mainstream ones (my concern was about the not so mainstream ones...), so over time Gtk2 apps will face extinction and will not be supported anymore. It's a bit like you said (when Gtk2 came out, 10 years ago ?) : "I will not use gtk2 apps, and stick to Gtk(1) apps". today that means you would not have that many apps on your computer, and all of them would be completely obsolete and unsupported/unmaintainted, IOW pretty useless.

---

### Post by mcduck on 2012-06-04
Xfce itself and apps included with it are using GTK2, while many of the other apps (like all in your list) have already moved to GTK3. You can (and already do) have both versions of GTK installed at the same time, both as the theme format has changed GTK2 themes only work for apps that use GTK2, and the other way round.

If you want all your applications to look  the same, you have to use a theme that includes both GTK2 and GTK3 support. You should find plenty of such themes under the GTK3 section on gnome-look.org. Sadly, there's no easy way to convert your old theme for GTK3, so you'll pretty much have to find a new one you like.

---

### Post by troutrou on 2012-06-04
Thanks for your comment.

I have just had a look through all 19 pages of Gtk3 themes in Gnome-look.org and sadly none of them look like Gilouche, they all look roughly the same, ie not very useable, dark or gray themes which I don't like. I found many of them do not offer a Gtk2 counterpart.

What I liked most in Gilouche were the colour. So I guess my best bet is to find a dark theme I sort of like the shape of the controls of, and modify the colours by hand in the definition files, as I guess it's about the only customization a clue-less user like me can do to a theme, by hand, without any "theme programming" knowledge.

Failing that, I would have to ask a theme developer how much he would want to sort this mess out for me :-/

---

