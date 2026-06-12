---
title: "Help with Linewire...."
date: 2006-01-05
forum: General Help
---

### Post by AgonxOC on 2006-01-05
I was messing around trying to get to know the software and I installed Limewire. Now it shows up on the menu, but when I click on it Nothing, Nada, what did I do wrong?

Alex

---

### Post by DoorGunner on 2006-01-05
did you try rebooting.....sometimes programs need to be set by rebooting

---

### Post by briancurtin on 2006-01-05
[QUOTE=DoorGunner]did you try rebooting.....sometimes programs need to be set by rebooting[/QUOTE]
that really shouldnt be the problem

---

### Post by mEtho on 2006-01-05
[QUOTE=DoorGunner]did you try rebooting.....sometimes programs need to be set by rebooting[/QUOTE]

i dont think rebooting have anything to do with that, the following command does this!!!

*killall gnome-panel*

could u please post us the contents of the */usr/share/applications/LimeWire.desktop*, this may have not configured properly!!!

---

### Post by Perfect Storm on 2006-01-05
You need java to be installed if you want to run limewire.

---

### Post by DoorGunner on 2006-01-05
Yes AI is absolutly right......man...im getting tired or something thats 3 mistakes tonight.....see you all tomorrow and sorry about my posts....](*,)

---

### Post by AgonxOC on 2006-01-05
I have installed Java accordingly, but I am not sure if it was intalled for sure. How can I tell? 

Alex

---

### Post by AgonxOC on 2006-01-05
[QUOTE=mEtho]i dont think rebooting have anything to do with that, the following command does this!!!

*killall gnome-panel*

could u please post us the contents of the */usr/share/applications/LimeWire.desktop*, this may have not configured properly!!![/QUOTE]

I followed that link and in APPLICATIONS there is a LIMEWIRE ICON, but that wont do anything either....

Alex

---

### Post by mEtho on 2006-01-05
[QUOTE=AgonxOC]I followed that link and in APPLICATIONS there is a LIMEWIRE ICON, but that wont do anything either....

Alex[/QUOTE]

To be honest, its very hard to tell what the problem is if you dont show us the files for limewire or java, or tell us how you installed it, etc:confused: . all i could suggest is remove it and try to install again!!!

---

### Post by magnusbb on 2006-01-05
Launch Limewire from a terminal and see where it hangs. I'm quite sure this has to do with your Java installation. There can be a conflict between the Java version you've installed and the GNU Java version shipped with Ubuntu. That was the case when I had problems with Java programs. 

If that's the case, you'll have to look at some of the Java solution threads from earlier in this forum.

---

### Post by hornett on 2006-01-05
Tried automatix, and latest rpm from the net, both give me the following:

```
./runLime.sh: 44: Syntax error: "(" unexpected (expecting "}")
```

Line 44 is the one in bold:
> ...
look_for_javaImpl()
{
  IFS=$'\n'
  **potential_java_dirs=(`ls -d1 "$JAVADIR"/j* | sort | tac`)**
  for D in "${potential_java_dirs[@]}"; do
    if [[ -d "$D" && -x "$D/bin/java" ]]; then
      JAVA_PROGRAM_DIR="$D/bin/"
      echo $MSG2 $JAVA_PROGRAM_DIR
      if check_version ; then
	return 0
      fi
    fi
  done
  echo $MSG8 "${JAVADIR}/" $MSG9 ; echo $MSG4
  return 1 
}
... 


Not knowing much about shell programming, I can't see where there error is...

PS. I have the gnu interpretter for Java installed - is that good enough for Limewire to run?

> d600 ~ $ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


---

### Post by Perfect Storm on 2006-01-05
Lets start all over again:

First uninstall the java.

then:

```

sudo gedit /etc/apt/sources.list

```

add these line:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
#deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
[/b]

```

sudo apt-get update
sudo apt-get install sun-j2re1.5

```

Additional you can add java control center to your application tab:

```

smeg
```

Pick **System Tools** and click **New Entry**

Name: Java Control Center
Command: sh /usr/lib/j2re1.5-sun/bin/ControlPanel
Icon: Whatever you prefer Or use this I've attached

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=4778&d=1135285593[/IMG]

---

### Post by truthfatal on 2006-01-05
I tend to look through Limewire's Forums when I have a problem with limewire..

[Installing Limwire on Ubuntu/Debian]("http://www.gnutellaforums.com/showthread.php?threadid=39850")

I don't know / havn't seen any problems with Sun's JRE -- I recall there was something about it, but that might have been while I was still using Fedora.

---

### Post by AgonxOC on 2006-01-05
How do I uninstall programs...

Alex

---

