---
title: "Java programs Title  bug in 5.10?"
date: 2005-12-19
forum: Desktop Environments
---

### Post by index_0@ya.com on 2005-12-19
Hi ..
        I recently installed ubuntu 5.10 in  my system  and tried to run some Java  programs , even the Sun 's Netbeans ... and i found that the Title of the window is null !!
 There is no title displayed for any windows Applications written in Java !! Somebody pls try this  in ur system and tell ...

---

### Post by index_0@ya.com on 2005-12-19
[QUOTE=index_0@ya.com]Hi ..
        I recently installed ubuntu 5.10 in  my system  and tried to run some Java  programs , even the Sun 's Netbeans ... and i found that the Title of the window is null !!
 There is no title displayed for any windows Applications written in Java !! Somebody pls try this  in ur system and tell ...[/QUOTE]


Somebody out thr to help ??

---

### Post by Kray on 2005-12-19
Did ya install JRE/JDK? If so, which one (Sun, IBM, what version)?

Breezy comes with build-in GCJ and this is default virtual machine for Java apps. I really don't think that it is 100% reliable solution. I would suggest u to install Sun JRE (or better JDK, since it looks that ure interested in programming) and then run
```
sudo update-alternatives --config java
```
and switch to freshly installed JDK (details here [http://ubuntuforums.org/showthread.php?p=534891#post534891]("http://ubuntuforums.org/showthread.php?p=534891#post534891"))

Cheers, Kray

---

### Post by index_0@ya.com on 2005-12-19
[QUOTE=Kray]Did ya install JRE/JDK? If so, which one (Sun, IBM, what version)?

Breezy comes with build-in GCJ and this is default virtual machine for Java apps. I really don't think that it is 100% reliable solution. I would suggest u to install Sun JRE (or better JDK, since it looks that ure interested in programming) and then run
```
sudo update-alternatives --config java
```
and switch to freshly installed JDK (details here [http://ubuntuforums.org/showthread.php?p=534891#post534891]("http://ubuntuforums.org/showthread.php?p=534891#post534891"))

Cheers, Kray[/QUOTE]

Well i ofcourse  use Sun's JRE , but when i  run Simple JFrame  Application .. there's no title diasplayed .. and even Netbeans IDE doesnt show up !!

---

### Post by Kray on 2005-12-20
If u sure that Sun JRE is picked as default JVM... hmmm... what version do u use? Paste output from```
java -version
```
ATM I can think about one reason of such weird bug - sometimes* Sun JRE/JDK try to use native GTK theme engine to render widgets and something goes wrong here. TBH I think that this is bullshit anyway (;-)), because windows frames and titles are (usually) painted by Windows Manager, not Java itself. Just a stupid guess :]

* JRE/JDK 1.5 can use themes based on BlueCurve engine, 1.6 (beta) can use  whatever gtk engine is used

---

### Post by index_0@ya.com on 2005-12-20
> **Kray]If u sure that Sun JRE is picked as default JVM... hmmm... what version do u use? Paste output from```
java -version
```
ATM I can think about one reason of such weird bug - sometimes* Sun JRE/JDK try to use native GTK theme engine to render widgets and something goes wrong here. TBH I think that this is bullshit anyway ( said:**
> 

* JRE/JDK 1.5 can use themes based on BlueCurve engine, 1.6 (beta) can use  whatever gtk engine is used

I have only one JDk installed apart from Ubuntu's GiJ .. and my version of  SUN's JDK is 1.5.04 .. 
Where do u think can i trace for this debug .. ?

---

### Post by Kray on 2005-12-20
Sadly, I don't think that I can help ya. If windows title isn't showed at all its sign of bug IMO. U can go to [http://bugs.sun.com/bugdatabase/index.jsp]("http://bugs.sun.com/bugdatabase/index.jsp") and search bug database... or just report this bug (registration required).

Of course u can try and debug it yourself, but I suppose that C/C++ skills are required - this isn't problem with JFrame.setTitle() method - it is too simple to be broken. IMO its issue with underlaying native libraries.

AFAIK sources for JVM <= 1.5 aren't accesible. If u *really* interested u can download Mustang (1.6, current in beta phase) JVM sources from [https://mustang.dev.java.net/]("https://mustang.dev.java.net/") and start playing with it...  not for those faint of heart, I suppose ;-) I wouldn't dare anyway, but my C/C++-fu is weak :p

--

Some thoughts... bzzzz, boring Java stuff :p

Now, this is source of Frame.setTitle():```
    public void setTitle(String title) {
        String oldTitle = this.title;
        if (title == null) {
            title = "";
        }


        synchronized(this) {
            this.title = title;
            FramePeer peer = (FramePeer)this.peer;
            if (peer != null) {
                peer.setTitle(title);
            }
        }
        firePropertyChange("title", oldTitle, title);
    }
```

take a look at lines ```
            if (peer != null) {
                peer.setTitle(title);
            }
```

When peer is null, title isn't set. Peer is (usually) native control/widget - underlaying to Java AWT controls (for example, AWT Frame will be Window on Windows and GTKWindow on Gnome*. Uhm, ok, Frame peer really shouldn't be null anyway). You can debug some simple Java applications, but... first u need JDK (JRE doesn't contains libraries sources), second - default Java libraries (JAR's) are distributed without debug informations, so u must to rebuild them.

* don't quote me on that ;-) It is just generic schema, maybe underlaying controls are called different

---

