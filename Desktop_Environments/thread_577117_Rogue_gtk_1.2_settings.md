---
title: "Rogue gtk 1.2 settings"
date: 2007-10-15
forum: Desktop Environments
---

### Post by ridetheteapot on 2007-10-15
disclaimer--- i have searched many posts on similar subjects, the fixes offered either don't apply or don't work, so here it goes another thread.

    My problem is that i cannot switch the gtk1.2 theme, i used to be able to. Usually i just open up .gtkrc.mine and put in the path. But now it doesn't work (if it means anything the program 'switch' is not previewing the themes either, each preview is the same)
I am using gnome, and do not use any other de's (many of these type problems are from a de conflict)
    I did have gtk-qt-engine installed, but i don't know why i had it or when i installed it (all i can guess is that i did by mistake while installing other gtk engines, but that was long ago, and the problem probably wouldnt have just popped up now, but thats all i can think of. I just want to match my gtk2 theme :(
    Maybe there is another file that could override gtkrc.mine? I've been searching the filesystem for the bugger but can't find it.
I had white gtk1 menu background white and text white so it really sucked (libnotify doesnt like my white text either... YOU GOTTA BE ABLE TO SEE THE TEXT! white on white is the most annoying *bug* around). I've managed to get the text to change darker, but im baffled as to how, because nothing else has changed.
    If anyone has any insight onto the mysterious workings of gtk theme settings i really could use some help thanks.

---

### Post by ridetheteapot on 2007-10-15
while i was changing gtk thmese before the themes a tried must have all been using the industrial engine. If i use a theme that uses the smooth engine the colors are all fine.
But the menu drawing takes a long time and is obvuiosly not working correctly; it really looks like its straining to draw the menus. so smooth engine is unusable for me right now.
maybe that means industrial engine is broken or something and thats why all the themes that use it are broken?


__________
EDIT: i went to reinstall gtk-engine-smooth and industrial. it looks like smooth is no longer an official package. I installed some new engines too, lighthouseblue and mist, but they are acting just like industrial.. (the font color changes but everything else is the defualt theme).
FYI you can still use smooth themes without the engine for color schemes, as long as you can ignore the error libsmooth.so not found... If i try to edit out all the engine smooth parts the theme acts like all the others :(

---

### Post by TeaSwigger on 2007-10-16
Well you're probably way ahead of me on these things, but just to talk in case it stirs any thoughts. 

Now I'm not using Gnome, but I seem to recall mention that it manages the GTK themes. Wouldn't using the switch / switch2 rather than Gnome potentially cause conflicts? I suppose I'd remove ( --purge, really) all the engines possible and reinstall, testing as each is added.

With Courier New and the Mist theme/engine, GTK 1x actually looks "decent" and it's blazing fast. Another relatively good one for GTK 1x is the legacy human theme. In KDE I've been using KDE for Qt & GTK2 apps, and switch for GTK1x. No .mine file's been needed.

Sorry I can't help more. I'm hoping to get an understanding of this stuff to help me manage theming in future.

---

### Post by ridetheteapot on 2007-10-16
I haven't messed with this at allsince last post cause its ticking me off.
But i hope someone sees this:
The package gtk-engines-mist installs itself (official repo version) to /debian/gtk-engines-mist/usr/lib/gtk/themes/engines .
/debian didnt even exist before i installed this theme engine.

why are all these gtk engine all messed up (and i am not referring to my problem)?

---

### Post by ridetheteapot on 2007-10-16
ok i got mine fixed....
the correct files and format, at least for my gnome system is as such:
2 files are needed in your home folder
  .gtkrc-1.2-gnome2
this file has 2 entries.
 the first is an include to the gtkrc (gtk 1.2) file for your theme.
 the second is an include ~/.gtkrc.mine

the next file is .gtkrc.mine
this file has can not include and include statements, all im using it for is the font

style "default-text" {
font="-monotype-arial-bold-r-normal-*-*-90-*-*-p-*-microsoft-cp1251"
}
class "GtkWidget" style "default-text"

as long as those 2 files don't have any extra entries gtk settings will work (for me)
maybe you could just use .gtkrc-1.2-gnome2 and defince the font there and lose the include .gtkrc.mine but i dunno, and its working now so doesnt really matter to me ;)

---

