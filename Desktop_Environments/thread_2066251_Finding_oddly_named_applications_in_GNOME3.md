---
title: "Finding oddly named applications in GNOME3"
date: 2012-10-04
forum: Desktop Environments
---

### Post by sideshowAnthony on 2012-10-04
Hi.

I am using Ubuntu 12.04 with the lovely GNOME3 desktop. I have one trouble with it: Finding applications I cannot remember the name of.

For example, I play the Tetris clone Quadrapassel, but would like to be able to find it using the word 'Tetris' and not having to remember it's proper name. Is there a way I can associate tags with an application maybe?

Thanks.
Anthony

---

### Post by kostkon on 2012-10-04
Yes, you can, but you'll have to edit the desktop file of Quadrapassel.

I don't know about Gnome Shell's dash but Unity's can take advantage of the Keywords entry in desktop files and give you better and more relevant search results.

So, according [to the spec]("http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html"), in Quadrapassel's desktop file, for example, you would add a line like this:
```
Keywords=tetris;retro;oldies;
```
etc., I think you get the point.

Hope that helps.

---

### Post by jarreboum on 2012-10-04
This is one of the big grudge I have against Unity, it's that it merges all the applications together in a big alphabetical mess and you must know the name to find something. I'm more a visual person, I remember the icon, it's position in some menus, but very rarely the name itself. Categories (as in the old gnome applications/place/system) were ideal to me as it was very easy to find something as I knew where it was.

However one option to circumvent this problem would be to use the filters in the dashboard. In applications you have a filter option in the top right which essentially mimic the old categories system. You knew the application you were looking for was a game, click "game", and I doubt you have more than a dozen installed so much more easy to find.

But I agree this is annoying and the keyword solution can never be ideal.

---

