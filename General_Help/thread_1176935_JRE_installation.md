---
title: "JRE installation"
date: 2009-06-02
forum: General Help
---

### Post by IanBorn on 2009-06-02
Hello everyone,

  I need help how to install JRE on my machine. I  download the file :

  jre-6u14-linux-i586-rpm.bin

 and have no clue  how to run the installation.

Thanks.

---

### Post by divague on 2009-06-02
open a terminal and type

```
sudo apt-get install sun-java6-jre
```

---

### Post by IanBorn on 2009-06-02
Thank you.

---

### Post by IanBorn on 2009-06-02
Somehow I screw up by closing the console too early. And after I reboot and try it
again, it gave me like this :

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-13-1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-13-1) but it is not going to be installed
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

==============

I don't understand the menaning of these messages.

---

### Post by michy99 on 2009-06-02
Enter in terminal:
```
sudo apt-get -f install
```Then try to install again.

---

### Post by IanBorn on 2009-06-02
It still get stucked like this on the console and I press Enter several times and have
no response.
14. MISCELLANEOUS.  Any action related to this Agreement will be                                   &#9618;
 &#9474;     governed by California law and controlling U.S. federal law.  No                               &#9618;
 &#9474;     choice of law rules of any jurisdiction will apply. If any                                     &#9618;
 &#9474;     provision of this Agreement is held to be unenforceable, this                                  &#9618;
 &#9474;     Agreement will remain in effect upon the parties' agreement to                                 &#9618;
 &#9474;     revised terms that most nearly accomplish the same effect. This                                &#9618;
 &#9474;     Agreement is the entire agreement between you and Sun relating to                              &#9618;
 &#9474;     its subject matter.  It supersedes all prior or contemporaneous                                &#9618;
 &#9474;     oral or written communications, proposals, representations and                                 &#9618;
 &#9474;     warranties and prevails over any conflicting or additional terms                               &#9618;
 &#9474;     of any quote, order, acknowledgment, or other communication                                    &#9618;
 &#9474;     between the parties relating to its subject matter during the term                             &#9618;
 &#9474;     of this Agreement.  No modification of this Agreement will be                                  &#9618;
 &#9474;     binding, unless in writing and signed by an authorized                                         &#9618;
 &#9474;     representative of each party.                                                                  &#9618;
 &#9474;                                                                                                    &#9618;
 &#9474;                                                                                                    &#9618;
 &#9474; For inquiries please contact: Sun Microsystems, Inc., 4150 Network Circle, Santa Clara,            &#9618;
 &#9474; California 95054, U.S.A.                                                                           &#9618;
 &#9474;                                                                                                    &#9646;
 &#9474; DLJ v1.1                                                  27APR2006ANS                             &#8595;
 &#9474;
 &#9474;                                               <Ok>
 &#9474;                                                                                                    &#9474;
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by michy99 on 2009-06-02
Use the Tab key until <ok> is selected and press enter.

---

### Post by IanBorn on 2009-06-02
That was it. However, I could not find the command jre. Where all those files got installed to?
I need the jre command to make sure installation is correct.

I don't know why japi need jre.

Thanks for your help.

---

### Post by t0p on 2009-06-03
There is no command "jre".  If you want to run a java program, you should navigate to wherever you've saved the .jar file and give the command

```
java -jar somejavacommand.jar
```

replacing **somejavacommand.jar** with whatever's appropriate.

For instance, I've got the java app **freedom.jar** inside a directory called **freedom**.  So to run it, I type into the terminal

```
java -jar freedom/freedom.jar
```

Hope this helps.

---

### Post by IanBorn on 2009-06-03
I am trying to use JAPI C GUI to develop some applications. JAPI requires JRE
and said that I should issue a command jre to see if it insalled correctly.
JAPI require jre.

Anyway, I get JAPI running on Vista. I will try to develop my application on Vista
first before porting to Linux.

Thanks for your efforts.

---

### Post by Yellow Pasque on 2009-06-03
Run this command to check the JRE version:
```
java -version
```

---

