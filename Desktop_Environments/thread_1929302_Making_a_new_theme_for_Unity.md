---
title: "Making a new theme for Unity"
date: 2012-02-21
forum: Desktop Environments
---

### Post by fballem on 2012-02-21
I'm hoping that someone can direct me to a good set of instructions for making a new theme for Unity. I'm thinking of basing it on the GTK2 Nimbus theme, which I always liked.

I suspect that I will have to build it from scratch, which is fine, as long as the instructions are very clear.

In a perfect world, I would not only like to apply it to the desktop but also to the login screen.

Any help would be much appreciated.

Thanks,

---

### Post by Frogs Hair on 2012-02-21
As you may know there is just not a lot of detailed information yet . I have a link to themes template , but don't know how to use it . I have learned a little opening theme files and attempting to modify some of the themes I use.

I can tell you that gtk 3 theme components are much different than gtk 2 . I don't what you may be able to apply from a gtk 2 theme . 

[http://gnome-look.org/content/show.php/GTK+3+Theme+Template?content=142117](http://gnome-look.org/content/show.php/GTK+3+Theme+Template?content=142117)

---

### Post by fballem on 2012-05-06
In the GTK2 world, there was documentation around all of the following:

[LIST=1]
[*]How to make a background wallpaper
[*]How to make icons - and where they needed to be put to be selectable.
[*]Where to put fonts so that they were selectable.
[*]How to package all of the above items so that it could be easily installed using existing System tools.
[/LIST]

There are three ways that the theme can be made available.

[LIST=1]
[*]Locally to a single user.
[*]Globally to all users so that they can easily select the new theme if they choose to apply it.
[*]As a default theme, so that any new user who is set up on the system would have this theme as a default.
[/LIST]

There are two other things that I would like to be able to include in the package - the ability to turn on/off the Global Menu and the ability to set the titlebar icons to the left or to the right.

If you would be able to point me to documentation, that would be most helpful - especially around packaging the theme. If the documentation does not yet exist, then I will be happy to create it as a wiki, but I will need instructions on how to package the theme. I would like to use Nimbus as the basis for creating the package.

Thanks,

---

### Post by fballem on 2012-05-06
Also to the above, I would like to be able to re-theme the Login screen if possible, and I would be most grateful for any documentation that tells me how to do that, and how to prepare a package so that the new login theme is easily installable.

Thanks again,

---

