---
title: "PATH trouble with Eclipse"
date: 2009-06-09
forum: General Help
---

### Post by xlns on 2009-06-09
Hello!

I had dilemma should I post here or to programming section, hope I didn't missed the forum.

I am a new ubuntu user and I'm having problem setting up Eclipse. 

I do not have a internet connection on my PC to use apt-get so I DL'd a Eclipse package on public PC and simply extracted it to my ~ . Then, I've added JDK path ( by editing .bashrc ) to PATH and Eclipse works great when I start it from terminal ( by ./eclipse ). When I check Eclipse's Window/Preference/Java/Installed JRE - there is my JDK recognized with correct path. Problem is that I can't run Eclipse by doubleclicking it because it complains that it 

"...JRE or JDK must be available in order tu run Eclipse. No JVM was found in ~/eclipse/somewhere or 
java in your current path
"?!

Of course, should I run "java -version" from any directory I get version information displayed 

java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Client VM (build 14.0-b16, mixed mode, sharing)

so I know PATH is set correctly. JAVA_HOME is also added to bashrc. I did find solution with linking java's bin to eclipse directory, but I would *really* like to know why this happens and any other not-so-hard-coded(!!!) solution would be truly appreciated. Thanks! :)

---

### Post by heepie on 2009-11-14
I just set a new thread with a similar question... I just installed the eclipse 3.5 that comes with Karmic but Eclipse doesn't seem to find java anywhere...

help !!!!

This is my thread:

[http://ubuntuforums.org/showthread.php?t=1326626&highlight=eclipse+java](http://ubuntuforums.org/showthread.php?t=1326626&highlight=eclipse+java)

---

### Post by heepie on 2009-11-14
installing eclipse-jdt from synaptic solved the problem

---

