---
title: "XFCE OpenGL 3D desktop"
date: 2014-12-15
forum: Desktop Environments
---

### Post by tcll5850 on 2014-12-15
kinda surprized nobody's attempted this yet... :P

I'm a PyOpenGL programmer who's worked with:
-GLUT
-freeglut
-QtGL
-SDL (pygame)

I hate all of them, the best one with the most base-support and no issues seems to be GLFW :P

anyways... what I'd like to do is turn my desktop into a house I can walk through with various rooms that can be resized, extended, and whatever.

your desktop icons can be turned into wall objects or other objects that can be interacted with.
(I'm hoping to go as far as game characters that can walk around your house)
 for me, that'd be a pikachu that I can click on to start up a game I'm working on :P
or perhapse your front door opens up Chrome (walking outside into the internet, lol)

you can prbly tell by now I'm autistic and have a severely overactive imagination. :P
lolol

anyways I love XFCE as it has the most customizable interface that can make my desktop look like WinXP.
I've used 3D desktops before with WinXP:
[[IMG]http://lh5.ggpht.com/-PvJ_WxZoG54/U6sEjBHVWTI/AAAAAAAAG7Y/7QZ07KXL1I4/s640/WinXP.jpg[/IMG]]("http://lh5.ggpht.com/-PvJ_WxZoG54/U6sEjBHVWTI/AAAAAAAAG7Y/7QZ07KXL1I4/s1400/WinXP.jpg")
^XFCE has given me the same layout,
but with a top-bar that actually resizes my windows appropriately, and goes across both of my monitors like I want:
[[IMG]http://lh6.ggpht.com/-hyuTprApGr4/VImxYnh--VI/AAAAAAAAIGE/ZPBTo6etea8/s640/Screenshot%2520-%252012112014%2520-%252009%253A59%253A13%2520AM.png[/IMG]]("http://lh6.ggpht.com/-hyuTprApGr4/VImxYnh--VI/AAAAAAAAIGE/ZPBTo6etea8/s3200/Screenshot%2520-%252012112014%2520-%252009%253A59%253A13%2520AM.png")
^both of these images are clickable. ;)

so my question is does anyone know how I can get PyOpenGL working on my desktop??

---

### Post by tcll5850 on 2014-12-15
also, I must note, you'll see stuff that says I'm a hacker...
I'm not a hacker in the traditional stereo-typed sense.
I hack to do cool stuff, such as get Win7 Aero working on WinXP (if I knew how)

unfortunately that ain't never gonna happen with me as I hate what MS put in the new kernels that gives everyone complete control over your compy (once figured out).
I have a Win7 laptop I'm trying to empty all my game-rips off so I can install Linux on that (it was given to me as the screen was snapped off, and at the time, I couldn't fix the compy I'm on now).

so yes, I'll admit I'm a hacker, but I'm not the type of hacker who'd go around doing stupid stuff like DDoS-ing, RATting, or even web-hacking and stealing money.
I don't do that and never will, I know about these things as I have friends who think they're "special" with these tools, and I keep telling them they're idiots... heh

so I hack for knowledge to do cool stuff :)
(such as removing viruses from system32 or sysWOW64)

---

### Post by tcll5850 on 2014-12-16
anyone??

comon guys, I feel as excited as a kid getting his first game system just thinking about this idea. :3

and I've seen OpenGL desktops done before, though I'm not sure if that was XFCE or something else...
XFCE looks to be capable of doing it though... but how?? >.>

---

### Post by grahammechanical on 2014-12-16
Hi

It is good to be enthusiastic and willing to work at what you want to do. I have no qualifications in this area as I am not into hacking code. Yes, I am old enough to remember what a hacker originally was and still is, I suppose.

[http://ubuntuforums.org/showthread.php?t=2144468](http://ubuntuforums.org/showthread.php?t=2144468)

It seems that standard XFCE does not use an OpenGL compositor. Ubuntu uses Compiz for this. That can also be installed. Have you tested getting PyOpenGL working in Ubuntu+Compiz? If that works then you know that installing Compiz on Xubuntu will work. I am assuming that you are using Xubuntu. But I understand that Compiz  will replace the XFCE window manager which you may not want. So, Compton or something similar may be the direction for you.

[http://www.neowin.net/forum/topic/1148464-using-compton-for-tear-free-compositing-in-xfce/](http://www.neowin.net/forum/topic/1148464-using-compton-for-tear-free-compositing-in-xfce/)

The PPA is up to date with the recent releases of Ubuntu and its flavours built on Ubuntu.

[https://launchpad.net/~richardgv/+archive/ubuntu/compton](https://launchpad.net/~richardgv/+archive/ubuntu/compton)

Regards.

---

### Post by tcll5850 on 2014-12-16
nice =)
many thanks :)

hmm... I'm honestly not sure what exactly is installed, Linux on my compy started it's life as Zorin OS (I think 6) which was Ubuntu 12.04, then I upgraded from that to Ubuntu 14.04 before playing around with Gnome a tad...
after figuring out Gnome couldn't span both of my monitors, I tried a bunch of different DEs, which each had their own issues:
-desktop files displayed on only 1 monitor (Lubuntu), or in a particular window (KDE)
-options and UI was scattered, didn't display correctly, or was just a pain to use (Unity, MetaCity, and a few others)

so I finally found XFCE/Xubuntu and was able to configure that in a similar fashion to SharpEnviro on my WinXP image :P

I'm not sure if Compton might be installed, but I've seen Compiz here and there, and THAT might be installed


I see alot of people having issues with tearing it seems >.>
luckilly I use some CRT monitors I've tweaked, so I don't have to worry about tearing. :P
(CRT monitors have smaller pixels than LCD monitors, though the WiiU game-pad can compete with it's pixel-size)

I still prefer the triad pixel layout over squares as shapes blend better and aren't so edgy around the curves.
(I don't need antialiazation to fix that for me) :3


anyways, I'm working on a project that uses pygame with PyOpenGL...
here's an image of that with my current window manager:
[IMG]http://lh3.ggpht.com/-5A5VbtuxJ0s/VI0d58yu0wI/AAAAAAAAIGg/5a0L_PL7a_Q/s802/Screenshot%2520-%252012142014%2520-%252012%253A17%253A44%2520AM.png[/IMG]

so yea, it works, I'm just not sure what I have that makes it work... heh

*checks window manager*
oh wait, that's Numix, I don't see compiz or comption, but I'll try them out :)

EDIT: nvm, I don't need to remove numix, my mistake :P

---

### Post by tcll5850 on 2014-12-16
ok, so I've gotten this far where my desktop actually renders with OpenGL... thank you grahammechanical :)

anyone have any references for an interactive desktop BG with compton??

---

### Post by grahammechanical on 2014-12-16
I came across this for you. It is not answer for your last specific request. Just more information.

[http://duncanlock.net/blog/2013/06/07/how-to-switch-to-compton-for-beautiful-tear-free-compositing-in-xfce/](http://duncanlock.net/blog/2013/06/07/how-to-switch-to-compton-for-beautiful-tear-free-compositing-in-xfce/)

Check out the links at the bottom of the page for the source of much of the information. You might want to think about showcasing your work in the Cafe section of the forum.

Regards.

---

### Post by tcll5850 on 2014-12-16
thanks :)

> **grahammechanical said:**
> You might want to think about showcasing your work in the Cafe section of the forum.

haha, I was already considering a means of sharing my work :)

I was just recently talking with my UMC group about this project, and had the idea to implement an older idea I had for a similar project to this, but as a game rather than a virtual world.
imagine having an avatar like on X360, where you could walk around as that avatar in your desktop-house and interact with your desktop items and such.

the idea of the front door being the internet could be changed to where you could actually walk outside.
ideas for the outside world are being discussed, but for the most part, should turn into something like Oz from Summer Wars, 
except with alot less control over resorces compared to the movie :P

idk... that front-door area is really left wide open for whatever ideas flow... heh

the main purpose though is to be able to interact with other's avatars in a similar fashion to something like an open-world Sims, but everyone is their own person.
(there's a better comparison, but I'm not thinking of it atm... heh)

---

### Post by tcll5850 on 2014-12-24
just wanted to note, I've found a method to have a 3D desktop BG, but it's not entirely what I'm looking for...

I've created a new issue here of me simply trying to get this working.
[http://ubuntuforums.org/showthread.php?t=2257983&p=13193314#post13193314](http://ubuntuforums.org/showthread.php?t=2257983&p=13193314#post13193314)

I think the best method I could do though would simply be to replace xfdesktop with my 3D desktop application.

anyone know how I could do that??

EDIT:
any documentation as to how to build a desktop management interface??

---

### Post by tcll5850 on 2015-01-04
well, I'm on the start of something with this:

```

#Gnome-tested: (original code)
#export SDL_WINDOWID=`xwininfo -root|grep "id:"|sed 's/^.*id: //'|sed 's/ (.*$//'`
#XFCE-tested:
export SDL_WINDOWID=`xwininfo -name "Desktop" | grep 'Window id' | sed 's/.*\(0x[0-9a-z]*\).*/\1/g'`
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false

python `exec '''

import pygame
import sys
import random
import time

pygame.init()

window = pygame.display.set_mode((1280, 1024))
screen = pygame.display.get_surface()

while 1:
    for event in pygame.event.get():
        if event.type == pygame.QUIT: sys.exit(0)

    x = random.choice(range(640))
    y = random.choice(range(480))
    radius = random.choice(range(100))
    col_r = random.choice(range(255))
    col_g = random.choice(range(255))
    col_b = random.choice(range(255))

    time.sleep(.01)
    rect = pygame.draw.circle(screen, (col_r, col_g, col_b), (x,y), radius)
    pygame.display.update(rect)

'''`

```
NOTE: IDK how to run python in a shell-script, so that doesn't work...
if local directories worked, I'd post that

here's a local directory method that doesn't work
```

#Gnome-tested: (original code)
#export SDL_WINDOWID=`xwininfo -root|grep "id:"|sed 's/^.*id: //'|sed 's/ (.*$//'`
#XFCE-tested:
export SDL_WINDOWID=`xwininfo -name "Desktop" | grep 'Window id' | sed 's/.*\(0x[0-9a-z]*\).*/\1/g'`
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false

python ./desktop_circles.py #this method is used in another program's launcher, which works just fine for that
#python ~/desktop/desktop_circles.py #alternate, also doesn't work

```


the actual code itself works, but I had to use a stupid full directory...

I'd like to get one of the 2 above methods working, favorably the 2nd.


on XFCE:
the only downside is the desktop is still active, so clicking anywhere shows your original desktop for a frame before it's over-drawn.
I personally havn't tried Gnome


now if I can figure out how Compton works, I can rasterize the windows in a 3D space.

---

