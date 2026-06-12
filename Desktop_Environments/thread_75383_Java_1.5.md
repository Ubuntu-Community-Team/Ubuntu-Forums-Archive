---
title: "Java 1.5"
date: 2005-10-13
forum: Desktop Environments
---

### Post by chadwick359 on 2005-10-13
Using the fakeroot java-package method, I can't create .debs for java packages. Can somebody who has had succes with this please mail a copy of the .deb to [email]chadwick359@gmail.com[/email] ? I'm really sorry for not hunting down one of the threads that this has been discussed in before, but I am inbetween classes and need this by tonight. Again, sorry, and thanks for any help in advance.

---

### Post by cbudden on 2005-10-13
as it is nearly 30 mb i am uploading to my webspace.

---

### Post by cbudden on 2005-10-13
[http://www.sitesled.com/members/cbudden/sun-j2re1.5_1.5.0+update05_i386.deb](http://www.sitesled.com/members/cbudden/sun-j2re1.5_1.5.0+update05_i386.deb)

---

### Post by cbudden on 2005-10-13
Could someone please either mirror this or upload it as an attachment as my bandwidth is running out fast, as i must now go.

---

### Post by Stealth-X on 2005-10-13
I just went to java.com got latest one.
copied to /usr/java
and limewire worked.

---

### Post by Zhukov on 2005-10-13
Try this:
[www.jpoa.ecwhost.com](www.jpoa.ecwhost.com)

---

### Post by chadwick359 on 2005-10-13
Thanks so much guys. I didn't get it quite in time for my class, but I'm installing now, so all seems to be well.


edit/ 
Second cup of Ubuntu! Yay!
/edit

---

### Post by Zhukov on 2005-10-13
ubuntu-towers still have the java debs in case you ever need them again in the future

---

### Post by chadwick359 on 2005-10-13
Hmm, well I got the package installed, but gji is still handleing my java functions, and still reports a 1.4.2 java -version. Also, eclipse still won't compile 1.5 applets. I tried editing the /etc/eclipse/java_home to point at the new dir created by the 1.5 package, but still no dice. Anybody have any luck on this?

---

### Post by Zhukov on 2005-10-13
I really think you should try the little program i told you... It handles all that fuss :P

---

### Post by chadwick359 on 2005-10-14
Thank you Zhukov, i did try that program, and it was nice, but it didnt fix my problem, it needed more love than that.

---

### Post by dto on 2005-10-14
Did you put the /bin directory of the Java 1.5 install in your system path (and before /usr/bin)?

---

### Post by babui on 2005-10-14
The way to select java 5 as the default java wm globally is:

$ sudo update-alternatives --config java

and selecting the java 5 wm

---

### Post by Zhukov on 2005-10-14
Have you solved your problem?

---

### Post by chadwick359 on 2005-10-14
I have, and it turned out that I needed to change the default java, as well as manually edit some of the configs for eclipse. Thanks for the help, all.

---

### Post by cbudden on 2005-10-14
Sorry but have run out of bandwidth (free host) so must take it off. Sorry.

---

### Post by chadwick359 on 2005-10-14
Thats okay, thanks for posting the file!

---

### Post by sbassett on 2005-10-14
[QUOTE=chadwick359]Thats okay, thanks for posting the file![/QUOTE]


I have a deb as well. Will be posting this evening.

---

### Post by Zhukov on 2005-10-14
Once again: the deb is available at ubuntu towers!!!

---

### Post by cbudden on 2005-10-14
[QUOTE=Zhukov]Once again: the deb is available at ubuntu towers!!![/QUOTE]

What are ubuntu towers?

---

### Post by Zhukov on 2005-10-14
They're kinda like the Lord of The Rings towers and... :P Just kidding!
Add this repositories and search for sun ;)

deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java

But dont forget to add the PATH at /etc/profile:

JAVA_HOME=”/usr/lib/java”
export JAVA_HOME

umask 022


and remove both gij and gij-4.0

---

### Post by sbassett on 2005-10-14
I have also added the deb to my downloads section. See my sig.

A small problem was fixed. The Deb is now available.

---

### Post by BLTicklemonster on 2005-10-15
[QUOTE=Zhukov]Try this:
[www.jpoa.ecwhost.com](www.jpoa.ecwhost.com)[/QUOTE]

YAY!!! Now if I can learn a foriegn language (other than enlish, y'all) I'd be set. ](*,)  How do I get it in English?


NM, dad made me learn to understand root words and base latin crappola, so most of all that makes sense.


*edit:

It's installing, but I can see that it's having problems finding stuff that isn't in latin or pig latin, Southern Drawl or gibberish.

don't have J2SDK... among other things. Wonder what I have to do to get java working? Installed that, but still... I'll just keep hammering away...

---

### Post by jdong on 2005-10-15
Please note that repackaging and redistributing Java in this way is a violation of Sun's license. For those making the packages, keep them to yourself; help others do it if possible. If you post it, you're subject to legal action from Sun. You have been warned. :)

---

### Post by BLTicklemonster on 2005-10-15
Well, I'm getting rid of it anyway, it messed up libdvdcss2 and now I cant run synaptic until I reinstall it. 

yeah, be warned kids!!!

---

### Post by Zhukov on 2005-10-16
Lol
The english version will be up tomorrow (at night in the worst case) :D So chill out
The Java included there is proven to work in at least 10 machines.

---

### Post by s0lid on 2005-10-17
[QUOTE=jdong]Please note that repackaging and redistributing Java in this way is a violation of Sun's license. For those making the packages, keep them to yourself; help others do it if possible. If you post it, you're subject to legal action from Sun. You have been warned. :)[/QUOTE]

Is that the reason why the java is out of the backports? can you give me links on this legal issue?

thanks bro!

---

### Post by vassie on 2005-10-17
Has anyone got a link to sun-j2re1.5_1.5.0+update05_i386.deb ?

I can mirror it if you like?

Ben

---

### Post by Zhukov on 2005-10-17
English version uploaded!
( [www.jpoa.ecwhost.com](www.jpoa.ecwhost.com) )

Do note the part about the script to detect and mount automatically win and mac partitions ( thanks to [www.ubuntulinux.nl](www.ubuntulinux.nl) ).

Enjoy!

Ill add Eclipse as soon as i can!

---

