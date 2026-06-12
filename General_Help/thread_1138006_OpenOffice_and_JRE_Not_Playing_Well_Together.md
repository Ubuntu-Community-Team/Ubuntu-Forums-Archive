---
title: "OpenOffice and JRE Not Playing Well Together"
date: 2009-04-26
forum: General Help
---

### Post by BJ_Covert_Action on 2009-04-26
Howdy All,

I am trying to use some of the wizard templates in OpenOffice. However, when I click on them, OpenOffice is telling me, "JRE not installed." I browsed through synaptic to see which packages I had installed and, sure enough, I have sun-java-6 installed. I figured out that you can set the JRE path in OpenOffice via the Tools>Options>Java dialog. 

Unfortunately I am note sure what, specifically, it is looking for as a "Java Run Time Environment." I tried pointing it to every directory I can find that has a java executable/bin in it. That didn't work. I ran:

```

 sudo update-java-alternatives --list

```

...and got...

```

java-6-sun 63 /usr/lib/jvm/java-6-sun

```

...so I tried pointing OpenOffice to /usr/lib/jvm/java-6-sun. It complained that the path specified does not contain a java runtime environment. So I browsed through this directory and found the following folders:

>bin
>ext
>jre
>man
>.systemPrefs

I tried pointing it to the 'jre' directory, same error, no java runtime environment in that path. I tried pointing it to bin, that didn't work. I tried going into >jre and tried pointing to >>lib, >>bin, >>lib>>>i386, and still nothing.

I think the problem is that I don't know what kind of file/path OpenOffice is looking for. I have pointed it square at numerous bin files and nothing. Does anyone know what I should be trying to point OpenOffice at to get it running with my JRE?

Thanks for all help in advance.

Cheers,
Brady

---

### Post by BJ_Covert_Action on 2009-04-30
Can anyone help me with this issue? It seems like there might be something simple that I am missing, but I am not sure what that simple thing is...

---

### Post by taurus on 2009-04-30
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
java -version
```

---

### Post by giovannilenzi on 2009-05-05
I've the same problem after upgrading to 9.04.
Before that, Openoffice and Java worked fine.

If I ask Java version I get

> java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu7)
OpenJDK 64-Bit Server VM (build 14.0-b08, mixed mode)

I even tryed to set JRE manually inside OpenOffice, but it doesn't work.

Notice I've a AMD64

---

### Post by giovannilenzi on 2009-05-05
Solved ... at least for me.
I went to Synaptic and I installed (just to try): 

```
openoffice.org-gcj

```

I had to close QuickStartOpenOffice and to restart it.
I'm not sure which was the problem, but anyway ... now it works fine as it did in Intrepid.
I hope this will be usefull to others.

---

### Post by virgil_machine on 2009-05-07
Worked for me. Thanks!

---

### Post by BJ_Covert_Action on 2009-06-20
Hey guys, sorry for the 2 month delayed response. After posting this a bunch of crap came up and I forgot all about it since I abandoned what I was working on. I am installing the gcj base right now. Hopefully it will work and thank you all for the posts so far :)

---

### Post by BJ_Covert_Action on 2009-06-20
It worked great. Thank you guys.

---

