---
title: "Ubuntu 11.04  - missing min,max bars on windows"
date: 2011-04-29
forum: Desktop Environments
---

### Post by COMTIBoy on 2011-04-29
Hi Everyone,

I just installed Ubuntu 11.04 (gnome flavor ) on my notebook.

Everything installed fine except that I'm seeing three problems I'm hoping someone can help me with (or point me in the right direction).

1. When I open any window (gcalc or Firefox for example), the 3 little buttons which are used to maximize, close, etc...) are missing. So basically in order to exit any app, I have to do it through the application rather than clicking the close button.  If you go to Themes, you can see what I'm talking about. For example, the theme 'ClearLook' show's the buttons. If I choose this, these buttons are not there.Any ideas why this is happening or how I can fix it ?

2. When I open any application, it positions itself in the upper left hand corner of my screen.  The menu of the application is tucked under the Gnome menu bar, so basically to use any application requires me to move it first....so I can get to the app menu.  Any ideas why this is happening or how I can fix it ?

3. When I open any application, I'm unable to position the mouse such that I can resize the window.  Its like the mouse cursor can't find the the fine line where it changes so that I can grab the screen to increase or decrease it.  Pretty annoying... :(   I've used Ubuntu since vs. 8x and I've never had this problem.  The prior version 10.10 didn't seem to have this problem. 

Any tips would be greatly appreciated.

---

### Post by magnificent on 2011-04-29
I have exactly the same problem.  I think Compiz is to blame but I don't know why yet.
Try resetting all the window decorator plugins to default values?
Didn't work very well for me but I did get some buttons when the screen is full.

---

### Post by COMTIBoy on 2011-04-29
Hummm....interesting. I believe when I installed the OS , I didn't see the behavior I describe above.  I only started seeing these problems after I intstalled compiz and tried to get the 3D cube flipping. 

I did get that working, although I don't get a cube. I only get 2 sides ( like a pancake)  

I think I'll try removing compiz to see what happens

---

### Post by COMTIBoy on 2011-04-29
So I un-installed .9.4-0ubuntu2 (compizconfig-settings-manager), but I suspect whatever changes it made , still persist....

Same problem.

Wonder if there's some sort of restore that would allow me to revert my system to factory like conditions ? :)

---

### Post by Krytarik on 2011-04-29
1.) Check the setting "CompizConfig Settings Manager -> Window Decoration -> Command", the default value is "/usr/bin/compiz-decorator".

2.) No idea right now.

3.) I regularly have this issue, too, in my Lucid install, although if you are really precise and patient, you usually get that point. But in those cases I just grab them at their corners, which provide are much greater 'grab-area'.

I just noticed that, while was writing my post, you removed CCSM. Just reinstall it, it doesn't affect anything, it's really just a "Settings Manager".

---

### Post by KegHead on 2011-04-29
Hi!

Try to goto classic.

system...admin login chose classic..reboot.

Could be a video card situation. 

KegHead

---

### Post by COMTIBoy on 2011-04-29
Yup.

I'm already in Classic mode. (.e.g not using the new interface that came out with 11.04). 

I switched to Classic mode (no effects) and that restored everything to the way it should.  (Also, the new Ubuntu interface (unity ?:roll: seems to work fine. 

I'm using NVIDIA Driver Version: 173.14.30 on my machine.

---

### Post by COMTIBoy on 2011-04-29
> **Krytarik said:**
> 1.) Check the setting "CompizConfig Settings Manager -> Window Decoration -> Command", the default value is "/usr/bin/compiz-decorator".

2.) No idea right now.

3.) I regularly have this issue, too, in my Lucid install, although if you are really precise and patient, you usually get that point. But in those cases I just grab them at their corners, which provide are much greater 'grab-area'.

I just noticed that, while was writing my post, you removed CCSM. Just reinstall it, it doesn't affect anything, it's really just a "Settings Manager".



Thanks. This fixed the button problem.  I think that was the most annoying thing. 

Any ideas why I only have 2D flipping instead of 3D cube flipping ? My graphics card supports it.  I was able to do this on my previous install of Ubuntu.

---

### Post by Krytarik on 2011-04-29
> **COMTIBoy said:**
> 
Any ideas why I only have 2D flipping instead of 3D cube flipping ?
Maybe because there are only 2 workspaces set in "CompizConfig Settings Manager -> General Options -> Desktop Size (tab)"? ;-)
That is the default.

