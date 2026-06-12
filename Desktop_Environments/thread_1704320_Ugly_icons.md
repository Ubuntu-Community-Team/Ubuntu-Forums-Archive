---
title: "Ugly icons"
date: 2011-03-10
forum: Desktop Environments
---

### Post by Old *ix Geek on 2011-03-10
So the other night I finally upgraded from 9.10 to 10.10, but now I'm stuck with some really UGLY icons and can't seem to change them.

Compare my old, beautiful icons with the new, ugly ones:

[img]http://smartassproducts.com/images/blog/ugly_icons.png[/img]

They're black and white and just look awful. :( Plus, I cannot adjust the size of the LCD weather station--and it's way too small as it is right now.

Any ideas on what to do to get pretty icons back? Choosing different icon themes [in System Settings] has no effect on these particular icons. Nor is there a right-click (or any other choice that I can find) to change them on an individual basis.

---

### Post by JRV on 2011-03-10
Wow, that is one **ugly** icon set.

I'm not familiar with Kubuntu, but I installed Lubuntu and I did not like the icons.  I installed the Ubuntu Human theme.

The command to install it was:
```
sudo apt-get install human-theme

```

I can't tell you how to apply the theme, I am not familar with KDE.

---

### Post by Old *ix Geek on 2011-03-10
> **JRV said:**
> Wow, that is one **ugly** icon set.Glad I'm not the only one thinking that! It *IS* hideous, huh? :eek:
> I'm not familiar with Kubuntu, but I installed Lubuntu and I did not like the icons.  I installed the Ubuntu Human theme.

The command to install it was:
```
sudo apt-get install human-theme

```

I can't tell you how to apply the theme, I am not familar with KDE.No, that's just it--I have dozens of **beautiful** icon themes, but applying them does *NOT* change these specific hideous ones, nor can I find a way to do it manually. And I really can't live with these...ugh, they're awful!

---

### Post by Zorael on 2011-03-10
Those icons are specific to the plasma theme you're using. It may be possible to just copy the icon set of one into another, I don't know. I think the network management plasmoid started using an svg icon inbetween 4.5 and 4.6 though, so you probably can't bring that old graphic back.

I'm currently using [Produkt](http://kde-look.org/content/show.php/Produkt?content=124213), downloaded and installed via Get Hot New Stuff. I really like its icon set and its textured feel.

I have no idea as to what you can do about the weather station except [filing a bug](http://bugs.kde.org) describing the regression. You even have nice screenshots displaying the differences at the ready.

---

### Post by Zorael on 2011-03-11
In KDE 4.6+;

System Settings -> Workspace Appearance -> Desktop Theme, click Get New Themes and install the one you want. Then select the one you want in the list and hit apply.

---

