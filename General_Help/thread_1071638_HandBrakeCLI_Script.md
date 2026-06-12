---
title: "HandBrakeCLI Script"
date: 2009-02-16
forum: General Help
---

### Post by SlalomMan on 2009-02-16
My Dad's got an iPod Touch and I'd like to rip some DVDs to it. I know you can use Windows by using DVD Decrypter, Handbrake, Videora, and the whole shebang. That's what he has installed on his computer, and the process is slow and cumbersome. I discovered that HandBrake for Linux and Mac has many more features than the Windows port; Linux and Mac versions can handle encryption, whereas the windows version can't. I have the GUI, but I'd like to make a nice script that does two things in the CLI.
First, it should open up a terminal and display something like "Enter Output File Name: ". Then, the user would type in something like "Movie.mp4."

HandBrakeCLI would then execute the command "HandBrakeCLI -i /media/cdrom -o Movie.mp4 --preset="iPhone / iPod Touch" --longest -b 256" and display the output with progress settings.

If this isn't possible the GUI is also very easy to use; I'd just like a script that runs quickly and does it all in one quick step.

The movie.mp4 would be the only variable that would change, as the DVD would always be in the cdrom slot.

How would i go about doing this? I know C++, but can I use that to make a program like this?

---

### Post by mb_webguy on 2009-02-16
It would be easier to use a shell script.  I haven't tested it, but I think something like this would work.

Here's a start...```
#! /bin/sh

HandBrakeCLI -i /media/cdrom/VIDEO_TS -o "$@" --preset="iPhone / iPod Touch" --longest -b 256

```

If you save this as something like "~/bin/dvd2ipod" and make it executable, you can use it by typing "dvd2ipod filename.mp4".

---

### Post by SlalomMan on 2009-02-16
Thanks. That seems logical. I know how to make a shell script and such, but I'm not familiar with anything aside from running a simple command.

Looks like this is just what I needed.

Thanks.

---