---

### Post by COMTIBoy on 2011-04-29
> **Krytarik said:**
> Maybe because there are only 2 workspaces set in "CompizConfig Settings Manager -> General Options -> Desktop Size (tab)"? ;-)
That is the default.


I'm an idiot.  That was it.  Thanks!

---

### Post by magnificent on 2011-04-29
I've got this problem in unity using the ubuntu option in the log in screen.  Everything else works fine, the cube rotates, deforms etc.  I just don't have any window border or controls.  I can get into stuff using cairo dock and the launcher and move the windows around and resize them.
Just no buttons...
Compiz command line in window decorator is set to default.  Using gconfig editor I find that the valus for window decorator are currently active; compiz, default; metacity.  Re-enable metacity in the terminal gives me back the window controls but of course stops compiz from running...
Is there a window decorator compatible with new compiz?

---

### Post by Krytarik on 2011-04-29
> **magnificent said:**
> I just don't have any window border or controls.  I can get into stuff using cairo dock and the launcher and move the windows around and resize them. Just no buttons...
So, are there no title bars as well, and you move the windows by another method, for example by pressing the Alt key?
> **magnificent said:**
> Using gconfig editor I find that the valus for window decorator are currently active; compiz, default; metacity.  Re-enable metacity in the terminal gives me back the window controls but of course stops compiz from running...

Compiz and Metacity are "window *managers*", not "..decorators".

---

### Post by magnificent on 2011-04-29
Yes I can use alt and mouse to move windows.  No window borders at all.  I do get a close max min button in the top bar when a window is full, but if I resize a window these go away.  Any ideas?

---

### Post by Krytarik on 2011-04-29
> **magnificent said:**
> Yes I can use alt and mouse to move windows.  No window borders at all.  I do get a close max min button in the top bar when a window is full, but if I resize a window these go away.  Any ideas?
Ok, thanks for clarification.

Are you usually running Emerald or just the default?

If Emerald, try running this via Alt+F2:
```
emerald --replace
```If the latter, run this:
```
gtk-window-decorator --replace
```

---

### Post by magnificent on 2011-04-29
Thanks, already tried this.  emerald --replace was the command line in compiz config settings.  It seems emerald and the new compiz don't like each other.
The command is now this:"/usr/bin/compiz-decorator" in window decorator plug-in.  Compiz now seems to be the decorator in 11.04.  I've tried all sorts of variations and replacing metacity, compiz using the terminal.  I can get it to run other decorators and there are plugins in compiz to enable all of these, but the default setting in compiz is "/usr/bin/compiz-decorator"
Any more ideas I will gladly try.
Many thanks for your help!

---

### Post by Krytarik on 2011-04-29
So, what happens when you run either of the given commands?

---

### Post by magnificent on 2011-04-30
emerald --replace does nothing
metacity --replace reverts all graphics to something like mutter was but with no visual effects.
If I try the command compiz replace I get this:

user@ubuntu:~$ compiz-decorator --replace
Couldn't find a perfect decorator match; trying all decorators
Starting emerald
Segmentation fault
user@ubuntu:~$

---

### Post by Krytarik on 2011-04-30
> **magnificent said:**
> emerald --replace does nothing
metacity --replace reverts all graphics to something like mutter was but with no visual effects.I didn't say to try 'metacity', but 'emerald' and 'gtk-window-decorator'. Then try the latter now.

Also, is Emerald actually installed?:
```
dpkg -l |grep emerald
```And themes for it? Did you use it before?
> **magnificent said:**
> 
user@ubuntu:~$ compiz-decorator --replace
Couldn't find a perfect decorator match; trying all decorators
Starting emerald
Segmentation fault
user@ubuntu:~$
Neither said I to try 'compiz-decorator', but that actually gives us an important hint, thanks. ;-)

---

### Post by magnificent on 2011-04-30
Tried this:gtk-window-decorator --replace
Not installed, so this:sudo apt-get install compiz-gnome
Voila!  Title bar and buttons back!
When I close the terminal the buttons go away again.

---

### Post by Krytarik on 2011-04-30
> **magnificent said:**
> Tried this:gtk-window-decorator --replace
Not installed, so this:sudo apt-get install compiz-gnome
Voila!  Title bar and buttons back!
When I close the terminal the buttons go away again.
Sure, but if you run it through the Alt+F2 dialog, it keeps running.

