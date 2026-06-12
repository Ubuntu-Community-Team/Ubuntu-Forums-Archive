---
title: "switch between two xorg confs"
date: 2009-11-04
forum: Desktop Environments
---

### Post by arrow.69 on 2009-11-04
Hi,

So After alot of googling and trial and error, I've finally set up dual head to work perfectly with compiz and ATI proprietary drivers.

Now, this is great.  But I use a laptop with a second external monitor hooked up.  This means that often enough (maybe once a week)  I want to be able to grab my laptop, unplug the monitor and maybe have to restart X or whatever but after a short period of time have a working desktop again.

I'm thinking of maybe having two xorg.conf files.  And then have a bash script that would kill X, copy the xorg.conf file I want, and start X.  Does this sound doable?  Or are you aware of an easier way to accomplish this?

The other thing is I use a single gnome panel on my desktop.  Now usually I have it on my larger, external monitor.  Is there a command to change its location from one monitor to the other?  So far I've had to create a bunch of panels until they run out on the one monitor and switch to the next one, then delete the ones I don't have.  Which is stupid.

So, if anyone has any ideas for things I could try to achieve this, let me know.

Thanks

---

### Post by Tuxor on 2009-11-04
I had kind of the same issue once. I had to have different xorg.conf depending on if my laptop was docked or stand-alone. I used a script to determine from "lspci" if the dock was present, if so then it ran a program called "Switchconf" which replaced the xorg.conf as necesarry. Maybe you could modify my script to look for your external screen and just copy the correct xorg.conf to /etc/X11/? I think that the "Switchconf" program is redundant in the solution, since you can let the script copy the right xorg.conf. Link to script goes here: [http://ubuntuforums.org/showthread.php?t=1020299#post7120767](http://ubuntuforums.org/showthread.php?t=1020299#post7120767)

---

### Post by arrow.69 on 2009-11-04
Thanks for the quick reply!

I took a look at your script and installed switchconf.  That's pretty much exactly what I was looking for.  I also solved the gnome-panel issue.  I realized you can simply unexpand the panel and then drag it to wherever, then reexpand it.

I'm having two problems implementing your script, however.  From what I can tell lspci won't return the state of my VGA controller.  It identifies the ATI VGA output, but can't tell me whether or not a monitor is connected.  Does anyone know which command would give me that information?

Also, I'm having trouble actually getting that second xorg.conf file.  I tried unplugging the external monitor and rebooting my computer.  As I expected the desktop was acting really weird, no window decorations, compiz half broken, etc.  So I went into a terminal only session and ran 

sudo -dpkg -reconfigure xserver-xorg

But when I rebooted the computer, even the boot splash screen didn't display properly and my computer froze there.  I eventually reverted to the dual head .conf file, but this means I can't run my laptop without the monitor, even if I change .conf files manually.  Any thoughts on this?

---

### Post by Jenkins1 on 2009-11-04
Hi,

I have a laptop that is connected to an external monitor, I often take it to lectures/albs etc and I do usually have my menu bar on my external display.

Edit1: It only supports Nvidia.

I used this thread [http://ubuntuforums.org/showthread.php?t=1114767&highlight=disper](http://ubuntuforums.org/showthread.php?t=1114767&highlight=disper) 
Edit2: [http://willem.engen.nl/projects/disper/]("http://willem.engen.nl/projects/disper/") disper project page

The code needed to move the panels to the external display are as follows.
For the top pannel
```
gconftool-2 \
        --set "/apps/panel/toplevels/bottom_panel_screen0/monitor" \
        --type integer "1"
```
For the bottom panel
```
        
   gconftool-2 \
       --set "/apps/panel/toplevels/top_panel_screen0/monitor" \
       --type integer "1"  
```

to move them to the internal monitor change the "1" to a "0"

I have a script biased on the one in the above thread that runs at login. It specifically looks for my external display and if any other display is connected then it clones rather than extending the desktop. Unfortunately as disper does the changes, at least in my case the screen does go black or show the desktop in a muddled puzzle like form. As this is only for 2 seconds its not really a problem. I have also got the script linked to a keyboard shortcut if i forget to plug my monitor in.

Hope this helps

---

### Post by arrow.69 on 2009-11-04
Thanks for the reply, Jenkins1.

I don't think I can use Disper since I'm running on an ATI video card.  However, I'd like to see your code for detecting which display is connected.  I can definitely use that and switchconf to get the results I'm looking for.

---

### Post by Jenkins1 on 2009-11-05
unfortunately the code relies on the disper command output but I will paste it in case you might find it useful in any way.

```
#set a local varaible as if functions can only answer 0 or 1.
local 1="ACI ASUS VH222H"
#looking for my model of screen in the disper output.
if disper -l | grep "ACI ASUS VH222H" ; then
```

---

### Post by Tuxor on 2009-11-05
Ok, good that my tip helped you somewhat. Instead of using lspci, you can use xrandr in the script to see what screens are connected. Catch the output from "xrandr -q" which should list all outputs that has a monitor connected. For details about xrandr, which is a far too underrated tool in my opinion, see [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) . See where that takes you.

Oh, and about the settings for the xorg.conf without the external monitor, I think that xrandr can help you figure out what you need there too.

---

### Post by Jenkins1 on 2009-11-05
the disper launchpad page: [HTML]https://launchpad.net/disper[/HTML]

Says > The focus has been on NVidia cards, but testers/contributors for for XRandR and ATI are welcome.

So you never know it might be worth a go.

---

### Post by arrow.69 on 2009-11-05
Hi,

so I've made some progress on this little project of mine.  I now have two configuration files for extended desktop with the external monitor, and the second one for the laptop only.  I've tested copying the right configuration file, restarting X, and it works perfectly.  If I plug in a monitor while the laptop configuration is running, I get a mirror of the same resolution on the external, which is fine for stuff like projectors during presentations or whatever.

So here's what I have to do now.

- Find a way to detect whether or not the external monitor is plugged in
     - lspci won't work in my case
     - xrandr -q outputs the virtual resolution for both my monitors, so I don't think I can use it.
- Copy the right .conf file to /etc/X11 depending on above's output
- Restart X

for now since I can't figure out the detection part I'll try making a script for each configuration file and see how that works out for me.

If you have any other ideas for how I might detect the external screen, let me know

---

### Post by Tuxor on 2009-11-08
Eh, why can't you use "xrandr -q"? You should be able to do like this:

1. Run the "xrandr -q" command when not having external monitor attached. Copy the output.
2. Run the "xrandr -q" command when having the externa monitor attached. Copy the output.
3. Note what differs in the output from step 1 and 2. Use the uniqe difference in the output to determine what state the computer is in - external monitor attached, or not. You can use my script as a base for looking for the unique output string.

Or am I not getting your point??

---

