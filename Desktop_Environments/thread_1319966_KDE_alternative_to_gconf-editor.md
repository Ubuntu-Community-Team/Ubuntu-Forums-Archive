---
title: "KDE alternative to gconf-editor"
date: 2009-11-08
forum: Desktop Environments
---

### Post by schmidtbag on 2009-11-08
So I've been using gnome for several years and ever since the last update, I got fed up with more options being taken away from me.  But, one tool I've always liked about gnome was gconf-editor.  I've switched to KDE but I haven't found a tool similar to it.  I'm aware it works in KDE but is it just as functional?  Can it manipulate every little detail including the title bar or what the desktop does, or if the desktop even shows up at all?

I need an advanced graphical tool like gconf-editor, and KDE should definitely come with one native to it.

---

### Post by RedSingularity on 2009-11-08
Look at [this](http://ubuntuforums.org/showthread.php?t=955034) thread.

---

### Post by schmidtbag on 2009-11-08
hmm thats it?  kinda disappointing.  i don't have time to try out kwriteconfig right now but how useful, easy, and practical is it?  typically when theres a large collection of features, a command line tool is not going to suffice

---

### Post by RedSingularity on 2009-11-08
Thats what i figured.  I am surprised KDE doesn't have a editor like gnome.

---

### Post by tamasrepus on 2009-11-09
AFAIK, no, there is no KDE equivalent. For the specific things you mentioned, see System Settings (except, unfortunately, for the plasma stuff which tends to have it's own separate configuration dialogs).

Most KDE users (including myself) will tell you that the thing they hate the most about GNOME is gconf, so I'll doubt you'll see KDE imitating this anytime soon.

KDE stores most of it's configuration files as flat text files within ~/.kde/share/config/, editable with your favorite text editor. However, there tend not to be hidden settings. Generally, whatever preferences worth having are exposed in application's UI.

---

### Post by schmidtbag on 2009-11-09
> **tamasrepus said:**
> AFAIK, no, there is no KDE equivalent. For the specific things you mentioned, see System Settings (except, unfortunately, for the plasma stuff which tends to have it's own separate configuration dialogs).

Most KDE users (including myself) will tell you that the thing they hate the most about GNOME is gconf, so I'll doubt you'll see KDE imitating this anytime soon.

KDE stores most of it's configuration files as flat text files within ~/.kde/share/config/, editable with your favorite text editor. However, there tend not to be hidden settings. Generally, whatever preferences worth having are exposed in application's UI.

What exactly about gconf-editor do you hate?  Its a very easy program that does very advanced things.  I'll look into what you told me when I get home but I have a strong feeling that will not be what I'm looking for.  One thing I really do like about KDE is how you are given many more options in a graphical interface, which is the main reason why I switched to it.  But, its still missing some options that would make my desktop perfect, so I guess my question now is, would these configuration files allow me to make modifications that you can't do in graphical tools?

---

### Post by 3Miro on 2009-11-09
> **schmidtbag said:**
> What exactly about gconf-editor do you hate?  Its a very easy program that does very advanced things.  I'll look into what you told me when I get home but I have a strong feeling that will not be what I'm looking for.  One thing I really do like about KDE is how you are given many more options in a graphical interface, which is the main reason why I switched to it.  But, its still missing some options that would make my desktop perfect, so I guess my question now is, would these configuration files allow me to make modifications that you can't do in graphical tools?

The part that I personally don't like, is that I have to learn quite a lot of stuff about Gnome in order to customize it. KDE on the other hand gives all options in a way that is easy to access. If the particular graphics feature that you want gets implemented, then it will be readily accessible via system-settings.

KDE 4 is also somewhat new, more features will be added in the near future. I am not sure for the exact feature that you are looking for, it might already exist as a widget or something.

---

### Post by Simian Man on 2009-11-09
I can't believe gconf-editor is the thing you miss from Gnome!  It's never really bothered me, because I'd rather be able to configure something there than not at all, but it really is a hack job.

---

### Post by tamasrepus on 2009-11-09
gconf is not bad itself per-se, but the way a lot of applications (mis)use it is:
[list]
[*]It ends up as a dumping ground for settings. If the GNOME philosophy is to reduce the number of settings, then why does a setting still exist if it's not worth exposing in the application's UI? AFAIK one of the original design tenants was for configuration storage only, i.e. settings should be accessible from somewhere else
[*]Settings in gconf are completely undiscoverable. You (generally) need to know the magic key, know what it does, and know how to edit gconf. Thus, settings only accessible via gconf rarely get used, so they get tested less and more likely to break, etc.
[*]While gconf has a schema exporting what keys/values an application uses, this doesn't work particularly well for upgrades. If you've been running GNOME for years you end up with a bunch of unused, irrelevant settings (much like Windows registry) cluttering everything.
[*]Settings cannot easily be copied between different machines. Where are settings stored? Some mysterious text file, without consistent naming, in ~/
[/list]
What kind of settings/options where you looking for, exactly?

---

### Post by schmidtbag on 2009-11-09
see i don't think many of you are right about gconf-editor.  it has a very good search in it, it is very organized, and lets you customize things that you typically wouldn't want to edit but its nice you get the option to, such as simple things like editing where the buttons go on the title bar, how the desktop responds to certain actions, the brightness level of a screen on a laptop, the increment level when you raise or lower the volume - to me this is nice stuff to be able to edit, and i don't think they're significant enough to make a whole gui out of it but they're significant enough that they're all put into 1 program that i can easily search for

---

### Post by tamasrepus on 2009-11-09
In KDE, if you want to change where buttons are in a title bar, you can do so under System Settings &#8594; Look & Feel &#8594; Appearance &#8594; Windows &#8594; Buttons. There's a nice GUI (with preview), and you can drag and drop buttons into place. I've not used gconf for this but I don't see how it could be any easier or better there.

Not sure how you want to change how the “desktop responds”... but it's likely you can change this within one of Plasma's configuration dialogs as I've mentioned already.

Not sure what you mean by brightness level of a laptop, or volume control, but these are exactly the kind of things I'd want a UI. They have natural places in both the configuration GUIs for GNOME and KDE, why they're left out, I don't know. I've never personally felt the need to change them, which is probably the same for many other people, so this may be part of the reason.

IMHO, the only benefit of gconf that it is a lot better than what GNOME was doing before. That is, applications stored settings wherever they wanted (in random dot files in your home directory), they each were responsible for reading/writing their own settings, and there was no standardization whatsoever.

---

### Post by schmidtbag on 2009-11-09
hmm i never noticed the gui for the title bar, i'm not sure how i missed that.  i'm still learning kde.  the plasma configurations do not do enough, and thats actually one of the things i'm looking for a gconf-editor replacement for - i don't want that plasma icon on my desktop, i don't use it and i never will.

i don't use kde on my laptop so it doesn't matter, but what i mean by brightness is when you're running on batteries, gnome lets you configure the exact brightness of the screen automatically.  gnome also lets you change the increment in volume change (and brightness change).  so for example, lets say you pressed the volume up button on your keyboard.  you can change the increment from 6% to maybe 10%, or 2%.

when it comes to computers, i like manipulating them in every way possible, and although i don't find this a high demand, it'd just be a convenience

---

### Post by 3Miro on 2009-11-09
Look into keyboard shortcuts and power management options. At first glance I do not have such option, but then again, I am using a desktop.

The part of gconf-editor that lets you customize stuff is good, the part that requires you to have a lot of knowledge (as opposed to navigate via a nice gui) is bad. KDE setting-manager has a lot of options that sometimes takes me couple of tries to find.

---

