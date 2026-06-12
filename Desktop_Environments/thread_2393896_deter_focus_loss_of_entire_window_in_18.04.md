---
title: "deter focus loss of entire window in 18.04"
date: 2018-06-09
forum: Desktop Environments
---

### Post by Claus7 on 2018-06-09
Hello,

having upgraded to gnome-flashback 18.04 from 16.04 I face a window focus problem:
While opening a window, for example tweaks, and then terminal, the tweaks window has lost focus in its entirety. In the old days, only the title bar of the unfocused windows was grayed out. Now, the entire window looses focus. 

Attached are two pictures with lost focus (unfocused) and normal focus (focused).

I was able to change preferences under tweaks->windows->window focus to no avail.
The same thing happens if I try to change ~/.config/openbox/lxde-rc.xml file, which I'm not sure that it does the work for ubuntu gnome.

Some changes I made were:
<focus>
  <focusNew>[COLOR="#00FFFF"]no[/COLOR]</focusNew>
  <!-- always try to focus new windows when they appear. other rules do
       apply -->
  <followMouse>no</followMouse>
  <!-- move focus to a window when you move the mouse into it -->
  <focusLast>[COLOR="#00FFFF"]no[/COLOR]</focusLast>

and adding towards the end:
<applications>

  <application class="*">
    <focus>no</focus>
  </application>

to no avail.

Also from ccsm and General Options-> Focus & Raise Behaviour toggling options does not change anything. 

Lubuntu and mate does not show such behaviour.

Any idea is more than welcome.

Regards!

---

### Post by Claus7 on 2018-06-09
Hello,

searching a little bit more I was able to find out that with the command:
> wmctrl -m
I get the following output:
> Name: Compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: ON
which means that the window manager I'm using is compiz, which means that I'm not using openbox window manager, as a result I should not bother with the lxde-rc.xml file. 

Also when I type the command:
> openbox --replace
I get:
> Command 'openbox' not found, but can be installed with:

sudo apt install openbox
Playing with ccsm I changed the Focus Prevention Level from Off to Very High. The result was that:
for the options Off, Low, and Normal if I was choosing to open terminal then it opened above ccsm window and
for the options High and Very High it opened below.

When the focus *prevention* level is to [COLOR="#FF0000"]off[/COLOR] - this means that we do not prevent new windows to get focus - as a result new windows will [COLOR="#FF0000"]get focus[/COLOR].
When the focus *prevention* level is [COLOR="#0000FF"]high[/COLOR] - this means that we do prevent new windows to get focus - as a result new windows do [COLOR="#0000FF"]not get focus[/COLOR].

The focus prevention windows does not seem to affect anything.

Either way, the windows loose or gain focus, which is what I would like to control.

Regards!

---

### Post by Claus7 on 2018-06-09
Hello,

the problem was found in the themes files. Using the Radiance theme I went to:
/usr/share/themes/Radiance/gtk-3.20

and under the /*default color scheme */ of the file: gtk-main.css

I changed the lines from:
@define-color backdrop_fg_color mix (@bg_color, @fg_color, 0.8);
@define-color backdrop_text_color mix (@base_color, @text_color, 0.8);

to:
@define-color backdrop_fg_color mix (@bg_color, @fg_color, **1.0**);
@define-color backdrop_text_color mix (@base_color, @text_color, **1.0**);

Regards!

---

