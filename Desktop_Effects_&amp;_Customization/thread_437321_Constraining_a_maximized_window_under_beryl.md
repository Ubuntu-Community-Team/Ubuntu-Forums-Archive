---
title: "Constraining a maximized window under beryl"
date: 2007-05-08
forum: Desktop Effects &amp; Customization
---

### Post by lungdart on 2007-05-08
I have been using beryl for quite some time now, and decided to give AWN a try.

I notice now that AWN is installed, I just don't like how maximized windows look. I would prefer to have them at a certain size, centered in my screen that takes up MOST of my screen, but leave a little padding on the sides. It would be great if there were a way to pad the maximize, so that when I click maximize, it goes to my desired limit.

I've been looking around for quite some time, but cant seem to find any such ability in beryl, and im not sure what else would have that preference, the X server maybe?

 Any help will be appreciated, thanks!

---

### Post by jbus on 2007-05-08
I would really like to do this as well... Unfortunately, the only way I have found to accomplish this is to create transparent panels on all four sides in addition to my regular panels. Though, this doesn't look well if you have shadows enabled for panels. I've attached a screenshot.

---

### Post by lungdart on 2007-05-09
I thought of this workaround myself, but IT just will not do. It has too many things I don't like to make it worth what I like.

For instance

1) if I try to move my window to another side of my cube, it goes under the side panels, making it disappear for 40 or so pixels on each side. Not good in my books.

2) If I click anywhere that I believe is my desktop, it is not my desktop, it is a panel, and I don't have the same menu, or area selected that I wanted.

3) If I click on the bottom, the large bottom panel hides my AWN Dock until I remove it.

4) It truncates the shadows of my windows and also truncates the sides of them. They just disappear into "no monitor" land.

For now, I'm just using the ability to create new windows in the center of my screen, and trying to ignore the maximize button.

Maybe I am looking for the wrong thing, maybe I need a new button on my tittle bars that sets it to a certain size (one I specify) and restores it from that size. Then I could replace my maximize/restore button with it.

Anyone know of any such scripts or if such a thing exists in emerald/beryl?

---

### Post by jbus on 2007-05-09
You might want to try KDE... It gives you much more control over window sizes and placement than gnome does. 

If you do find a solution to this issue in gnome, please post it here.

---

### Post by lungdart on 2007-05-09
I do not like KDE. I used to use it prior to gnome 2, but when the new gnome came out, it one my heart with its easy on the eye interface.

---

### Post by lungdart on 2007-05-13
**_BUMP_: Solution!**

If you want to be able to set your window to a specific size at a specific position, this is for you. Its not the same as constraining the maximized size. But it is a little better. The only thing right now though, is I haven't found a way to map the command to the maximize button or what have you. Ill update this thread when I figure that out. But for now here we go. Also, you need beryl to do this.

First we need to install a program that allows us to manipulate windows from the command line

```

sudo apt-get install wmctrl

```

Now you need to add a command to beryl that will use the program to set the size and position of the active window. Open up beryl settings manager, and go to general options -> commands. add this command

```

wmctrl -r :ACTIVE: -e 0,X,Y,W,H

```

Where X and Y are your position (horizontal and then vertical) And W and H are your window size (Horizontal and then vertical again) You can then click on the shortcuts tab in general options and add the command to a hot key. Heres mine for an example:

wmctrl -r :ACTIVE: -e 0,50,100,1180,834

And I have it mapped to "<Control>m"

Enjoy!

---

