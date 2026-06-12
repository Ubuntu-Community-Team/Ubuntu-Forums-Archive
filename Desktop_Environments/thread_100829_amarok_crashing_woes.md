---
title: "amarok crashing woes"
date: 2005-12-08
forum: Desktop Environments
---

### Post by hogweed on 2005-12-08
So, I have yet to really get amarok in shape since upgrading to Breezy. Streams tend to result in cpu overload, a problem that I have noticed other people having as well.

The biggest one, though, is that some .mp3s in my collection cause a complete and sudden crash of amarok. These are usually files that have bitrates below 128, or that were created using iTunes.

I have upgraded to 1.3.7 using the Kubuntu rep, and have tried everything from gstreamer to arts to xine. I am at a loss, since everything is working fine with xmms and bmp, which have no problem with any files or streams.

I am stumped. This is the first time that I really just haven't been able to figure out a problem like this. All was fine in hoary, so this isn't a hardware issue...

Any ideas from the more enlightened out there?

-- hogweed

---

### Post by mlomker on 2005-12-08
Xine is the only one that always works for me.  Have you tried compiling the [SVN version]("http://www.ubuntuforums.org/showthread.php?t=80492")?

It's been solid for me...I'd be hard-pressed to even consider it a beta (even though it is).

---

### Post by hogweed on 2005-12-08
Yeah, well, xine does work, but each track starts out with a very loud screech/garble noise when I use it, and then there is some low-level distortion during the rest of the track as well.

This is an odd problem, as I also have the exact same problem with the exact same files when I use my laptop.

I tried the SVN a while back, but had the exact same problem anyway; not wanting to mess up my install too much, I went back to the .debs of stable releases.

Perhaps it is time to try the SVN yet again... Thanks for the tip, and I am glad to hear that amarok is looking good for the future.

-- hogweed

---

### Post by Zaventh on 2005-12-09
fyi, the SVN version isn't entirely as stable as it usually is at the moment (at least not if you want ipod support.) Their transitioning to some new libraries. Are you using the Helix engine by chance? I heard that has had the most problems with AmaroK. You probably saw the Breezy 1.3.7 packages for AmaroK by now. Give those a try.

---

### Post by yjsoon on 2005-12-15
I'm facing the same problem here running AmaroK 1.3.7 for Kubuntu Breezy. It doesn't seem to be an engine problem (though xine crashes less violently than arts), because even trying to "edit track information" makes AmaroK crash. 

The guilty tunes don't seem particularly special... encoded at 192 in MP3 format, though they do have album art (but then others that work do, too).

Guess I'll try the SVN version at some point.

---

### Post by wolfe on 2005-12-15
I jumped on #amarok on the freenode irc server the other day and had them help out.  Installing the svn and taglib 1.4 solved it all for me.  Taglib was amarok was crashing on me, seems the 1.3 doesnt play well with amarok.  Maybe jump on that irc channel, those guys were extremely helpful.

---

### Post by hogweed on 2005-12-15
Yes, this does seem to be a taglib problem. As yjsoon mentioned, trying to edit track information without playing the offending files (encoded at 192 in MP3) will also bring a quick crash. 

To test, I took some of the offending files and edited the tags with kid3. They were, in fact, messed up, and once I got decent information into them the tracks played without much problem (amarok 1.3.7).

I just tried installing taglib-1.4, as wolfe recommended, but the .deb that I grabbed from the amarok svn howto has a different name from the default Kubuntu package (which is libtag), so there seems to be some conflict. 

Once I get a chance I will try to fix this to work with amarok 1.3.7 and/or svn. 

Stay tuned....

-- hogweed

---

### Post by mlomker on 2005-12-15
[QUOTE=hogweed]Once I get a chance I will try to fix this to work with amarok 1.3.7 and/or svn. [/QUOTE]

Yeah, I left the Ubuntu package installed because K3B depends upon it.  Other people have had trouble having both installed and needed to delete the /usr/lib/libtag.so.1 file.  It hasn't caused me any problems so far.

---

### Post by hogweed on 2005-12-16
Hmmm... I am not sure that I am up to breaking compatibility with the smooth updates that I have come to enjoy with Kubuntu. I am in no hurry right now, so perhaps the backports people will come out with a fix for this; if not, I am probably just about a month or two away from updating to Dapper, so I'll do it then.

Besides, I am really starting to enjoy the speed and simplicity of bmp, and the streaming is flawless...

-- hogweed

---

