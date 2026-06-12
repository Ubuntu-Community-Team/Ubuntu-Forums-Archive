---
title: "System Sound Preferences:  Help Needed"
date: 2009-03-31
forum: General Help
---

### Post by enodicalp on 2009-03-31
ok, I'm pretty sure that the problem is on my end, but since I'm new to linux/ubuntu, i have no idea how to fix it.

here's the problem...

I'm trying to set up customized system sounds to enhance the feel of my computer.  I've followed markbuntu's post called "Intrepid sound solutions" as an attempt to fix this problem of mine.  I did manage to make the computer sound louder, and even got my microphone working using his setup, so I thank markbuntu for the post.  Here's a link if you want to check it out.

[http://ubuntuforums.org/showthread.php?t=997506]("http://ubuntuforums.org/showthread.php?t=997506")

even though I open the sound preferences( system>>preferences>>sound )and set a custom sound somewhere, it will NOT play the sound when the required action is met.  for example...

[IMG]http://i20.photobucket.com/albums/b238/doublebqsauce/Screenshot-SoundPreferences.png[/IMG]

here, i have a custom sound for 'Empty trash' called LTTP_Menu_Erase.wav

The sound will play on the preview button just fine, but if I try to 'Empty trash' from the trash bin, No sound is played.  

I've tried converting the file into an .ogg file, and that didn't work either.  I've even tried using a sound thats located in filesystem/usr/share/sounds, and I came up with the same results.

I'm at a loss, can someone help me out here?

btw, i'm using Ubuntu 8.10 - the Intrepid Ibex.  I downloaded the 64-bit version.  hope this helps.

---

### Post by krishna1650 on 2009-03-31
i have also same problem.

---

### Post by enodicalp on 2009-04-02
Ok, I've managed to fixed most of the buttons' custom sounds by finding some info about it on the bug section of these forums.

Since it took me a while to figure it out, I'll fill you in on how I did it.  Keep in mind, some of the buttons still don't work, but it's better to have some of them working rather than none.

Ok, so here's what I did...

first you'll need to go to software sources.  (System>>Administration>>Software Sources)

on the 'Third-Party Software' tab, click on add  button.  A new window should appear asking for a specific website.  Type the following...

deb [http://ppa.launchpad.net/gkulyk/ubuntu](http://ppa.launchpad.net/gkulyk/ubuntu) intrepid main

after that, close the window and immediately, the new libcanberra 0.10 should show up as an upgrade.

If it doesn't, go to (System>>Administration>>Update Manager) and update the system.

after that, I went to (System>>Administration>>Synaptic Package Manager) and searched libcanberra.  I then selected every libcanberra package that was available and installed them.

Then, I rebooted my system and tested out the sounds.  I was surprised to hear the custom sounds when I started clicking things!  I then started fooling around with the sounds.  I haven't checked every single one of them, but I do know that if fixed the sounds for minimizing and maximizing windows.  Unfortunately, I still can't get the 'empty trash' one to work...but like I said before, some custom sounds are better than none.

Hopefully, this will help some of you guys out with the sound issue.  Good luck!  ^_^

---

