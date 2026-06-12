---
title: "Error when trying to use J2Se runtime.."
date: 2005-03-28
forum: Desktop Environments
---

### Post by xNight Wraithx on 2005-03-28
Okay so I input this:

$ cd browse_to_your_download_folder

and I get this message:

No such file or directory

am I doing something incorrectly?

---

### Post by kassetra on 2005-03-28
[QUOTE=xNight Wraithx]Okay so I input this:

$ cd browse_to_your_download_folder

and I get this message:

No such file or directory

am I doing something incorrectly?[/QUOTE]

If you are actually typing in $cd browse_to_your_download_folder, then yes, that is incorrect.

In the Terminal Window (Applications->System Tools->Terminal), you should see something called a "prompt" ... where the cursor blinks like a little block.

At that point - to change to the folder (directory) where you downloaded the j2se runtime, you have to give the command "cd" which stands for "change directory" ... but you also have to tell it where to change it to.  Most likely you downloaded the j2se to your "home" directory or to your "desktop" ... 

When you first open your terminal, you start at your home directory, so no need to change directories.  But if you downloaded the j2se to your "desktop" here is the command you need to type in the terminal window to change to that folder:
 ```
cd Desktop
``` 
Just like that.  (Note the capital D)

Now, if you don't know where the j2se file is - you can open up a browsing window and find it (Computer->Home) and then when you find it, you'll know the "path" to get to it in the terminal window.

Make sense?

---

### Post by xNight Wraithx on 2005-03-29
Makes good sense now, hopefully it does when I try it. I unfortunately deleted and formatted my entire hard drive because I was going to revert back to Windows XP because I was getting frustrated with my lack of knowledge on how to use Linux  #-o  But, I kept on getting corrupt files when trying to reinstall XP so I think that I am going to reinstall Ubuntu tonight and go back to the drawing board. I'll let ya'll know how it goes. Thanks again for your help.

---

