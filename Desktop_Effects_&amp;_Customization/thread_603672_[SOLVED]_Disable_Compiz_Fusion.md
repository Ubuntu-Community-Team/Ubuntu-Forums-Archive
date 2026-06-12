---
title: "[SOLVED] Disable Compiz Fusion?"
date: 2007-11-05
forum: Desktop Effects &amp; Customization
---

### Post by slughappy1 on 2007-11-05
My question is, is it possible to disable compiz-fusion for a specific program? For example, I need to use a program called matlab. But when I load it I can't see the top menu buttons (picture 1), but when I use the compiz-fusion tray icon and switch compiz -> metacity -> compiz I can see them (picture 2). Is there a way to make it so I can see the whole program without having to disable compiz and the re-enable it?

---

### Post by kshane on 2007-11-05
> **slughappy1 said:**
> My question is, is it possible to disable compiz-fusion for a specific program? For example, I need to use a program called matlab. But when I load it I can't see the top menu buttons (picture 1), but when I use the compiz-fusion tray icon and switch compiz -> metacity -> compiz I can see them (picture 2). Is there a way to make it so I can see the whole program without having to disable compiz and the re-enable it?

<bump>

 Good question!  What say you, Compiz pros?

---

### Post by psyopper on 2007-11-05
No, there isn't any way to have Compiz ignore a single program. Compiz is a desktop rendering tool, it's all or nothing.

---

### Post by slughappy1 on 2007-11-05
Well then, is there a way to fix that problem then?

---

### Post by psyopper on 2007-11-05
Just what you're doing, disabling Compiz before launching the application. 

This isn't the only application that has problems like this - others that rely on Java based navigation have similar problems - LimeWire comes to mind.

I do wish I had better news for you though...

Edit: Captain Quark rocks! I'm trying to talk my wife into getting a PS3 40G with R&C for Christmas.

---

### Post by tuwe on 2007-11-06
Hello,

the third post in this thread might be the solution to your problem:

[http://ubuntuforums.org/showthread.php?t=467133](http://ubuntuforums.org/showthread.php?t=467133)

edit:

sudo apt-get install sun-java6-jre sun-java6-fonts
sudo vi /usr/local/matlab/bin/matlab

and insert the following after the comments:

export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.00/jre/
export AWT_TOOLKIT=MToolkit

you might prefer "export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/" instead of the first line to have future versions of java properly recognized. (mine is 1.6.0.03, i think)
hope this helps

---

### Post by slughappy1 on 2007-11-06
OMG thanks, it was really annoying having to restart compiz every time. I used the following commands:

sudo apt-get install sun-java6-jre sun-java6-fonts
sudo gedit /usr/local/matlab74_sv/bin/matlab (I don't know how to use VIM)


export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/
export AWT_TOOLKIT=MToolkit

---

### Post by tuwe on 2007-11-07
> **slughappy1 said:**
> OMG thanks, it was really annoying having to restart compiz every time. I used the following commands:

sudo apt-get install sun-java6-jre sun-java6-fonts
sudo gedit /usr/local/matlab74_sv/bin/matlab (I don't know how to use VIM)


export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/
export AWT_TOOLKIT=MToolkit

hi again, 
if you run into problems like not being able to type ^, or nothing at all after returning to the command window from a figure, you might want to look here:  [http://ubuntuforums.org/showthread.php?p=3723379#post3723379](http://ubuntuforums.org/showthread.php?p=3723379#post3723379)

---

