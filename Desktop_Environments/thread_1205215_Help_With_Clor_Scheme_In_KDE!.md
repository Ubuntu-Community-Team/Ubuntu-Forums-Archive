---
title: "Help With Clor Scheme In KDE!"
date: 2009-07-05
forum: Desktop Environments
---

### Post by izizzle on 2009-07-05
I am using the [DarkPearl]("http://www.kde-look.org/content/show.php/darkPearl+for+QtCurve?content=97644") color scheme in kubuntu 9.04 right now, and I am having issues with text boxes in Firefox. The scheme has fonts set to the color white, but in some sites firefox text-boxes to not follow the theme's settings and the text box stays white, and I am typing in white. So, I can't see what I am typing!

I have tried unchecking "Apply colors to non-kde4 applications", but that does not help. Can anyone tell me how to fix this?

Thanks.

---

### Post by krazyd on 2009-07-06
Could be a gtk theming issues, but since it is only specific sites that you have problems with, are you sure that those sites are not setting the textbox background manually?

can you give an example of a site which works for you, and a site which doesn't?

---

### Post by izizzle on 2009-07-08
Google's search box works fine.

If I go to [Craigslist]("https://post.craigslist.org/aus/S/sys/none/x") and try to type in the boxes, the problem occurs.

---

### Post by krazyd on 2009-07-08
Here's your problem. The This line near the bottom of [https://post.craigslist.org/styles/craigslist.css](https://post.craigslist.org/styles/craigslist.css) :
```
#pp input, #pp textarea { border: #ccc 1px solid; background: #fbfbfb }
```

Craigslist is forcing the background on its input forms and text areas to be #fbfbfb, which is almost white, so their theming support is broken for dark themes. Google, on the other hand, doesn't specify colours so your system's theme takes precedence.

You might be able to work around this by playing with the settings in firefox Preferences > Content > Colors... but this might make other pages look crappy too.

Other than that there might be an extension to fix this problem - I don't know but you can search the firefox addons site.

---

### Post by izizzle on 2009-07-09
Thanks krazyd. I'll look into my options.

---

