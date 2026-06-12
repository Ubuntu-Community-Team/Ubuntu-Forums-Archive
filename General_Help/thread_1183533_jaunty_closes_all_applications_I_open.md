---
title: "jaunty closes all applications I open"
date: 2009-06-10
forum: General Help
---

### Post by anilcr on 2009-06-10
Hi guys...
    Jaunty closes all applications whenever I open it. Now I can't even login as the gdm greeter also keeps restarting. This happened only after I upgraded my system this morning and now i have to use stupid windows :(. Any help?

---

### Post by Nevart on 2009-06-10
I don't have much to go on, but it could be that you are running on very low RAM and your swap partition is too small.  If there is not enough swap space, you can't start new processes.

If you're able to get it to launch, you could check this by starting up the System Monitor (System-Administration-System Monitor) and see how your memory stats look.  If the RAM consumption is very high and swap space is all used up or non-existent, then this could be the cause of the trouble.  Make a bigger swap partition!

Otherwise, you might need to try reinstalling.  You could optionally try exiting out of Gnome and starting up a raw X session and see how it goes. It could be Gnome that is contributing to this (going just into X will not load as much junk).  Or try XFCE, KDE, etc.  

Experiment!

---

### Post by anilcr on 2009-06-10
well... I have a 1 Gig ram and half a gig of swap space... and not more than half of it is used on start up ( I've seen this before )

---

### Post by Nevart on 2009-06-10
1Gb should be plenty, but 500MB could be too small for swap... not sure.  Better to have a big one than a small one.  Like with most things!

Anyway what I suggest is to try booting up with a different window manager than the default and see if you can launch applications manually.

You can also try going to System->Preferences->Sessions and disabling some of the start-up apps (careful with this... don't turn off something that looks important... but if it is just something goofy then turn it off and see what happens).

Do this systematically and you might find out which app is doing the damage.  Then just don't run it at start-up.

Let me know if none of that helps.  I probably an answer for you, but at least the next guy will know where to start from.

... edit....  

I forgot to add:  Can you run it with no problems from the Live CD?  If you can do that, then it is definitely your install that is the problem and not your hardware.  One more thing we could then say is not the problem!

---

### Post by anilcr on 2009-06-10
I think this is a problem with the gnome settings as my system was fine till today...

---

### Post by anilcr on 2009-06-10
Oh btw the other desktop managers, will try...

---

### Post by mschraier on 2009-06-12
I upgraded when Jaunty first wsa released and it worked great.  Now when I start yo bbot up, after the Kubuntu splash, an error comes up that ther greeter widget is nto installed and to check the configuration.  If i cannot log in, how can I chec anything?  Is there like a low level re-install that I can do so that I dont have to begin all over?

---

