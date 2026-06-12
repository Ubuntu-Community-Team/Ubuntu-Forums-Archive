---
title: "MATLAB windows/figures mouse interaction problem"
date: 2015-01-21
forum: Education &amp; Science
---

### Post by simgunz on 2015-01-21
Hi all,
I'm not an Ubuntu user but I'm opening this topic to ask if some Ubuntu user is suffering the problem I'm going to explain (I'm interested because Ubuntu is officially supported by MATLAB).

The problem is that when MATLAB creates a new window detached from the main window, it's not possible to interact with this new window (below I'm talking of figures, but the same happens with Find&replace, Help and other windows).

[COLOR=#121212][FONT=Arial]How to reproduce:[/FONT][/COLOR]
[COLOR=#121212][FONT=Arial]1) Open matlab[/FONT][/COLOR]
[COLOR=#121212][FONT=Arial]2) Plot something > can interact with the figure (sometimes)[/FONT][/COLOR]
[COLOR=#121212][FONT=Arial]3) Close the figure window[/FONT][/COLOR]
[COLOR=#121212][FONT=Arial]4) Plot again > cannot interact with the buttons of the figure window nor with the figure itself.[/FONT][/COLOR]
[COLOR=#121212][FONT=Arial]If I click on the window the matlab main window is activated. The figure window appear to be transparent to the mouse pointer.
If I right click on the MATLAB main window I can interact with the figure (doesn't work with left click).
When the figure loses focus the problem appears again and can be solved in the same way.

[/FONT][/COLOR]
[COLOR=#121212][FONT=Arial]Matlab version: R2014b.
System: Manjaro Linux (Arch derivate)
Video card:  [COLOR=#222222][FONT=Verdana]00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
Notebook: Dell E7440[/FONT][/COLOR][/FONT][/COLOR]


References:
[http://se.mathworks.com/matlabcentral/newsreader/view_thread/338444#929361](http://se.mathworks.com/matlabcentral/newsreader/view_thread/338444#929361)
[http://se.mathworks.com/matlabcentral/answers/160294-how-can-i-resolve-gui-issues-under-debian-linux-unable-to-open-menus-nor-use-buttons-on-graphics](http://se.mathworks.com/matlabcentral/answers/160294-how-can-i-resolve-gui-issues-under-debian-linux-unable-to-open-menus-nor-use-buttons-on-graphics)

---

### Post by Portaro on 2015-02-18
Please try to run matlab by terminal and see them essages of aplication if appears something.

---

