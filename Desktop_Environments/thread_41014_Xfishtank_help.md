---
title: "Xfishtank help"
date: 2005-06-11
forum: Desktop Environments
---

### Post by Omnios on 2005-06-11
I installed Xfishtank and can not seem to get it working. I tryed running it and it is aperently running in root but does not show. It does appear for a sec when I log off so It is running in root but not shire on how to show it. Any help would be apreacieted.

 Xfishtank sems to run on rood but has a xfishtank host:display option. I tryed running it with host display but got a failed message "xfishtank: XOpenDisplay failed"

---

### Post by intangible on 2005-06-17
xfishtank looks like an old X app that assumed you would only use it to draw your desktop background (known as your root window).  As long as nautilus is running, it will display your background on top of anything that draws to the root window, such as xfishtank.

Most have programs have an option to display inside a window instead of to the root window, but not it, oh well, here's a couple work arounds:

Option 1: Xnest
install xnest: **sudo apt-get install xnest**
then: **Xnest -ac :1& xfishtank :1**

Option 2: turn off nautilus desktop drawing
before running xfishtank, run this:
**gconftool-2 /apps/nautilus/preferences/show_desktop -t bool -s false**
and then
**xfishtank**
when you are done, run this to bring back your desktop icons:
**gconftool-2 /apps/nautilus/preferences/show_desktop -t bool -s true**

Hope this helped.

---

### Post by Omnios on 2005-06-17
Thanks Found I could run it in xsceensaver and found it wasn't what I was looking for. Im actualy looking for a cartoon or graphic fishtank with realistic movements.






 Linux is like Monster Garage!
 Freebee value = $3000
 Total build cost= Priceless

---

