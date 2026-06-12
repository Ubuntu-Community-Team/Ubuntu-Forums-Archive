---
title: "Questions about script storage"
date: 2009-06-17
forum: General Help
---

### Post by cloudfrog on 2009-06-17
Hey everyone,

I'm fairly new to ubuntu and shell scripting, but I'm starting to really get into it.  I've officially moved over from XP to running Ubuntu as my primary operating system.  Right now, I'm storing all of my scripts in my Documents folder, but I take it that isn't recommended.  I was wondering, where do you store your scripts and why?  Is there an optimal place to throw them so that they can easily be accessed when needed?

Thanks everyone!  You've all been a huge help!

---

### Post by Mighty_Joe on 2009-06-17
Any directory should do, as long as you can remember where you put things.  I have a "projects" directory with sub-directories for each programming project.  Inside each sub-directory is a README file which explains what the project does, how to build it and how to run it.  It's very important to document both the code and the project.  You'll be surprised what you can forget in a few days/months/years.

---

### Post by Augsburg on 2009-06-17
As for easier access, it's always good to keep the path short so a script can be run from the terminal without typing a long path (soft links are helpful for this).  If you are making executable files, you can store them in /usr/bin and make sure you can execute them (chmod).  Then all you have to do is type its name from the command prompt, without any path at all.

---

### Post by cloudfrog on 2009-06-17
Awesome!  I appreciate the advice greatly!

---

### Post by cariboo on 2009-06-17
Actually /usr/local/bin was designed to store locally created scripts and self compiled programs.

---

### Post by mcduck on 2009-06-17
I usually put my scripts in ~/bin instead, as most of them are for personal use anyway and there's no need to have them available for all users.

Besides, it makes working with the scripts easier (no need for sudo) and is included in path by default (after you actually create that directory) so you can run your scripts without having to type the path, just like if they were in one of the system-wide binary directories..

---

### Post by sdennie on 2009-06-17
> **mcduck said:**
> I usually put my scripts in ~/bin instead, as most of them are for personal use anyway and there's no need to have them available for all users.

Besides, it makes working with the scripts easier (no need for sudo) and is included in path by default (after you actually create that directory) so you can run your scripts without having to type the path, just like if they were in one of the system-wide binary directories..

That's the method I would recommend as well.  It's easier to do backups if the all the interesting data is in /home and /etc.

---

### Post by Augsburg on 2009-06-18
Thanks for the tip! I'll start doing that instead.

---

