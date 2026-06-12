---
title: "Desktop went away, how can I get it back?!"
date: 2009-04-15
forum: General Help
---

### Post by tippyaloishes on 2009-04-15
I was installing a new theme that I downloaded, and then the light on the tower kept flashing but my screen was froze. I waited about 10 mins. and then turned it off and back on. And when I tried to login I get a beige screen with a box in the upper left corner, my mouse pointer shows up and that's about it (except if I put the pointer over the box in the corner then the pointer turns into a line). I can still use my pc but under a different username and limited access. How can I get my main desktop up and running again? 
I tried the failsafe terminal and ran 'sudo apt-get install ubuntu-desktop' and was told everything is current. I also tried 'startx' and was told that I'm not authorized to use startx. Can someone please help? Oh and I'm using ubuntu 8.04 I think...

---

### Post by sowelie on 2009-04-15
It sounds like you may be having hardware issues.  My guess would be your graphics card.  What video card do you have and what drivers are you using?  What you may want to do is re-set up X.  So, when you get to the recover shell, do the following:

```
cd /etc/X11
cp xorg.conf xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg
sudo shutdown -r now

```

That'll reset your video drivers (and back up your old configuration).

---

### Post by tippyaloishes on 2009-04-16
Thank you for your reply. But I don't rightly know what a video card is, also to be honest I don't know what a driver is or for.I don't know much about PCs I only tried those other steps cause I saw them in other posts and I hoped that something would work. Can you tell me how to do what you just said but break it down in steps a little please? Thank you again for any help that you can give....

---

### Post by tippyaloishes on 2009-04-16
I put in a terminal what you said and when I got to 'sudo dpkg-reconfigure xserver-xorg' a (configure xserver xorg) messsage was displayed that said mainly that it wants to "use kernel framebuffer device interface'... Yes or No? I didn't do it cause I don't know what it does. The message said in theory that it could work. What exactly will happen if I run the configure thing? Will I get my desktop back?

---

