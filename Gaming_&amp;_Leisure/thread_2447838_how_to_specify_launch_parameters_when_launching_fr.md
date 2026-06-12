---
title: "how to specify launch parameters when launching from terminal"
date: 2020-07-27
forum: Gaming &amp; Leisure
---

### Post by jcdenton1995 on 2020-07-27
Hello all,

Last night I downloaded 'streets of rogue' from GOG.com and installed it by running the provided shell script. However when I tried to launch the game I was met with a purple screen - a common problem apparently.

The solution is to launch the game with the following parameters ```
-screen-width [screen width] -screen-height [screen height] -screen-fullscreen 0
```but how do I do this? I tried appending the above syntax to the end of the start command but it seemed to have no effect as the game still launched in full screen, I tried just adding it under "options" within the shell script that launches the game but that had no effect either. In the end I think I managed to get it working by editing ~/.config/unity3d/Streets of Rogue/Streets of Rogue/prefs.txt to specify my monitors resolution, however I'd like to know how to pass the parameters using the terminal

Is the syntax for passing parameters to a program unique to that specific program? or are there some parameters that are universal and some which are specific to a program? If so how is someone expected to know what they are?

---

### Post by Holger_Gehrke on 2020-07-27
No, the syntax for options and parameter is completely up to the program. There are some conventions like '--' for long and readable option names and '-' for short options (and there's getopt, a function in the standard libraries that makes doing things that way quite simple ...) and there are some options that a lot of programs have like '-v' for verbose or '-q' for quiet, but that's all they are, conventions and options used by a lot of programs. There are some standard option for programs that use the same set of libraries, but those are options to the libraries, not to the program itself. 

Finding out options should normally be a matter of reading the documentation. If the documentation is bad or incomplete you can try to run 'strings' on the program file, but you'll need a lot of patience and a bit of luck with that approach.  For open source programs you can of course look at the source code, but for a commercial product that usually is not an option.

Holger

---

### Post by jcdenton1995 on 2020-07-28
> **Holger_Gehrke said:**
> Finding out options should normally be a matter of reading the documentation.

Thanks, yeah I've had a poke about online but I can't find any documentation or anything, I could message the developer but it works now so I'll probably not bother. The syntax that he/she gives (which I wrote in my original post) doesn't seem to work for me, I did try using it with two dashes in front of each option as I thought it was strange that long options would have a single dash in front, but still it had no effect.

It's definitely a fun game though! I was a little underwhelmed at first as I didn't really know what rouge-lites were all about and I thought it would be more rootin' tootin' shootin', but after a few hours I realised it actually has lot's of interesting gameplay mechanics and good depth.

---

