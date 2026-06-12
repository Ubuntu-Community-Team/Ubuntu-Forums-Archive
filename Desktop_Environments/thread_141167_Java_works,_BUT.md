---
title: "Java works, BUT"
date: 2006-03-07
forum: Desktop Environments
---

### Post by osuchasenuts on 2006-03-07
java -version

java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

Using newest versions of firefox, opera, and ubuntu updates.

All of my java websites work correctly, except for facebook. There is a "program" within facebook for uploading pictures from my computer, and it uses java. 

On a windows machine it will load the java flash screen, and then display my computer's file manager where I can browse around and select files to upload.

On my ubuntu breezy, it will show the java splash screen, load half way, and then the loading bar will just stop moving. My guess is the java script is asking for permission to look at my hard drive, and ubuntu is refusing it. I have tried using sudo firefox , but there is no difference.

Any ideas on how to make this work? i.e. give java sudo permissions?

You have to have facebook access to test it out, but I am sure there are members on this forum that have it...

---

### Post by rjwood on 2006-03-13
I am having what sounds like the same issue with yahoo card games. I've been playing with it for 2 day's now and thought I had it but no luck yet.. I'm using dapper. Was working fine untill update a few day's ago.

---

### Post by bradlis7 on 2006-04-09
I don't think it's permission problems... it wouldn't be able to see the file in the first place without the correct permissions. I'm having a similar problem, except it never begins the upload. The java program will still respond somewhat, but the browser is completely unresponsive upon clicking upload.

I'm sure it has to do with the jre on linux, seeing that it works on windows. But since facebook's code is not open, facebook will have to submit the bug back to java, or create a workaround. I'll submit a problem to facebook, but it will probably be low priority for them.

---

### Post by x5452 on 2006-04-10
I totally think java 1.5 sucks. I had it installed as default and programs wouldnt even run, but I installed java 1.4 and everything immediately ran smooth with no problems...just my 2 cents.  :mrgreen:

---

### Post by bbarrons on 2006-04-10
I have the same problem with ameritrade.com On windows it opens java windows to buy and sell and for news for stocks. On linux the windows open but are not all there. 
The top of the window that states what account flickers so fast that you cant select. This is true on ubuntu and xandros. I tried different versions of java with the same result. The only way I could get it to work was install crossover and use IE6. It worked fine then. I hate IE6 and wont even use it on my windows machine. Any thoughts??
thanks
Bill

---

### Post by bradlis7 on 2006-04-10
On facebook, you can use the "simple upload thinger." That's the response I got from the facebook staff. I don't think they knew what Ubuntu was, cuz they said "try another browser". It's pretty frustrating when you know more about computers than the people working for computer companies.

---

### Post by akshayas1986 on 2007-09-30
Same problem with me too. 
I have been using Beryl display manager. Java typically runs into issues witht either Beryl or Compiz. So I tried with Metacity and yet it failed. Dont know what next to do.

---

### Post by akshayas1986 on 2007-09-30
Hey,
Well I had the same problem too but I fixed it.

See your Java version on your shell is different from Java for browser. You need a java web browser plugin. Now my problem was I had initially installed jdk 1.4 browser plugin and later installed java 6. Though on shell it gave version as 1.6, [Javatester]("http://www.javatester.org/version.html") showed java 1.4. So all I did was remove java 1.4 Blackdown from my synaptic manager (Applications > Add/Remove) and added java 5 browser plug in. Its working fine now

Hope this helps you

---

### Post by nicatron on 2007-09-30
I do a _LOT_ of java coding and have the same error. When I try to load my client, it fails to see images then complains about its java version... I installed from java.sun.com so im quite bugged. :confused:

---

### Post by nicatron on 2007-09-30
> **akshayas1986 said:**
> Hey,
Well I had the same problem too but I fixed it.

See your Java version on your shell is different from Java for browser. You need a java web browser plugin. Now my problem was I had initially installed jdk 1.4 browser plugin and later installed java 6. Though on shell it gave version as 1.6, [Javatester]("http://www.javatester.org/version.html") showed java 1.4. So all I did was remove java 1.4 Blackdown from my synaptic manager (Applications > Add/Remove) and added java 5 browser plug in. Its working fine now

Hope this helps you
nice but go to java.com and folow their linux instructions, they will tell you how to link your browser to the JRE on your computer
sry for double posting...

---

