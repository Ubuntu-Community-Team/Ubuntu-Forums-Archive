---
title: "Video editor"
date: 2006-08-16
forum: Desktop Environments
---

### Post by Chris Tucker on 2006-08-16
Yet again, im looking for a video editor.... I need something with reasonable transition options, and control of things like zoom and pan for static images (jpegs in this case)
I have tried Blender's sequencer before, and it was a major headache generator because the interface is so different...
I have legal access to an outdated copy of Adobe Premiere 5.0 , which i know how to use well, but i want to keep it linux (without wine), and i want something a little more up to date...

I'm saying a video editor not just fancy things in a presentation program because this will be a video/slide show for a wedding thats eventually going to be exported to DVD...

anyone know any such app(s)? i dont need a lot of transitions, most used will be crossfade, but i definatly need to be able to zoom and pan images...

---

### Post by orb9220 on 2006-08-16
Non-linear editor for Digital Video data
Kino allows you to record, create, edit, and play movies recorded with DV
camcorders. This program uses many keyboard commands for fast navigating and
editing inside the movie.

The kino-timfx and kino-dvtitler are now provided with kino.

In synaptic

---

### Post by orb9220 on 2006-08-16
Cinelerra does primarily 3 main things: capturing, compositing, and editing audio and video with sample level accuracy. It's a seamless integration of audio, video, and still photos

[http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3)

---

### Post by chalex on 2006-08-16
You should also look at the Diva video editor: [http://www.diva-project.org/](http://www.diva-project.org/) 
The site seems down at the moment.

---

### Post by gunksta on 2006-08-17
I really don't recommend messing around with Kino, PiTivi, Diva, etc. They *will* be terrific apps, I'm sure. But for right now, they are limited in the extreme. They can only handle dv from a digital camcorder. So, if you have video files on your hard drive that you want to edit....like .mpg or .mov files, you are out of luck with the current crop of GNOME video editors. 

I'm sure they will eventually import other formats since they all seem to be using gstreamer as their underlying engine...but right now they aren't really very good.

OTOH, Cinelerra is quite nice. It's kind of hard to figure out, but once you do, it is wonderful. I don't recommend the link above. The upstream guys don't provide any binaries and compiling cinelerra is a bear. If you decide you want to spend all day compiling, search the forums for the How-To, it will save you hours. I prefer to use binaries whenever possible. There is a community oriented version of Cinelerra here: [Cinelerra]("http://cvs.cinelerra.org/")

I you decide to explore this option, you will need to read [this]("http://www.kiberpipa.org/%7Egandalf/ubuntu/README"). The directions worked flawlessly for me. But of course, YMMV.

Two other options are [LIVES]("http://lives.sourceforge.net/index.php?do=downloads") and [Jashaka]("http://www.jahshaka.org/content/blogcategory/1/46/"). I never could get the Ubuntu version of Lives to do anything other than waste processor cycles. According to their documentation, there is something wrong with my ALSA setup..but none of their solutions helped me and all of my other apps work great. I got Jashaka running with minimal effort and it looks great but I couldn't figure out how to make it do anything. But, it does look exciting and the idea of using OpenGL for this is definitely the way to go...now if I could just figure out how to make it do something......

If you decide to start playing around with installing and uninstalling various repositories / programs, I recommend using aptitude over synaptic or apt-get. 

Aptitude does a good job of locating orphaned libraries and will offer to remove them too if you delete a program. For example: 

If program foo requires lib-bar, apt-get will install lib-bar. Synaptic and aptitude do the same thing. You gotta love intelligent package management.

But if you remove foo using apt-get / synaptic, they will leave lib-bar on your system. In contrast, aptitude will offer to remove lib-bar for you. This helps prevent you from having lots of unnecessary libs scattered all over the system.

I hope this brain dump is useul to somebody.

---

### Post by Chris Tucker on 2006-08-18
current findings: Cinelerra - waste of time. EDIT: er, maybe not... Spent 1.5 days getting it working, and half a day learning it. Its an awesome program, but it cant do what i need to do.. i can only mimic my original version of the video i'm creating, which was with windows movie maker... "ease in" and "ease out" is a little too simple, im looking to recreate the "ken burns effect" like iMovie can (wish i had a mac but i dont ... and im not about to go grab OSX86...)
EDIT: managed to do this, takes a lot longer to do than iMovie (just a checkbox), but all i was missing was a few extra keyframes... slow to render but not worried, ive rendered 3D animations from raw 3D model data before... now THATS slow! ;)

Kino seems to be only for DV editing... cant get it to load any of my files.

about to try LiVES, and or jashaka... the diva site is broken
EDIT: LiVES is really... weird. and never got a chance to try jashaka before i got cinelerra to do what i needed...


Thanks to everyone for your help in finding an application to do this... i think cinelerra really has the potential to rival things like Adobe Premiere!

---

