---
title: "change adwaita theme border width"
date: 2018-05-15
forum: Desktop Environments
---

### Post by arapaho on 2018-05-15
How can I decrease Adwaita theme border width? I use Plasma KDE in 18.04 but for gtk apps I use Adwaita. The problem is that right border width is too thick and when I move mouse to the right side of the screen mouse cursor doesn't touch scrollbar and it is impossible to scroll. I need to make right border thinner. And I would prefer to set it in pixels if possible.

I found those guidelines but I need to know the exact component that need to be changed.

[https://developer.gnome.org/gtk2/stable/GtkWindow.html]("https://developer.gnome.org/gtk2/stable/GtkWindow.html#GtkWindow--default-width")

[https://developer.gnome.org/gtk3/3.5/GtkWindow.html](https://developer.gnome.org/gtk3/3.5/GtkWindow.html)

I prefer to do it directly in theme because I don't want to install additional Gnome tools.

---

### Post by cruzer001 on 2018-05-18
In Adwaita gtk2 the border is only 1 pixel wide.  It can be set to 0, but I can't see how 1 pixel will help.
[ATTACH=CONFIG]279735[/ATTACH]
Have you tried other themes?

Can you post a screenshot?

---

### Post by arapaho on 2018-05-18
Perhaps I am wrong. Maybe not border is a problem but the space between right border and slider, I mean the frame that surrounds the slider / scrollbar. Perhaps making slider wider would help but if there is a way to get rid of the space between right border and slider that would be a better solution. 
[IMG]https://imgur.com/a/Pd87Gaz[/IMG][IMG]https://imgur.com/a/Pd87Gaz[/IMG]
[https://imgur.com/a/0eSqNHc](https://imgur.com/a/0eSqNHc)

Blue colour shows windows frame. Red colour shows frame of the slider / scrollbar.

On minimized windows it is clearly visible that there are a lot of pixels from right window border to scrollbar.
[https://imgur.com/a/E3bVCu5](https://imgur.com/a/E3bVCu5)

And I don't have this problem with KDE / Qt applications.

I don't know what versions of gtk are responsible for this. Perhaps gtk2 but I want to know what to change in gtk3 as well. Here is my adwaita so you can check yourself:
[https://drive.google.com/drive/folders/1eCF2V0j7o6YuLYI0n9pncEtFrAFobG5h](https://drive.google.com/drive/folders/1eCF2V0j7o6YuLYI0n9pncEtFrAFobG5h)

---

### Post by The Cog on 2018-05-18
I think the clearlooks-phenix theme has the same problem (on Xubuntu, at least). With firefox, if you slam the cursor to the right edge of the screen and try to grab the scroll bar, you miss it and the screen just auto-scrolls to the top or bottom. You have to back off from the edge of the screen by 1 pixel to reach the scrollbar. And a KVM guest in full-screen mode gains scrollbars because the window is 1 pixel wider than the guest screen. Which is a shame because if it weren't for that bug, clearlooks-phenix would be my favourite theme. With the bug it's intolerable.

So if there's a way to correct it, I would be interested as well.

---

### Post by cruzer001 on 2018-05-18
> Perhaps making slider wider would help

That area is outside the window and I don't think it will do any good, but it won't hurt to try increasing the "padding" and widen the slider.
Copy the below and created file in Home /.config/gtk-3.0/gtk.css (I'm guessing your running gtk3).
```
scrollbar slider {
    /* Size of the slider */
    min-width: 15px;
    min-height: 15px;
    border-radius: 17px;

    /* Padding around the slider */
    border: 5px solid transparent;
}
```
Log out/in for change to take effect.

Where are these bug reports?

---

### Post by arapaho on 2018-05-18
No, it didn't help. I think it may be gtk2 app (this from example screenshot), because when I change gtk2 theme it changes colour. 

> **cruzer001 said:**
> Where are these bug reports?
What bugs? I didn't reported bugs for this. 

Is it possible that application may have specific coding that override theme specific window drawing?

I don't have this problem with libreoffice, although it uses adwaita too. 
Wersja: 6.0.4.2
Build ID: 1:6.0.4~rc2-0ubuntu0.14.04.2
CPU threads: 2; OS: Linux 3.13; UI render: domy&#347;lny; VCL: **gtk2**; 

[https://imgur.com/a/nnL9AL4](https://imgur.com/a/nnL9AL4)

On the screenshot is minimized window but with maximised there is no problem and mouse touches scrollbar.

---

### Post by Frogs Hair on 2018-05-18
There are some slim variants.

[https://www.gnome-look.org/p/1174686/](https://www.gnome-look.org/p/1174686/)

[https://www.gnome-look.org/p/1181146/](https://www.gnome-look.org/p/1181146/)

---

### Post by cruzer001 on 2018-05-18
> **Frogs Hair said:**
> There some slim variants.
That would be a nice option.

I haven't played with gtk2 in 18.04 so here are some links that you can try.

[https://askubuntu.com/questions/775201/how-do-i-get-a-bigger-static-scrollbar-aka-normal-scrollbar/827213#827213](https://askubuntu.com/questions/775201/how-do-i-get-a-bigger-static-scrollbar-aka-normal-scrollbar/827213#827213)

[https://unix.stackexchange.com/questions/47674/how-should-one-change-the-width-of-scrollbar/47678#47678](https://unix.stackexchange.com/questions/47674/how-should-one-change-the-width-of-scrollbar/47678#47678)

Gnome-color-chooser may still work on gtk2.
[https://superuser.com/questions/346491/how-do-i-change-the-width-of-scrollbars-in-gnome/346492#346492](https://superuser.com/questions/346491/how-do-i-change-the-width-of-scrollbars-in-gnome/346492#346492)

GTK2 has its bugs, since its old code I don't hold much hope for it.  How hard would it be (in kde) to switch over to gtk3?  May not be possible, I don't run kde so just asking.

@The Cog
I'll load up clearlooks-phoenix later today, maybe it will have some clues.

---

### Post by arapaho on 2018-05-18
After checking I know that my problem is related to gtk2.

Settings proposed by @cruzer001 indeed make slider wider but slider frame still exist regardless of slider width, so looks like this frame is responsible for trouble. Maybe there are some bugs in gtk2. I don't know. 

I checked proposed themes but they have the same slider frame.

---

### Post by cruzer001 on 2018-05-18
Clearlooks-phenix works ok in the Gnome environment, but that's gtk3.  No help to KDE or Xubuntu users.

Maybe a better fit for kde is adwaita-qt.
[https://github.com/FedoraQt/adwaita-qt](https://github.com/FedoraQt/adwaita-qt)

---

### Post by arapaho on 2018-05-19
> **cruzer001 said:**
> Maybe a better fit for kde is adwaita-qt.

No, if this is for qt apps only qt apps will use it. Gtk apps will use gtk themes even when they are used within Plasma KDE environment. 

The solution to my problem need to be solved by editing gtk2 theme and changing the frame of the scrollbar slider. But I can't find good guidelines.

---

### Post by cruzer001 on 2018-05-19
Possibly the [Kubuntu forum]("https://www.kubuntuforums.net/forum.php") could help in this.  Not running your environment puts me at a disadvantage.

---

### Post by cruzer001 on 2018-05-19
Well I dug out my $20 laptop, it runs Lubuntu 16.04 and gtk2.

Both adwaita and clearlooks-phenix v7 test ok.

@arapaho
Have you tried changing your kde theme and see if it has any effect on adwaita?

---

### Post by arapaho on 2018-05-20
Thank you for testing. The problem is with stardict 3.01. I tested on xfce and with other themes and on all of them the problem exist. With other programs like libreoffice, firefox I don't have this problem. I sent an email to stardict developers and I will wait for answer.

---

