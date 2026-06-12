---
title: "Ubuntu 18.04 + XFCE4.14 desktop switcher background"
date: 2020-03-13
forum: Desktop Environments
---

### Post by u666sa on 2020-03-13
I'm not new to XFCE. I also did google search and posted on XFCE forums (no reply so far).

How do I change background (highlight, hoover, etc) color of desktop switcher? Changing gtk.css has no effect.

---

### Post by u666sa on 2020-03-14
What's happening. I did follow goids on google, but the result was that I couldn't change background of XFCE desktop switcher, not via gtk 2.0 rc not via gtk 3.0 css. I made posts about this on [Ubuntu forums]("https://ubuntuforums.org/showthread.php?t=2438495") and on [XFCE forums]("https://forum.xfce.org/viewtopic.php?id=13834"), nobody helped me. As it usually happens on Linux, problems are solved by you. Here is such case. The following is the proper way of installing XFCE 4.14 on Ubuntu 18.04 LTS (not Xubuntu).  I'm assuming you have Ubuntu without xfce installed. If you have it installed, login to gnome and do [COLOR=#b22222]sudo apt remove xfce4* [/COLOR]and then [COLOR=#b22222]reboot[/COLOR].

Then, 

[s](it shows face there, but it is actually : followed by x)[/s]

```
sudo add-apt-repository ppa:xubuntu-dev/staging
sudo apt-get update
```

Then you go [COLOR=#b22222]Software & Updates[/COLOR] from the menu

On first page, unselect everything you see

[[IMG]https://i.ibb.co/SfSGDtz/2020-03-14-11-28-02.png[/IMG]]("https://ibb.co/MBdQycm")

Then on second screen, unselect everything but xubuntu dev staging and it's source, you can see unit193 repos there, those are also for XFCE, either ignore it or add, doesn't matter. 

[[IMG]https://i.ibb.co/SxGrFbq/2020-03-14-11-28-07.png[/IMG]]("https://ibb.co/ZJ7mq5y")


After this, close Software and Updates.

Then,

```
sudo apt install xfce4*
```

and ```
reboot
```

That's it.

Once you login into XFCE it will say XFCE 4.12 is about dialog. What you now need to do is 

[COLOR=#b22222]sudo apt upgrade[/COLOR] 

and then [COLOR=#b22222]reboot[/COLOR]. 

[url=https://imgur.com/vpm2k0B.png]
  [img]https://imgur.com/vpm2k0B.png[/img]
[/url]


Congrands boy! You just installed XFCE 4.14 on your system. I've used it on Fedora 31, and it can tell you it's great! 

Now we are going to install some addons and stuff, I'll add more to this thread during the day or two which proper steps. The result will be amazing!

---

### Post by u666sa on 2020-03-14
Here is the solution [https://ubuntuforums.org/showthread.php?t=2438550&p=13938761#post13938761](https://ubuntuforums.org/showthread.php?t=2438550&p=13938761#post13938761)

---

### Post by coffeecat on 2020-03-14
@u666sa, I've merged your guide into this thread. Your link in what is now post #3 will lead back to here.

You posted the guide in the Desktop Environments sub-forum, but separate tutorials and howtos are only permitted in the Tutorials section, and if posted there must conform to the [Tutorials Guidelines]("https://ubuntuforums.org/showthread.php?t=2143602"). This doesn't constitute a full tutorial, but is a useful tip which is why I have merged it here, so that it is available for those who would find it useful.

The smiley is because you did not enclose your terminal commands in code tags. I have now done this for you. There is a link in my sig for using BBCode code tags if you need it.

---

