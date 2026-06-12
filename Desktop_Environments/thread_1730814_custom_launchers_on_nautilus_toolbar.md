---
title: "custom launchers on nautilus toolbar?"
date: 2011-04-16
forum: Desktop Environments
---

### Post by wim.glenn on 2011-04-16
hello, i'm new to linux but enjoying it so far.  i have a question about customising the toolbar in the file explorer, which i think is called nautilus.  i was able to add a few buttons by hacking about in  /usr/share/nautilus/ui/nautilus-navigation-window-ui.xml ..but they were already defined actions.  what i would really like to add is custom launchers.  i have whipped up a python script that will foo and bar a glob of files in a directory, which i can pass as an argument to the script, and i would like this to be a toolbar button so i can just click an icon up there.  so the launcher would need to know what directory is open in the tab which is in focus, or alternatively be able to launch from that directory as current working directory and then i can dig out the path in python.  a keyboard shortcut for the launcher would be nice too.  any ideas?  thanks !

---

### Post by Copper Bezel on 2011-04-16
I think the closest you're going to get to that would be to use Nautilus' scripts folder. You'd still need to right-click your target and then select your script. Nautilus scripts don't have any trouble identifying the path and such, so they might be rather close to what you're looking for.

---

### Post by wim.glenn on 2011-04-17
ok thanks !  no toolbar icon (yet), but i was able to get the nautilus scripts working, and set custom accels for it by editing in ~/.gnome2/accels/nautilus file.  

for anyone else trying to do the same thing, you can dig the folder name out of python by getting it from os.environ, nautilus sets them as environment variables before running your script.  the only way i could find to get the terminal window to stay open was to call the python from a .sh file wrapper and put 

read -p "Press enter to continue" nothing

at the bottom of the .sh file.  cheers  :popcorn:

---

### Post by thecamelcoder on 2011-04-17
Hey mate, i've been done the same road a number of times until I came across nautilus actions. 

Check out this walk through and see it its what your looking for. 

[http://www.linux-geek.co.nz/2011/04/17/how-to-add-items-to-nautilus-menus/](http://www.linux-geek.co.nz/2011/04/17/how-to-add-items-to-nautilus-menus/)

If it helps, please make sure to add a comment.

Thanks

):P

---

### Post by wim.glenn on 2011-05-02
thanks, i had already come across nautilus-actions and it looks very useful but it wasn't what i wanted (shortcut key or toolbar icon)

edit:  i just checked again and found the toolbar button to be working now, in nautilus actions, don't know why i missed it there before!

---

