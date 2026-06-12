---
title: "gnome-settings-daemon problem"
date: 2007-06-12
forum: Desktop Effects &amp; Customization
---

### Post by KitChy on 2007-06-12
Okay. So I've been running my ubuntu fesity install fine for a few days but I've never been able to change themes but that's never bothered me untill today. So I read on the forums here that if you're unable to change themes with beryl and xgl that if you run he command "gnome-settings-daemon &" this will solve your problem...and it did. So I added this command to my start up programs so that it would do it auto when I log on. So I restarted my computer because I had to anyways and it worked fine...I was able to change themes, icons etc. Then suddenly about an hour or two into my session things would take forever to load. So I restarted hoping this would solve my problem. It didn't. What I realized was that If I look  in my process there are *two* gnome-settings-daemons running, but if I kill the top one of the two my theme stays and PC goes back to normal with me being able to change themes etc...But if I remove the bottom one, theme changing goes away and my PC returns to normal. I've tried removing that command from my startup sessions and that didn't work as my computer would load fast but I would not be able to change themes. 

So basically I want to remove "the bottom" 'gnome-settings-daemon' and keep the top one and remove the bottom one of this process. I really hope this makes sense to you. Sorry if it doesn't!

KitCh x

---

### Post by KitChy on 2007-06-13
Anyone...any help? x

---

### Post by FuturePilot on 2007-06-13
What type of graphics card do you have? If you have a Nvidia card you don't need XGL and that will solve your problem.

---

### Post by KitChy on 2007-06-13
ATI X1800 so I need to use XGL.

---

