---
title: "nvidia and compiz"
date: 2008-01-10
forum: Desktop Effects &amp; Customization
---

### Post by giok13 on 2008-01-10
hi i satrted using compiz cause i saw this video [http://www.youtube.com/watch?v=ZD7QraljRfM](http://www.youtube.com/watch?v=ZD7QraljRfM)

and i want to make some off the stuff run on compiz. i want to make the cube tht he does, were he makes the windows popout the cube, and make the cube itself disapear and the whole thing he does with the cube. i also want to make a 3d desktop. and also is thr a theme like his  tht i can get, were it shows the top part of the screen looks like tht. and also wen he closes the window how does he make it do the color thing? 
thx

---

### Post by warbread on 2008-01-11
Ok....

I'll assume you're using Gutsy.  First, make sure your video card drivers are install.  Go to System -> Administration -> Restricted Drivers Manager.  Enable your video card, let it install and then reboot. 

 When you're back, you'll have to enable Compiz-Fusion.  Go to System -> Preferences -> Appearance.  You'll see a 'Desktop Effects' tab at the top.  Go to that and enable the highest level. 

 If that works, then you want to get the settings manager.  In synaptic, do a search for compizconfig-settings-manager  and install it.  

When that's done, go to System -> Preferences -> Advanced Desktop Settings.  There you will find lots of settings.  Enable Desktop Cube, Rotate Cube, etc.  Play around with it.  Just don't disable anything under the 'Windows Manager' section.  That will make things not work so good.

Here's a site with some pretty pictures of the steps up until now: [http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200]("http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200")

The next step is to install Emerald (this gets you the nice themes).  'sudo apt-get install emerald' will do just fine for the program, but you'll need to download themes from here [http://themes.beryl-project.org/]("http://themes.beryl-project.org/").

That should be it.  If you have any more problems, there are tons of posts here about Compiz-Fuzion and Emerald.

---

