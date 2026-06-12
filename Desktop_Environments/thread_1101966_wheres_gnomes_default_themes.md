---
title: "wheres gnomes default themes?"
date: 2009-03-20
forum: Desktop Environments
---

### Post by elitenoobboy on 2009-03-20
Why does ubuntu not have any of gnomes default themes and wallpaper by default? <a href=http://library.gnome.org/misc/release-notes/2.24/#rnusers.backgrounds>Example</a>
When I go into appearance preferences, instead of seeing any of that, I am greeted only by some ugly brownish background on the default install. Is there any particular reason for this? Gnome goes through all of that trouble to look nice and then ubuntu comes and screws it all up... 
   How do I get all of that (without searching for each background one by one on the web) for my install? And while I'm at it, the icon themes, window controls, and everything else as well?

   And I also indented my paragraphs in this post. Why is that being screwed up as well? Do the forum website developers not believe in spaces, or were they just too busy making hundreds of stupid smiley pictures to take that into account?:confused::lolflag::guitar:):P:mrgreen::biggrin::frown:

---

### Post by MissKitty on 2009-03-20
> **elitenoobboy said:**
> Why does ubuntu not have any of gnomes default themes and wallpaper by default? <a href=http://library.gnome.org/misc/release-notes/2.24/#rnusers.backgrounds>Example</a>
When I go into appearance preferences, instead of seeing any of that, I am greeted only by some ugly brownish background on the default install. Is there any particular reason for this? Gnome goes through all of that trouble to look nice and then ubuntu comes and screws it all up... 
   How do I get all of that (without searching for each background one by one on the web) for my install? And while I'm at it, the icon themes, window controls, and everything else as well?

I've got the same problem! :S

---

### Post by linux_tech on 2009-03-21
This explains the basic internals of the desktop 
[www.tuxist.org/pub/get_kde-gnome_desktops_in_line.pdf](www.tuxist.org/pub/get_kde-gnome_desktops_in_line.pdf)

---

### Post by elitenoobboy on 2009-03-23
That pdf is great and all for knowing what paths the configs are stored at, but it doesn't really answer the question of where the actual gnome content is, as stated in original post.

---

### Post by mcduck on 2009-03-24
> **elitenoobboy said:**
> That pdf is great and all for knowing what paths the configs are stored at, but it doesn't really answer the question of where the actual gnome content is, as stated in original post.

/usr/share/themes
/usr/share/icons
/usr/share/backgrounds

You'll find plenty of extra themes and other artwork available in the repositories. Probably most of Gnome's own themes and wallpapers are there so you can install them if you want them.

---

### Post by elitenoobboy on 2009-03-24
> **mcduck said:**
> /usr/share/themes
/usr/share/icons
/usr/share/backgrounds

You'll find plenty of extra themes and other artwork available in the repositories. Probably most of Gnome's own themes and wallpapers are there so you can install them if you want them.
Still not it. In /usr/share/backgrounds there is nothing but the default and a couple of space pictures. It is nothing like what is in my example screenshot of what a default install should have, according to gnome.

---

### Post by mcduck on 2009-03-24
> **elitenoobboy said:**
> Still not it. In /usr/share/backgrounds there is nothing but the default and a couple of space pictures. It is nothing like what is in my example screenshot of what a default install should have, according to gnome.

Like I said, there's a wide selection of themes and other artwork installable from the repositories. You will probably find what you are looking for from there.

Ubuntu doesn't install the default Gnome setup and the themes are not the only difference. For example Ubuntu has Firefox by default while Gnome's browser is Epiphany..

---

### Post by AntiBodies on 2009-03-24
```
sudo apt-get install gnome-backgrounds
```

---

### Post by jlimon on 2009-03-24
You people get more annoying every year.


BLAH BLAH BLAH BROWN IS UGLY UGH I WANT THIS I WANT THAT.

Two freakin' clicks to change a theme, just like with Windows XP's ugly default.

---

### Post by elitenoobboy on 2009-03-25
> 
Code:

sudo apt-get install gnome-backgrounds



Thanks, that was what I was looking for. I had previously tried searching for wallpaper instead of backgrounds.

> 
jlimon  	
Re: wheres gnomes default themes?
You people get more annoying every year.


