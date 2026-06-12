---
title: "Ubuntu 8.10 blank screen after login"
date: 2009-03-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by snakey12 on 2009-03-02
Hello,

I'm a software developer by trade but have very little experience with hardware.
I have Dell Dimension 2400 desktop. The hard drive is on its way out so I bought a new one. I was running Windows XP but have been toying with the idea of trying Ubuntu so this seemed like a perfect opportunity. I successfully managed to install Ubuntu, however when I boot up, after i enter my username and password I am taken to a blank screen; the screen is coloured kind of peachy. I can move my mouse around the screen but the screen is completely blank.

Where do I go from here?

---

### Post by utnubuuser on 2009-03-02
Google: "blank screen ubuntu", - there are lots of threads about this subject.

It's probably the video card.

If you can, from the blank screen try ctrl+alt+F1, this should get you to terminal mode. ctrl+alt+F7 to get back to graphic from there.

If you can't access a terminal, try using the liveCD and going to a terminal, (Applications>>Accessories>>Terminal), then post the output from> lspciand > dmesg, someone will know what to do.

Have you tried Googling: "the_make_and_model_of_your_laptop ubuntu"?

---

### Post by Sysero on 2009-03-02
Something else you could try too.

See this thread: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=984296]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=984296")

Then scroll down to post number 7 by Marcus Derekus and follow his instructions.  See if it works for you.

---

### Post by sirebral on 2009-03-03
CTRL - ALT - F1. Open a terminal that way.  I might be video card.  You might need to update.

---

### Post by armandh on 2009-03-03
if that model has onboard video you may find that the removal of compiz is exactly what will allow it to work

it did for me on a gateway box.

---

