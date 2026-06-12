---
title: "Mouse Theme"
date: 2006-06-10
forum: Desktop Environments
---

### Post by sprucio on 2006-06-10
I'm having an issue with a mouse theme.

I've used update-alternatives to change my mouse theme back to the old X style black mouse pointer. When I start am at GDM, it looks fine but as soon as Gnome is loaded, it changes it to the default white pointer.

Can anyone help me on how I can figure this out?

---

### Post by Irony on 2006-06-10
System > Preferences > Mouse > Pointers

Shows your mouse pointer options.

Go to;

[http://www.gnome-look.org/index.php?xcontentmode=36&PHPSESSID=c235ffdedc3d2dcb5c753308323df2c8](http://www.gnome-look.org/index.php?xcontentmode=36&PHPSESSID=c235ffdedc3d2dcb5c753308323df2c8)

for more options. To install these options simply extract them to your .icons folder in home.

---

### Post by jbm222 on 2006-06-10
I had that same issue... it would load a pointer theme, then revert to the default white one for MOST, but not all of the pointers (i.e. the resize one would show up as the new theme).

I did [this](http://www.psychocats.net/ubuntu/puregnome) to remove KDE and Xfce, and the problem went away.  Sort of.

For some reason, my current pointer theme *still* doesn't show up under System->Preferences->Mouse.

So if I change it, i'm not sure I will be able to get back to the current one.

why is this?

---

### Post by sprucio on 2006-06-10
I've actually tried unzipping to the .icons directory and nothing happened after I restarted X.

---

### Post by sprucio on 2006-06-11
Would anyone even know which section I should research on the bugs Web page?

---

### Post by sprucio on 2006-06-12
Really, any help or thought would be great here. I'd like to file a bug but not sure if I should do it under the package "xcursor-themes" or GNOME. In the latter case, I'm not even sure which package would control this.

Please help me get rid of this ugly mouse pointer.

---

### Post by shuttleworthwannabe on 2006-06-12
install gcursor (in universe, or multiverse); [www.gnome-look.org](www.gnome-look.org) mouse themes has some good one there: I like the neutral (its on the first page i the middle somewhere). Its a tarball. Downlaod in and in System>preference>cursor selection>install theme>browse to the downlaoded file.

HTH

---

### Post by sprucio on 2006-06-14
Thank you so much for this help.

How did you come about this package?

---

### Post by shuttleworthwannabe on 2006-06-14
The one thing I think Ubuntu excels in is a superb community- ready to help at any point. 
 
When I first started using Ubuntu sometine in March of this year, I just stuck with the wiki, and I was good to go. There was a good howto there that I do not see anymore, but I tracked a smilar (updated version) using google. Here it is: [http://doc.gwos.org/index.php/Desktop_EyeCandy#HOWTO:_INSTALL_CURSOR_THEMES_ON_UBUNTU.2FGNOME]("http://doc.gwos.org/index.php/Desktop_EyeCandy#HOWTO:_INSTALL_CURSOR_THEMES_ON_UBUNTU.2FGNOME")

---

