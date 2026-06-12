---
title: "Yes! You CAN restore default keyboard shortcuts!"
date: 2009-04-15
forum: General Help
---

### Post by Megrimn on 2009-04-15
So here's the story:

I usually know what I am doing, so I decided to experiment with the keyboard shortcuts in System > Preferences > Keyboard shortcuts.  

Unfortunately, after I decided I liked some of the defaults better, I couldn't go back to the defaults because I had no clue what they used to be.  Should have written them down... :( 


[SIZE="4"] Fortunately, I figured out the solution!!! Amazing, yes?

Here are the directions:[/SIZE]

1. Boot the Live CD

2. When you get to the desktop, go to System > Preferences > Keyboard shortcuts

3. Write down the shortcuts you want to restore (don't forget to label them so you know what they are for!).

4. Shut down the Live CD

5. Boot-up Ubuntu normally

6. Open a terminal and use this command: 
```
gconf-editor
```
It will open the Configuration Editor

7. In the Configuration Editor, navigate to 
apps > gnome_settings_daemon > keybindings

8. Now find the shortcut that you wish to change back, and click the "Value" twice (double-click is too fast - click once to select, click again to edit)

9. Type in the shortcut.

10. Repeat steps 8 and 9 for all shortcuts you wish to change back.

11. REJOICE!


I would think you would do something similar if you are running KDE.  Feel free to post those directions as well.

Have fun, I guess.

---

### Post by rosswmcgee on 2009-06-15
I followed the insrtuctions but the key board  short cut settings in  9.04 are not there.

---

### Post by nallen00 on 2009-12-31
Well, if no one else will say it, I will...

Thanks!  It's one of those, "Gee, why didn't I think of that...?", sort of things.

---

### Post by jbatista on 2010-06-27
That's great, thanks. It helped me quite a bit.

Instead of having to boot from CD, you may want to just start a guest session and take note of the keys to be changed, as described above. 
I suppose it "works" because the new (temporary) guest session is always restarted in /tmp from stuff in /etc/skel and other places, so unless you change stuff *there*, you should have a "clean" image to inspect from.

---

### Post by ilankizner on 2011-11-30
what if the shortcut is a global shortcut like Ctrl + A 
mine in missing . and i get an error : 
Error while trying to run (<Control>a)
which is linked to the key (<Control>a)

---

### Post by thomassisson on 2013-04-04
As a special but not helpful note to KDE users, this typing the above command launched the APT installer for me. I don't know why. Unfortunately, I was doing an install from the terminal at the same time, so I it just said, "Waiting for other package managers to quit."

Booting from a Live CD is not always an option. For some users, it has been a while since their disc install. Many have upgraded several times since, and the Live CD or DVD may have been lost, written over, or destroyed.

In my opinion, there should always be an easy way to reset all of the keyboard shortcuts to the defaults in any distribution of Ubuntu since many users of Ubuntu distributions are not experienced Linux users.

---

### Post by CaptainMark on 2013-04-04
Please, not more necromancy

---

### Post by QIII on 2013-04-04
Thanks for sharing, but this was a pretty old thread.

From the Ubuntu Forums Code of Conduct:  [http://ubuntuforums.org/misc.php?do=showrules](http://ubuntuforums.org/misc.php?do=showrules)

> If a post is older than a year or so and hasn't had a new reply in that  time, instead of replying to it, create a new thread. In the software  world, a lot can change in a very short time, and doing things this way  makes it more likely that you will find the best information. You may  link to the original discussion in the new thread if you think it may be  helpful.
[I]
Thread **Closed.**[/I]

---

### Post by lisati on 2013-04-04
> **CaptainMark said:**
> Please, not more necromancy

Exactly. 

Things can change in the space of a year, and if a thread hasn't had a response in over a year, it's often safer to let it rest in peace by starting a new thread. It's OK to refer back to the old thread if necessary.

---

