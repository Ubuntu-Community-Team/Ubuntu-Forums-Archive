---
title: "KXDocker1.1.4a Icons"
date: 2006-10-08
forum: Desktop Environments
---

### Post by spacecowboy706 on 2006-10-08
Just recently I got kxdocker1.1.4a and i have figured out how to make the icons add to the dock by using the kxdocker_conf.xml page. I am able to get actual programs to work fine (like firefox, thunderbird, X-Chat, etc...) but when i try to make a "file folder" open doing the same, it doesn't work.

What i have done in the past is creat a launcher on my gnome panel and then just copy the command that it takes to start (cause i dont know the commands) then used it on the "onclickexec" part of the xml page, then changed the icon after the docker was restarted and this technique has worked fine for applications.

I created the same file launcher on my gnome panel and it works fine. The start command for it is: file:///home/myname/Downloads/Unsorted

So i then copy this over to the kxdocker_conf.xml and insert it into the "onclickexec" and it should launch the file just like all the other ones i created.... right.

well it doesnt... it does nothing... can anyone tell me how to do this? for file folder, not applications?

---

### Post by wieman01 on 2006-10-09
Appears not many people using KXDocker... ;-) Mind if I replied to this one?

This is an example of my KXDocker icon that opens the folder "/mnt" (which I call "My Secret Files" because I actually mount a encrypted volume on startup) using "konqueror". "konqueror" is the KDE file browser, so all you'd have to do is replace "konqueror" with Gnome's file manager - whatever it's called (cannot remember).

This definitely works for me:
```
<objectsicons>
   <info OverText="My Secret Files" className="GIcon" Name="My Secret Files" Group="My Secret Files" fileName="" />
   <images imgFileName="Personal 2" imgFileDrop="drop.png" PoofName="poof.png" imgFileArrow="arrow.png" />
   <status MiniTextShow="1" />
   <actions onDropExec="" onClickExec="konqueror /mnt" iAnimationMask="0" />
   <matchtasks ClassName="Konqueror" TaskName="konqueror" WindowTitle="My Files" />
   <matchdcop dcopName="konqueror" />
   <pluginconfiguration>
    <pluginconf/>
   </pluginconfiguration>
   <actionlist/>
  </objectsicons>
```

---

### Post by wieman01 on 2006-10-09
> file:///home/myname/Downloads/Unsorted 
...does not look right at all. Because it does not actually fire up a program. Try to run it from a terminal window...  KXDocker can only handle stuff that works from a terminal if you know what I mean.

---

### Post by ayoli on 2006-10-09
to launch nautilus in a specific folder your "onclikexec" should contain something like this:
```
nautilus --no-desktop /path/you/want
```

---

### Post by spacecowboy706 on 2006-10-09
right on the money Ayoli.. that was what i needed. Works like a champ now. This site is freakin fantastic

---

