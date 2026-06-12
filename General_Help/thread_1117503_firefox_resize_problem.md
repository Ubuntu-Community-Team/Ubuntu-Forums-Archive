---
title: "firefox resize problem"
date: 2009-04-06
forum: General Help
---

### Post by aLarM on 2009-04-06
im having a little problem with firefox in ubuntu 8.10
when i start firefox it opens up and covers up my top and bottom ubuntu menus. its not  set to full screen either it just covers up my menus. i also cant hit close maximize or minimize. this also occurs when i click a link that is in a window other than firefox like a link sent in an instant message. in order to get the menus to show again i have to go into full screen and then deactivate full screen. i recorded a very short video of it and put it on youtube because im not very good at explaining things.
[http://www.youtube.com/watch?v=q0FNzkZIyCk](http://www.youtube.com/watch?v=q0FNzkZIyCk)
you can see it better if you hit the hd button.

---

### Post by MarcusA on 2009-04-06
I had the same problem, however it's been some time since I last had it. :p which is weird.

---

### Post by binbash on 2009-04-06
Did you try going to compizconfig settings manager > workarounds plugin and untick legacy fullscreen support?

---

### Post by aLarM on 2009-04-06
thanks i think that was the problem although im not sure if it just went away like that guy posted above you or that really worked

---

### Post by JC Cheloven on 2009-04-06
> **aLarM said:**
> im having a little problem with firefox in ubuntu 8.10
when i start firefox it opens up and covers up my top and bottom ubuntu menus. its not  set to full screen either it just covers up my menus. i also cant hit close maximize or minimize. this also occurs when i click a link that is in a window other than firefox like a link sent in an instant message. in order to get the menus to show again i have to go into full screen and then deactivate full screen. i recorded a very short video of it and put it on youtube because im not very good at explaining things.
[http://www.youtube.com/watch?v=q0FNzkZIyCk](http://www.youtube.com/watch?v=q0FNzkZIyCk)
you can see it better if you hit the hd button.

There are two maximize functions which work slightly different. On one hand, the F11 key in firefx and other apps, which hides most things (menu, tabs row, tool bar, etc). On the other hand, there is the maximize function in gnome, which is usually accesed via keyboard shorcut (check your system-preferences-keyboardshortcuts, windows section). This one only hides the title row on top of the window.

Perhaps you're messing both types. It happened to me, and was cumbersome until I realized that.

---

### Post by Tobine on 2009-04-06
> **aLarM said:**
> im having a little problem with firefox in ubuntu 8.10
when i start firefox it opens up and covers up my top and bottom ubuntu menus. its not  set to full screen either it just covers up my menus. i also cant hit close maximize or minimize. this also occurs when i click a link that is in a window other than firefox like a link sent in an instant message. in order to get the menus to show again i have to go into full screen and then deactivate full screen. i recorded a very short video of it and put it on youtube because im not very good at explaining things.
[http://www.youtube.com/watch?v=q0FNzkZIyCk](http://www.youtube.com/watch?v=q0FNzkZIyCk)
you can see it better if you hit the hd button.

I was having the same problem for a while. If you press F11 once or twice the unmaximize button will be visible again and you can shrink it then maximize it to the proper size. make sure you close firefox properly or else the next time it opens you'll have the same problem

---

### Post by aeronutt on 2009-04-08
I've had the same problem in a few different application windows; firefox, xsane, and something else.

So far, F11 has allowed me to gain back control of the window size. But I'm not sure what causes it in the first place!

---

### Post by Sabar on 2009-07-22
I am having the same problem, with firefox covering the Ubuntu Tool bar. and yes it goes away if you hit f-11 twice. how ever it comes back for me. If I minimize then maximize or open tabs or what ever it just does it again. 

So I am looking for a more permanent solution.  Can some one tewll me what this post means? what's a compizconfig.


> **binbash said:**
> Did you try going to compizconfig settings manager > workarounds plugin and untick legacy fullscreen support?

Thanks for any help
Sabar

---

### Post by green69 on 2009-07-22
> **aeronutt said:**
> I've had the same problem in a few different application windows; firefox, xsane, and something else.

So far, F11 has allowed me to gain back control of the window size. But I'm not sure what causes it in the first place!

I was having you same problem during a period. After a lot of time and forum read I found that I was having "maximus" and "maximus windows management" enabled. When I disabled them I solved my problem... I hope this can help you.
Are you using a netbook?

Try to go in system > preferences > sessions

And check if you have "maximus" and "maximus windows management" enabled. If you have it, just disable them.

If this doesn't work try to work on compiz config setting manager.

This is all the help I can give you.

---

