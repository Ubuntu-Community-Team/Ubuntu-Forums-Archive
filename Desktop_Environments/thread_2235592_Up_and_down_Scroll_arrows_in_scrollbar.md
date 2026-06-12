---
title: "Up and down Scroll arrows in scrollbar?"
date: 2014-07-21
forum: Desktop Environments
---

### Post by rmcd on 2014-07-21
I am sure there must be a simple solution but havem't been able to find it. How do i restore scroll arrows (above and below the scroll bar) in Xubuntu 14.04? None of the themes that I have provide the scroll arrows and it is incredibly annoying to scroll around in 500 page documents without them.

Thanks.

---

### Post by Toz on 2014-07-22
Do you have overlay-scrollbars installed? If so, they might be the problem. Try removing the package.

---

### Post by vasa1 on 2014-07-22
> **rmcd said:**
> I am sure there must be a simple solution but havem't been able to find it. How do i restore scroll arrows (above and below the scroll bar) in Xubuntu 14.04? None of the themes that I have provide the scroll arrows and it is incredibly annoying to scroll around in 500 page documents without them.

Thanks.

Which themes? There are still some themes that provide those arrows but I just grab the "thumb" of the scrollbar and pull down or up as required and so I don't miss those arrows at all.

In any case, there are many themes available at [http://gnome-look.org](http://gnome-look.org). Make sure you choose a recent one because GTK3 changes quite rapidly and some of the older themes may not work in 14.04.

---

### Post by Dennis N on 2014-07-22
There is a Clearlooks theme that has the arrows on the scrollbar. 

[http://gnome-look.org/content/show.php/Clearlooks-Phenix?content=145210](http://gnome-look.org/content/show.php/Clearlooks-Phenix?content=145210)

Choose the Clearlooks Phenix 3 - Works in Xubuntu 14.04 - Try it out and see if you like it.

---

### Post by rmcd on 2014-07-22
> **Dennis N said:**
> There is a Clearlooks theme that has the arrows on the scrollbar. 

[http://gnome-look.org/content/show.php/Clearlooks-Phenix?content=145210](http://gnome-look.org/content/show.php/Clearlooks-Phenix?content=145210)

Choose the Clearlooks Phenix 3 - Works in Xubuntu 14.04 - Try it out and see if you like it.

I installed  clearlooks-phenix-theme and am using Clearlooks-Phenix. I logged out and then back and I don't see scroll arrows (I do see them in the URL you linked). I don't care that much about appearance, I do care about the window border being thick enough to select for resizing (clearlooks is fine for this) and I do care about scroll arrows. 

@toz: thanks, but I don't have overlay-scrollbars installed ('dpkg -l | grep overlay' returns nothing).

---

### Post by Kirkx on 2014-07-23
I set my theme to Raleigh, it was preloaded with Xubuntu v14.04:

[http://i.imgur.com/DLCPbIJ.png](http://i.imgur.com/DLCPbIJ.png)

It has classic Windows scrollbars:

[http://i.imgur.com/wKYB87j.png](http://i.imgur.com/wKYB87j.png)

Then you can play around with styles in Window Manager, on my screenshot above it's Albatross, but you can get any other style, the scrollabars don't seem to be affected:

[http://i.imgur.com/5yEPJiB.png](http://i.imgur.com/5yEPJiB.png)

---

### Post by Dennis N on 2014-07-23
> **rmcd said:**
> I installed  clearlooks-phenix-theme and am using Clearlooks-Phenix. I logged out and then back and I don't see scroll arrows (I do see them in the URL you linked).

Well, that's strange. I have them in mine. I attached an image - scrollbar arrow in the red box. Another on the other end.

Did you forget that the scrollbars don't appear unless scrolling is needed to see all the content - i.e. a long enough document, or more files than fit in the window height?

---

### Post by rmcd on 2014-07-23
Thank you all for you help, I have to be missing something. I have no Raleigh theme and no arrows.

Here is a screenshot of the themes available in Settings|Window Manager [ATTACH=CONFIG]254969[/ATTACH].

And here is a screenshot of three scrollbars taken under Clearlooks-phenix.[ATTACH=CONFIG]254968[/ATTACH].

What am I overlooking?

---

### Post by Dennis N on 2014-07-23
Hi rmcd,

You are looking at the Window Manager, but should be looking at Settings > Appearance > Style
See the screenshot I have attached, showing this dialog and the Albatross theme.

There are actually 4 themes already in there that have arrows. 5 when you add clearlooks-phenix

Albatross
Clearlooks-flat-compact
HIgh Contrast
projets-divers-clearlooks-phenix
Raleigh

Of these, I now prefer the Albatross theme, as it has uncommon dark gray menu backgrounds (as you can see), and very subtle arrows on the scrollbars.

Edit: In the image, I hadn't yet changed the window manager style to Albatross. Do that, and it all matches.

---

### Post by Dennis N on 2014-07-24
> **Kirkx said:**
> I set my theme to Raleigh, it was preloaded with Xubuntu v14.04:

[http://i.imgur.com/DLCPbIJ.png](http://i.imgur.com/DLCPbIJ.png)

It has classic Windows scrollbars:

[http://i.imgur.com/wKYB87j.png](http://i.imgur.com/wKYB87j.png)

Then you can play around with styles in Window Manager, on my screenshot above it's Albatross, but you can get any other style, the scrollabars don't seem to be affected:

[http://i.imgur.com/5yEPJiB.png](http://i.imgur.com/5yEPJiB.png)

Thanks for point these out. I had forgotten that there were themes there with arrowed scrollbars, and didn't check either. I actually like the Albatross theme and plan give it a try. Need to fix the desktop icon text background, however.

---

### Post by Kirkx on 2014-07-24
Rmcd, first you need to go to Appearance, Raleigh style should be pre-installed there:

[URL="http://i.imgur.com/QlaATfg.pngThen"]http://i.imgur.com/QlaATfg.png

[/URL]Then go to Window Manager and experiment with different styles. They shouldn't affect the scrollbars, though, only window borders, titlebars and their colours, minimize/maximize buttons, etc.

[http://i.imgur.com/sHtPwSy.png](http://i.imgur.com/sHtPwSy.png)

There are also lots of Windows XP themes for Linux all over the web, they should have standard scrollbars.

Personally, I always look at the combination of styles that results in  the active window having different colours and standing out from all  remaining open windows.

---

### Post by Dennis N on 2014-07-24
Notice that Raleigh provides only a gtk 2 theme version. Applications are not going to theme properly if they need a gtk 3 theme. So keep that in mind. It also has no window manager theme designed to match.

---

### Post by rmcd on 2014-07-24
Thank you DennisN and Kirkx. "Appearance" does indeed solve the problem. I've been using xubuntu for years, but have never wanted to customize the appearance in this manner before. Seems to me that one dialog should handle the job of both the window and appearance manager, but that's not for this thread. 

Thanks!

---

