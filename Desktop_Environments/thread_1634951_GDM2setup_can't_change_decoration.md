---
title: "GDM2setup: can't change decoration"
date: 2010-12-01
forum: Desktop Environments
---

### Post by Belgatom on 2010-12-01
Currently playing with Ubuntu 10.10 and installing the usual programs but one thing is bothering me. Previous versions of Ubuntu (last I tried was 9.04) have always had nice and configurable loginscreens.  This time however, I am not having so much success. After following the advice of downloading GDM2setup, I was able to change the background image. But I wanted to change the login to something darker. The white login screen looks so &#8230; white. Even using Gdm2setup &#8211; Decoration doesn&#8217;t make any difference in what I get on startup. Can anybody give me a hand? 

What I currently get is a white/grey square a nice computer icon and Username in black. I've seen a few tutorials on the net but further than change the background and icons, I can't see anyone change this to a darker background. Am I asking/expecting too much?

Among different tut, I tried this one ([http://www.n00bsonubuntu.net/content/how-change-login-screen-ubuntu-1010-maverick-meerkat](http://www.n00bsonubuntu.net/content/how-change-login-screen-ubuntu-1010-maverick-meerkat)) but can't seem to change the color of the login dialog. What's up with that?

---

### Post by Frogs Hair on 2010-12-01
When appearance preferences shows up like in the tutorial  ,  go to themes > customize > controls (select a control) > colors . You will then be able to change the colors of the login box if the control supports color change.

---

### Post by Belgatom on 2010-12-01
So I assume that this control does not allow colorchange.

How can I change the whole thing then? Is there no way to implement something like [these]("http://art.gnome.org/themes/gdm_greeter") on Gnome-art?  Change the "greeter" as it seems to be called.

---

### Post by Frogs Hair on 2010-12-01
The control will display a message when it doesn't allow color change. I used the tutorial a couple of times and works great for me. I'm afraid you can only change the color and not the style of the login box and I think the login screens @ the Gnome link are obsolete with the current Ubuntu releases .

---

### Post by the blackbull on 2010-12-01
I got to change the background image, the ubuntu logo and icons of the Maverick's gdm login screen. Here the steps:
1. Open a terminal
2. Type he following command:

sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/

3. Close your session. Then the Appearance properties dialog raises and there you can change the background image, the theme and icons. Close the dialog and restart.
4. Log in and delete the file at /usr/share/gdm/autostart/LoginWindow/ to avoid his execution everytime the pc starts.
Actually you can't change the full login theme.

---

