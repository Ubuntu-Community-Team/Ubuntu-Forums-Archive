---
title: "Building a ubuntu kiosk for university"
date: 2012-08-02
forum: Desktop Environments
---

### Post by TheOriginalPol on 2012-08-02
Alright all you brilliant individuals and shining minds, here's my stitch.

I work for Appstate university, in IT. Right now my boss has got me on a fun project to pull this old thing:



[IMG]http://i1208.photobucket.com/albums/cc379/theoriginalpol-/IMG_0644.jpg[/IMG]



...out of the storage room, blow off the dust, and get it up and running again. The lower screen is a capacitive, while the upper is of course just a screen -- both of which are connected to a tower that is nested in the back. Ultimately, they want the lower screen to host a web browser for public use (as pictured), while the upper screen scrolls through a variety of photos (also pictured, although they'll probably be more education-related).

I've tried a number of methods to get this working.

I've got 12.04 x86_64 going on an upgraded Optiplex 745, with a Radeon HD 2400 XT for dual-monitor support. I'm working with chromium and feh for the desired tasks. Ultimately I think the best solution would be to get the two monitors on separate X screens/viewports, and then use the following entries (or similar) as startup scripts:

```
/usr/bin/chromium-browser %U
```
  — which has already been configured for kiosk mode

```
DISPLAY=":0.1" feh --fullscreen --zoom --hide-pointer --image-bg black --no-menus --quiet --slideshow-delay 7 '/home/kioskuser/Pictures/'
```
  — which will start feh going, with the appropriate settings, in the second monitor up top

I tried the open source ATI driver first but it proved too hard to 'control' (and I could never get the xorg.conf to generate correctly). fglrx proved better, and I was able to switch mode in the control panel to Multi-desktop, so that I am now *this* close to getting it working. However there are still a few stupidly frustrating issues I'm running into:

  > the "DISPLAY=:*,*" modifier does NOT work as a startup script — even when executed as a terminal application:
```
Failed to execute child process "DISPLAY=:0,1" (No such file or directory)
```
When executed normally from a term window, it runs just fine.

  > whenever the (or any) account is logged out and back in again, an extra set of "default" gnome desktop panels and applets is added. This results in, after a few reboots, three or four panels stacked in a row on both the top and bottom, and many duplicates of Application menus, volume icons, etc squashed up against one another. This happens for EVERY user, and happens ONLY when Catalyst is configured for multi-desktop mode. 

 > I've also got the white desktop background on the second monitor, but I don't really care about that since the slideshow will be going fullscreen over it.


Sorry for the novel, but that's about it. I'm open to any suggestions, whether it's fixes for the above issues or completely different methods. Any insight is appreciated!

---

### Post by TheOriginalPol on 2012-08-02
Well for anyone who cares, here's an update. Figured out the DISPLAY=":*.*" issue &#8212; by putting the command into a bash shell and having THAT executed at login, I am able to get the slideshow to automatically load perfectly.

Now the ONLY thing still giving me issues is the constant panel/applet creation issue. It's as if gnome always thinks that it is the first time I am logging into this account, and is creating a new set of default panels and applets for me. Very annoying. Please advise.

---

