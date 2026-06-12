---
title: "window control buttons now on left!????!"
date: 2010-04-30
forum: Desktop Environments
---

### Post by jflaker on 2010-04-30
I don't like the window controls switch from right to left...made in 10.04. Easy script to move the buttons here. [http://is.gd/bOLJr](http://is.gd/bOLJr)

Very easy fix.....This is what I love about Linux.

---

### Post by nisbeam on 2010-04-30
Fantastic - thank you.  As a newbie I will also analyze  the script to understand how it works - a useful little lesson.  Thanks again. :)

---

### Post by mrreality13 on 2010-04-30
all i did was change the theme to one i preferred as the default mac'ish look isn't to my taste. I use Dark Looks ,fyi

---

### Post by Julita on 2010-04-30
But I love those buttons! I use Netbook Remix; I have heard a lot of "surprise-surprise" stuff here, but, honestly, all the changes have been discussed long before the actual release :) I just wanted to say that I welcome the changes; Ubuntu is a lot prettier now. Thank you for the script; it is useful for "conservative" Linux users :) I have thought that I could change the button placement in appearance settings; never bothered to look, though! :)

---

### Post by ricardisimo on 2010-04-30
No, I'm sorry... the obsession with Mac at the global GNOME evil genius laboratories is out of control. Here's a [simple tutorial]("http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/") on moving them back via gconf-editor.

---

### Post by Perkins on 2010-04-30
As someone who supports computers for a number of elderly people, many of whom it has taken me years to get to where they consistently understand the function of the buttons in the upper left, I can honestly say that changing the default was probably a Bad Idea.  Were it not for the nifty little script posted at the beginning of this thread, I would be looking at either a large amount of pain to move them all back, or a large amount of pain to retrain everyone.  Significant changes to look and feel should either prompt on upgrade, or have an easy way to change them built in to the system.

---

### Post by alvevind on 2010-05-01
Another easy way to restore the window button position is to install the right aligned theme:

Step-by-step procedure:
1. Download the modified theme [http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz](http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz)
2. Open the menu "System" > "Preferences" > "Appearance"
3. Click the button "Install"
4. Open the folder "Downloads"
5. Select the file "Ambience_Radiance-Right.tar.gz"
6. Click "Open"
7. Select the new theme "Ambiance-right"

You then have both the standard unmodified left-aligned theme and the right-aligned theme available and can easily switch back and forth between them with a single click, without adjusting the button position every time.

---

### Post by horseshoe on 2010-05-01
thanks!

---

### Post by mf205 on 2010-05-01
I tried the gconf fix, and it doesn't quite do it for me.  (I haven't tried the other two fixes yet.)  The problem is this: although the buttons look the same as before and function as they should, if you move have a maximised window and move the mouse pointer to the top right corner of the screen, it's not over the close button - you have to move down a pixel or two to get over the button.

You might think this is picky, but it's miles easier to move the pointer to the corner of the screen quickly than to move it just shy of the corner.

Any ideas?

---

### Post by sigurnjak on 2010-05-01
You can use gstyle  to put buttons anywhere you want .

[https://launchpad.net/~s-lagui/+archive/ppa](https://launchpad.net/~s-lagui/+archive/ppa)

---

### Post by auh2o on 2010-05-01
I upgraded through the Update Manager, and my buttons stayed on the right! I was all set beforehand to go directly into gconf and edit them back to where they should be, but was pleasantly surprised when I didn't have to!

---

### Post by alvevind on 2010-05-01
> **mf205 said:**
> I tried the gconf fix, and it doesn't quite do it for me.  (I haven't tried the other two fixes yet.)  The problem is this: although the buttons look the same as before and function as they should, if you move have a maximised window and move the mouse pointer to the top right corner of the screen, it's not over the close button - you have to move down a pixel or two to get over the button.

You might think this is picky, but it's miles easier to move the pointer to the corner of the screen quickly than to move it just shy of the corner.

Any ideas?

The buttons are where they are. In the default theme they do not extend out to the corner. So clicking the corner should not close the window since that would be outside the button.

If you want to click the very corner to close windows the easiest way is to choose a theme that is designed to work that way. The "New Wave" theme seems to have a close button that goes all the way to the corner.

---

### Post by drreed on 2010-05-01
I too found this unsettling, until I thought about it.

Years ago considerable research was conducted to study how people see and interact with GUI applications. There are some cultural differences, but the overwhelming majority of those of us who read left-to-right instinctively want those buttons on the left, that's where we look for things first, especially children.

As I recall, buttons on the right have always seemed foreign to me. My eyes have to move a long way to find them usually. 

But I'm used to it. I think I'll give the other way a try for a while and see if I can adjust.

---

### Post by starpollo on 2010-06-26
> **alvevind said:**
> Another easy way to restore the window button position is to install the right aligned theme:

Step-by-step procedure:
1. Download the modified theme [http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz]("http://people.ubuntu.com/%7Edylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz")
2. Open the menu "System" > "Preferences" > "Appearance"
3. Click the button "Install"
4. Open the folder "Downloads"
5. Select the file "Ambience_Radiance-Right.tar.gz"
6. Click "Open"
7. Select the new theme "Ambiance-right"

You then have both the standard unmodified left-aligned theme and the right-aligned theme available and can easily switch back and forth between them with a single click, without adjusting the button position every time.

Great solution for me, thank you ^^

---

### Post by w0Rm210 on 2010-06-27
> **ricardisimo said:**
> No, I'm sorry... the obsession with Mac at the global GNOME evil genius laboratories is out of control. Here's a [simple tutorial]("http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/") on moving them back via gconf-editor.

I actually like the switch and i think people should at least give the new buttons a chance before auto switching them back. I think the new buttons show that Ubuntu is an OS open to change :).

---

### Post by agd19682 on 2010-10-22
[FONT=Georgia][SIZE=2]Does anyone know whether the script mentioned in the beginning works on ver 10.10 as well?[/SIZE][/FONT]

---

