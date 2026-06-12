---
title: "OpenOffice.org Launchers - Call them by name"
date: 2010-12-08
forum: Desktop Environments
---

### Post by jlanawalt on 2010-12-08
I've been using OpenOffice.org (OOo) since sometime in it's 1.x version and I've seen the launch experience migrate from the "one application" experience where you have a single icon that pulls up the application in "Start Center" mode to the multiple-icon direct launch mode.

When OOo was launching as a "*Works" type application on other platforms where you'd pick "Text Document" at the launch screen, it was a pretty easy mental mapping to click "Word Processor" in the office menu in Ubuntu. Once the "Start Center" wasn't default on Windows, it became more of a mental disconnect when switching platforms. "Where is Writer? Oh ya, 'Word Processor'".

Around the Ubuntu 10.10 release I got into the Unity shell buzz and decided to try it on my laptop. I had been using Windows 7 for a few months and saw some enjoyable similarities in my user experience. In W7 I have gotten into a habit of hitting the windows key and typing Writer or Calc and hitting enter to pull up OOo Writer or OOo Calc. In Unity I pulled up applications and tried to search for Writer as was my habit. No dice. Again that disconnect.

What do I install when I want to do word processing with OpenOffice.org? Writer

What is the command line argument to ooffice to launch the word processor? -writer

When I go to OpenOffice.org to look at the product description, what does it contain? Writer, Calc, Impress, Draw, Base, and Math.

The Unity application search pushed me over the edge for a rant, but not far enough to make a QA account for Brainstorm. I want the desktop file to list OOo applications by name, and not by function. I want "OpenOffice.org Writer" or just "Writer" and not "OpenOffice.org Word Processor." I don't want to tell someone "Open Writer" and have to follow up with, "Oh, ya on Ubuntu it's called Word Processor."

What do you think?

---

### Post by bobcollard on 2010-12-08
user/bin/oowriter is the command  Find icons in usr/share/icons  be aware it is case sensitive.

---

