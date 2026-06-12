---
title: "compiz window issue"
date: 2007-12-27
forum: Desktop Effects &amp; Customization
---

### Post by snypercore on 2007-12-27
every time i open a window on this machine which is running compiz and emerald (with or without a theme) the small bar at the top that has the minimise exit and maximise buttons isn't there and all windows spawn maximised. how can i fix this?

---

### Post by 0g_Trans_Fat on 2007-12-27
try this:
press [ALT]+[F2] and type
```
emerald --replace
```
after you select a theme and compiz is running

---

### Post by snypercore on 2007-12-27
stupid question but whats the alternatice to the ALT+F2 hotkey, im a newbie and this keyboard im using is a bit messed?

---

### Post by 0g_Trans_Fat on 2007-12-27
Its 'Run Application'.  to get to it right click on a panel>Add to Panel>Run Application.  Then just click on the button that it puts on your panel

---

### Post by snypercore on 2007-12-27
ok that didnt work, even without a emerald theme, i might add ive just updated from 7.6 to 7.10 on this rig and before it was using beryl, if thats any help to anyone


EDIT**
when i stop desktop effects its ok..

---

### Post by 0g_Trans_Fat on 2007-12-27
If desktop effects if off, then it is running metacity and you wont have a problem with the windows but you wont get any special effects because compiz isnt running.

Try making sure that Window decoration is checked under System>Preferences>Advanced Desktop effects(or CompizConfig Settings Manager)

---

### Post by snypercore on 2007-12-27
yeah its checked

and its fine when compiz is off

---

### Post by snypercore on 2007-12-27
fixed, went to APPS>OTHER> and went through the window managers and changed some things seemed to do the job

---

