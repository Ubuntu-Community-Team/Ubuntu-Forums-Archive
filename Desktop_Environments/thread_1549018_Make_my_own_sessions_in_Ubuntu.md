---
title: "Make my own sessions in Ubuntu?"
date: 2010-08-09
forum: Desktop Environments
---

### Post by Farsk1 on 2010-08-09
I've been using Ubuntu on and of for about 2 years now, and it has now become my primary OS, and I know it fairly well by now. 

I have one question though: is there a way for me to make my own sessions which i can choose from in the login window. Because when I'm at home I'm using my notebook with an external monitor, so when I'm out of the house and I boot my notebook i get the very large dual-screen wallpaper all squeezed into my single monitor and my conky (which I usually have on the external monitor) ends up taking about half of my space on the desktop. So I was wondering if there was a way to make a setup like: One Screen session, Dual-screen session.

And one more thing: If you're familiar with the Elive distro, you would have noticed the option you get on the login where you can choose between day and night mode. The day mode features a very bright and shiny theme and wallpaper, works fine for using the computer in daylight etc..The night mode is a more darker theme and wallpaper, and fits better in a dark room or at night. I was wondering if there was a way to make something similar to this in Ubuntu?

---

### Post by Zorgoth on 2010-08-10
This may not be the most elegant solution, but "wmctrl -d" will list your desktops, so if you could figure out a bash conditional to determine whether you have 1 or 2 screens that way you could have Startup Applications link to a script to do what you need.

If you aren't comfortable doing that yourself post the output of wmctrl -d when both monitors are hooked up and maybe I'll see if I can help.

I think though there should probably be a better way...

---

