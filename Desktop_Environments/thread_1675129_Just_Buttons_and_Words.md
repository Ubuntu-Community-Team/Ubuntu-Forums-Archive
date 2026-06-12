---
title: "Just Buttons and Words"
date: 2011-01-25
forum: Desktop Environments
---

### Post by ampc123 on 2011-01-25
Hi guys, I'm new to the world of Linux, kind of. I decided to start using Ubuntu after I got an Android phone and customized the GUI and found that the extent of customization on Windows 7 did not at all satisfy. So I'm kind of looking to customize my desktop with a very specific, very simple look to match my Android's.

Basically what I want to do is get rid of the color of window borders, and make them completely invisible. I want to be able to see only the words, icons, and images floating on my background!

I have kind of been able to accomplish this, by choosing the Dust theme and setting my panels to completely transparent, but this only accomplishes the affect on a completely black background, and only if I have no windows open (although the terminal looks neat). I want to know, in what direction should I go to complete my goal?

I have been searching all day and haven't been able to find any current information. :|

---

### Post by nshiell on 2011-01-25
Not sure exactly what you mean, I use Compiz to turn down the transparency of my Gnome Panels.

The ability to turn the backgrounds to windows transparent but keep the foreground 100% opaque (like terminal or Windown vista/7) is in the pipeline for the future I think.

Desktop Screenshot:
[http://nshiell.uk.to/Screenshot.png](http://nshiell.uk.to/Screenshot.png)
(p.s. ignore the IM conversation with my cousin)

---

### Post by Krytarik on 2011-01-26
I gathered a bit of experience recently on editing gtk/metacity themes.

Flat spoken, metacity is the window title and border, and gtk the window content.

What you want to achive, can be accomplished by changing the settings/images of the metacity theme you want to generaly use.

You should make a copy of the theme you want to use for that. The default and system wide installed themes are located in "/usr/share/themes". The personal ones are in ~/.themes.

Then you have to edit the file "metacity-theme-1.xml" in the "metacity-1" subdirectory of the theme: First change it's name in the upper part to a custom one. In the next section you will find the geometrics of the window. You may want to disable the borders at all, or you want to set it's color to black or such in the more lower sections.

Next you have to also change the names in the file "index.theme" in the root directory of the theme, therefore you have to open that file from within the text editor. Only change the entries of "Name" and "MetacityTheme".

Then proceed with the most important part, to make the title bar completely transparent: Back in the "metacity-1" subdirectory, you will find images which are used to compose at least the title bar and maybe even the frame, like it is the case in my theme. If the latter is the case, you have of course to treat the first part differently.
So, all you have to do now is to open each of those images with an image editor (I recommend GIMP), and clear its content entirely.

That would be all, if I didn't forget anything.

So, go ahead then!;)
Please give feedback how it worked, a screenshot would be nice!:p

---

