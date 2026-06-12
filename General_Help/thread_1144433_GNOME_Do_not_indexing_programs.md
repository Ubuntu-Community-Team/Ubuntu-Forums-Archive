---
title: "GNOME Do not indexing programs"
date: 2009-04-30
forum: General Help
---

### Post by Genius314 on 2009-04-30
Hi.

I just installed 9.04 today, and haven't had many problems so far.
I installed [Gnome Do]("http://do.davebsd.com/"), because I had used it in 8.10, and liked it. But for some reason, Do never indexed any of my programs. So basically, the only things I can access from Gnome Do are a few folders, and Do-related things (like preferences and "About Do").
Is there a way to force Gnome Do to index my programs, or is this just a bug that I can't do anything about? :(

Thanks.

---

### Post by Genius314 on 2009-05-02
Bump.
Is anyone else having similar problems?

---

### Post by Tipped OuT on 2009-05-02
I'm guessing you're on Kubuntu, since you said you had to install GNOME. Any ways, why don't you just install Ubuntu if you're going to use GNOME :confused:

And if you're using Ubuntu and it was just a miscommunication then it's probably due to a bad installation. Everyone that I've delt with got a bad installation when they first installed 9.04 (including me).

---

### Post by Genius314 on 2009-05-02
Sorry about the confusion.
I'm talking about the program ["Gnome Do"]("http://do.davebsd.com/"). I installed Ubuntu, and am using Gnome. But Gnome Do won't index any programs, so when I search for them, nothing shows up.

I'll update the first post to make it a bit clearer.

---

### Post by Tipped OuT on 2009-05-02
Oh, it's my fault, I didn't know what GNOME Do was. Well I can't help you, sadly I do not know about that. :(

---

### Post by Genius314 on 2009-05-04
I tried Gnome Do out on my brother's computer... it worked fine. He has the same installation (32-bit 9.04), so I don't know what the problem is... it couldn't possibly be a hardware issue, could it?
Or maybe there's some old configuration files left over from my old installation that are interfering with it? What would I have to delete, if that were the case?

---

### Post by Genius314 on 2009-05-08
Bump...
Anyone know?

---

### Post by Tipped OuT on 2009-05-08
Try re-installing it?

---

### Post by jjblackfox on 2009-05-08
I have the same problem, I am using ubuntu 9.04 also. 
Tried reinstalling it, but it did not fix the problem.

---

### Post by mattgyver83 on 2009-05-08
Im not sure if i understand indexing correctly but ill take a stab at it.

I kept loosing my icons on do after restart, i just made sure that i used app launchers that are always on my main menu.  Seems if you just create a launcher on the desktop, drag it to do and delete the launcher, it will remain until a restart.  I think even if it remains on the desktop it will go away.

Just make sure your using shortcuts to icons that are always there.  Might have to clutter up your main menu a bit, but who cares right, your using do!

I hope thats what your speaking of.

*
If you mean indexing for searching of apps then im way off however i did read in another post that gnome-do may take a while to recognize apps but will learn them faster if you run them through do.  May somehow be linked to ubuntu's indexing tool as well.

---

### Post by Genius314 on 2009-05-10
> **mattgyver83 said:**
> If you mean indexing for searching of apps then im way off however i did read in another post that gnome-do may take a while to recognize apps but will learn them faster if you run them through do.  May somehow be linked to ubuntu's indexing tool as well.

Yup, they're not showing up at all. I tried running programs like Firefox through Gnome-Do (because if you type "firefox," you can just run the command), but that's annoying, and it still hasn't shown up as a program.

And no, reinstalling hasn't helped. And I've tried several times.

---

### Post by Genius314 on 2009-06-09
Has anyone found an answer to this yet? I haven't found anything...

---

### Post by Genius314 on 2009-06-27
Okay, so I found the answer on my own.

As it turns out, I had a few corrupted/invalid icons in my Gnome menu (courtesy of WINE... :P). Gnome Do must have seen these icons, gotten an error, and stopped indexing. Basically I just started Do in a terminal, which gave me an error, and the name of the file that it came from.
So I went to /home/USER/.local/share/applications, and deleted the bad files. I also had to delete the corresponding folder in /home/USER/.local/share/applications/wine/Programs/.

I still seem to get errors in the terminal from these icons, but they're gone from the menu, and Do works again.

Hope that helps anyone who ends up with the same problem! :D

---

