---
title: "Black background around mail in Evolution in Gnome 3.10"
date: 2014-02-25
forum: Desktop Environments
---

### Post by cdysthe on 2014-02-25
Hi,

I have this annoying problem in Gnome 3.10 where Evolution has black background around e-mail previews and when you click open e-mail. If you open email source the background is completely black and it is hard to read the content. It used to be gray and I would like to get it back to be gray. i have tried with different GTK themes (gtk 3) men they all have this problem. I'm sure this is a GTK/Gnome issue but I can't for the life of me figure out how to solve this sine changing theme doesn't help. I'm sure what's needed is someone who knows the innards of gtk theming who could suggest where I begin to look for a solution. I'm sure if I knew where to look in /usr/share/themes/ there would be a line or to in a config file I would have to edit, but I can not figure it out so I am hoping someone who knows more than me about these things could point me in the right direction. 

It would also be good to know if others who run Gnome 3.10 on Ubuntu 13.10 and have Evolution set up are seeing the same thing and could tell me if this is a feature or bug.

This is what it looks like. I would like what is black to be gray as it is in Gnome 3.8:
[ATTACH=CONFIG]250677[/ATTACH]

---

### Post by buzzingrobot on 2014-02-25
Yep, I've seen it, too, and it is a theme thing. I tried finding the theme code, or the Evolution code, that controlled that, without success.

I got rid of it by trying GTK different themes. I needed to restart Evolution after each theme change.

it is a bit of a pain.  I believe this has been reported as an Evo bug, but rejected on the grounds that it's the theming that is at fault.

---

### Post by cdysthe on 2014-02-25
> **buzzingrobot said:**
> Yep, I've seen it, too, and it is a theme thing. I tried finding the theme code, or the Evolution code, that controlled that, without success.

I got rid of it by trying GTK different themes. I needed to restart Evolution after each theme change.

it is a bit of a pain.  I believe this has been reported as an Evo bug, but rejected on the grounds that it's the theming that is at fault.

I've tried to bring it up on the Evo and Ubuntu GNOME mailing lists, but they are pointing at each other or Gnome in general. The problem is that it only seems to affect Evolution which isn't exactly the most used Gnome application these days (I do not think people know how good it has become over the last two releases). I guess I'll just have to live with it until someone figures it out. I have only found one theme that doesn't have this problem, but that one has other issues in Gnome 3.10. Which theme(s) have you found that doesn't have the black background issue?

---

