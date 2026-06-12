---
title: "dpi madness (xorg.log v. xdpyinfo)"
date: 2010-06-25
forum: Desktop Environments
---

### Post by awry on 2010-06-25
I'm struggling to figure out the "right" dpi settings for my kubuntu setup. Currently ubuntu-karmic, kde-4.4.2, linux-2.6.33.2, and the new open source radeon drivers.

I have a ThinkPad T400 with a 1440x900 14.1" display. That gives the display panel a resolution of 120dpi (see [http://directedge.us/node/36](http://directedge.us/node/36)).

'xdpyinfo | grep resolution' properly reports a resolution of 120x120 dpi.

However, 'grep DPI /var/log/Xorg.0.log' returns '(==) RADEON(0): DPI set to (96, 96)'.

I initially had my KDE settings set to 96x96 dpi, as this "feels" more "right" to me. When I set KDE to 120x120, 8pt text seems pretty big, and the fonts in my gtk apps go crazy-huge.

OTOH, a 72 point font should always be 1 inch at the proper resolution, and that is about spot-on at KDE's 120dpi setting (at least in native kde/qt apps; gtk is another story).

I just want to use my display at its native resolution and have it look good all the way around. :-)

Can anyone explain why radeon is logging 96x96 dpi to xorg.log, when the display is clearly 120dpi? I'm currently running without an xorg.conf. Is there an option to force dpi that I should add there?

---

### Post by Zorael on 2010-06-26
In my eyes fonts should always be in the de-facto standard of 96 dpi, regardless of physical screen size.

On one hand you have the ideology where fonts should be displayed in a dpi deemed "appropriate" for your screen, so that text in size 10 is the same physical size (millimeters) on your screen as it is on any and all others. This can make fonts mismatch graphics, such as if a menu doesn't expect a bit of text to be as wide as your dpi setting makes it. I imagine that extreme screen sizes (very large or very small) would do better with this approach.

The other ideology is to keep pixel sizes as they are by clamping dpi to a given value, traditionally 96. Obviously this makes the "physical" size of a font vary between screens, while they retain the same pixel dimensions.

I think what's happening here is a clash between the two ideologies. xdpyinfo looks at your reported screen dimensions and calculates that you want 120 dpi, but your driver looks to skip all that and just set it to 96.

You can set a global dpi for the entire X session if you add a parameter to the command that starts the actual server. In **/etc/kde4/kdm/kdmrc**, find the following tidbit and add the highlighted part.
```
ServerArgsLocal=-br -nolisten tcp **[color=green]-dpi 96[/color]**
```
You'll need to restart X completely after this, which a simple login/logout doesn't do (unless you've set TerminateServer in kdmrc to true). So save stuff and then restart **kdm**.
```
$ sudo restart kdm
```
Alternatively, reboot.

---

### Post by elnur on 2012-03-31
> **Zorael said:**
> 
You can set a global dpi for the entire X session if you add a parameter to the command that starts the actual server. In **/etc/kde4/kdm/kdmrc**, find the following tidbit and add the highlighted part.
```
ServerArgsLocal=-br -nolisten tcp **[color=green]-dpi 96[/color]**
```
You'll need to restart X completely after this, which a simple login/logout doesn't do (unless you've set TerminateServer in kdmrc to true). So save stuff and then restart **kdm**.
```
$ sudo restart kdm
```
Alternatively, reboot.

Oh, man, thank you so much!

---

### Post by elnur on 2012-10-19
> **Zorael said:**
> 
You can set a global dpi for the entire X session if you add a parameter to the command that starts the actual server. In **/etc/kde4/kdm/kdmrc**, find the following tidbit and add the highlighted part.
```
ServerArgsLocal=-br -nolisten tcp **[color=green]-dpi 96[/color]**
```
You'll need to restart X completely after this, which a simple login/logout doesn't do (unless you've set TerminateServer in kdmrc to true). So save stuff and then restart **kdm**.
```
$ sudo restart kdm
```
Alternatively, reboot.

How can I do the same in Kubuntu 12.10?

---