BLAH BLAH BLAH BROWN IS UGLY UGH I WANT THIS I WANT THAT.

Two freakin' clicks to change a theme, just like with Windows XP's ugly default. 

I counted about 10 clicks and some typing. Care to tell me how I would switch to gnome's backgrounds and themes with only "two freakin' clicks"?

---

### Post by AntiBodies on 2009-04-13
Windows XP by default you CANNOT change the theme (well baring the three luna ones.. blue, silver and olive and a few you can download from microsoft (media center and zune theme))

themes need to be properly signed by microsoft or some such so you need to patch a file (uxtheme.dll or something) before you can apply any thing.. you can also install objectdock and a few other commercial, read pirated, apps that allow this.

all of the above if vastly longer and more annoying than installing themes in ubuntu, read gnome, and is another example of microsoft's crippleware strategy (read xp home, starter edition.. blah blah)

---

### Post by elitenoobboy on 2009-04-15
> **AntiBodies said:**
> Windows XP by default you CANNOT change the theme (well baring the three luna ones.. blue, silver and olive and a few you can download from microsoft (media center and zune theme))

themes need to be properly signed by microsoft or some such so you need to patch a file (uxtheme.dll or something) before you can apply any thing.. you can also install objectdock and a few other commercial, read pirated, apps that allow this.

all of the above if vastly longer and more annoying than installing themes in ubuntu, read gnome, and is another example of microsoft's crippleware strategy (read xp home, starter edition.. blah blah)
I wasn't being critical of the changing of themes in ubuntu, just the themes (or more precisely, the desktop background, of which XP has better variety and more than ubuntu) that come with the os by default.
It looks like the next ubuntu release is going to be on DVD, so it's not like the extra space taken up by a few extra nice backgrounds is going to be missed much.

---

### Post by ahbart on 2009-04-15
> **elitenoobboy said:**
> It looks like the next ubuntu release is going to be on DVD, so it's not like the extra space taken up by a few extra nice backgrounds is going to be missed much.
There have been a dvd's for some time now: [look](http://cdimage.ubuntu.com/releases/)

---

### Post by elitenoobboy on 2009-04-15
> **ahbart said:**
> There have been a dvd's for some time now: [look](http://cdimage.ubuntu.com/releases/)
That's weird. Downloading it from ubuntu.com will give you a cd image, while cdimage.ubuntu.com has only DVDs for download. Why the discrepancy? Is it because the DVD images both desktop and server editions or something like that?

---

### Post by Mulenmar on 2009-04-15
> **elitenoobboy said:**
> I counted about 10 clicks and some typing. Care to tell me how I would switch to gnome's backgrounds and themes with only "two freakin' clicks"?

Actually, it's four. At least.

At the Desktop, right click->Change Desktop Background->select on of the images. If there is an image elsewhere on the computer that you want to use, click the Add button and browse.

---

### Post by lesterness on 2009-04-28
> **Mulenmar said:**
> Actually, it's four. At least.

At the Desktop, right click->Change Desktop Background->select on of the images. If there is an image elsewhere on the computer that you want to use, click the Add button and browse.
[I]
So how (or where) do I find a greater variety of backgrounds?  At one time I had some pix of grass blades, a drop of water splashing  into a pool, etc. But they have disappeared.  I'd like them back.
[/I]
Lesterness

---

### Post by mcduck on 2009-04-28
> **lesterness said:**
> [I]
So how (or where) do I find a greater variety of backgrounds?  At one time I had some pix of grass blades, a drop of water splashing  into a pool, etc. But they have disappeared.  I'd like them back.
[/I]
Lesterness

read the previous page of this very same thread and you'll find the answer. ;)

hint: "gnome-backgrounds"-package.

---

### Post by elitenoobboy on 2009-04-28
> **mcduck said:**
> read the previous page of this very same thread and you'll find the answer. ;)

hint: "gnome-backgrounds"-package.

See, I knew it. Other people want what ubuntu stripped from the default gnome install. The extra backgrounds are only about 10MB: enough to fit on the install cd. But instead everyone is forced to the default "brown" desktop. There is no reason for this.
At the same time the default theme should be changed, too. Even the WinXP fisher price theme is better.

---

