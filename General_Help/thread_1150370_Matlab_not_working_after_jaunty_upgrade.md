---
title: "Matlab not working after jaunty upgrade"
date: 2009-05-06
forum: General Help
---

### Post by aptperson on 2009-05-06
I have recently upgraded to jaunty, which went well. Now Matlab does not work. when I go to run Matlab I get the following:

/usr/local/matlab/bin/glnx86/fvwmfix: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
/usr/local/matlab/bin/glnx86/MATLAB: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory

I am running version 2008b.

Now I thought about reinstalling Matlab to see if this would help but I get a similar error


                         Welcome to the MATLAB Installer

   ---------------------------------------------------------------------------
   | Please review the license agreement on the next set of screens.  On any |
   | screen the options to proceed are at the bottom.  Type your response    |
   | at the prompt.                                                          |
   ---------------------------------------------------------------------------

                      The MathWorks, Inc. [screen 1 of 87]
                      -------------------                 
Software License Agreement 


IMPORTANT NOTICE

READ THE TERMS AND CONDITIONS OF YOUR LICENSE AGREEMENT CAREFULLY BEFORE 
COPYING, INSTALLING, OR USING THE PROGRAMS OR DOCUMENTATION.
----------------------------------------------------------------------------
                >>>>>>>> For this License Agreement <<<<<<<<
Enter either:  <return>       a        r        p      ^C
To:          [next screen] [accept] [reject] [print] [abort]
----------------------------------------------------------------------------
> a
/media/cdrom0/unix/update/bin/glnx86/xsetup: error while loading shared libraries: libXp.so.6: cannot open shared object file: No such file or directory


I have searched my computer and found the two files that 'do not exits', they are in /usr/lib
I have also made symbolic links to these files in the directories, but to no avail (well actually only the first one, but I got the same error).

Any help would be great.

Thanks in advance.

---

### Post by aptperson on 2009-05-06
I managed to solve my own problem. I had to install the 32 bit libraries using getlib.

---

### Post by madu on 2009-05-26
I have a similar problem.
Could you please elaborate what you did?

Thank you.

---

### Post by aptperson on 2009-05-26
Firstly I am using 32bit student Matlab on 64bit Ubuntu. What I think happened is that when I upgraded from 8.10 to 9.04 the 32bit version of libX11.so.6 must have been removed as it was no longer required by Ubuntu. So I installed getlib, which I am pretty sure I down loaded from the internet not from the repositories (not to say that it isn't in there somewhere). The place I got it from had pretty good instructions on using it, or maybe this forum, I can't quite remember. Then I used getlib to install the required 32bit libraries, which I my case was: libX11.so.6.

I hope this helps.
Good luck.

---

### Post by madu on 2009-05-26
Thanks Aptperson.
I got this error after going from 8.04 to 8.10.
The Matlab was working super until this. NOw I get the :SimpleException:.
I have tried everything on the web to no avail. Even re-installed.

---

### Post by XCan on 2009-05-27
> **madu said:**
> Thanks Aptperson.
I got this error after going from 8.04 to 8.10.
The Matlab was working super until this. NOw I get the :SimpleException:.
I have tried everything on the web to no avail. Even re-installed.

Just for the sake of it, have you tried starting matlab in a terminal, what kind of output does it give? Have you also tried it in a terminal with the -nojvm switch?

I can just add that I've gone from 8.04 -> 8.10 -> 9.04 with the same Matlab install with no issues. Both Ubuntu and Matlab on 64 bit though.

---

### Post by madu on 2009-05-27
> **XCan said:**
> Just for the sake of it, have you tried starting matlab in a terminal, what kind of output does it give? Have you also tried it in a terminal with the -nojvm switch?

I can just add that I've gone from 8.04 -> 8.10 -> 9.04 with the same Matlab install with no issues. Both Ubuntu and Matlab on 64 bit though.


Thank XCan.
I always start from the terminal and I tried the -nojvm but still the same result. 
But, I upgraded to 9.04 and then it starts working again!
Originally I was going to go from 8.04->8.10->9.04. But when I tried to go to 9.04 the upgrade manager said I will have video issues because I have an ATI card. So I didnt upgrade to 9.04. But because of this issue, I decided to go for it anyway becuase right now Matlab was more important for me.
Anyway the Matlab works but the display is screwed. Got to fix that now. Even my terminal didn't work after the upgraded! I had to put some line I found from web into the fstab. Who would've thought that!

Thanks a lot guys. Sometimes its very strange what Ubuntu does.

---

