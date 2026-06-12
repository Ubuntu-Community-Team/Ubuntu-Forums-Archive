---
title: "Running a program at startup"
date: 2006-05-17
forum: Desktop Environments
---

### Post by N8MAN1068 on 2006-05-17
I have a program that has variable settings that I normally run through terminal.
I'd like to be able to just have that program startup in the background as a daemon or whatnot. I know I have to add a '&' to the end of the command line for it to return a prompt in the terminal, and I'm pretty sure I have to add it to init.d somehow, but not really sure how.

Can anyone point me in the right direction?

---

### Post by Sef on 2006-05-17
To get it to run at start up:

System > Administration > Services

Likely then /usr  then /bin and find the program you want to start.  click on it.

---

### Post by frodon on 2006-05-17
If you want to execute a script on startup (before GDM/KDM login screen) put your script under /etc/init.d and make it executable then do a : ```
sudo update-rc.d *name_of_script* defaults
```

---

### Post by Spyder89 on 2008-04-11
Ok I tried this for me and it gives me an error "./setCommonEnv.sh can't open file". In the directory of the  script that I want to run the setCommonEnv.sh script is there so I copied and pasted into /etc/init.d and run update-rc.d setCommonEnv.sh defaults and still get that error on startup. 

Anyone have suggestions?

---

