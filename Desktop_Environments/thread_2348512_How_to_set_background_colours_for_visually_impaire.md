---
title: "How to set background colours for visually impaired"
date: 2017-01-04
forum: Desktop Environments
---

### Post by neilajarn on 2017-01-04
I've just installed Xubuntu 16.04 on a laptop for someone who is visually impaired.

We would like the desktop background to be a dark colour and the text to be a light colour sp ots easier to read.

I have read several articles online but am beginning to think Ubuntu would be an easier option to change the desktop background colour because there doesn't seem to be an option to alter the desktop background colour in Xubuntu - only change wallpaper.

Once I have figured out how to do this I also need to change the colours of each window so that the background is a dark colour and the text is a light colour.

Any advive appreciated.

Thanks in advance.

---

### Post by neilajarn on 2017-01-04
have solved the background problem by setting the style to none and then selecting a colour.

Still need a user friendly way to change the background and text colours  inside the windows- thunar, web browser etc They need to be a dark  background colour with light text...

---

### Post by vasa1 on 2017-01-04
> **neilajarn said:**
> have solved the background problem by setting the style to none and then selecting a colour.

Still need a user friendly way to change the background and text colours  inside the windows- thunar, web browser etc They need to be a dark  background colour with light text...

**Edit: please read caution about Stylish at the end of this post.**

For the browser (unspecified), I suggest installing the Stylish Extension which is available [for Firefox]("https://addons.mozilla.org/en-us/firefox/addon/stylish/") and [for Chrome (and Vivaldi)]("https://chrome.google.com/webstore/detail/stylish/fjnbnpbmkenffdnngjfgmeleoegfcffe?hl=en"). There may also be a version for Opera.  

Once that's installed, visit userstyles.org for "dark global themes". (The *global* bit is important; otherwise, you'll find themes that only darken the "chrome" of the browser and not the webpage itself.

You'll also need to get acquainted with gtk themes because Xubuntu, by default, comes with a majority of its applications being gtk-based. You'll also need to mention the gtk theme in use. Xubuntu has Greybird as its default. If you're using Greybird, I could offer you some suggestions on darkening things!

I'm attaching an image of my system with a few windows open.
[LIST]
[*]Top-most left: conky with dark background and lighter text
[*]Top-most right: a panel (tint2) with dark background
[*]Fore-most window is gedit's preferences allowing you to select a dark theme for the text area
[*]Below that is the gedit window itself; note the dark background (because I've chosen a slightly modified version of the *Cobalt* color scheme)
[*]To the left of the gedit window is a bit of Thunar and
[*]the lowest window is my Vivaldi browser in which I'm responding to your post.
[/LIST]

In the image, I've used *gedit* but *mousepad*, which is Xubuntu's default text editor, also allows you to change the color scheme. Click on *View* and then hover over *Color Scheme* to see the options available. Before you do so, it would help if you've got a text file such as *~/.bashrc* open (but make sure you don't make any unintentional changes to the file)!

BTW, I just noticed you're looking for a "user friendly way". I think Xubuntu has a small application for that but it had limited options when I last looked. Here's a thread from 2012: [https://ubuntuforums.org/showthread.php?t=2053698](https://ubuntuforums.org/showthread.php?t=2053698). Maybe the application is still present and even better than when I looked at it. Maybe a Xubuntu user can tell you about it.

[center]=====[/center]
There's yet another route with a fancy GUI and all. It's called Oomox: [http://www.webupd8.org/2016/06/tool-to-customize-numix-theme-colors.html](http://www.webupd8.org/2016/06/tool-to-customize-numix-theme-colors.html). You can use it to customize the version of the Numix theme which is present in Xubuntu 16.04 and later.

[center]=====[/center]
Caution re. the Stylish extension
This extension recently changed owners. There's concern now, that the "new" Stylish *maybe* be collecting some sort of user data:
[https://www.ghacks.net/2017/01/04/major-stylish-add-on-changes-in-regards-to-privacy/](https://www.ghacks.net/2017/01/04/major-stylish-add-on-changes-in-regards-to-privacy/)
[https://www.bleepingcomputer.com/news/software/2-million-users-impacted-by-new-data-collection-policy-in-stylish-browser-add-on/](https://www.bleepingcomputer.com/news/software/2-million-users-impacted-by-new-data-collection-policy-in-stylish-browser-add-on/)

---

### Post by neilajarn on 2017-01-05
This worked perfectly.

The stylish extension  with one of the dark global themes helped change the browser colours in firefox.

Then the oomox utility  took care of the rest.

Many thanks.

---

### Post by vasa1 on 2017-01-05
@neilajarn, please see my note at the bottom of my previous reply re. Stylish!

---

### Post by Bucky Ball on 2017-01-06
And please mark as solved to help others (see link in my signature). :)

---

