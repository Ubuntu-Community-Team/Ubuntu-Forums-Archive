---
title: "Interpid + Matlab (R2007b) experiences?"
date: 2008-11-03
forum: Education &amp; Science
---

### Post by ppm on 2008-11-03
I am consider update 8.04 -> 8.10, but I am worried if Matlab (R2007b) runs ok after the update :confused:

So I would like to hear if anyone has some experiences.

Cheers

---

### Post by chengzi86 on 2008-11-03
**[Plastic valve](http://www.corrosion-resistant-valves.com)** special for controlling the corrosive media which features low weight, nonpoisonous and no pollution. It has wide temperature adaption, high mechanical stress and can take place of many kinds of expensive rare metal. It is high economic benefit. plastic valve [www.corrosion-resistant-valves.com](www.corrosion-resistant-valves.com)

---

### Post by loe on 2008-11-04
Im running Matlab 7.4.0 (R2007a) Student Edition. I installed it with hardy in /opt/Matlab_740.

After the upgrade to intrepid everything worked like before :-)

---

### Post by iToy16 on 2008-11-04
Matlab 7.4.0 (R2007a)???


:confused:

---

### Post by loe on 2008-11-04
Matlab R2007b has Version Number 7.5

The upgrade should have same effect on 2007a and 2007b...

---

### Post by emmdarakis on 2008-11-04
I'm relatively newbie in Linux too, so my experience might not be 100% accurate.

I'm using matlab 2008a and recently upgraded to ubuntu Intrepid. Matlab itself, simple m files etc work fine BUT Intrepid installs by default gcc 4.3 (c/c++ compiler) which IS NOT supported by matlab!

For several days now I'm trying (unsuccessfully so far) to add and use gcc 4.2 because I need to compile some files.   

This will (probably) affect you only if you are using/compiling mex files, and not for standard simple m functions. 

You can check which compilers are supported by your version at

