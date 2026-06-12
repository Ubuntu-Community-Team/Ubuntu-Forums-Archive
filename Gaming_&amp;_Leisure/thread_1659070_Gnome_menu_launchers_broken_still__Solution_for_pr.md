---
title: "Gnome menu launchers broken still?  Solution for programs using relative paths?"
date: 2011-01-03
forum: Gaming &amp; Leisure
---

### Post by Yfrwlf on 2011-01-03
The Clockwork Man fails to run due to using relative paths, and thus the binary cannot be run from any location other than the same folder/directory the binary is in, so it will start up, but then can't find any of it's other binary kin to progress very far.

I would think that Gnome should make it so that all binaries are run from the same paths that they are in to avoid this kind of thing, users wanting to create menu shortcuts and not being able to do so.  I've had this problem countless times and it just helps to make the usability of the menu system atrocious, not to mention the menu editor and other things about the menu just are not very friendly and need updating.

As for now, I'm sure a cd /path/to/binary && ./binary or some such solution will have to be used here, but that's not something most any users would know about unless they are Linux geeks.  Normal users are going to surf to the binaries and double click them.  And I'm not going to even bring up the whole lack of proper cross-distro installers being the root cause of this whole mess to begin with.  Oh darn, I just did. :lolflag:

Perhaps this will all be taken care of with Unity, if most users switch to that?  Anyone know?

Thanks.

---

### Post by Yfrwlf on 2011-01-03
FYI, for others having issues, an example of the correct syntax to change the folder and run the binary that you should use for your run boxes or launchers is:

> bash -c "cd /home/username/Games/TheClockworkManENv.1.0.3.6x32/ && './The Clockwork Man'"

Keep in mind if there are any special characters, like species, you need to wrap single quotes around those parts, so if your path has spaces like the binary "The Clockwork Man" does, you could put single quotes around the whole path, i.e. '/home/username/games/The Clockwork Man 1/'.

But the intention of this thread was just because I was wondering what the best solution to this mess would be, and if that solution was going to be the menu's replacement by Unity.

---

### Post by Pixelsprite on 2011-01-11
Hello!

Making custom launchers for your applications is a pain most times.

We've included step-by-step instructions in the Readme file inside the tar.gz, which have been pretty summed up by the instructions given by Yfrwlf. For your convenience I'll include them again here.

Installing The Clockwork Man for Linux
----------------------------------------------------------------
If you have a 64-bit OS, you need to install 32-bit compatibility libraries.

1.Extract the compressed tar.gz
2.Copy the extracted folder to your desired location ensuring the permissions requirements are met. A good location choice would be under your user folder, i.e. ~/myGames /.
3.Browse to the /tcm/ folder, containing the &#8220;TheClockworkMan&#8221; executable file.
4.Execute (double click) the file named TheClockworkMan to run.
5.(optional) Create a launcher. 

To create a launcher :
1.Right click on your desktop and select &#8220;create a launcher&#8221;
2.In the &#8220;command&#8221; field, type : 
	bash -c "cd YourFullDirPath/ && ./TheClockworkMan" 
	where  YourFullDirPath is the full path to the executable file's folder

	eg : bash -c "cd ~/myGames/tcm/ && ./TheClockworkMan" 


This is the only way to make a custom launcher for The Clockwork Man at the moment.  As Yfrwlf said don't forget to add single quotes *'* if you have any spaces in your path or filename.

Thank you for supporting us!

Maria / Total Eclipse

---

### Post by thatguruguy on 2011-01-11
> **Yfrwlf said:**
> The Clockwork Man fails to run due to using relative paths, and thus the binary cannot be run from any location other than the same folder/directory the binary is in, so it will start up, but then can't find any of it's other binary kin to progress very far.

It doesn't fail to run if you invoke it correctly. As far as the implementation of relative paths in linux, I'm pretty sure that it's a feature, not a bug.

---

### Post by Yfrwlf on 2011-01-11
Thanks Maria/Pixelsprite!  I did notice that after I had posted but figured others might hit the forums first so thought I'd post the solution here.  See my potential solution below, I don't understand why it shouldn't solve your program's problem.

> **thatguruguy said:**
> It doesn't fail to run if you invoke it correctly. As far as the implementation of relative paths in linux, I'm pretty sure that it's a feature, not a bug.

I'm not sure what feature you're referring to, and running a program from a different current working path is something you do all the time in Linux and isn't incorrect.  Every time you type in "ls" or any other common shell commands you are running them from /usr/bin, a different working directory, which luckily happens to already be in your PATH unlike the files we're discussing.  Regardless, it's the *inability* of programs to use relative paths that is the problem here as they are being tossed for a loop while being run from another path.  I've encountered many programs which try to reference files around them or in deeper directories only to fail due to not having the current working path that was used when they were launched being the same path that they are in.

I'd think the easiest solution to this problem would be for scripts and programs to reference all path locations by using '$0' which is the path and file name used to to run it.  That way internally any subsequent calls like to a buried library could be used with this value, say '$0/lib/cool.so', to always be able to find the correct location of nearby files.

If all programs used this, that would hopefully solve that issue.

---

### Post by Softworn on 2011-06-08
> **Yfrwlf said:**
> FYI, for others having issues, an example of the correct syntax to change the folder and run the binary that you should use for your run boxes or launchers is:



Keep in mind if there are any special characters, like species, you need to wrap single quotes around those parts, so if your path has spaces like the binary &quot;The Clockwork Man&quot; does, you could put single quotes around the whole path, i.e. '/home/username/games/The Clockwork Man 1/'.

But the intention of this thread was just because I was wondering what the best solution to this mess would be, and if that solution was going to be the menu's replacement by Unity.

 That solved my problem! Thanks ^_^  Now that I have a working launcher for Unreal Tournament 2004, I just need to figure out how to get ALSA to cooperate, so I'll have a fully another functional game.  I should probably learn more bash scripting in my spare time, too.

---

### Post by Yfrwlf on 2011-06-15
> **Softworn said:**
> That solved my problem! Thanks ^_^  Now that I have a working launcher for Unreal Tournament 2004, I just need to figure out how to get ALSA to cooperate, so I'll have a fully another functional game.  I should probably learn more bash scripting in my spare time, too.

Good to know for automation purposes for system administrators, but certainly not something a normal user should ever have to learn for doing something as simple as creating a launcher icon somewhere.  I wish advancements in usability would include areas like this.

---

