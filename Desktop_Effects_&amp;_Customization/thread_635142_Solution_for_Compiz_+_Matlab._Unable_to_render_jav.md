---
title: "Solution for Compiz + Matlab. Unable to render java correctly or even launch Matlab"
date: 2007-12-08
forum: Desktop Effects &amp; Customization
---

### Post by Breathe on 2007-12-08
[SIZE="5"][COLOR="Navy"]*********************************** COMPIZ + BERYL ***************************************[/COLOR][/SIZE]

[SIZE="3"][COLOR="Navy"]This solution is for those who have tried adding an environment variable with the next command before executing matlab with no results.[/COLOR][/SIZE]

[SIZE="5"][COLOR="Red"]The old-school solution[/COLOR][/SIZE]

For those, who still don't know what the hell I'm saying... let me explain. Matlab hates Compiz Fusion and Beryl... xD  The problem is that Matlab starts but it doesn't show anything in the window, only a blank screen with a window border (If you mess around with your mouse over the screen you'll see the matlab messages when you cross over an icon). Some people seem to have solved this problem opening a terminal and writing the next code before they run matlab.

> $ export AWT_TOOLKIT==MToolkit
$ matlab

NOTE: If this works for you and solves your problem make the environment variable auto-set on start-up

> $ sudo gedit /etc/environment

Add the string "export AWT_TOOLKIT==MToolkit" to this file and restart


[SIZE="5"][COLOR="Red"]The new solution[/COLOR][/SIZE]

I've been playing around with matlab bin file and searching through the web and found that using the next piece of code just after the "#!/bin/sh" command of your matlab bin file the problem is solved and you don't need the "export" thing

> export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/

The result after editing the file would be something like this...

> #!/bin/sh

export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/

#
#  Name:
#     matlab    script file for invoking MATLAB
#

bla bla bla


Save and run matlab... ;)

Hope this works for all...

---

### Post by rambomedic on 2007-12-19
Woohoo! Thank you! So many other solutions claimed to work, but both of yours worked flawlessly.

Good job!

---

### Post by urosh2 on 2007-12-21
It works for me when i do it in a console. But when i tried to use my batch file program doesn't run, it dissapears in one second. I created a new document matlab.sh

```
#!/bin/sh

export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/

#
# Name:
# matlab script file for invoking MATLAB
#
 /media/sda3/matlab/bin/matlab

```
thank you for help

---

### Post by turboxs on 2008-01-09
Thanks ! Was unable to get "old school solution" to work but your solution worked like a charm for Matlab version 7.3.0 (R2006b) on 7.10 with Compiz fusion.

---

### Post by davis152 on 2008-01-25
Worked for me too on 7.10 with Compiz fusion and Matlab 7.5 (2007b). The old school solution was working (I could see and use Matlab), but I had other strange problems with window focus. For example, if I ran a script that generated a plot and then switched back to the main window, it would not accept keyboard input. I'd have to select a menu with the mouse, then close the menu with the Esc key before I could type again. Tab completion was also broken. The Tab key would bring up a list of possibilities, but I could only select from them using the mouse.

The "new school" solution has fixed all those problems. Matlab now works like it should. Thanks!

---

### Post by mathe on 2008-01-29
The export AWT_TOOLKIT==MToolkit 'solution' is NOT recommended. Sure, at first it looks like a fix but I've seen the weirdest side effects, one being the keyboard focus mentioned but in general huge freeze-ups of the whole desktop. So, although interesting to hear about this possible new solution, I've had it with compiz for other reasons than matlab. Certain websites that, I assume, uses java freezes up while browsing with firefox. And then, after the initial laugh over compiz hilarious desktop effects and realization that it's a lousy human interface, the REAL solution is: TURN COMPIZ OFF, it's faster, better and rock solid.
Hopefully 8.04 will have it turned off by default for a better user experience!

---

### Post by RudolfMDLT on 2008-02-09
hi,

Thanks for this! Just thought I'd add something:

Matlab works fine without compiz running. But when using this method to fix the problem of the matlab buttons not appearing, you have to install "Sun Java 6 Web Start", otherwise matlab won't start.

Why though?:confused:

Thanks for the handy post!

Rudolf

---

### Post by kapst0k on 2008-02-27
Super it works great. Thanks

---

### Post by RudolfMDLT on 2008-03-01
Hi,

Could some one maybe confirm this:

Using this fix "breaks" the ability of matlab to print. When I plot my graphs, and click "File"->"Print", nothing happens, and there are a lot of errors in the main command interface?

uncommenting the line entered here, allows me to print again, albeit, you have to turn compiz off.

---

### Post by kapst0k on 2008-03-26
> **RudolfMDLT said:**
> Hi,

Could some one maybe confirm this:

Using this fix "breaks" the ability of matlab to print. When I plot my graphs, and click "File"->"Print", nothing happens, and there are a lot of errors in the main command interface?

uncommenting the line entered here, allows me to print again, albeit, you have to turn compiz off.

I can confirm that. Exporting the plot (as a .jpg for instance) and printing that file works fine though.

---

### Post by AegisTalons on 2008-04-06
Thanks for the help, I now have matlab working on linux.

---

### Post by mojoe on 2008-04-07
The solutions above work well in case of java rendering problems, but not for the keyboard focus problem at all. By installing the newest version of java jre, this bug is solved too. (on my machine)

ubuntu 7.10
kernel: 2.6.22-14
java-installation: jdk1.6.0_05 (previous: java-6-sun-1.6.0.03)

thanks for the thread and good luck....:)

---

### Post by Adman on 2008-04-08
Hi all

If I use the "old-school solution" (export AWT_TOOLKIT==MToolkit) as well as the "new-school solution" (export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/) in my matlab bin file I get Keyboard focus problems.

If I use only the "new-school solution", I cannot access any help files!

Can anyone help ? ;) Thanks

---

### Post by KosmoZ on 2008-04-18
Pfew thanks man! I was getting really frustrated, hitting my keyboard like crazy with the 1st solution!! Now it seems to work well so far.. From now on it's fun to program in Matlab :)

---

### Post by Adman on 2008-04-18
Guys, 

I had the drawing of my desktop by Nautilus turned off having gone through a tutorial and how to customize the background of each side of the compiz desktop cube.  I found that after re-enabling Nautilus to draw the desktop, most of my problems have gone away, including the Matlab keyboard locking!

I hope this helps!

---

### Post by Parksy on 2008-04-24
The MATLAB_JAVA solution works great for me too.

As an alternative, you can add that line to /etc/bash.bashrc and avoid problems whenever Matlab is updated.

---

### Post by SorryGoFish on 2008-05-16
A year later, still helping people.... thanks.

---

