---
title: "Anoying Beep!"
date: 2009-05-30
forum: General Help
---

### Post by kyle2595 on 2009-05-30
Hi, I had heard a very loud and annoying beep whenever I shutdown/ restarted my Dell D620 running Ubuntu 9.04.  I have tried going to System -> Preferences -> Sound and unchecking the "Play Alert Sound" box, but that did not work.  Is there a command or any way I can disable the beep?  Thanks.

---

### Post by Rocket2DMn on 2009-05-30
At what point does the beep occur?  As soon as you tell it to shutdown, or right around the power off time?  Have you checked in your BIOS to see if you can disable the System Beep?

---

### Post by spiderbatdad on 2009-05-30
can also be disabled under System>>Prefrences>Sound>Sounds uncheck play alerts and sound effects. Will have to reboot to notice change.

---

### Post by kyle2595 on 2009-05-30
The beep occurs right after I hit Shutdown on the box that says "The system will shutdown in 60 seconds"

---

### Post by ActiveFrost on 2009-05-30
My box loves to beep on shutdown as well :D On 8.04/8.10, Sounds -> System Beep, but .. I can't find it on 9.04 ! Any ideas on how to "fix" it ?

---

### Post by s.fox on 2009-05-30
Hi,

Yes,  it seems to be a common problem for many people.  One of my friends solved it by following [this]("http://ubuntuforums.org/showpost.php?p=7162033&postcount=12") post and black listing. I really hope this bug gets sorted out soon!

-Ash R

---

### Post by spiderbatdad on 2009-05-30
the file system in jaunty has changed slightly and the command in that post will not work. You can manually add "blacklist pcspkr" to the file **/etc/modprobe.d/blacklist.conf**
```
echo 'blacklist pcspkr' | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by kyle2595 on 2009-05-30
Thanks Ash R! It worked!

---

### Post by Rocket2DMn on 2009-05-30
Cool, good find Ash R!

---

### Post by spiderbatdad on 2009-05-30
my foot. since the file in that thread doesn't exist in jaunty.

---

### Post by kyle2595 on 2009-05-31
It worked for me.

---

