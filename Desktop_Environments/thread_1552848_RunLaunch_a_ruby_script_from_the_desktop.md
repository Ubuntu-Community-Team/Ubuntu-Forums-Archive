---
title: "Run/Launch a ruby script from the desktop"
date: 2010-08-14
forum: Desktop Environments
---

### Post by dglnz on 2010-08-14
okay I've got 2 **fxruby** programs and they run from the command line okay
but now I want to have it _executed from the KDE desktop_.:confused:

things I'd tried

1. copy konsole (terminal) to the desktop and change settings so that a
script would run.:(

2. repeat for 2nd program.

**PROBLEM** they both ***share*** 1 .desktop config settings file (so change something for 1 version, open the other up and _its changed too_.

**solved this** by copying and renaming the .desktop file
now I have _[COLOR="Blue"]myscript1.desktop[/COLOR]_ file and _[COLOR="Blue"]myscript2.desktop[/COLOR]_ file each
pointing to their own directories but they wont work!!  From the file
manager I can right mouse click them and see from the pop-up sub menu
Open-with the 2 config files and they work there but this is a poor
second.:o

**PROBLEM**

these programs would not execute/launch from the desktop icons!! :mad:

**SOLUTION?**

Found that my moving the .desktop files from
      [COLOR="red"]/home/user/.local/share/applications[/COLOR]
to
     [COLOR="red"]/home/user/.local/share/applications/kde4[/COLOR]

I get the action I want namely user clicks on the icon for ruby script
it gets executed just like a 1st class kde program.:D

It is by chance that it has a GUI frontend and i get the benefit of
having NO CLI console visible too so this is equivalent to the .rbw
files in windows.

Hope this helps someone down the track.

rgds,

Dave. ):P

---

### Post by chip616 on 2010-09-12
Dave:

Yes, this will probably help me.  I have a few rsync scripts that I need to run from desktop icons.  I've been doing this happily in KDE 3.5 for a long time.  I'm now moving to KDE4, and a new learning curve.  I came across this thread by accident while looking for something else, but it will be very valuable to me.  Thank you for taking the time to post it.

Frank.

---

