---
title: "Touch/Type + other tweaks and goodies for a touchscreen interface!"
date: 2011-02-09
forum: Desktop Environments
---

### Post by ninjaaron on 2011-02-09
Hey there. I didn't know where to post this, but anyway, I got a Dell Inspiron duo for Christmas, and I've been working at getting the most out of the tablet interface. This thread is for sharing what I've found, and hearing what other have found too.

I created a system of scripts that together I call the "Touch/Type" system. These scripts work to sync screen rotation (xrandr), onscreen keyboard (supports onboard and florence) and cursor visability (unclutter). It can also sync with gnome-do, but I imagine that I'm the only one interested in something like that.

Here it is in a tarball: [http://ubuntuone.com/p/cKL/](http://ubuntuone.com/p/cKL/) follow the instructions in 'setup' to get it working.

I made it because the auto-rotation with the accelerometer doesn't work on my computer, so I made a toggle button for it. Then I started looking for a way to hide my cursor when I was using the touch screen. Eventually, I realized that if I was using screen rotation, I would not be using the cursor, so I linked the two. I also realized that I would be in tablet mode, so I linked it to the onscreen keyboard as well.

Then I had a problem. When the screen would rotate, the onscreen keyboard would stay the same size, so I had to get that linked in too.

The end result was Touch/Type. It basically boils down to two buttons. One is rotation button. When you push it, it toggles between portrait and landscape orientations. It also kicks on "touch mode" if it was off. Touch mode activates the keyboard and hides the cursor. 

The other button is the Touch/Type button. In "type mode" moves the tablet in "touch mode" without rotating the screen. Touch it again, and it moves the screen to normal orientation, turns off the keyboard, and turns on the pointer.

Course, the keyboard is always resized to the screen rotation, whatever button might be pushed.

I tried to make the system as modular as possible so that it could easily be adapted to a system with an auto-rotation daemon or other configurations.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
There are other goodies in this tarball. One, I re-themed Onboard. Now it looks like this:
[IMG]http://i4.photobucket.com/albums/y124/ninjaaron_0/portrait.png[/IMG]
and rotated:
[IMG]http://i4.photobucket.com/albums/y124/ninjaaron_0/lanscape.png[/IMG]
You can turn off this theme, of course. You can also drop it's files in ~/.sok/layouts to use it without using Touch/Type. They are in the NotUgly folder.

In addition, I also made a Metacity theme with larger buttons that would be easier to touch because the duo has very small pixels, so the normal sized buttons were very difficult to touch. To use it, drop the "Big-Touch-Dark 2.0" folder into ~/.themes. Open the appearance preferences, click customize, go to the Window Border tab, and it will be there. you can see how it looks in the pics above.

There is also the backligher script, which I have on a button next to my systray. You can see it in this picture on the right side:
[IMG]http://i4.photobucket.com/albums/y124/ninjaaron_0/right-panel.png[/IMG]. 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Something not included in this tarball that anyone can do:
[IMG]http://i4.photobucket.com/albums/y124/ninjaaron_0/Launcher-layout.png[/IMG]
I turned my main menu into a pretty, touchable box of drawers.

To do this, right click on the software centre in the main menu. Then click Entire Menu>Add this as drawer to panel.  That only gets the applications menu in however. To add the System menu, you have to right click on the Control Center and do the same (you may have to enable this at the "edit menus" dialog). I made the places one myself by creating a new drawer and dragging in the folders manually. Then I took out any programs that I didn't think I would ever need while working as a tablet, consolidated some things, and added the real gnome menu on top in case I need it for anything.

At the bottom of the pic, you can also see where I have stowed my rotation an Touch/Type togglers. I'm also using a Docky dock with intelle-hide. Compiz expo corners also work great with a touch-screen. I have one do a window expo, and the other is a workspace expo.

So that's what I got.

What about you?

---

### Post by jdcnc on 2012-01-09
I have not been able to down load the tar ball. can you help me out. clicking on the link for the tatball results in a 404 error. I joined ubuntu 1 but it did not help.
 
Thanks.

---

### Post by spacestationspaz on 2012-08-28
Been following the main thread- what was the fix for the touchpad/touchscreen not rotating? I am flummoxed.

---

