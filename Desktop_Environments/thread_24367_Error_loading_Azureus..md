---
title: "Error loading Azureus."
date: 2005-04-06
forum: Desktop Environments
---

### Post by Jaivaz on 2005-04-06
root@Kamigawa:/home/horace # /home/horace/azureus/azureus
Starting Azureus...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE [java = ]
You need to upgrade to JRE 1.4.x or newer from [http://java.sun.com](http://java.sun.com)
Java exec found in  /usr/java/jre1.5.0_02/bin/
Suitable java version found  [/usr/java/jre1.5.0_02/bin/java = 1.5.0_02]
Configuring environment...
Loading Azureus:
/usr/java/jre1.5.0_02/bin/java -Xms16m -Xmx128m -cp "/home/horace/azureus/Azureus2.jar:/home/horace/azureus/swt.jar:/home/horace/azureus/swt-mozilla.jar:/home/horace/azureus/swt-pi.jar" -Djava.library.path="/home/horace/azureus" -Dazureus.install.path="/home/horace/azureus" org.gudy.azureus2.ui.swt.Main ''
/home/horace/azureus/azureus: line 107: 24905 Segmentation fault      ${JAVA_PROGRAM_DIR}java -Xms16m -Xmx128m -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dazureus.install.path="${PROGRAM_DIR}" org.gudy.azureus2.ui.swt.Main "$@"
Azureus TERMINATED.

---

### Post by keyshawn on 2005-04-06
hey,
I remember I ran into this problem as a newb, on mandrake 9 [wow, that seems awhile back].....:razz:

it's unable to find where you have java installed on your computer...

1. If you don't have installed - check out the ubuntu guide - [http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre)

OR 

If it's already installed, then the configuration file needs to be edited to match the location of where you have java installed at. edit the executable, [the file is named 'azureus' and should be in its installed directory. mine's in /opt/ for example] 

there's a section on the top that says 

 ```
######## CONFIGURE ########
JAVA_PROGRAM_DIR="/put/the_path/for/java/here"    			# use full path to java bin dir, ex. "/usr/java/j2sdk1.4.2/bin/"
##########i#################
``` 

edit the _PROGRAM_DIR to match your java's location.

---

### Post by bored2k on 2005-04-06
try > Another possibility is to add a new repository entry to your /etc/apt/sources.list (AddingRepositoriesHowto) or use synaptic for this.

In the repository you can find the latest Sun JRE and Sun JDK prebuilt for Ubuntu Warty. At the moment there is Sun JRE/JDK 1.4.2_06, Sun JDK 1.5.0 (package from above source) and Sun JRE/JDK 1.5.0 Update 1.

deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) warty java

If you have not done already, you must add the multiverse repository for one dependency, too:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

The package is called something like sun-j2sdk1.5 (to find out its actual name do a search in synaptic for 'sun-j2' or type 'apt-cache search sun-j2'. 

---

### Post by Jaivaz on 2005-04-06
I did what you both said to do and now I get...

Starting Azureus...
Loading Azureus:
/usr/java/jre1.5.0_02/bin/java -Xms16m -Xmx128m -cp "/home/horace/azureus/Azureus2.jar:/home/horace/azureus/swt.jar:/home/horace/azureus/swt-mozilla.jar:/home/horace/azureus/swt-pi.jar" -Djava.library.path="/home/horace/azureus" -Dazureus.install.path="/home/horace/azureus" org.gudy.azureus2.ui.swt.Main ''
/home/horace/azureus/azureus: line 107:  6255 Segmentation fault      ${JAVA_PROGRAM_DIR}java -Xms16m -Xmx128m -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dazureus.install.path="${PROGRAM_DIR}" org.gudy.azureus2.ui.swt.Main "$@"
Azureus TERMINATED.

---

### Post by dabeej on 2005-04-10
java -Xms16m -Xmx128m -cp "/opt/azureus/Azureus2.jar:/opt/azureus/swt.jar:/opt/azureus/swt-mozilla.jar:/opt/azureus/swt-pi.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" org.gudy.azureus2.ui.swt.Main ''
/opt/azureus/azureus: line 107: 12494 Segmentation fault      ${JAVA_PROGRAM_DIR}java -Xms16m -Xmx128m -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dazureus.install.path="${PROGRAM_DIR}" org.gudy.azureus2.ui.swt.Main "$@"
Azureus TERMINATED.

It use to work. Gnome-panel crashed and wham.
Same thing here!

---

