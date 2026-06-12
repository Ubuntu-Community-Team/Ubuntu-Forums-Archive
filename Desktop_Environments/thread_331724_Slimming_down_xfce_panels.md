---
title: "Slimming down xfce panels"
date: 2007-01-05
forum: Desktop Environments
---

### Post by michael117 on 2007-01-05
Upon the request of another user, I installed xfce through the xubuntu-desktop package and I must say I like it so far. I've used KDE (7 years ago), Gnome, IceWM on my server (I need to run a GUI app), and now xfce. I really enjoy the responsiveness and lightweight of xfce, but I would really like to thin down my top and bottom panels in order to give myself as much real estate to work with because I enjoy two panels.

At the moment, here's what I've got: 
[IMG]http://img501.imageshack.us/img501/8899/screenshotla4.png[/IMG]
I sized down the font on the bottom and have the panel at 17 pixels. I'd like to go a bit more and would like the text on the title bars to be in the middle and not kind of hang near the bottom. At the top, I've tried sizing it down but it just doesn't want to budge. You can tell the icons on the left top size are smaller but it seems like I'm having the most trouble with the system tray. I can do without the extra panel items.

To give you an idea of how I'd like to slim it down, here's a fluxbox desktop I found on deviant art: [http://ic1.deviantart.com/fs10/i/2006/075/b/0/fluxbox_v6_by_masturbi.png]("http://ic1.deviantart.com/fs10/i/2006/075/b/0/fluxbox_v6_by_masturbi.png")

I don't necessarily want it THAT small (maybe twice or thrice the size) but just to give you an idea of what I'm talking about. Maybe even size down the titlebars on regular apps? Any programs I could get from synaptic that might give me better control over this? Any config files I could toy with? Thanks!

---

### Post by Kindred on 2007-01-05
Well the panel will only go as small as the biggest element on the panel, some items might have a minimum size of 18px or whatever and so you wont be able to go lower than that.  On the top panel in this case you'll probably find the system monitor plugin you have there is preventing the panel from going smaller, maybe try removing the uptime from it (it takes up two lines) or even altogether.  

I think the minimum you'll get with xfce panel is 16px so at 17 you're not far off.  I can't say that i've seen text be at the bottom like that before though.   

As to the titlebar size, that'll be dependant on the xfwm4 theme you're using (in window settings or something, I do agree the default themes are clunky) and perhaps even the size of the titlebar font, I haven't used xfce for some time so I forget if it's based on that also.

---

### Post by kerry_s on 2007-01-05
I would say it's most likely your theme. I just shrank mine all the way down to 16 and it still looks fine in mine. See pic->

---

