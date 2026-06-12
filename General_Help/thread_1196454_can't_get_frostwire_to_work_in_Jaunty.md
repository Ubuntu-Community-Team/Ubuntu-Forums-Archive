---
title: "can't get frostwire to work in Jaunty"
date: 2009-06-25
forum: General Help
---

### Post by Barney Oatmeal on 2009-06-25
Am told it's a java issue but don't know what to do about it....
anybody got experience with this???

---

### Post by hibliss on 2009-06-25
Try gtk-gnutella. It uses the same network, connects to the same peers, and does the same thing as Frostwire, but it is a native client instead of a Java AIO.
[URL="http://gtk-gnutella.sourceforge.net/en/?page=news"]
http://gtk-gnutella.sourceforge.net/en/?page=news[/URL]

By the way, it is in Synaptic with standard Jaunty repos.

---

### Post by Soul-Sing on 2009-06-25
hibliss right,+1.

Barney Oatmeal frostwire needs java, thats is Sun java, which can be installed via synaptic package manager: ubuntu-restricted-extra's. And then you have make the Sun java active/default, via:

```
sudo update-alternatives --config java
```
(type the number for sun java==>enter)

---

### Post by Barney Oatmeal on 2009-07-07
Going to try the GTK offering - likely simpler to learn to use it than to figure out why frostwire isn't working for me. Tried the code and changing the default - made zero difference other than I got a different error message from frostwire.
Thanks, all, for the help!
Blessings!

---

### Post by Barney Oatmeal on 2009-08-05
Tried GTK Gnutella - too complicated-looking, didn't like it.
Have had java issues with previous Ubuntus and am kind of afraid to mess up what I have going now - if I go to sunjava, alot of things on webpages quit working - graphics, movies, etc. - am using open java6 jdk now and everything works except Frostwire.
Is there any way I can use both javas and keep everything functional at the same time? That would be the "in a perfect world" solution..........

Thanks for the help so far!!!!!!!

---

### Post by Soul-Sing on 2009-08-05
What was the outcome of: ```
sudo update-alternatives --config java
```
What are the exact errormessages you get?

---

### Post by Barney Oatmeal on 2009-08-05
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          2    /usr/lib/jvm/java-6-sun/jre/bin/java



Am afraid that if I reselect sunjava that I'll lose the use of web graphics as has happened before....

Error message from frostwire tells me that java is not enabled.

---

### Post by Soul-Sing on 2009-08-05
But did you tried/enabled sun java to solve your problem?
You need sun java to run frostwire, and it is not set as default java...

---

### Post by Barney Oatmeal on 2009-08-05
If I enable Sunjava, doesn't that disable the other java (the one that is currently working fine for everything except frostwire)???
If I can run both simultaneously, that would work for me.

---

### Post by michy99 on 2009-08-05
I use the sun java for everything and have never had a problem.

---

### Post by Barney Oatmeal on 2009-08-15
Frostwire is working - but kava stuff on webpages is worse than it was before since going to sunjava6
guess it's a tradeoff........

---

