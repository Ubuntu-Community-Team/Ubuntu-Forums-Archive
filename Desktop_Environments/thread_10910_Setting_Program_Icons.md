---
title: "Setting Program Icons"
date: 2005-01-12
forum: Desktop Environments
---

### Post by wulf on 2005-01-12
How do you set the icon associated with a program? I'm not talking about the image used in the menu or on the panel, which is easy to update. I'm thinking about the image that is shown when, for example, you click on the Window Selector dropdown or Alt-Tab between applications.

Many programs have unique icons shown - for example, Firefox uses a blue globe, the same as the default program icon - but others just user a generic "blank paper" icon. I'd like to set up specific images for one or two applications I regularly have open, such as urxvt or gkrellm so that it is easy to distinguish between them.

I've done some searching around but I think I haven't got the right vocabulary to frame the question properly. Any clues?

Wulf

---

### Post by Vulc on 2005-01-12
curious about this too

---

### Post by wulf on 2005-01-13
Okay - that's two of us who are curious... any takers for an answer? :D

Wulf

---

### Post by wallijonn on 2005-01-13
You would show properties, push the ICON button, or "use custom icon", and change the icon. You could copy an icon to /usr/share/pixmaps or you could create your own icon and then copy it to /usr/share/pixmaps.

---

### Post by Perfect Storm on 2005-01-13
I think he mean in the 'applications tab'.

write in the console:

nautilus applications:///Internet

or 

nautilus applications:///System

or what you want to modify

---

### Post by wulf on 2005-01-13
Sorry - I tried both right clicking icons and choosing properties, etc, and also going through the Nautilus URI. I can change the appearance of icons in the menus with no problem but it's the icons when you use alt-tab (etc) that I'm after. 

That's got to be hidden somewhere different. For example, if I change to the default Ubuntu icons (I'm using the Gnome set at the moment), the icon for Thunderbird changes... but not the alt-tab graphic. There must be a gnome setting somewhere or a directory that I need to place an icon of a suitable filetype into for it to be picked up.

Wulf

---

### Post by artnay on 2005-03-20
I'd like to get more information on the icons, too. Does it have something to do with Gnome or with the provided package? I really think it's a horrible idea to replace well-known icons with some blue globe or bad quality envelope.

After upgrading to Ubuntu's FF 1.0.1 package downloading was buggy. I also disliked the blue globe (because other users don't know what that is, but they do know the FF icon) and inserting the package name into User-Agent form. So I decided to "sudo apt-get remove mozilla-firefox". I downloaded the Debian package and installed that. The globe was still there and User Agent was changed from "Ubuntu-xxxpackage" to "Debian-xxxpackage". So once again I removed Firefox.

This time I decided to grab the binary from Mozilla's site. I installed it and, wow, I was finally able to see the cool fox!  8-) I also got rid of the User Agent modifications, now it displays this:

User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.6) Gecko/20050225 Firefox/1.0.1

After all, it's all about privacy and security.

Oh well, that didn't have much to do with this thread. So any idea is it possible to replace the blue globe with the well-known fox icon?

EDIT: OK, the answer for this question can be found from [here](http://ubuntuforums.org/showthread.php?t=21076). That's too bad, guess I'll be sticking with Mozilla's binary. :-k

---

### Post by abhi on 2005-06-20
I am having the same problem with the Emacs icon.  When I navigate from "Applications-->Accessories," I see an Emacs icon with a gnu bull.  I click on this icon to start emacs, but then when i use Alt-Tab to navigate between windows, there is no bull-- instead, there is a blank icon (perhaps the default icon for applications with unspecified icons).  How can I change this?

I have been looking all around for a solution to this.  Many people seem to have the problem, but no one has posted a solution to this.

---

### Post by wulf on 2005-06-21
If there is a solution, I still haven't found it! I think I've just adapted the way I work (making more use of different desktops) that it's not a burning issue for me any more. Anyway, I guess you could always use vim... ;) (joke! - no serious flame intended).

Wulf

---

### Post by berserker on 2007-02-09
> **wulf said:**
> How do you set the icon associated with a program? I'm not talking about the image used in the menu or on the panel, which is easy to update. I'm thinking about the image that is shown when, for example, you click on the Window Selector dropdown or Alt-Tab between applications.

Anyone figure out how to do this?

---

### Post by tweedledee on 2007-02-24
It is possible, because the panel program fbpanel has this feature.  However, I have no real idea of how it works, and don't read enough C to translate it.  I came across this feature while experimenting with different panels, and while fbpanel is quite good, it doesn't respect workspaces properly, so won't work for me.  HOWEVER, you can still make use of its ability to modify the window icons.

1. Install fbpanel (version 4.1 is in the universe repository, or if you plan to really use it as a panel I recommend building 4.5 from source from the fbpanel homepage, but you'll need to install the libgtk-dev, libglib-dev, and libxmu-dev packages, and maybe libxmuu-dev).

2. Create a .fbpanel folder in your home folder, and paste the following into a new file called default in ~/.fbpanel/ (no extension):
```
Global {
    edge = bottom
    allign = right
    margin = 0
    widthtype = pixel
    width = 0
    heighttype = pixel
    height = 0
    Transparent = true
    TintColor = 0xFFFFFFFF
    Alpha = 0
}

Plugin {
    type = icons
    config {
        application {
            Image = /usr/share/pixmaps/python2.4.xpm
#            AppName = emacs
            ClassName = Toplevel
        }

    }
}

```(This particular example changes the python IDLE icons from the generic folder to the correct icon used in the menus.)

3. Add fbpanel to your session startup commands.

Notes:
1. Despite the code in the global block, the smallest you can make the panel is actually 1x16 (I think) pixels (where 16 is the height).  It will show up as a gray bar for a second when it loads, then go transparent.  I place it on the bottom right because it hides behind the clock in my bottom panel; you can try moving it around as suits your panel(s), but I suggest sticking it somewhere "out of the way" and near another panel, because it will affect window positioning (it is a panel, after all).

2. You can have has many "application" blocks as you want.  The "image" is the actual icon image you want the program to use.  You can use either or both of AppName and ClassName.  To get those values, fire up the program you want to change the icon for, fire up a terminal, type "xprop" in the terminal, and click on the titlebar of the window you want that information for.  You'll see two values near the bottom of the output, WM_CLASS(STRING) and WM_NAME(STRING), that have the values you can match against.  I don't know if you have to match the whole string, but it is definitely case sensitive.  I suggest Class if possible, as that is usually very specific to a program, and constant across multiple windows.

If anyone finds an actual solution instead of this hack, please post.  In the meantime, this should work for anyone wanting to do this.

---

