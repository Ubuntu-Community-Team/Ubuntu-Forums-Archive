---
title: "Compiz: change desktop using mouse wheel over the viewport switcher"
date: 2009-05-25
forum: Desktop Environments
---

### Post by infinito on 2009-05-25
Hello,

I've never used Compiz before Jaunty, so I have a question. Using Metacity I can switch from one desktop to another scrolling the mouse wheel over the viewport switcher, but in Compiz I can only get that behaviour if I scroll the mousewheel over the desktop.

Is there any way to get the old behaviour on Compiz?

Thanks in advance!

---

### Post by cmost on 2009-05-25
I actually prefer the Compiz way myself.  I think you might too, if you get used to it.  ;)  Have you tried playing around with the settings in the 'Viewport Switcher' applet available in CCSM (Compiz Settings Manager?)  It's possible you can emulate the old behavior somewhat by customizing the settings.

---

### Post by infinito on 2009-05-26
Well, minimizing windows to change desktops is not an option for me. I like the old behaviour, because i think it's easier and faster...

---

### Post by nanderv on 2009-05-26
Can't you just use CTRL-ALT-arrow key. That seems to be much faster to me. Or you could just click on the viewport you want to go to.

---

### Post by xMarine73 on 2009-05-26
> **nanderv said:**
> Can't you just use CTRL-ALT-arrow key. That seems to be much faster to me. Or you could just click on the viewport you want to go to.

I actually set mine up to use CTRL-ALT-Mouse4/Mouse5 (down/up on the mouse wheel).  This changes desktops no matter what I'm doing without having to minimize anything.

---

### Post by infinito on 2009-05-27
Well, I know there are other options, but I do like the old behaviour... Any way, the Ctrl+Alt+Wheel option doesn't work if you're over Firefox, so....

---

### Post by pgn674 on 2009-07-07
This might start you in the right direction. In CompizConfig Settings Manager, go to Desktop > Desktop Wall > Bindings > Move Within Wall, and give the mouse's Move Left and Move Right options some bindings. My mouse's wheel rocks left and right, so I mapped those to these. It works no matter where the mouse is hovering, so it would break your scrolling in any application if you map it to scrolling.

BTW, I used imwheel -c in Terminal to figure out which mouse buttons were what numbers.

---

### Post by Pogeymanz on 2009-07-07
The short answer is no. Here is the 'why':

gnome-panel's workspace switcher is told to switch desktops when the mouse scrolls over it. Since you are running Compiz, you have multiple viewports and only one desktop, so the switcher can't do anything when you scroll over it.

The only way around this would be to edit the source code of the gnome-panel desktop switcher.

Compiz has its ups and downs, I guess. :)

---

### Post by vgrisham on 2009-11-25
> **infinito said:**
> Hello,

I've never used Compiz before Jaunty, so I have a question. Using Metacity I can switch from one desktop to another scrolling the mouse wheel over the viewport switcher, but in Compiz I can only get that behaviour if I scroll the mousewheel over the desktop.

Is there any way to get the old behaviour on Compiz?

Thanks in advance!

Yes you can. See [this]("http://video.aol.co.uk/video-detail/viewport-switcher-ccsm-ubuntu-910/2292722427") video.

---

### Post by derelict888 on 2010-02-02
Glad I stumbled onto this thread, I love switch between desktops with the mouse wheel. :popcorn:

---

### Post by pearjam on 2010-10-04
Hello there... This is TOTALLY POSSIBLE!!

Kinda freaked when I was reading the thread - this is how the default Compiz used to be a few versions back..

Open the Compiz Settings Manager.

Click on Desktop > Viewport Switcher.

In the Viewport Switcher settings, click on the "Desktop-based Viewport Switching" tab.

Edit "View Next" by clicking 'disabled' or the Pencil icon. Check the Enabled box, and switch the button number to be Button5. Hit 'Ok'.

Edit "View Prev" by clicking 'disabled' or the Pencil icon. Check the Enabled box, and switch the button number to be Button4. Hit 'Ok'.

