---
title: "Intrepid: Matlab 2007b keyboard stops working"
date: 2008-12-03
forum: General Help
---

### Post by drdan14 on 2008-12-03
Howdy!

I just upgraded to Intrepid 8.10 from Hardy 8.04, and I'm now having a problem in Matlab R2007b where, randomly, Matlab will stop accepting keystrokes. Sometimes I can fix this by clicking in a different section of Matlab, but sometimes nothing works, and I need to restart Matlab. The same version of Matlab was working fine under Hardy, and I haven't noticed this problem in any other applications.

Could this be a Java bug? I know that Matlab depends strongly on Java.

I saw that someone had posted a similar problem here: [http://ubuntuforums.org/showthread.php?t=740087](http://ubuntuforums.org/showthread.php?t=740087), but I can't reply to that thread for some reason.

Thanks,
Dan

---

### Post by drdan14 on 2009-01-02
*Update* This problem occurs more frequently in Matlab R2008b than in Matlab R2008a, and is usually less recoverable.

I've determined that the bug occurs when opening a new figure and typing simultaneously.

Steps to reproduce:

o In the command window, open a new figure by typing
```
>> figure
``` [enter]
o While the figure is opening, mash on the keyboard constantly
o Matlab will stop accepting keyboard input for that session, and it will be necessary to quit and restart Matlab to restore keyboard input
o Mouse input is not affected

I didn't have this problem until upgrading to Ubuntu Intrepid 7.10. Has anyone else had a similar experience?

Thanks for the help!
Dan

---

### Post by seppav on 2009-02-24
I'm having exactly the same problem after updating to matlab R2008b although I can't evoke it the way you describe it there. It seems to happen pretty randomly. I was in contact with Mathworks sometime last year but at that time they couldn't resolve the problem.

It's really annoying that you have restart Matlab every few minutes...

---

### Post by drdan14 on 2009-02-24
Update: my problem went away after installing the latest Ubuntu updates.

Dan

---

### Post by Gizenshya on 2009-02-24
well, if you're using matlab, you should already know that randomness is not a factor ;)

---

### Post by seppav on 2009-02-24
My Ubuntu should be up to date. At least it's updating packets almost on a daily basis.

---

### Post by michael_habib on 2009-07-23
I also update my Ubuntu almost every day.

This problem is very annoying. I really hope some one found a solution to it.

I try some things that works sometimes, I open any variable in the workspace, and by maximizing the variable editor window and minimizing it again, Matlab starts accepting input from the keyboard.

Michael Habib

---

### Post by dalyx on 2011-01-28
I had the same problem with the keyboard freezing during Matlab sessions.

I observed that it had to do with changing the current focus. For instance, with window focus on the editor, then changing focus to a figure, and back to the editor sometimes causes the keyboard to stop functioning. The keyboard would sometimes get back into working mode if I focused on the figure, pressed the ESC key and then focus back on the editor, thought that doesn't work every time. Closing the figure didn't do much except make the editor completely unusable.

I am using Ubuntu 10.04 LTS. I upgraded the Matlab version in case it was related to an old bug.
>> version
7.11.0.584 (R2010b)

I checked that I was using the Sun Java by issuing the following command in the Matlab prompt:
>> version -java
Java 1.6.0_21-b06 with Sun Microsystems Inc. Java HotSpot(TM) Client VM mixed mode, sharing
To change java versions that Matlab is using, I use the MATLAB_JAVA environment variable (see [http://www.mathworks.com/support/solutions/en/data/1-1812J/](http://www.mathworks.com/support/solutions/en/data/1-1812J/))

Then I found a posting on mathworks.com ([http://www.mathworks.com/matlabcentral/newsreader/view_thread/290037](http://www.mathworks.com/matlabcentral/newsreader/view_thread/290037)) that relates this problem to the use of iBus and Java.

So I disabled iBus from the command prompt before starting Matlab with
# killall ibus-daemon

After that, Matlab has been running without the keyboard problem. If I don't diable ibus-daemon and the keyboard freezes in Matlab, it starts working again right after I kill the ibus-daemon.

---

