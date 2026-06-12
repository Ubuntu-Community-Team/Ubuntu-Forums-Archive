---
title: "Applications are installed... but not installed!!!"
date: 2006-04-15
forum: Desktop Environments
---

### Post by dnccnd on 2006-04-15
Hallo!

I am pretty new to Ubuntu, this is just my second thread asking for help :) 
I am enjoying Ubuntu very much and I am also trying to promote it with friends.

I use a IBM T23 notebook with a Windows partition and a Ubuntu partition.

I have installed a few application, especially in the sound & video and internet sections. Among these are Mplayer and Totem Movie Player. They work quite well, though I still have to figure out which types of files they handle best.

My **problem** is that the applications are installed, they work, **but** when I open Add Applications, both applications seem to be not installed! Then when I try to mark Mplayer in order to (re)install it, I get this message:

Application 'mplayer' not available
The application can not be found in your archive. This usually means that it is not available for your hardware plattform.

Instead, when I mark Totem, I get this other message:

Cannot install 'totem'
Installing this application would mean that something else needs to be removed. Please use the "Advanced" mode to install 'totem'.

Do you have any idea why this is happening? And whether this affects the functioning og the two applications? Can I solve the problem?

Thanks a lot...

---

### Post by bscbrit on 2006-04-15
If it is saying that mplayer cannot be installed for your hardware then it is probably a good clue.  How do you _know_ that mplayer is installed if nothing is showing that it is - in fact, it is telling you that it most certainly isn't?

The problem being displayed by totem is probably caused be a conflict of version numbers for some dependency.  For example 'playerX' requires lib1.2.3.4 but totem requires lib1.4.3.2.  If totem is installed, it will have to remove lib1.2.3.4 and thus also remove 'playerX'.  I think the cure is to decide which one you want and then install it.

---

### Post by dnccnd on 2006-04-15
Mplayer is installed! I can open it and with it I can open videos and audios. Then the question is why Add Applications tells me that it is not installed!

I made a research in Synaptic and I attach a screenshot with the results. Do you think I should install more components/application?

As far as Totem is concerned, I made a research in Synaptic as well and I attach a screenshot with the results. Here too... should I install something?

Thanks a lot for helping!

---

### Post by bscbrit on 2006-04-15
Well that looks fairly certain then - if you can use it, it must be installed.   If it is not asking for anything else to be installed then it doesn't need it.  And 'Add Application' won't let you install it because it is already installed.  I haven't used Add Application much - I prefer Synaptic or apt-get - this might be a known bug.

Is there some media that you cannot play using MPlayer - and, if not, why bother with totem?  But you said that you can use both programs and it is simply Add Applications that is confused.  The only thing I can suggest is that you might want to report it as a bug.

---

### Post by dnccnd on 2006-04-15
Well, there is a an AVI movie that I cannot play in Mplayer. It gives an error. Neither could I play it in Totem, and therefore I installed VLC Media Player which opens it easily. The strange thing is that Totem could open this AVI file in my previous session! ](*,) 

I guess the problem is in the file itself as I had problems playing it also in Windows.

Another strange thing is that Mplayer doesn't see my external hard disk, while the other applications do this!

Do you know how I can submit a bug?

Thank you again for your support. :-D

---

### Post by bscbrit on 2006-04-15
[http://www.mplayerhq.hu/DOCS/HTML/en/bugreports.html](http://www.mplayerhq.hu/DOCS/HTML/en/bugreports.html)

That looks like the info you need....

---