Check if it's run on login.

Also, how about Emerald?

---

### Post by magnificent on 2011-04-30
emerald is on and I can access it

user@ubuntu:~$ dpkg -l |grep emerald
ii  emerald                                   0.7.2-0ubuntu6                             Decorator for compiz-fusion
ii  libemeraldengine0                         0.7.2-0ubuntu6                             Decoration engines for compiz-fusion
user@ubuntu:~$ 
not the same version as compiz which is 1:0.9.4+bzr20110415-0ubuntu2

Gtk themes can be applied but only from an open terminal.

---

### Post by Krytarik on 2011-04-30
> **magnificent said:**
> emerald is on and I can access it
Meaning that it's run on login, and it works?
> **magnificent said:**
> 
user@ubuntu:~$ dpkg -l |grep emerald
ii  emerald                                   0.7.2-0ubuntu6                             Decorator for compiz-fusion
ii  libemeraldengine0                         0.7.2-0ubuntu6                             Decoration engines for compiz-fusion
user@ubuntu:~$ 
not the same version as compiz which is 1:0.9.4+bzr20110415-0ubuntu2
Of course not, Emerald is basically a separate app.
> **magnificent said:**
> 
Gtk themes can be applied but only from an open terminal.
Meaning that it's not run on login? How about Alt+F2?

Which window decorator would you like to run then on login?

---

### Post by magnificent on 2011-04-30
Ok I am making some progress I think.  Restart with gtk as decorator.  Then enabled compiz.  Window borders and controls in place.  Re-enabled each compiz plugin one by one.  Some conflicts with the unity plugin to be resolved and with desktop cube plugin.
But I have unity running with desktop cube and gtk window borders and controls.
They are a bit basic on eye candy but they are there and staying put.
Can I use a UI to select themes with gtk or would I be best using Gconf editor to change themes?

---

### Post by Krytarik on 2011-04-30
> **magnificent said:**
> 
They are a bit basic on eye candy but they are there and staying put.
Can I use a UI to select themes with gtk or would I be best using Gconf editor to change themes?
If you want to run Emerald instead, just set "CompizConfig Settings Manager -> Window Decoration -> Command" to  "emerald --replace".

Metacity themes (gtk-window-decorator) are usually in a set with GTK themes, and I wouldn't set different ones for each. To change them click at the power button, choose "System Settings", then in the upper part "Appearance", then you will already be in the tab "Theme". If you want to set them indiviually, choose a theme you use generally, click at "Customize":
- "Controls" is for the general look
- "Window Border", you get it, is for the window decoration

---

### Post by magnificent on 2011-04-30
Nice!
Thanks Krytarik
Had to change a few bits in gconf-editor first to replace cairo default.  But now it's nice and shiny, opaque and all good.  Apparently there is an alpha channel in gtk themes for opacity but it's set nice now.
I still can't get emerald to work with compiz, but at least my system is all as it should be now.
Must be a conflict with trying to run emerald and compiz with some plugin effects enabled.  I didn't have gtk installed before so maybe that was the problem?

---

### Post by Krytarik on 2011-04-30
> **magnificent said:**
> 
I still can't get emerald to work with compiz, but at least my system is all as it should be now.Ah, you said before that there is no output at all if you run "emerald --replace". But I couldn't really believe it, apparently. =/
> **magnificent said:**
> 
Must be a conflict with trying to run emerald and compiz with some plugin effects enabled.  I didn't have gtk installed before so maybe that was the problem?
I don't think so. But you may try reinstaling both Emerald packages, if you want to keep on trying to get it to run.

---

### Post by magnificent on 2011-04-30
Found this by trolling...
Re: Using emerald window decorator with Ubuntu 11.04
Emerald doesn't work in 11.04 because it doesn't work with the new version of Compiz. There is however a work around if you build it from git.

[http://ubuntuforums.org/showthread.php?t=1702253](http://ubuntuforums.org/showthread.php?t=1702253)

The link gives details on building emerald to work with compiz.  Think I'll just wait till I can get a new one via synaptic...

---

### Post by Krytarik on 2011-04-30
> **magnificent said:**
> 
The link gives details on building emerald to work with compiz.  Think I'll just wait till I can get a new one via synaptic...
Yeah, seems to be the better alternative. =)
You may also periodically check if it's provided by a PPA, not as of now it seems.

