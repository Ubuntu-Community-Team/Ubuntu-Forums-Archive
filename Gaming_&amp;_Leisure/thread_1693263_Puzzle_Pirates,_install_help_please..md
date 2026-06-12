---
title: "Puzzle Pirates, install help please."
date: 2011-02-22
forum: Gaming &amp; Leisure
---

### Post by Zurrgle on 2011-02-22
It installed into a weird named folder in my "Home" folder.

It's called "@client_name@"

There is a few pngs in there and a folder named "java" in that folder theres a few more folder, such as "bin"

I also have the desktop image.

When i click it, it says.

"Details: Failed to execute child process "/home/myname/@client_name@/java" (Permission denied)"

I changed this to go to the java folder because it seemed like where it needed to be, before it was pointing to thin air lol. I can't change the folders permission because it says im not the owner.

---

### Post by Perfect Storm on 2011-02-22
You can properly execute one of the bin files. Also check if the java or one of the bin files is set to allowed to be executes (right click ---> properties).

Also make sure you have sun java installed first.

---

### Post by Zurrgle on 2011-02-22
I installed sun java.

The file called java i cant make it executable. It says the owner is "root"

I cant do anything with it.

---

### Post by Perfect Storm on 2011-02-23
I just checked the game, as far as I can see it's a browser game.
Where did you get the download?

---

### Post by jhroach on 2012-06-19
Only Sun java is supported, so if its installed properly you just need to make sure the installer knows where to look for it.  Run the bin agian (*sh yohoho-0--en-install.bin*) and when it prompts you to point it at java, use  */usr/lib/jvm/java-6-sun *instead of leaving it at* /usr* or* /usr/bin/java*.  Its looking for the virtual machine in particular.[I]  Cheers.
              -jim
[/I]

---

### Post by ambermollers on 2012-06-20
What exactly is sun java?

---

### Post by Perfect Storm on 2012-06-21
> **ambermollers said:**
> What exactly is sun java?

Oracle have taken over Sun so it's Oracle java.

If you want to install Oracle java; [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

