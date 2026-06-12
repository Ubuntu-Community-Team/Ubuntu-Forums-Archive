---
title: "Messy mouse pointer position and screenshot problems..."
date: 2007-04-23
forum: Desktop Environments
---

### Post by d-Pixie on 2007-04-23
Intro and niceness:

Hi all ... I usually solve my problems (which are notably fewer now than with windows, and always solvable) with a combination of ubuntuforums and google. It takes a couple of hours, but the learning experience is totally worth it!
But now, sadly, I've run head long in to a brick wall. So, dear friends and fellow bug stumblers, see if you recognize any of the following ;o)

Setup:

This might well be a first, but. I have two cards in my computer, both ATI. One is a 9200pro PCI and the other is a x700 AGP. The x700 has two screens attached to it and the 9200pro has one.
My xorg is setup to use one server, one session for all three screens. So I span them all with xinerama to one huge desktop. Very nice, and loads of screen real estate ;o)

Setup is as follows:

card                     |  9200  | x700 | x700 |
connection         |  VGA    | VGA   | DVI    |
screen number  |  3         | 2        | 1        |
(in xorg.conf)

And thats how the setup looks IRL to, ei thats how the screens are orientated on my desk ...

Problems/Symptoms:

Part 1, the cursor: And now the dark side. The mouse pointer bugs frequently in two ways: 
1. It "sticks" in a certain form (hand, arrow, resize ...) on screen 2 and wont return to normal until I move the pointer to the bottom right corner of screen 1.
2. The pointer is correctly oriented on the desktop. But when I pass over the edge (window decorators border) of a window (read program) it offsets about -20, -20 px. Thats 20 px both up and left for you who don't read screen x y offsets ;o) And the problem is thats it's only the pointer that jumps, not the actual mouse position. Working with anything that requires precision is a nightmare (gimp, inkscape, any selections). This problem only appears on screen 1 and 2.

Part 2, the screen shot: I'd have loved to attach a screen shot of this in action. But unfortunately 
the gnome screen shot tool only takes a picture of screen 3. Sure, the space is reserved for screen 1 and 2, but there is no image to be found ;o) I've included a screen anyways, just to show the problem.

Also included my xorg.conf, for your reading pleasure ;o)

Sketching the reasons:

I first suspected my use of ATI's fglrx drivers for my sorrows. But a close inspection of the ATI bugzilla page gives at hand that none of the known bugs fit my bill. But I wont exclude it from the suspects list.
Now I'm leaning towards xinerama as the culprit but I cant substantiate the claim.
It could also be a problem with Gnome itself. But again thats just a fall back, I can't prove anything.

Thanks and bye (for now):

Hope someone recognizes one or two of the problems and has an idea of a solution. Thanks for reading anyway. Best regards and no bugs to all of you! /Jonas Erlandsson, Sweden

---

