---
title: "MonoDevelop &amp; java"
date: 2008-08-21
forum: Education &amp; Science
---

### Post by Uchiha_madara on 2008-08-21
Hi every one....
I am a computer Science and I have changed to Ubuntu

I hope from you to read my post to The Last :

1 - When I downloaded Mono Develop , I completed Building of My Project
    With Vb.net Code It give My an errors , My Friends told me to Compile and run it from terminal ....I don't Know How can I compile The Vb, C#,c++, or C code

2- I need to Know about good editor for java ...
   when I need to compile the java file with javac 

  there well be a message told "There are some packages are not installed"
  what is the recommended packages ....

---

### Post by alternatealias on 2008-08-23
If you want a Java Development Studio, you most definitely want Eclipse which is most likely the best there is. Best of all, it is both free and Free Software.

Here are the packages you'll want to grab:

> 
root@alternatealias:~# apt-show-versions | grep eclipse
eclipse-platform/hardy uptodate 3.2.2-5ubuntu2
eclipse-jdt/hardy uptodate 3.2.2-5ubuntu2
eclipse-source/hardy uptodate 3.2.2-5ubuntu2
eclipse/hardy uptodate 3.2.2-5ubuntu2
eclipse-platform-gcj/hardy uptodate 3.2.2-5ubuntu2
eclipse-rcp/hardy uptodate 3.2.2-5ubuntu2
eclipse-pde/hardy uptodate 3.2.2-5ubuntu2
eclipse-pde-gcj/hardy uptodate 3.2.2-5ubuntu2
eclipse-rcp-gcj/hardy uptodate 3.2.2-5ubuntu2
eclipse-gcj/hardy uptodate 3.2.2-5ubuntu2
eclipse-jdt-gcj/hardy uptodate 3.2.2-5ubuntu2


`apt-get install eclipse` should pull in all of the required packages listed above as well as all the necessary Java packages.

However, just in case, here are the Java packages I have installed for Java development:

> 
root@alternatealias:~# apt-show-versions | grep java6
sun-java6-bin/hardy uptodate 6-06-0ubuntu1
sun-java6-jdk/hardy uptodate 6-06-0ubuntu1
sun-java6-plugin/hardy uptodate 6-06-0ubuntu1
sun-java6-fonts/hardy uptodate 6-06-0ubuntu1
sun-java6-jre/hardy uptodate 6-06-0ubuntu1


(actually, I have a whole ton more - but they aren't necessary for what I suspect you'll be doing)

---

### Post by Uchiha_madara on 2008-08-24
I need to ask ....

Eclipse is heavy and eating the Memory and the Hard drive
isn't it?

---

### Post by alternatealias on 2008-08-24
> **Uchiha_madara said:**
> I need to ask ....

Eclipse is heavy and eating the Memory and the Hard drive
isn't it?

Then, you could always just use vi or emacs.

IDE's are usually a lot heavier than a text editor, but I thought that was what you were asking for.

I've used Eclipse on my old 1.6 GHz computer w/ 1 GB RAM just fine, and I suspect most people have machines more powerful than that.

---

