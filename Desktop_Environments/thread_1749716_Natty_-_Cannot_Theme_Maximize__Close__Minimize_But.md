---
title: "Natty - Cannot Theme Maximize / Close / Minimize Buttons when in Full Screen?"
date: 2011-05-04
forum: Desktop Environments
---

### Post by bcollier on 2011-05-04
In Natty no matter what theme you are using it appears the maximize / close / minimize buttons in the top left (or right) always look the same when the window is maximized (somewhat poorly drawn x   -   [ ]  (see screenshots of full screen).  

Is it possible to have these buttons change to the standard from the theme?

---

### Post by osu761 on 2011-06-18
I am also having this problem.  Does anyone know how to change the control icons for maximized windows in Natty?

---

### Post by bringingdadaback on 2011-07-07
Just chiming in to say I've got the same issue and that I can't stand looking at the hideousness and off-centeredness of it all. If anyone has a workaround I'll be eternally grateful.

I hope 11.1 features actual customization options for the globalmenu.

---

### Post by diandal on 2011-07-07
i too have natty with unity 2d and have moved my minimize,maximize,close buttons to right but whenever any file is open full it reverts to left side again

how can i keep buttons on right even when fully open?

Have used gconf etc etc and also ubuntu tweak

---

### Post by bringingdadaback on 2011-07-07
I've discovered a workaround for this! 

Go into /usr/share/themes and copy your theme. Paste its contents into either the Ambiance or Radiance folders (back them up first). You'll end up overwriting some files and you may have to change some file permissions, as ubuntu doesn't seem to want its default themes messed with). 

Customize your set theme under 'Appearance', selecting Ambiance/Radiance for your 'Controls' and 'Window Borders' settings. You may need to log out and log in again. If your theme's file names are identical to those of Ambiance/Radiance, you should be good to go! 

If they were different, however, you'll have to rename all your minimize/maximize/close files to match the names of the originals in the Ambiance or Radiance theme. This is a bit tedious (and hopefully won't be necessary in future releases) but worth it in my opinion.

---

### Post by bringingdadaback on 2011-07-07
Looks like I spoke a little too soon. The first few button replacements worked, but once I tried renaming them all the edited 'Radiance' theme refused to work, showing up as a question mark in the appearance tab. How unfortunate. At the moment I'm running Orta Squared with Radiance buttons in maximized mode -- not ideal but certainly a big improvement.

---

