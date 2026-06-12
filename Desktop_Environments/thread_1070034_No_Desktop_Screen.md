---
title: "No Desktop Screen"
date: 2009-02-14
forum: Desktop Environments
---

### Post by kb7ypf on 2009-02-14
Hi-

I think I shot myself in the foot.  I updated (added) Gnome apps and then restarted my computer.  It rebooted and allowed to to log in without any problem.  When I got to the Desktop screen there was nothing there but the Desktop background picture.  

How do I get my Desktop back?  I really need help on this one.  :confused:

Thanks,
Dick

---

### Post by UbuntuNerd on 2009-02-14
what happens if you hit alt+f2?

---

### Post by kb7ypf on 2009-02-14
Nothing happens as I can only see the Desktop screen picture.

I can get to my terminals via control-alt-f1.

The terminals work correct and take input.


I just don't know what to do to get my gnome back.

---

### Post by UbuntuNerd on 2009-02-15
ok copy this code to a piece of paper:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```
 and drop back to the terminal by typing alt+f1 or Ctrl+alt+f1, it should ask you to log in so enter your user name and password then type each line of the code follow by enter, in other words type the first line and hit enter then the second and hit enter ans so on. then hit alt+f7 to go back to your desktop, see if this works
note: make sure you type the code exactly like it is, some sections have a space in between them.

---

### Post by kb7ypf on 2009-02-16
Thanks for all the help.  It worked and I am back in business.  :p :popcorn:

---

### Post by UbuntuNerd on 2009-02-16
Im glad you got it working.

---

### Post by kb7ypf on 2009-02-17
Since I got my Gnome Desktop back working there is "one" issue to clean up.  No matter what application I have open, when I click on the "minimize" button the application shuts down instead of minimizing.  

Do you have any suggestions as this is really a pain in the butt.  :(

Again, thanks for all your help.




Dick

---

### Post by UbuntuNerd on 2009-02-17
what happens exactly do the windows look like the go away and did you check to see if the program was still running after you minimized the window?

---

### Post by kb7ypf on 2009-02-17
The windows (program) goes away completely.  I check in the "Resources" in "System Monitor" and the programs are not listed or running.  

Pressing the Minimize button an any app terminates the program.  I am going to try to reload Gnome and see if that works.  Also, I am going to redo the code you provided above to see it that will fix my problem.

Dick

---

### Post by UbuntuNerd on 2009-02-17
make sure you have the "window list" at the bottom left, this is what allows you to change in between windows when they're minimize, if you don't have it when you minimize the window it will just go away. if you want to reinstall your desktop just use this command:
```
sudo aptitude install ubuntu-desktop
```

---

### Post by kb7ypf on 2009-02-17
I reloaded Ubuntu-desktop and all is well.  Thanks much for all your help.  :popcorn:


dick

---

### Post by F W Adams on 2009-02-25
I have the same symptoms as post #1, kb7ypf. No screen icons on boot up. Then I followed the instructions given in post #4 and that solved the problem. On booting up from cold however I just get the same problem back again?

I also noticed about half an hour later that I 'lost' thunderbird from the top panel. I solved that by just reloading thunderbird, don't know if the two things are related?

I also did do a clean install on this ( new ) machine recently making a clean encrypted system from the 8.04 alternate CD. Then I loaded the whole of /home from my old machine via a USB drive. All that home partition data including the desktop files look fine. This is perhaps related?
Any ideas?

---

### Post by F W Adams on 2009-02-25
The #4 suggestion didn't work a second time and thunderbird was again missing from the panel after a reboot. Don't waste any time on problem in previous post. I will load the system from scratch and try again. I must say I'm completely fed up with trying to get different things working in ubuntu on this new machine, the sound, graphics card, dual screen have wasted days already and no end in sight.

---

### Post by UbuntuNerd on 2009-02-25
Im my opinion getting things to work in Ubuntu is like a reward, sometimes things may not work the first time and what may work for some computers may not work with yours so you have to try different things and different guides because some of them maybe missing what you need but others may have it. I know I have try to do things before and didn't get it the first time and try it again and got it working, don't give up so easily :)

---