That's it!

(Make sure 'viewport switcher' is checked to be enabled.)

:)

---

### Post by Freaky#Funga on 2010-10-13
> **pearjam said:**
> Hello there... This is TOTALLY POSSIBLE!!

Kinda freaked when I was reading the thread - this is how the default Compiz used to be a few versions back..

Open the Compiz Settings Manager.

Click on Desktop > Viewport Switcher.

In the Viewport Switcher settings, click on the "Desktop-based Viewport Switching" tab.

Edit "View Next" by clicking 'disabled' or the Pencil icon. Check the Enabled box, and switch the button number to be Button5. Hit 'Ok'.

Edit "View Prev" by clicking 'disabled' or the Pencil icon. Check the Enabled box, and switch the button number to be Button4. Hit 'Ok'.

That's it!

(Make sure 'viewport switcher' is checked to be enabled.)

:)

Well... I'm sorry to say that, but this is not working for me. Ubuntu 10.04 here. (Compiz is enabled)

An screenshot attached.

---

### Post by 3Miro on 2010-10-13
I always enjoy a good piece of necromancy, especially when it is actually with a valid comment.

The settings seem correct and you are sure compiz is running (System -> Admin -> System Monitor should list a compiz process working). Can you change other settings in ccsm? Your mouse has to be pointing at an empty place on your desktop, do you have that?

I have experienced a bug on my desktop with nvidia. If I move the mouse all the way to the left of the screen and then back a little to try and switch the desktops, it will not work. It will not work, until I move the mouse back over an open window and then back over the desktop. Then it works.

I hope this makes some sense.

---

### Post by zuerston on 2010-10-13
> **derelict888 said:**
> Glad I stumbled onto this thread, I love switch between desktops with the mouse wheel. :popcorn:

Have you tried Expo yet?

---

### Post by Freaky#Funga on 2010-10-14
> **3Miro said:**
> I always enjoy a good piece of necromancy, especially when it is actually with a valid comment.

The settings seem correct and you are sure compiz is running (System -> Admin -> System Monitor should list a compiz process working). Can you change other settings in ccsm? Your mouse has to be pointing at an empty place on your desktop, do you have that?

I have experienced a bug on my desktop with nvidia. If I move the mouse all the way to the left of the screen and then back a little to try and switch the desktops, it will not work. It will not work, until I move the mouse back over an open window and then back over the desktop. Then it works.

I hope this makes some sense.

OOOH. I misunderstood Your post. When I point on empty space on desktop, it works fine. 
What I want is that there is a little applet called "workspace switcher" sitting in right bottom corner of gnome panel. When compiz is disabled, You can point mouse on it and switch to another desktop using mouse wheel. With compiz enabled nothing happens. 
Pogeymanz's response makes sense then.

---

### Post by pearjam on 2010-10-20
Yep - after using the instructions above to enable switching desktops with the mouse wheel - you have to have the mouse over an empty spot on the desktop (no windows beneath the mouse - just your desktop background) - then spin the wheel...

I think it's always been this way, but I don't honestly remember. :)

The 'workspace switcher' can also be added to a panel (as noted). I use both... lol

Glad it's working!

---

### Post by southernman on 2010-11-18
> **pearjam said:**
> Hello there... This is TOTALLY POSSIBLE!!

Kinda freaked when I was reading the thread - this is how the default Compiz used to be a few versions back..

Open the Compiz Settings Manager.

Click on Desktop > Viewport Switcher.

In the Viewport Switcher settings, click on the "Desktop-based Viewport Switching" tab.

Edit "View Next" by clicking 'disabled' or the Pencil icon. Check the Enabled box, and switch the button number to be Button5. Hit 'Ok'.

Edit "View Prev" by clicking 'disabled' or the Pencil icon. Check the Enabled box, and switch the button number to be Button4. Hit 'Ok'.

That's it!

(Make sure 'viewport switcher' is checked to be enabled.)

:)

Thanks. Works perfectly for me.

First time caller to the compiz hour. :P

---

