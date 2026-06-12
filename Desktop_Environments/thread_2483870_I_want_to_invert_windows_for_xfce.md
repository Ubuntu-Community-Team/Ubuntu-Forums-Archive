---
title: "I want to invert windows for xfce"
date: 2023-02-11
forum: Desktop Environments
---

### Post by ant2ne on 2023-02-11
compiz had a feature where you could target any window in hit a hot key and invert it. It was great. Is there such a utility for xfce xubuntu?

---

### Post by TheFu on 2023-02-13
> **ant2ne said:**
> compiz had a feature where you could target any window in hit a hot key and invert it. It was great. Is there such a utility for xfce xubuntu?

That's a compositor.  So, you'd need to look for xubuntu compositors.   Maybe you can add a compositor with the feature you seek, perhaps. [https://docs.xubuntu.org/current/user/C/settings-preferences.html#customizing-appearance](https://docs.xubuntu.org/current/user/C/settings-preferences.html#customizing-appearance) at the very bottom of this page says a bit about it.

It appears that the package is available  [https://packages.ubuntu.com/search?keywords=compiz](https://packages.ubuntu.com/search?keywords=compiz)

I tried to add it to an 18.04 desktop here that isn't using Gnome and it turned out badly.  That was slightly unexpected. I remember compiz working with a few different WMs, just not the one I use.  YMMV.  When I ran it with --replace, it kicked me out, closing all my GUI windows.  I should have expected it.  Compiz wasn't listed in the available GUI versions on the login page.  I had Mate installed ... but that didn't work with Compiz, so it seems. 

I'll spin up an xubuntu 22.04 shortly inside a VM and see if it works any better there.  Virtual machines didn't used to handle compositors at all, but perhaps with the much improved graphics, they will now?  Give me a few minutes.  I'm personally curious.

Update:
Ok, that took longer than I expected.  XFCE has a built-in compositor.  In the "Window Manager Tweaks" applet, there's a "Compositor" tab where the available options exist.  I spent a little time playing with the opacity settings and learning how XFCE has changed since the time when I used it full-time.  

I didn't find anything related to inverting windows ... is that flipping a window vertically or horizontally?  I assume all the text is flipped to need a mirror to read?  If you are just trying to have the active window much more visible than other windows, the opacity settings can do that easily.  I have my focus setup to follow the mouse, never raise a window, and only if I click on a window border does a window get raised.  That's how I was taught X/Windows should work in the lab where I worked in my younger days.

I did get compton to install. It doesn't like my qxl GPU drivers, but it does seem to be working except where Firefox's window doesn't display anything inside it.
```
  sudo apt install compton
  xfconf-query -c xfwm4 -p /general/use_compositing -s false 
  cd
  mkdir .config/picom
  vi  .config/picom/picom.conf
  vi ~/.config/autostart/picom.desktop 

```
For more details: [https://wiki.manjaro.org/index.php/Using_Compton_for_a_tear-free_experience_in_Xfce](https://wiki.manjaro.org/index.php/Using_Compton_for_a_tear-free_experience_in_Xfce) ... obviously, translate from Manjaro to Ubuntu style commands where necessary.

Thanks for the question.  It confirms that my WM choice, fvwm, is the right one for me, still, after all these years.

---

### Post by #&amp;thj^% on 2023-02-13
I'm not sure I fully understand your define of "invert", so just disregard if this is not a help for you:
```
xdotool help
Available commands:
  getactivewindow
  getwindowfocus
  getwindowname
  getwindowpid
  getwindowgeometry
  getdisplaygeometry
  search
  selectwindow
  help
  version
  behave
  behave_screen_edge
  click
  getmouselocation
  key
  keydown
  keyup
  mousedown
  mousemove
  mousemove_relative
  mouseup
  set_window
  type
  windowactivate
  windowfocus
  windowkill
  windowclose
  windowmap
  windowminimize
  windowmove
  windowraise
  windowreparent
  windowsize
  windowunmap
  set_num_desktops
  get_num_desktops
  set_desktop
  get_desktop
  set_desktop_for_window
  get_desktop_for_window
  get_desktop_viewport
  set_desktop_viewport
  exec
  sleep

```
But I like this one below:
> **TheFu said:**
> 

I did get compton to install. It doesn't like my qxl GPU drivers, but it does seem to be working except where Firefox's window doesn't display anything inside it.
```
  sudo apt install compton
  xfconf-query -c xfwm4 -p /general/use_compositing -s false 
  cd
  mkdir .config/picom
  vi  .config/picom/picom.conf
  vi ~/.config/autostart/picom.desktop 

```
For more details: [https://wiki.manjaro.org/index.php/Using_Compton_for_a_tear-free_experience_in_Xfce](https://wiki.manjaro.org/index.php/Using_Compton_for_a_tear-free_experience_in_Xfce) ... obviously, translate from Manjaro to Ubuntu style commands where necessary.



all i had to run is:
```
xfconf-query -c xfwm4 -p /general/use_compositing -s false
xfconf-query -c xfwm4 -p /general/use_compositing -s true
```
I do use "xdotool" and xprop, once in a while I'll use Compton as well.

---

### Post by monkeybrain20122 on 2023-02-13
i think you can install compiz on xubunt, xfce is compatible with compiz. Just grab it from the repository.

---

### Post by TheFu on 2023-02-14
> **monkeybrain20122 said:**
> i think you can install compiz on xubunt, xfce is compatible with compiz. Just grab it from the repository.

It definitely installs - both  compiz and compton are in the repos, so we have a choice.

Just to clarify my test 22.04/22.10 systems are virtual machines, so they don't have a real GPU, which I'd expect compositors to really need.

---

### Post by mikodo on 2023-02-24
Hi,

  I use xcalib for inverting on my Xubuntu desktop. Maybe this might be helpful to you.       

Install: ```
sudo apt install xcalib
```      

Stick it in: Settings Manager > Keyboard > Application Shortcuts > Add > Shortcut Command > Command > 

```
xcalib -i -a
```  Key Presses = Super+X > Done. 

     I use Super+X for the key presses; you of course can use anything you like. Do it once for Invert, again and no Invert.

---

### Post by &amp;KyT$0P# on 2023-02-26
> **monkeybrain20122 said:**
> i think you can install compiz on xubunt, xfce is compatible with compiz. Just grab it from the repository.

+1, can confirm this, but getting it usably working for me required some configuring in CompizConfig Settings Manager **before** running the Terminal command to replace xfwm4 with Compiz -
```
compiz --replace & exit
```

I would suggest experimenting with this in a disposable environment before trying any of it on a production system.

---