[http://www.mathworks.com/support/compilers/previous_releases.html](http://www.mathworks.com/support/compilers/previous_releases.html)

Hope this helps and good luck...

---

### Post by ppm on 2008-11-04
Yes, 7.5.0.338 is the version in question.

> **emmdarakis said:**
> I'm relatively newbie in Linux too, so my experience might not be 100% accurate.

I'm using matlab 2008a and recently upgraded to ubuntu Intrepid. Matlab itself, simple m files etc work fine BUT Intrepid installs by default gcc 4.3 (c/c++ compiler) which IS NOT supported by matlab!

For several days now I'm trying (unsuccessfully so far) to add and use gcc 4.2 because I need to compile some files.   

This will (probably) affect you only if you are using/compiling mex files, and not for standard simple m functions. 

You can check which compilers are supported by your version at

[http://www.mathworks.com/support/compilers/previous_releases.html](http://www.mathworks.com/support/compilers/previous_releases.html)

Hope this helps and good luck...

Thank you for emmdarakis. The problem that emmadarakis has is the very reason to ask the original question. It seems that no update goes smoothly regarding the compatibility, specially in case of Matlab.

emmdarakis: I think you could try to check if gcc 4.2 is installed:
```
sudo apt-get install gcc-4.2
```
Next, it should be told to Matlab to use this version. However, I do not know how to do that (symbolic link, environment variable etc. ?)

---

### Post by emmdarakis on 2008-11-04
ppm,

Thanks for the interest to my problem.

Yes, using an earlier version of gcc is possible (although it needs some tricks to overcome the default newer version during compilation - see [https://sourceforge.net/forum/message.php?msg_id=5570019](https://sourceforge.net/forum/message.php?msg_id=5570019) on the way that worked for me), and then everything should work fine.

In my case I had a second problem, but it didn't have much to do with matlab. Some conflicts in the repos I was using were preventing ffmpeg from being installed properly. And that didn't allow me to compile the things  I wanted. Now everything seems to be ok...

---

### Post by Tonie168 on 2008-11-05
I did a clean install of II and after that I installed matlab 2007b. Both 64-bit programmes. The license is correct and I first start the license manager. But when Matlab opens, it is all grey. It first says 'Initializing' and after a short time it says ready. I can use the start button to open different libraries and so, but the command window is grey. If I open the editor, it's grey too. 

I first used Wubi to install Hardy and Matlab. Everything worked, but was not as fast as I thought it would be. Can someone help me out please? Thanks in advance.

EDIT: same installation works fine for Xubuntu 8.10 on my Toshiba with Pentium 4. I get the same Locking Assertion failure, but I didn't end up with a grey screen. On this forum I found the solution, it has to do with Java and it is fixed for me now.

---

### Post by ppm on 2008-11-07
> **ilkolinux said:**
> wow thanks for the info guys, i just got a course in matlab on my faculty and i though that i would have a lot of trouble using it on linux(or even switching to windows, god forbid) but it seems that it works just fine.

In general Matlab + linux is a working combination. However, since the introduction of the java-based (?) user interface (from Matlab 6.x IIRC) you end up with problems such as indicated in this thread. I only hope M???Works support for other platforms finally starts to improve...


Tonie168:
Good to hear that your problem was solved. Would you please link here the post/thread that solved your problem.

---

### Post by VTphilipv on 2008-11-10
I am running 2007b on Intrepid 64 bit without problems... as long as I stay away from desktop effects.

---

### Post by XxX_VLAD_XxX on 2008-11-12
How did you installed it?, using WINE, Crossover or some like it...  Did you installed in a version for Ubuntu, if so, can you please put a link for download?

Thanks

---

### Post by Tonie168 on 2008-12-11
I'm sorry ppm, since my problem was solved I didn't check this topic.

The strange thing is, on my toshiba with xubuntu 8.10 matlab had the same java problem as on my desktop, but I now have an Acer Aspire One running Xubuntu 8.10 and Matlab works directly, but I get some errors. What I did was the following:

Install sun-java6-jre with synaptic and then add the following lines to the matlab file:
~/.matlab/etc/lmstart
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.10/jre/

The first line starts only the licence manager. The second line tells Matlab where to look for Java.

BTW, credits are not on me, but on some guys here. If you know where I found it, please pm me, so I can thank them.

---

### Post by Telescope_Nerd on 2008-12-12
> I did a clean install of II and after that I installed matlab 2007b. Both 64-bit programmes. The license is correct and I first start the license manager. But when Matlab opens, it is all grey. It first says 'Initializing' and after a short time it says ready. I can use the start button to open different libraries and so, but the command window is grey. If I open the editor, it's grey too. 

I first used Wubi to install Hardy and Matlab. Everything worked, but was not as fast as I thought it would be. Can someone help me out please? Thanks in advance.

EDIT: same installation works fine for Xubuntu 8.10 on my Toshiba with Pentium 4. I get the same Locking Assertion failure, but I didn't end up with a grey screen. On this forum I found the solution, it has to do with Java and it is fixed for me now.

Hmm, I remember having this same problem when I installed Matlab but I managed to get it fixed. If I remember correctly it was a Java issue, which version are you using? I would check to see if the version of Java you are using is compatible with Matlab and update as necessary.

EDIT: Whoops sorry, I somehow missed the end of this thread, Now I realize my post is redundant apologies.

---

### Post by ppm on 2008-12-12
> **Tonie168 said:**
> I'm sorry ppm, since my problem was solved I didn't check this topic.

The strange thing is, on my toshiba with xubuntu 8.10 matlab had the same java problem as on my desktop, but I now have an Acer Aspire One running Xubuntu 8.10 and Matlab works directly, but I get some errors. What I did was the following:

Install sun-java6-jre with synaptic and then add the following lines to the matlab file:
~/.matlab/etc/lmstart
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.10/jre/

The first line starts only the licence manager. The second line tells Matlab where to look for Java.

BTW, credits are not on me, but on some guys here. If you know where I found it, please pm me, so I can thank them.

Hey Tonie168

No worries and thank you for reporting your success. :)

Personally, I haven't made "the leap" yet since I need to make some cleanup to actually be able update the system to 8.10. Also KDE 4.x troubles me at the moment. At least it seems to be totally different compared to 3.y...:confused:

---

