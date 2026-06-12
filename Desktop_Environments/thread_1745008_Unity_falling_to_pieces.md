---
title: "Unity falling to pieces"
date: 2011-04-30
forum: Desktop Environments
---

### Post by electrojustin on 2011-04-30
Ok so just upgraded to unity and everything is fine. Then I accidentally enabled Desktop Cube and Cube Rotation. Suddenly, the top part of windows that you normally use to drag the window or close it etc. started dissapearing. In a panic, I rebooted. Upon reboot I found myself in an even bigger mess than I could have imagined. Not only did this fail to fix the problem previously mentioned, it also caused the sidebar and the ubuntu bar at the top to dissapear. Desktop icons still show, and my cursor is fully functional, but other than that, my system is unusable. Please help.

---

### Post by mikewhatever on 2011-04-30
Hit ctrl+alt+f1, login, then run unity --reset. That should return Unity to its default state.

---

### Post by electrojustin on 2011-04-30
I found a solution to the problem. I had to open up ccsm somehow (there were many workarounds for doing this) and enable the unity plugin. Then I had to install unity-window-management. Thank you for your suggestions! Also, sorry for making yet another thread about an already well known problem.

---

### Post by Meiketsu on 2011-05-19
How did you solve this issue? Im having the same problems but i cant figure out for the life of me how to fix it. Im trying Ubuntu for the first time and if im already having troubles like this im not sure how long ill use it.. Help?

---

### Post by 1angel on 2011-05-19
Same thing here, I'm stuck. I did the same mistake, activated the cube thing and now I can't find unity.

As I don't like half-answers, here is where I am:

How I got there:
1. got a little too fancy with compiz and activated the Desktop Cube and Rotate Cube, at this point I can't remember if there was any conflict with any buttons.
2. once active I lost my marquees on the windows, the top bar and everything... tried not to panic and because ccsm was still on the screen, (CompizConfig Settings Manager for those who want to know what ccsm stands for), I tried "reversing" the effects, got all sort kind of "conflicts" that I thought I was resolving.
3. Nothing worked, and because I didn't have my top menu bar to use the menu to reboot and because I had a terminal open, I executed a "init 6".
4. System rebooted (normal reboot, no error messages)

Where I am:
1. Was able to login
2. Once in I got to a "blank" desktop, no menus, no side bar, no nothing.
3. I right click on the background and created a "launcher", executable in a terminal, command /bin/sh
4. once there I opened firefox (that's how I'm connecting here)
5. became root:
     $ sudo su
     password: xxxxx
     #
6. executed unity &
     # unity &
7. Unity is working I can access ccsm, reset compiz to defaults, yadda yadda yadda, but I still don't get my menus/bars back.....

I tried rebooting, reseting, nothing works.

anyone help?

thanks,
angel.:confused:

---

### Post by 1angel on 2011-05-19
OK. I solved the mystery on why it was not working on my laptop :( my bad... my bad.....

short answer: I was using unity while resetting.... locked file.... I guess this Unity thing is either very smart or very dumb ;) or better said, one needs to know how it works......


First thing, please don't panic, everything in Unix/Linux is reversible unless you delete something permanently, and then still you can re-install

So, here is how I worked it:
1. Once you loose your top/side bar/menu, don't panic, close all your apps (just because I'm paranoid) and don't reboot, but if you did, just login as you usually do.
2. Once on your desktop right click on the background (not that there is anything on the screen!), and create a launcher: Type= Application in Terminal, Command=/bin/sh, click OK
3. Launch your "app" this will give you a "terminal, there you can type at the $ prompt:
     ccsm
4. this starts the CompizConfig Settings Manager, look for the "unity" button and check it
5. close the ccsm
6. in your terminal reset unity at the $ prompt
     unity --reset
7. this resets unity to defaults, and most important "restarts" unity.

Then you can logout or restart your applications.

Because I'm paranoid, I rebooted and had a clean start.
One important tip..... don't switch to root, that was one of my mistakes, the other one is that I "resetted" unity while I was still on ccsm, so I guess the manager has some kind of file locking tool.

so, here you are, full disclosure of how I did it.

hope this helps somone.
Angel.

---

