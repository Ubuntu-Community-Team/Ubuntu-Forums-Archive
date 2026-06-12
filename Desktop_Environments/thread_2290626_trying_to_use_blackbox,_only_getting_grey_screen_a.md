---
title: "trying to use blackbox, only getting grey screen and panel"
date: 2015-08-13
forum: Desktop Environments
---

### Post by don_mularz on 2015-08-13
Pretty new to a lot of things, and having trouble finding similar issues on the forums here.  I've been using xubuntu 14.04 for a while and i love xfce, but i can't leave anything alone so i did a little research and thought i'd give black box a try as my wm.  i installed it, logged out and selected it from the menu at the login screen, but when it logs in there is just a big grey screen and the task bar/panel at the bottom with the workstation selector.  tried opening a terminal with ctrl-alt-x, no luck.  tried right clicking stuff, no luck.  after a hard reset i was able to select xubuntu from the menu again and everything is back to normal, so no harm no foul but now i'm wondering how i would go about replacing xfwm4 with another wm, or if this is all stupid and i should just tweak xfwm4.

---

### Post by kerry_s on 2015-08-13
lol, linux is a adventure.

most wm's have a switch like "openbox --replace" for example. for xfwm4 you'll need to remove it from startup, then add what ever wm you choose to use.

personally, i find nothing wrong with xfwm4 that it would need replacing. i happen to like xfce4 just the way it is.

---

### Post by vasa1 on 2015-08-13
> **don_mularz said:**
> Pretty new to a lot of things ... so i did a little research and thought i'd give black box a try as my wm. ...
Just curious but what in your research pointed you to blackbox?

---

### Post by don_mularz on 2015-08-13
i found a page where someone had broken down and explained a bunch of different ones, it said black box was lightweight and geared towards efficiency.  this, combined with the cool name, intrigued me and since i didn't know *how* to change the WM and only recently learned i can change DE's, i decided to go for it.  i'll find the page and edit it in here in case it comes in useful for somebody.

i think what initially caused me to start researching different WM's in the first place was the bad screen tearing i get in vlc/flash video (haven't tested games in xubuntu yet, but this machine only playably runs stuff like shadowrun returns, risk of rain, etc) and i saw somewhere that people using compiz were able to fix this, so when i went to see what compiz was i was introduced to the concept of windows managers, and thought maybe a different one might reduce screen tearing (i didn't notice the issue with ubuntu-gnome).  turns out there are a lot of other more likely causes than the WM, the computer really is a junker, so i'm fiddling around with other stuff to reduce it instead of trying to eliminate it altogether.  Gilberto Torrezan's answer on [this]("http://askubuntu.com/questions/450593/how-do-i-eliminate-screen-tearing-on-14-04-and-xbmc-with-nvidia-331") post helped with vlc, but i haven't tackled flash issues yet, and probably won't as i hardly use it anyway and it's probably just something with hardware acceleration.  ok that came out longer than i thought, sorry!

---

### Post by don_mularz on 2015-08-13
i did that first thing but i didn't do anything, so i logged out and selected it from the menu and had the problem.  i'll try removing xfwm4 and see what that does.

xfwm4 is actually the best of the few i've experienced, and xfce is easily my favorite DE, i just get bored and have to try to make everything *&#8203;better.*  first distro was mint and i loved it until i saw debian, but debian ran very poorly (i think it was 7.8 using gnome) on this machine, so i looked into debian based lightweight distros and found solydx which was my favorite for a few months, but it struggled to run even basic games.  then i tried debian with xfce which was terrible, and now i'm nestled firmly in xubuntus warm pillowy bosom.  for now.

---

### Post by vasa1 on 2015-08-14
This old thread may interest you: [Fluxbox vs Openbox vs Blackbox]("http://ubuntuforums.org/showthread.php?t=819607")

---

### Post by don_mularz on 2015-08-14
oh that's excellent, i thought black/flux were based off of open lol

---

### Post by vasa1 on 2015-08-14
> **don_mularz said:**
> oh that's excellent, i thought black/flux were based off of open lol

Well, all the best in your adventure of finding something that suits you. I went with Lubuntu after trying out Unity and Xubuntu. Then, [I tried the Openbox session of Lubuntu]("http://ubuntuforums.org/showthread.php?t=2173126") and stayed with it since. But then I don't play games or use programs requiring heavy graphics.

---

### Post by don_mularz on 2015-08-14
oh i forgot lxde, i really liked that one a lot too but it was actually little bit too lightweight for my purposes, this machine is about 60% work and 40% very light gaming.  if it was straight work (mainly just libre base for customer records) i'd probably be using something small with lxde just because it was so responsive.  thanks for the info!

---

