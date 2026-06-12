---
title: "buttons and login actions in Unity"
date: 2018-06-30
forum: Desktop Environments
---

### Post by Skaperen on 2018-06-30
a while back i had asked about adding a button to my Unity display but was never able to get the button to show up (although others could).  i have thinking about that and now have the idea that a separate GUI app could do this.  it would be panel of just a few buttons off the edge of the display (but not appearing in other workspaces) that would be trigger to come into the display when the mouse comes to that edge.  then the program doing this would be configured (or modified) to carry out specific actions when a button is clicked.

this program would need to be started, run once and only once, when i log in.  would it need to be run once for each workspace?

i would like to know how (going to search for this next) to have Unity start a script/program of mine at user login on Unity.  such a script might start up one or more GUI apps like "terminal" or "firefox" or other things.

i am looking for things that are, on the programming side, written in C (not C++ or C# or Obj-C) or in Python (preferably Python3).  samples that i can start with and modify would be best.  that's how i can learn new stuff fast.

i am using a recently upgraded Ubuntu Xenial Xerus 16.04.4 LTS Desktop and plan to replace it with 20.04 LTS around 2020-05 or so.

---

### Post by vanadium on 2018-07-01
Overall problem is not quite clear to me, but to autostart programs/scripts when a user logs in, place the appropriate .desktop files in the users .config/autostart folder. Just copy the corresponding .desktop files for applications such as terminal or firefox from the systemwide .desktop files under /usr/share/applications. To launch your custom script, create your custom .desktop file. .desktop files are text files providing the shell instructions about lauching an application.

---

### Post by Skaperen on 2018-07-01
the 1st problem is, i want to have a few buttons of my own (not drop-down menus) that result in scripts/programs of my own (might be a #! script or a linked binary), possibly configured with arguments, being executed in the background (fd 1 and fd 2 open to "/dev/null").

the 2nd problem is, i want to learn about GUI programming, including things like displaying my own button images and make things appear and disappear by fading in/out or sliding from/to the edge.

the 3rd problem is finding sample programs to do things like this in C or Python3 that i can learn from and use as starter files to write programs.

---

