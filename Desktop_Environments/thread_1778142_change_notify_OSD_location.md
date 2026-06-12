---
title: "change notify OSD location"
date: 2011-06-08
forum: Desktop Environments
---

### Post by gamblor01 on 2011-06-08
Is there a way to change the location that notify OSD uses when it displays a new notification?  I have some large dual monitors at work which is great, but I typically do browsing/development work on the left display and leave email and other less used things on the right display.  Because notifications are displayed on the right monitor, I often miss the notifications because there are outside of my peripheral vision.  I generally notice them within a minute or two because the mail icon in the panel is blue instead of black, but I would rather get the notifications as they occur.

When running 10.10 there was no panel at the top of the right monitor, so all notifications showed up on my left monitor.  Since I upgraded to 11.04, Unity seems to display a panel on both monitors and thus, all notifications wind up on the right monitor.  I would like them to appear on the left monitor instead.

See attached screenshot for more info.  Sorry it's not the best quality -- but the idea is that I ran notify-send "test" in the terminal and you can see the bubble on the right monitor instead of the left one.

So...can the location of the notify OSD be controlled somewhere?

---

### Post by hhh on 2011-06-08
Not the default Notify OSD, but there is a patched version that allows it (use at your own risk)...
[http://www.webupd8.org/2010/07/patched-notifyosd-updates-option-to.html](http://www.webupd8.org/2010/07/patched-notifyosd-updates-option-to.html)

---

### Post by gamblor01 on 2011-06-09
Cool thanks.  It's not perfect but it's better I suppose.  It doesn't look like that tool allows you to configure it on a specific place per monitor -- it considers both screens together as if it were one large screen.  So I now have it on the left monitor (haven't decided if I like top left or bottom left yet).

The ppa by amandeepgrawal for notifyosdconfig doesn't work but you can add ppa:nilarimogard/webupd8 and from there install notifyosdconfig.  I just changed it so the timeout is only 3 seconds.  Finally a reasonable timeout!

Thanks again.

---

### Post by nilarimogard on 2011-06-10
> **gamblor01 said:**
> Cool thanks.  It's not perfect but it's better I suppose.  It doesn't look like that tool allows you to configure it on a specific place per monitor -- it considers both screens together as if it were one large screen.  So I now have it on the left monitor (haven't decided if I like top left or bottom left yet).

The ppa by amandeepgrawal for notifyosdconfig doesn't work but you can add ppa:nilarimogard/webupd8 and from there install notifyosdconfig. ** I just changed it so the timeout is only 3 seconds.  Finally a reasonable timeout!**

Thanks again.

One note though: the application must specify the timeout for this to work. For instance, Y PPA Manager does this...

---

