---
title: "JDownloader not starting"
date: 2009-06-24
forum: General Help
---

### Post by notoriousmic24 on 2009-06-24
So I've been using JDownloader, and loving it. But out of nowhere, it just stopped opening. I created a shortcut, and tried opening through terminal, and still nothing. I tried the whole process to reinstall everything and still nothing. I'm guessing it might be some sort of bug from recent updates. I'm running 9.04 on a Dell inspiron e1505. Any help on how to uninstall or fix this?

---

### Post by michy99 on 2009-06-24
What happens if you open a terminal, change to the directory where your jd.sh script is, and enter```
./jd.sh
```

---

### Post by notoriousmic24 on 2009-06-25
JD Installation found: Starting JD now
Jun 25, 2009 6:02:56 PM - INFO [jd.Main(main)] -> Start JDownloader
JAR
Jun 25, 2009 6:02:56 PM - FINEST [jd.utils.JDUtilities(getJDClassLoader)] -> Create Classloader: for: /home/mike/.jd
Jun 25, 2009 6:02:56 PM - FINEST [jd.JDClassLoader(<init>)] -> rootDir:/home/mike/.jd
/home/mike/.jd
 file:/home/mike/.jd/jd
Jun 25, 2009 6:02:56 PM - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/mike/.jd/plugins/JDShutdown.jar
Jun 25, 2009 6:02:56 PM - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/mike/.jd/plugins/JDUnrar.jar
Jun 25, 2009 6:02:56 PM - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/mike/.jd/plugins/JDLightTray.jar
Jun 25, 2009 6:02:56 PM - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/mike/.jd/plugins/JDChat.jar
Jun 25, 2009 6:02:56 PM - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/mike/.jd/plugins/JDHJMerge.jar
Jun 25, 2009 6:02:56 PM - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/mike/.jd/plugins/JDTray.jar
Jun 25, 2009 6:02:56 PM - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/mike/.jd/JDownloader.jar
Jun 25, 2009 6:02:56 PM - INFO [jd.Main(main)] -> init Eventmanager
Jun 25, 2009 6:02:56 PM - FINER [jd.config.DatabaseConnector(<init>)] -> Loading database
Jun 25, 2009 6:02:56 PM - FINER [jd.config.DatabaseConnector(checkDatabaseHeader)] -> Checking database
Loaded language: english
Jun 25, 2009 6:02:56 PM - INFO [jd.Main(main)] -> init Localisation
Exception in thread "main" java.lang.NullPointerException
	at jd.Main.increaseSplashStatus(Unknown Source)
	at jd.Main.main(Unknown Source)

---

### Post by notoriousmic24 on 2009-06-26
Bump =-(

---

### Post by notoriousmic24 on 2009-06-26
is there a way to remove it so that i can reinstall it?

---

### Post by Jiaz on 2009-06-26
Hi  jd.sh has a bug in current version  you can 1.) redownload the jd.sh file [www.jdownloader.org/download](www.jdownloader.org/download) (linux) or 2.) open it and remove the part with --add-links or 3.) start jd manually with java -Xmx512m -jar JDownloader.jar  jiaz jd-team

---

### Post by notoriousmic24 on 2009-06-30
Thanks a lot, fixed it

---