Thanks for the info!

---

### Post by magnificent on 2011-05-02
Found a good fix for emerald:
[http://abz89.wordpress.com/2011/05/02/how-to-fix-emerald-in-ubuntu-11-04/]("http://abz89.wordpress.com/2011/05/02/how-to-fix-emerald-in-ubuntu-11-04/")
Just work through the copypaste instructions, then run emerald in startup applications emerald --replace.
I have really nice transparent glass window borders now and I think it really compliments the other Unity effects.

---

### Post by Krytarik on 2011-05-02
Yeah, it looks indeed great, just like it should! :P

Nice summed-up instructions, just fresh today, however it pulls in a lot of additional packages necessary to compile apps. Did you by any chance install some of the latter before (referring to the purpose, not to the packages listed in the guide)?

Also, would you like to run the install again in order to additionally build a deb-package?, which you can
- handle by the package manager, + for you
- upload here, + for other Natty users

To do so, just run "sudo checkinstall" instead of "make install", therefore you need the package "checkinstall":
[https://help.ubuntu.com/community/CompilingEasyHowTo#Step%204:%20Build%20and%20install]("https://help.ubuntu.com/community/CompilingEasyHowTo#Step%204:%20Build%20and%20install").

If you do so, please include what version of Natty 11.04 you are running, i386 or AMD64.

It would be great if you do so!

Thanks in any case!

---

### Post by magnificent on 2011-05-02
Yes I have tried to compile this before, unsuccessfully.  There are a number of failed installs but since I purged ALL emerald files before I don't think it was an issue, however I did have emerald working well in 10.10 with a number of plugins...  Maybe something here?
I am running Natty on i386.
Got this when tried to checkinstall:

Installing with emerald...

========================= Installation results ===========================
emerald: Screen 0 on display ":0" already has a decoration manager; try using the --replace option to replace the current decoration manager.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

Any suggestions to make this package?

---

### Post by Krytarik on 2011-05-02
I was more meaning compile necessities than Emerald specific files/packages.

What exact command did you run then, with 'checkinstall'?
You should only run "sudo checkinstall" from inside the toplevel of Emerald's build directory.

---

### Post by Jerriy on 2011-05-03
> **COMTIBoy said:**
> Hummm....interesting. I believe [SIZE=2]when I installed the OS , [/SIZE][SIZE=3][SIZE=2]I did[/SIZE][SIZE=2]n't see the behavior[/SIZE] [SIZE=1](...) [/SIZE][/SIZE][SIZE=1]I [/SIZE]only started seeing these problems [SIZE=4]after I intstalled compiz[/SIZE] and...Glad I'm not the only one who caught this.

I'm thinking of operating on the default system ONLY as my regard to compiz has degraded (for such a crucial GUI comopnent compiz is too vulnerable to manipulations by all kinda programs that tinker with it and end up destroying your very personalized setup. I don't want to constantly uninstall-install the shabby Compiz-Fusion everytime I install and play with other programs.

So then I have the same problem: How do I go back to default ubuntu settings? Right now I have uninstalled Compiz and as a result I have no edge/border and all other kind of window-functions are not working.

DON'T tell me to type metacity in terminal I did that but I don't want to do that all the time. I want to go back to pre-compiz state.

Thank you for your help

---

### Post by magnificent on 2011-05-03
sudo checkinstall emerald to Krytarik.  How do I get to the top level of the build directory?

Jerry I think you mean Mutter for the pre-compiz state in unity or gtk for gnome desktop.  You can install it using a post somewhere back in this thread.

---

### Post by Krytarik on 2011-05-03
> **Jerriy said:**
> I want to go back to pre-compiz state.

Choose "Ubuntu Classic (No effects)" as the "Session" option at the bottom of the login screen, after clicking/entering your username, but before entering your password.

About those options, also see here:
[http://ubuntuforums.org/showthread.php?t=1741293](http://ubuntuforums.org/showthread.php?t=1741293)

Greetings.

---

### Post by Krytarik on 2011-05-03
> **magnificent said:**
> sudo checkinstall emerald to Krytarik.  How do I get to the top level of the build directory?
I was referring to the directory in which you ran "make" before.

And only run:
```
sudo checkinstall
```

---

