---
title: "Trouble installing xubuntu themes"
date: 2007-03-29
forum: Desktop Effects &amp; Customization
---

### Post by andycyca on 2007-03-29
Hi again everyone!

Yesterday I began wondering if I could get some (extra) eye candy for Xubuntu. Googling around I found Xfce-look.org and downloaded some themes. But, since I'm a **complete newbie**, i didn't know how to install them. Someone there said that I just needed to unpack the tar.gz files and then copy that folder to usr/share/themes.

I did it but the theme didn't showed up in my 'user interface' window. After that I discovered that  there are gtk 1, gtk 2 and xfce themes. I said to myself: "this could be the problem" I downloaded one of each kind (*how can I know if I have gtk 1, 2 or nothing?*) and got the same answer: nothing new on user interface.

Today I tried once more and noticed something: in usr/share/themes there are A LOT of folders with theme-like files and most of them aren't shown on UI. What is it? What can I do? If you need more info on my system I can get it...If I can't it's because I don't know Xubuntu very well, and maybe I will need some N00b lessons...

EDIT: I'm asking here because I can't register and ask in xfce-look. There seems to be some trouble with the verification-password email.

...And please excuse me if my english isn't too well.

---

### Post by john.nicholls on 2007-03-29
This doesn't answer your question, but have you looked at the forty-odd themes that are provided with Xfce4? Go to the Settings Manager (or open a terminal and type xfce-setting-show), and open Window Manager.

---

### Post by crimesaucer on 2007-04-06
I've been using xubuntu (and linux) for about 6 months, and when I first installed xubuntu last October, I also had troubles with installing themes from xfce-look.org

I followed all of the instructions properly and tried to install them two different ways, in the /.themes directory and also in /usr/share/themes. I had unzipped them and placed them in the correct places.

I was still very new at that time and maybe I missed one important detail. I might of not had the proper theme engines installed, I don't know, it was a while back.

So what I did was I installed a few new themes using the Synaptic Package Manager.

I installed the gtk2.0-engines-xfce that comes with extra themes, and also a few others themes like "Sphere Crystal".

Well, after using the Xfce themes like Xfce-winter or Xfce-4.0, I got bored and decided that I wanted to try to get a new theme again. I also had been using xubuntu for a few months then, and had realized how easy most things are written.

What I did was I experimented with modifying a theme's gtkrc that I already had installed. I just sort of reverse-engineered it through a lot of trial and error to see where colors went and what sizes effected what areas. I'll link you to a page I wrote about it: 

[http://ubuntuforums.org/showthread.php?t=377397](http://ubuntuforums.org/showthread.php?t=377397)

It sounds difficult, but it's not. If you've ever made a html/css web page, it is about as much effort.

At first you might want to just play around with the colors, but after a little research and practice you can basically change anything like button sizes, scroll bars, size of menus, gradients, sunken buttons or round buttons, etched in lines or etched out, or no dividing lines at all. 

If you have any questions just ask me in that thread I linked you to and I'll help you in there.

---

### Post by andycyca on 2007-04-08
Ha! I had nearly forgot this thread!
-----
Yes, now I can install themes from xfce-look.org. It was such a N00b's thing, but I post it here for future User Installers:

**You have to extract the files with their Full Path!** (Tick the mark that says "extract with full path")
----------
Crimesaucer, thanks a lot for the advice, I'm gonna see your thread right now!

---

