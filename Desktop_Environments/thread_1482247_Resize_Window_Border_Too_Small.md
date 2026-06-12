---
title: "Resize Window Border Too Small"
date: 2010-05-13
forum: Desktop Environments
---

### Post by Apv507 on 2010-05-13
This isn't a HUGE deal, just a little annoying. When I move the cursor to the edge of a window to resize it, i only get the resize arrow in a very small area and it takes me several tries to get it just right. Is there anyway to broaden the resize area threshold or something?

---

### Post by FootySr on 2010-05-13
Agreed... I love the Ambiance Theme I just wish it had a boarder more like the Crux windows.

That said, I'll usually grab the window from the bottom where there is a slightly larger boarder and bigger sweet spot.

---

### Post by mcduck on 2010-05-13
> **Apv507 said:**
> This isn't a HUGE deal, just a little annoying. When I move the cursor to the edge of a window to resize it, i only get the resize arrow in a very small area and it takes me several tries to get it just right. Is there anyway to broaden the resize area threshold or something?

You'll just have to use a window border theme that has wider borders.

..or hold down the Alt key and use the middle mouse button to resize the window from anywhere inside the window. ;)


(Also note that many themes have a bit extra border at the bottom, so resizing is easier if you grab the window from bottom right or bottom left corner.. Actually it's even quite common for the bottom right corner to have a specific larger area for this purpose.)

---

### Post by Apv507 on 2010-05-13
Thanks guys, I assumed it was a theme by theme thing. I'm using Smoothie, not because I'm a mac fan I just love the green yellow and red buttons, it feels clean. I ended up making CTRL+` the shortcut key for resizing, although its just as easy as right clicking on the title bar at the top. Compiz maximumize also is handy for resizing windows.

---

### Post by FootySr on 2010-05-13
> **mcduck said:**
> 

..or hold down the Alt key and use the middle mouse button to resize the window from anywhere inside the window. ;)



Ohhhh... I like! Thanks! :)

---

### Post by Apv507 on 2010-05-14
Yea, thats a very handy trick thanks guys!

---

### Post by dess on 2010-06-03
> **mcduck said:**
> ..or hold down the Alt key and use the middle mouse button to resize the window from anywhere inside the window. ;)
Very good solution. Much better than classic border-based approach. Thanks.

---

### Post by MissEileen on 2010-11-27
hmm, not very comfortable for a laptop touchpad though... :-k

---

### Post by light-vessel on 2011-01-01
This is one of the few things I find really annoying in Ubuntu. Thanks  for the tip about using the middle button and alt but it's not always  practical. I was hoping there would be a massive long thread full of  people complaining about it - enough to convince the programmers that  that's not the way we like it. Alas most people don't seem to be as  bothered about it as me.

The other thing that annoys me is having to accept script from google-analytics just to post on this forum.

---

### Post by Bimps on 2011-01-13
[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/160311](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/160311)

This bug is really annoying. Glad they're working on it already. You can fix it yourself in the time being, like the instructions on the launchpad page state. If you're not using Ambiance, change the path accordingly to the theme you're using and edit the .xml file:

Workaround:  Edit /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml.  Set the following values in **frame_geometry_****normal** as desired:
         <distance name="left_width" value="3"/>
        <distance name="right_width" value="3"/>
        <distance name="bottom_height" value="3"/>

---

### Post by jackbuntu2011 on 2011-01-13
Adding a solid 10 to the bottom is comfy. This is a problem of serious magnitude though in my opinion.

---

### Post by andrek on 2011-01-13
Great news - fixed in Natty. Each window gets a grip now, take a look - 

[[img]http://a.imagehost.org/t/0442/Screenshot.jpg[/img]](http://a.imagehost.org/0442/Screenshot.png)

It's an early progress, it needs some fixes though - see Chromium and how it handles semi-transparent windows (terminal).

Also it's not the theme that i'm using, the same happens on Ambiance/Radiance.

---

### Post by vandamme on 2011-01-14
I have a middle mouse button?...Oh yeah, the wheel! <alt> click, and resiziness!! Sweet :popcorn:

---

### Post by vandamme on 2011-01-14
I have a middle mouse button?...Oh yeah, the wheel! <alt> click, and resiziness!! Sweet :popcorn:

---

### Post by Faz1 on 2011-03-13
> **Bimps said:**
> [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/160311](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/160311)

This bug is really annoying. Glad they're working on it already. You can fix it yourself in the time being, like the instructions on the launchpad page state. If you're not using Ambiance, change the path accordingly to the theme you're using and edit the .xml file:

Workaround:  Edit /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml.  Set the following values in **frame_geometry_****normal** as desired:
         <distance name="left_width" value="3"/>
        <distance name="right_width" value="3"/>
        <distance name="bottom_height" value="3"/>

 Thank you Bimps! :D

---

### Post by bpsanborn on 2011-06-13
[andrek]("http://ubuntuforums.org/member.php?u=147551")

I am running Natty 11.04.  And I am a Windows geek trying to explore Linux.  Good so far.

If you look at your desktop photo and focus in on the Firefox window you will see the problem that I am trying solve.  The right bottom corner resizing "gripper" is overlaying the "scroll down" button.  It is very annoying to try and land the mouse on the tiny piece of of the scrollbar left exposed.   I believe this effects all apps that don't use the Unity skinny scrollbars.  I have deleted the skinny overlay scrollbars but this little affectation in the right lower corner is a bug.  You can make it less annoying by going into the Gnome Color Chooser tool and making the scroll buttons bigger.


Brian

---

### Post by prosist on 2011-12-05
> **Faz1 said:**
> Thank you Bimps! :D

thanks a lot!

---

### Post by prosist on 2011-12-05
> **Bimps said:**
> [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/160311](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/160311)

This bug is really annoying. Glad they're working on it already. You can fix it yourself in the time being, like the instructions on the launchpad page state. If you're not using Ambiance, change the path accordingly to the theme you're using and edit the .xml file:

Workaround:  Edit /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml.  Set the following values in **frame_geometry_****normal** as desired:
         <distance name="left_width" value="3"/>
        <distance name="right_width" value="3"/>
        <distance name="bottom_height" value="3"/>

thanks a lot

---

### Post by MarjaE on 2011-12-07
> **mcduck said:**
> You'll just have to use a window border theme that has wider borders.

..or hold down the Alt key and use the middle mouse button to resize the window from anywhere inside the window. ;)


(Also note that many themes have a bit extra border at the bottom, so resizing is easier if you grab the window from bottom right or bottom left corner.. Actually it's even quite common for the bottom right corner to have a specific larger area for this purpose.)

The narrow resize bars are an accessibility problem, and the middle-mouse-button solution can be an accessibility problem. Because of the perpetual pain in my outer fingers, I've switched back from the mouse to the touchpad, and it's pretty difficult to press both touchpad buttons and the touchpad itself at the same time. I don't have the dexterity to use touchpad gestures without everything going haywire either.

P.S. And I'm using Natty, it's not fixed here.

---

### Post by mcduck on 2011-12-07
> **MarjaE said:**
> The narrow resize bars are an accessibility problem, and the middle-mouse-button solution can be an accessibility problem. Because of the perpetual pain in my outer fingers, I've switched back from the mouse to the touchpad, and it's pretty difficult to press both touchpad buttons and the touchpad itself at the same time. I don't have the dexterity to use touchpad gestures without everything going haywire either.

P.S. And I'm using Natty, it's not fixed here.

There are also other keyboard shortcuts for window resizing, and also there's a Compiz plugin installed by default specifically to make window reszing easier with touchpads and for people who might otherwise have problems tarhgeting the window borders or reize area. (At least in Gnome2 Alt-F8 enabled window resize, and you'll have to check yourself if the Compiz plugin is enabled by default and what shortcuts it uses)

Gnome (even with Unity) is pretty much completely usable by keyboard only so it's just a question of learning the shortcuts for things you need and you won't even need the touchpad any more... :)

---

### Post by MarjaE on 2011-12-07
> **mcduck said:**
> Gnome (even with Unity) is pretty much completely usable by keyboard only so it's just a question of learning the shortcuts for things you need and you won't even need the touchpad any more... :)

No, Gnome 2 is still largely accessible with mouse and/or trackpad, and doesn't force us to use the keyboard for everything. Although I have yet to see any practical way to type with mouse and/or trackpad. I wish there were, typing HURTS.

---

### Post by thaelim on 2011-12-07
In Gnome Shell, the area of the window where you can resize it from includes the drop shadow, making it FAR easier to use the mouse/touchpad to resize. I'm surprised the Compiz guys have not yet thought of this.

---

### Post by Jetro on 2012-11-03
> **Bimps said:**
> [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/160311](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/160311)

This bug is really annoying. Glad they're working on it already. You can fix it yourself in the time being, like the instructions on the launchpad page state. If you're not using Ambiance, change the path accordingly to the theme you're using and edit the .xml file:

Workaround:  Edit /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml.  Set the following values in **frame_geometry_****normal** as desired:
         <distance name="left_width" value="3"/>
        <distance name="right_width" value="3"/>
        <distance name="bottom_height" value="3"/>
That's bloody brilliant. Thanks. Although it doesn't seem to be able to do anything for the top side, so the 'window' there is as small as ever. For the life of me I can't figure out why it isn't put at 6 or something like that as standard. It doesn't break any functionality but it adds tons. Trying to resize a window from the top left (as, surprising as it sounds, many would like to do) was a pain before this.

---

### Post by noisygecko on 2012-11-07
Wow, this is the first time anyone has ever given a reasonable solution to this stupid bug in the default theme on recent Ubuntu releases.  I can't believe I have to resort to a crazy hack like this, but it works.

Thank you!

I changed the values and now I can resize windows without cursing.  (As much.)

---

