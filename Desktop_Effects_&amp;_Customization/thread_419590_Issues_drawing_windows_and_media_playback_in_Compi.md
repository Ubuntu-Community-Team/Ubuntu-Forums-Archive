---
title: "Issues drawing windows and media playback in Compiz"
date: 2007-04-23
forum: Desktop Effects &amp; Customization
---

### Post by NegativeSpace on 2007-04-23
Hi,

I'm loving Compiz but I'm having a couple of issues:

Sometimes (I haven't figured out yet what triggers it) windows won't (re)draw -- for example, Firefox will appear to be frozen. It's not, as I can click on a link, minimise Firefox, maximise it again and it will have loaded the new page. This will happen for other applications, too; the program will respond to input but not refresh its contents.

Probably linked to the above problem, one application (IntelliJ IDEA, a Java IDE) will simply appear as a big grey box on screen except for the frame. Curiously, if I start the program up without Compiz running, then load up Compiz, it appears to work fine. I've noticed that the Java console behaves this way, too, so maybe it's something to do with Java?

Finally, I am having trouble using VLC and Totem. If I use VLC, the video will play fine until I either move the window or resize it, at which point it will go black (sound still plays, so maybe this is also linked to the first two issues?)
Totem kind of works -- there is a blue grid of dots over the video the whole time, which is moderately irritating. Also, when I modify the transparency the video will disappear.

Graphics-wise I'm running Intel 82852/855GM Integrated Graphics Device.

As I said, Compiz is genious, it's just these couple of niggling issues that are preventing me from using it the whole time.

Thanks in advance.

---

### Post by knorr.orange on 2007-04-24
I do not have an answer but I have a similar problem which may help give clues to others:

I have a laptop with an Intel GMA945 integrated video card.  Everything that I have seen so far works perfect with Compiz enabled except video (as in watching videos in Totem.)  As NegativeSpace has said in the previous post, the video plays and I can hear the sound, but the video doesn't actually show anything.  If I move windows around really fast I can sometimes get a frame or two to flash on the screen but that's it.

If it helps, I have just booted from the Desktop CD and am testing it as a live cd.  I just boot up, click the button to enable desktop effects and that's it.  All of the effects work great and all programs run fine with no crashes or anything like that.  The only problem is getting video to display in Totem.  I have not tried a different video player yet as I am only using what came on the CD and do not have an Internet connection for that computer.

---

### Post by knorr.orange on 2007-04-24
Ok, so I am a jerk and didn't read all of the other posts about Compiz here.  It turns out that there is a solution that has worked for others.  I will post my results when I get a chance to try it out.  For now here is a link to the thread:

[http://ubuntuforums.org/showthread.php?t=415012&highlight=totem](http://ubuntuforums.org/showthread.php?t=415012&highlight=totem)

NegativeSpace, please give it a try and post your results as well.

---

### Post by knorr.orange on 2007-04-24
Back again and have tested the configuration.  Making the change in the gstreamer-properties as suggested in the referenced thread above worked great for me.  The video does not look as good as it should but people in the other thread said the same.  However, I am not running with the 915resolution fix (which is required for my graphics card) so my lcd is not running at the optimal resolution.  Given that, I shouldn't comment much on image quality just yet.

---

### Post by hiruzzolo on 2007-06-01
I have the **same** problems with Compiz myself, and I'm on a nvidia 6550le.. 
I have the same "big grey box java" problem that is quite annoying and it doesn't let me use netbeans with compiz.
I have the same problem with programs and movies blocking the video (but only the video, because audio continue to work)for some seconds and then it return normal.
I have moreover the problem that Suspend feature doesn't work with compiz, because when I came back to ubuntu I have a black screen where only the pointer of the mouse works.
I have finally a problem that sometimes the titlebar hidden the title of the window but if I resize the windows it comes back.
I deactivate the desktop effects (so I deactive compiz) all this things work perfectly.
Especially the java bug is very bad if someone has to work with it! Has anyone found a solution for these things?

---

