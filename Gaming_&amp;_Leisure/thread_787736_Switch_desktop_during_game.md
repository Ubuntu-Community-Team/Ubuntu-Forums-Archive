---
title: "Switch desktop during game"
date: 2008-05-09
forum: Gaming &amp; Leisure
---

### Post by ahaslam on 2008-05-09
While playing games in Wine i can ctrl, alt + left/right to switch desktop, though I can't do this in native games such as Nexuiz. 

I assume I'm missing something simple, any suggestions will be greatly appreciated.

---

### Post by eragon100 on 2008-05-09
Yeah, full screen opengl apps such as nexuiz simply can't do that, period. Games running under wine can, because compiz and/or linux can't interact directly with them.

This is also why I can use alt-tab with some windows games under wine, while in real windows this was either completely impossible or chrashed the game :guitar:

---

### Post by ahaslam on 2008-05-09
Thanks for your reply & confirmation. It looks as though a separate Xserver needs to be started, which isn't too convenient or resource friendly. One of Linux's strengths is multitasking, it's a real shame it makes it harder than necessary to interact with other app's in this instance.

PS. Nice sig, I can certainly identify with that. ;)

---

### Post by Gorgofdoom on 2008-05-14
Actually, i just found a very simple solution to this problem. if you follow this link: [http://spring.clan-sy.com/phpbb/viewtopic.php?f=20&t=14644](http://spring.clan-sy.com/phpbb/viewtopic.php?f=20&t=14644), you will find the original source of this walkthru. (i did not write this)

---------------------------------------------------------------------------

This guide has Ubuntu 7.10 or 8.04 in mind, but may work on other distributions, but I won't know.

The aim of this guide is to show you how to setup a separate x-server to run spring. This improves spring's performance and allows you 'alt-tab' (or return to your desktop and back) as you would with windows, but better as that didn't always work well even under windows.

Step 1: Giving users the authority to start x-server sessions by editing Xwrapper.config:

First open the terminal and execute this:

Code:
gksudo gedit '/etc/X11/Xwrapper.config'


You should get something like this at the bottom of that file:

Code:
allowed_users=console
nice_value=0


Now you want to make sure it looks like this:

Code:
allowed_users=anybody
nice_value=0


Save and close you text editor.

Step 2: Edit your Xauthority to allow more than one session (I think :P) :

In a terminal execute:

Code:
xauth
list


You should get an output something like this:

Code:
rutter/unix:0  MIT-MAGIC-COOKIE-1  9fde426e5g03b20f4b7e51cb329d3033
localhost.localdomain/unix:0  MIT-MAGIC-COOKIE-1  9fde426e5g03b20f4b7e51cb329d3033


Yours WILL be different! Now we need to add a new line and then exit to save. So if I were to do this I would type in "add :1.0 MIT-MAGIC-COOKIE-1 9fde426e5g03b20f4b7e51cb329d3033" and then "exit".

Here:

Code:
add :1.0 MIT-MAGIC-COOKIE-1 your string of numbers/letters
exit


Remember YOU have to use YOUR OWN sting of numbers and letters copied form the output we got earlier, mine is just an example. Ok?

Step 3: Making your spring script!:

Open up your favorite text editor and paste this:

Code:
#!/bin/bash
xinit /usr/games/spring $* -- :1


Save it.

4. Making your spring script an executable:

Code:
cd /to/file/directory
chmod a+x ./spring


And that's it. Just run that file and spring with open up in a new x-server session. To swap back to your desktop session the key binding is ctrl+F7. To swap back its ctrl+F9. If you use springlobby or aflobby you just set this file to be your spring executable and it should work as normal.

---------------------------------------------------------------------------

Note: instead of:

#!/bin/bash
xinit _/usr/games/spring_ $* -- :1

just remove the "_/usr/games/spring_" and replace it with your own application/game's executable. 

i have tested this with both TA: spring and Urban Terror, and they both appear to work the same, if not better.

also, you must follow the instructions on the wiki for TA spring for this to actually work

Edit:

also, i do not mean to upset the original writer of this post, only to help spread his idea.(which is a very good one at that!)

---

### Post by Frem on 2008-05-15
An alternate means of fixing this would simply be to write a script to temporarily replace Metacity with Openbox while the game was being played. Edit the  ~/.config/openbox/rc.xml file to remove the keybindings which conflict with the game.

---

