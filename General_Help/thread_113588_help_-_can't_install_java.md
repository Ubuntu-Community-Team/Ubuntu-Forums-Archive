---
title: "help - can't install java"
date: 2006-01-06
forum: General Help
---

### Post by makba018 on 2006-01-06
hello
I get to step number 5 of the java installation package and then it says:

`Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type'

chmod +x jre-1_5_0_04-linux-i586.bin`

What does this mean? Where do find the command line? I also do not understand step number 6 which says:

''To install JRE, run the downloaded file. Type

fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin

dpkg -i sun-j2re1.5_1.5.0+update04_i386.deb''

How do i run the program, where do i type these lines.

Thanks for anybody's help, as i am a begginner at this.

Mokhtar, Ottawa, Canada

---

### Post by dcstar on 2006-01-06
[QUOTE=makba018]hello
I get to step number 5 of the java installation package and then it says:

`Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type'

chmod +x jre-1_5_0_04-linux-i586.bin`

What does this mean? Where do find the command line? I also do not understand step number 6 which says:

''To install JRE, run the downloaded file. Type

fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin

dpkg -i sun-j2re1.5_1.5.0+update04_i386.deb''

How do i run the program, where do i type these lines.

Thanks for anybody's help, as i am a beginner at this.

Mokhtar, Ottawa, Canada[/QUOTE]
Right-click somewhere on your desktop, select "Open Terminal" - that is your "command line" entry box.

You need to learn how to navigate directories with the "cd" command, then you should be able to just follow the instructions.

Personally, I'd add the following repository to my system and just install the sun-j2rel1.5 package via Synaptic:

[http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

---

