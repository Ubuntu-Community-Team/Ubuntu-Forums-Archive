---
title: "Certain programs missing window borders in 15.04"
date: 2016-02-08
forum: Desktop Environments
---

### Post by amadis2009 on 2016-02-08
I'm on Ubuntu flashback. Just upgraded to 15.04 from 13.10 and certain programs (nautilus, gnome system monitor, and gnome control center are the ones I see so far) don't have any window borders with the theme that I'm using. This makes it extremely difficult to differentiate between overlapping windows and makes it impossible to resize the windows. I know this is a problem with my theme. I'm just trying to find out where these programs find their window border theme info so I can make sure my theme has this info. When I use Ambiance or Radiance the windows borders are rendered correctly. However, using Ambiance or Radiance, the title bars do not respond to the 'minimize to title bar with mouse wheel scroll' function as other program windows do. I'm using a custom theme based off of Elegant Brit. I use Compiz and Emerald. I don't necessarily need someone to give me the 'fix' for this. I just want to know why this is happening. Does anyone know how and why these certain programs render window borders differently? If I could understand that, I think I could fix my theme.This is something that must have changed since 13.10, which is the last version I used, as this problem did not exist then.

---

### Post by vasa1 on 2016-02-08
> **amadis2009 said:**
> ... I just want to know why this is happening. ...
In short, gtk3 is evolving rapidly. While it maybe possible for you to fix things, other users may be advised to ensure that they use themes that are current. The "reverse" is also true. Some current GTK themes aren't suited for older *buntus. The [Arc theme]("https://github.com/horst3180/arc-theme") comes to mind.

---

### Post by grahammechanical on 2016-02-08
Before you get to involved fixing this you should know that Ubuntu 15.04 has reached end of life. You need to upgrade to 15.10.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You might be better off putting in an install of 16.04 development branch and working with that because 15.10 only has 9 months support which started Last October. 

There are a lot of changes to application tool kits and Gnome 3 DE on the way. 



[URL="https://wiki.ubuntu.com/Releases"]
[/URL]

---

### Post by amadis2009 on 2016-02-09
> **vasa1 said:**
> In short, gtk3 is evolving rapidly. While it maybe possible for you to fix things, other users may be advised to ensure that they use themes that are current. The "reverse" is also true. Some current GTK themes aren't suited for older *buntus. The [Arc theme]("https://github.com/horst3180/arc-theme") comes to mind.

That wasn't really the 'why' I was looking for. I would really like to *learn* what has changed in the way the themes work. This is a theme that I've custom built and rebuilt over several distros. Learning how the theme breaks in one distro helps me figure out how to fix or rewrite it in the next and the next.

> **grahammechanical said:**
> Before you get to involved fixing this you should know that Ubuntu 15.04 has reached end of life. You need to upgrade to 15.10.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You might be better off putting in an install of 16.04 development branch and working with that because 15.10 only has 9 months support which started Last October.

I am aware of these things already. What I was asking was if anyone could tell me how the theme worked differently for 15.04 than it did for 13.10. Specifically to the way window borders are drawn.

---

### Post by vasa1 on 2016-02-09
> **amadis2009 said:**
> That wasn't really the 'why' I was looking for. I would really like to *learn* what has changed in the way the themes work. This is a theme that I've custom built and rebuilt over several distros. Learning how the theme breaks in one distro helps me figure out how to fix or rewrite it in the next and the next.
If you've been following the development of GTK3, you should have come across several comments regarding all sorts of breakages from one version of GTK3 to the next. 

In your first post you mention "upgrading" from 13.10 to 15.04 (which is now EOL). In GTK3 years, that's a long time. [CSD]("http://stackoverflow.com/questions/28650646/what-is-client-side-decoration") has arrived, to name just one big change.

Since you're interested in learning, I can only suggest you sign up with various GNOME-related sites. Here's one for starters: [https://mail.gnome.org/archives/gnome-themes-list/](https://mail.gnome.org/archives/gnome-themes-list/)
More here: 
[https://mail.gnome.org/mailman/listinfo](https://mail.gnome.org/mailman/listinfo)
[https://blogs.gnome.org/](https://blogs.gnome.org/)

---

