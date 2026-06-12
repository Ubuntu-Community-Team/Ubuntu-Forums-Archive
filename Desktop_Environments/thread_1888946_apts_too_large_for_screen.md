---
title: "apts too large for screen"
date: 2011-11-30
forum: Desktop Environments
---

### Post by jlh68 on 2011-11-30
I am using Unity (Ubuntu 11.10) on my Netbook and all of the windows are too long for my screen, so I cannot check the "save" or other command at the bottom of the screen.

I need to shrink the vertical size of my applications so I can see the bottom and any command boxes located there.  I cannot even grabe the lower right corner and resize..

I am using an Acer ONE 8.9" Netbook.(1024 X 600).  Ubuntu 11.10 32bit

How do I make it work?

---

### Post by mcduck on 2011-11-30
Hold down the Alt key, and use left mouse button to move the window from any point inside it (as opposed to just the titlebar) or middle mmouse button to resize it.

The Alt-left button to move the window upwards is in most cases the only option, though, as many programs simply can't be resized smaller than a certain size and your vertical resolution really is rather low.

---

### Post by ajgreeny on 2011-12-01
> **mcduck said:**
> The Alt-left button to move the window upwards is in most cases the only option, though, as many programs simply can't be resized smaller than a certain size and your vertical resolution really is rather low.
Whilst I agree with that comment, it is a very common resolution for smaller screen, 10.1" netbooks, and it seems strange that unity can apparently not handle the screens for which, I feel, its layout is most appropriate, ie netbooks.

---

### Post by mcduck on 2011-12-01
> **ajgreeny said:**
> Whilst I agree with that comment, it is a very common resolution for smaller screen, 10.1" netbooks, and it seems strange that unity can apparently not handle the screens for which, I feel, its layout is most appropriate, ie netbooks.

It's in no way related to Unity. It's just a question of how the *application itself* has defined it's layout, and how much space the application widgets (buttons, text fields etc) it uses require.

Most applications weren't developed with netbooks in mind, keep in mind that netbooks are still relatively new thing (at least on the scale of time used in program development) and resolutions that small haven't been common on desktop systems for ages so most developers had already stopped considerng them when building their user interfaces.

---

### Post by ajgreeny on 2011-12-01
> **mcduck said:**
> It's in no way related to Unity. It's just a question of how the *application itself* has defined it's layout, and how much space the application widgets (buttons, text fields etc) it uses require.

Most applications weren't developed with netbooks in mind, keep in mind that netbooks are still relatively new thing (at least on the scale of time used in program development) and resolutions that small haven't been common on desktop systems for ages so most developers had already stopped considerng them when building their user interfaces.
A good point.

I'm afraid my dislike of unity got the better of me for a few minutes!

---

### Post by mcduck on 2011-12-01
One thing you could do, if you haven't done it already, is setting smaller font sizes. That should save a bit of screen space. You can do that using the [Gnome Tweak Tool]("apt:gnome-tweak-tool").

Disabling menu icons and setting icon sizes to small where ever possible helps a bit. There used to be gconf keys for those options in Gnome 2, but I'm not sure if Gnome 3 has any similar options.

Using a theme with a tighter layout and less padding on widgets would help as well, but I don't think I've seen any such themes for GTK3 yet. You could of course search [gnome-look.org]("http://gnome-look.org") in case you find one.

If I had a netbook I'd probably use Openbox on it to get as much screen space as possible and to minimize the need to use the mouse/touchpad as those tend to be pretty bad on most netbooks. But Openbox requires quite a bit of configuration by hand so unless you are comfortable with text-based configuration files and such things it might not be an option.

..so, in the end, it's pretty much just a question of moving the windows around with the Alt shortcut to access the parts that don't fit on the screen. And of course you could try replacing applications with ones that work better on the smaller screen to make the daily use more comfortable.

---

### Post by billstei on 2011-12-02
You may want to try this: Run CompizConfig Settings Manager, under General --> General Options (a button) --> Desktop Size tab, set Horizontal and Vertical Virtual Size(s) to 1.  Note that this is not the same as the number of desktops, and I suspect that (some) applications attempt to use some/all of that virtual "screen" size.  I had several applications placing windows completely/partially off screen because they thought it was fair game to do so.

---

### Post by Plattnum on 2011-12-22
> **mcduck said:**
> It's in no way related to Unity. It's just a question of how the *application itself* has defined it's layout, and how much space the application widgets (buttons, text fields etc) it uses require.


I have found this problem does not occur when using plasma, gnome 3, gnome classic, or even Unity 2D. This makes me think that it is a problem with Unity.

---

### Post by mcduck on 2011-12-22
> **Plattnum said:**
> I have found this problem does not occur when using plasma, gnome 3, gnome classic, or even Unity 2D. This makes me think that it is a problem with Unity.

Unity has absolutely no control over what happens inside a window. That's purely up to the application itself, and the toolkit it uses.

(Unity is pretty much just a Compiz plugin giving you a pair of panels and some keyboard shortcuts, the desktop environment you are using is still Gnome 3, and the apps use the same GTK3 themes they use in Gnome Shell or Gnome Classic.)

---

