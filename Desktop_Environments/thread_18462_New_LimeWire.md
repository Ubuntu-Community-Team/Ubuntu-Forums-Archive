---
title: "New LimeWire"
date: 2005-03-07
forum: Desktop Environments
---

### Post by JmSchanck on 2005-03-07
Hey, i just installed the new LimeWire, and its working fine when I double click the runLime.sh icon from nautilus, but when i try to do this: 
```

john@ubuntu:~ $ sh /opt/LimeWire/runLime.sh

```
It tells me "Unable to access jarfile LimeWire.jar" oddly however it works just fine if i do this:
```

john@ubuntu:~ $ cd /opt/LimeWire && sh runLime.sh

```

Anyone know why it would be doing this? Its bugging me cuz i want to make a desktop icon for it and a launcher with "sh /opt/LimeWire/runLime.sh" wont work.

---

### Post by bored2k on 2005-03-07
> **JmSchanck]Hey, i just installed the new LimeWire, and its working fine when I double click the runLime.sh icon from nautilus, but when i try to do this: 
```

john@ubuntu:~ $ sh /opt/LimeWire/runLime.sh

```
It tells me "Unable to access jarfile LimeWire.jar" oddly however it works just fine if i do this:
```

john@ubuntu:~ $ cd /opt/LimeWire && sh runLime.sh

```

Anyone know why it would be doing this? Its bugging me cuz i want to make a desktop icon for it and a launcher with "sh /opt/LimeWire/runLime.sh" wont work.[/QUOTE]
 Here is my desktop icon script for Limewire:

Procedures:
1. I make a file in my home directory called lime.sh [text file] with this inside:
> 
#!/bin/bash
cd /opt/LimeWire/ said:**
> 

2. I give enough permissions to every user on the box like this [terminal]:
[quote]chmod 777 /home/user/lime.sh

3. I create the launcher, and for the command I input:
[quote] sh lime.sh 
It works for me and i have given that to several ppl on the forums :) .


4. Double Clic on the  icon and enjoy .

---

### Post by JmSchanck on 2005-03-07
Alright thanks bored, I was trying to avoid writing another shellscript for it but if thats the only way to do it im fine with that. thanks again
-John

---

### Post by TheCondor on 2005-03-07
Hello guys  :-) 

I did all that in order to get the launcher working for limewire ( i havent used limewire before and i thought this could be a good chance to try it ) but i get this problem in CLI : /home/bill/.gtkrc-2.0:2: Unable to find include file: ".gtkrc-2.0-scrollbar_cog


Thats something I encountered in several other stuff. For example when i do nautilus applications:/// i get this same error again and nautilus tells me that applications is not a valid location. ( same thing happens with preferences:/// )

Anyone have any clue how could I possibly fix this? In order to have limewire and the other stuff running as well.

Thanks in advance  :-)

---

### Post by bored2k on 2005-03-07
[QUOTE=TheCondor]Hello guys  :-) 

I did all that in order to get the launcher working for limewire ( i havent used limewire before and i thought this could be a good chance to try it ) but i get this problem in CLI : /home/bill/.gtkrc-2.0:2: Unable to find include file: ".gtkrc-2.0-scrollbar_cog


Thats something I encountered in several other stuff. For example when i do nautilus applications:/// i get this same error again and nautilus tells me that applications is not a valid location. ( same thing happens with preferences:/// )

Anyone have any clue how could I possibly fix this? In order to have limewire and the other stuff running as well.

Thanks in advance  :-)[/QUOTE]
 I really dont have a fix, but in case you dont know Limewire requires java, wether u have it integrated [wich would open with a doubleclic on runLime.sh] or somewhere "around" [would work with java -jar Limewire.jar].

Btw i have  .gtkrc-1.2-gnome2 file on my $Home and its working fine . I wouldn't think gtk is the problem as Limewire doesnt even use gtk as default .

---

### Post by TheCondor on 2005-03-08
[QUOTE=bored2k]I really dont have a fix, but in case you dont know Limewire requires java, wether u have it integrated [wich would open with a doubleclic on runLime.sh] or somewhere "around" [would work with java -jar Limewire.jar].

Btw i have  .gtkrc-1.2-gnome2 file on my $Home and its working fine . I wouldn't think gtk is the problem as Limewire doesnt even use gtk as default .[/QUOTE]

Hello  :-) 

I have the latest java installed. I use azureus all the time so I know its installed because its needed. 

I didnt understand the part where you said 'integrated'. What do you mean? Whenever I have tried to open a *.sh file it opens in a text editor. 

I googled for some help on that problem I have and all that I could find is to delete this files as it wasnt practically needed. I deleted it and nothing changed. 

I also tried the java -jar Limewire.jar command and I got this : 

Error: No MANIFEST.MF found in Limewire.jar

What would that mean?

Im really confused. Is a part of my Gnome kinda broken or something?  ](*,)  ](*,)

---

