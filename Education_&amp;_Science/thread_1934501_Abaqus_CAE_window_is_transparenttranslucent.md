---
title: "Abaqus CAE window is transparent/translucent"
date: 2012-03-02
forum: Education &amp; Science
---

### Post by GenericPlayer on 2012-03-02
I've been using Abaqus for a while now but only just managed to get it installed on Ubuntu. My only warning during installation was that it could not find /lib/libc.so.6. 
 
Anyway when I launch Abaqus CAE the viewport looks fine but UI panes are transparent, allowing whatever is behind the CAE window to bleed through the display. The menus even bleed through each other. so it is difficult to use the UI. Here is a screenshot: 
 
[http://i278.photobucket.com/albums/kk109/hbadr/Screenshotat2012-03-02155656.png](http://i278.photobucket.com/albums/kk109/hbadr/Screenshotat2012-03-02155656.png)
 
As you can see, my terminal window is showing from behind the Abaqus UI, as are parts of my background image.
 
I would appreciate any ideas on getting rid of this problem.

---

### Post by GenericPlayer on 2012-03-03
I realized the screenshot link was faulty so I fixed it. 
 
With regards to the issue I am having, I also experience a crash whenever I try to open the materials window. The error says "ipc_connection failed"
 
When I get home I will try to turn off hardware acceleration. I was hoping that all that was required from my gfx was that it support opengl. I have a Geforce GTX 470. I know its not a workstation graphics card but its not like I will be doing any rendering in Abaqus.
 
I was curious if any Ubuntu Abaqus users use a graphicsConfig.env file and what kind of options typically go into it.

---

### Post by GenericPlayer on 2012-03-03
I discovered that the issues are being caused by compiz. I fixed it by setting the environment variable XLIB_SKIP_ARGB_VISUALS=1

I get two small phantom windows that obstruct the view somewhat, but that can be easily be solved by starting Abaqus in an unused workspace and then moving it to the workspace I want to use it in.

Next stop is installing torque and learning how to get Abaqus to work with a queue system!

---

### Post by caiuamelo on 2012-05-06
Solved this problem running ubuntu on classic no effects mode, thougth the problem is a conflict with Unity.

to run ubuntu on classic no effects mode:

$sudo apt-get install gnome-session-fallback

log out session, click on ubuntu icon, choose classic no effects and log in again.

---

