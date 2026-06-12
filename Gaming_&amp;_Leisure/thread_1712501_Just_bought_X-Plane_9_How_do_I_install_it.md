---
title: "Just bought X-Plane 9 How do I install it?"
date: 2011-03-22
forum: Gaming &amp; Leisure
---

### Post by pepsifx357 on 2011-03-22
There are only Mac and Win installers on the DVD, however under the "X-Plane 9" folder, there is a folder called Linux that contains a zip file named "X-Plane_i686."  Within that zip, there is a file with the same name.  I tried to run it with "Allow executing as a program" enabled.  All it did was bring up an empty window called X system and then dissapeared.

Am I doing this wrong?

Can you install X-Plane 9 on Ubuntu 10.04 using the retail DVDs?

EDIT:  Nevermind, I found an installer package on X-Plane's website that jump-started the install process.

---

### Post by lyricalpapa on 2011-03-22
Hi pepsifix,

It's been a while since I last ran x-plane 9, but there are some good write-ups on-line.

Start with a Google search for "ubuntu x-plane linux".

In general, you will first need to install ia32libs.

You will then need to run the linux installer batch file. There should be a copy on disk one or you can download the latest version from the X-plane site.

Enjoy. MS has laid off their flightsim programmers, so it looks like X-Plane might become the only fs left. Some of the third party vendors are now advirtizing support for X-Plane.

---

### Post by pepsifx357 on 2011-03-22
As far as I know ia32libs is no longer in the repository in 10.04.

```
ben@ben-desktop:~$ sudo apt-get install ia32libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32libs

```

I didn't need it though, after I downloaded the installer from their site, it ran like a champ.  

Now I can't get my saitek x52 controller to work.  lsmod shows me that a module is loaded for it.  I went to the /dev directory in nautilus and plugged\unplugged the controller until I found the file for it.  /dev/hidraw4.  I noticed that other people were saying that the joystick was under /dev/input/, so I went there and found 6 files called event*  the one that seemed to represent my joystick was event6 however no matter what I tried I couldn't get jscal to read it.  Here are some examples.

```
ben@ben-desktop:/dev$ sudo jscal -c /dev/hidraw4
jscal: error getting version: Invalid argument

```

```
ben@ben-desktop:/dev$ sudo jscal -c /dev/input/event6
jscal: error getting version: Invalid argument

```

Most people say this controller works right out of the box, which I beleive.  But seeing as how this is me trying to get it to work it's not.  In X-Plane the most I got out of it was the joystick moving the mouse.  When I go to setup the joystick in the game none of the axises move.

I'm really not sure what to do here.

EDIT: I'm getting this with jtest

```
ben@ben-desktop:~$ sudo jstest --normal /dev/hidraw4
[sudo] password for ben: 
Driver version is 0.8.0.
jstest is not fully compatible with your kernel. Unable to retrieve button map!
Joystick (Unknown) has 2 axes and 2 buttons.
Testing ... (interrupt to exit
```

I think it might be a kernel problem.  I run a studio with this computer and it's running an RT kernel.  I will try to install a normal kernel and try again.

---

### Post by pepsifx357 on 2011-03-23
Yup, it was the kernel.  However, Its still buggy.

---

### Post by lyricalpapa on 2011-03-23
Had problems with my joystick too - it was a Saitek.

Tried a friend's Thrustmaster and it worked fine.

So I got a TM on sale and that's what I use now.

You might try Saitek's internet site to see if they've released a Saitek driver for Linux.

Btw, you might have to unplug your joystick when you run other games like Quake Wars.
:popcorn:

---

### Post by pepsifx357 on 2011-03-24
When I'm in 3D cockpit view, the joystick will move the mouse.  You can see how that causes a lot of problems, considering the mouse moves the camera.  Kinda sucks.

---

### Post by bjdiaz1 on 2011-08-15
I run X-Plane 9 on my wife´s MacBook just fine, but would like to install it on my computer running Ubuntu Linux 11.04 so I can give her laptop back.   I downloaded ´X-Plane DVD Installer Linux´ and followed X-Plane website instructions on getting all the necessary libraries.  I´m stuck on what I believe should be the simplest task. In the Terminal I typed ´cd Desktop´ and I get the prompt: 
     bernie@ubuntu:~/Desktop$
Then I typed:
    ./&#8221;X-Plane DVD Installer Linux&#8221;
which is supposed to launch the installer and I get the this message:
bash: ./¨X-Plane: No such file or directory

I´m a real novice when it come to the Terminal and it looks like a simple problem to resolve if I just knew a little more about working with files in the Terminal.  I need a compassionate soul to have pity on my ignorance and tell me what to do.

---

### Post by GWBouge on 2011-08-15
> **bjdiaz1 said:**
> 
Then I typed:
    ./&#8221;X-Plane DVD Installer Linux&#8221;

Put the quotes around the entire path, not just the file name.

```
~/Downloads$ "./X-Plane DVD Installer Linux&#8221;
```

Or, you can just type the first character or two and hit TAB, and it will fill in the rest with escaped spaces, like:

```
~/Downloads$ ./X-[press TAB]
# should autocomplete to:
~/Downloads$ ./X-Plane\ DVD\ Installer\ Linux
```

If it doesn't run ('command not found' or something like that), make it executable, and try again.

```
~/Downloads$ chmod +x ./X-Plane\ DVD\ Installer\ Linux
~/Downloads$ ./X-Plane\ DVD\ Installer\ Linux
```

---

