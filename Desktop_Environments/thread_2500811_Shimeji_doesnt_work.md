---
title: "Shimeji doesnt work"
date: 2024-09-12
forum: Desktop Environments
---

### Post by makaroninn on 2024-09-12
So i've recently wanted one of these Shimejis but when I downloaded linux-shimeji i've got a few error messages.
*Error: Could not find or load main class com.group_finity.mascot.Main*
*Error: Unable to access jarfile /home/stepan/linux-shimeji/src/main/java/com/group_finity/mascot/image/SD-N*
Then i downloaded windows Slimeji and got this:



Gtk-Message: 18:37:27.781: Failed to load module "canberra-gtk-module"
*Exception in thread "main" java.lang.NullPointerException*
*    at com.group_finity.mascot.imagesetchooser.ImageSetChooser.<init>(ImageSetChooser.java:54)*
*    at com.group_finity.mascot.Main.run(Main.java:268)*
*    at com.group_finity.mascot.Main.main(Main.java:133)*
and I can't find this module anywhere. Could anyone help?

---

### Post by yancek on 2024-09-12
When you are posting a question about obscure, little used software it is a good idea to at least post a link to the site from which you downloaded it, that is if it is not in the repositories.  Is the page at the link below what you are referring to?  Did you follow the instruction on that page or a similar page? 

[https://github.com/fdibaldassarre/linux-shimeji?tab=readme-ov-file](https://github.com/fdibaldassarre/linux-shimeji?tab=readme-ov-file)

Did you notice the comment near the top of that page "This is a work in progress"?

What exactly were you doing to get the first error you report, what command did you enter if any?

Also, you forgot to post which version/release of Ubuntu you are using.

---

### Post by makaroninn on 2024-09-13
Sorry. I am currently using Ubuntu 24.04LTS. Yes, I did notice that is a work in progress. A previous version gave me so much bugs and errors that I've decided to wait till the next version. 
Yes, this is the pp I was talking about.
This is how I started the app:
*java -jar */home/stepan/linux-shimeji/src/main/java/com/group_finity/mascot/Main.java
becaune neither launch.sh nor build.sh gave anything. Absolute nothing.(launching build.sh gave absolutely nothing. no errors, no nothing.)
The next error is by a different, more adapted file that came with a Shimeji(not the app but the small guy):*java -jar /home/stepan/linux-shimeji/SD-N Shimeji/Shimeji-ee.jar *
[I]Error: Unable to access jarfile /home/stepan/linux-shimeji/SD-N
[/I]p.s. Yes I am well aware that this is Windows Shimeji app but I still thought it would be useful to give it a go
The third one is obtained by using stock Windows Shimeji app from [https://www.shimejimascot.com/p/desktop-tutorial.html](https://www.shimejimascot.com/p/desktop-tutorial.html) .
*java -jar /home/stepan/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/shimejiee/Shimeji-ee.jar *

---

### Post by makaroninn on 2024-09-13
Sorry for taking your time, I have reinstalled it through Dpkg and it works now!!!!!!!

---

### Post by makaroninn on 2024-09-13
Sorry, how do I put a "solved" mark here?

---

### Post by yancek on 2024-09-13
Have you tried the suggestion at the link below?

 [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

