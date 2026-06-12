---
title: "A few simple questions"
date: 2005-10-03
forum: Desktop Environments
---

### Post by drgreborn on 2005-10-03
First of all I'll like to apologise if my questions seem trivial.
1) I do not seem to be able to move any files watsoever around easily in UBUNTU. No read/write access. By default if I am not wrong, I should be able to move files into say /usr/local and do such without a problem. It seems that I have to constantly go into "root" to do this and this is tedious. Is there a way around this?
2)Installation of eclipse. I have insatlled the j2seSDK, it is located in /usr/loca/java. But when I try to run eclipse, it keeps saying that there is jre available. I believe this is a problem caused by not setting teh path. Could someone be kind enough to point me in the right direction?
Thank you in advance.

---

### Post by frodon on 2005-10-03
To move, copy or modify a file in your linux partition you will always need to be root (expect in your home directory), it's one of the reasons why linux is really secure.

---

### Post by tehwa on 2005-10-03
After setting up your system, you shouldn't really need to move files between directories that aren't writeable by the user, so it's really just a temporary nuisance. In the meantime, run nautilus in root by opening a command prompt and running:```
gksudo nautilus
```
This is where the command line is useful, since you can simply prefix move, or file editing commands with 'sudo', and you wont have to worry about whether you are root.

With regards to your Java issue, verify this is a typo:```
 /usr/loca/java
```
Unless this is where you keep your crazy applications.

(kidding)

Edit: command

---

### Post by drgreborn on 2005-10-03
yes its a typographical error. So sorry bout that.:oops:

---

### Post by tehwa on 2005-10-03
[QUOTE=drgreborn]yes its a typographical error. So sorry bout that.:oops:[/QUOTE]
nah, sorry. I saw the joke, I had to go for it. Wasn't really funny in the end anyway. I'm looking at the Java thing...

---

### Post by tehwa on 2005-10-03
Are you running it with -vm /path/to/java?
```
eclipse -vm /usr/local/java
```

---

### Post by drgreborn on 2005-10-03
Actually what I am looking for is a small guide or howto in setting up eclipse+lombozz+CDT on ubuntu. I just switched from the "Other OS" and would like to do my gaming dev project on linux if possible.

---

### Post by tehwa on 2005-10-03
Try alt java loc:
```
./eclipse -vm /usr/lib/j2sdk1.5-sun
```
Your location may differ, check /usr/share/j*.
I'm afraid i've never heard of this Howto, you should write one.

---

### Post by drgreborn on 2005-10-03
Haha, yah cant seem to find any howtos. Everyone just seems to say taht u just need to install java and unzip eclipse and hey presto. Which by the way should be the case. Anyhow thanks tehwa for the headsup.

---

### Post by drgreborn on 2005-10-04
I did what tehwa had told me to do. But it still cant seem to find the jre. Any ideas why?
[IMG]http://i9.photobucket.com/albums/a51/drgreborn/error.png[/IMG]

Using this to launch:
/home/drgreborn/eclipse/eclipse -vm /usr/local/j2sdk1.4.2_09/jre/bin/java_vm -vmargs -Xmx512M

---

### Post by drgreborn on 2005-10-04
Isn't there anyone? There seems to be alot of people using eclipse,so if anyone coul d help me out that would be much apreciated.

---

### Post by drgreborn on 2005-10-04
I've figured out what I did wrong in my installation. I'll like to apologise to anyone that may be annoyed by this thread and my questions.
Now the only problme that remains is creating an application launcher for eclipse. How those one go about creating it?

---

### Post by tehwa on 2005-10-04
What was the solution (Tell us how you fixed it, then add it to your Howto).

For a launcher, you can add one to your applications menu using smeg. If you dont' have smeg, look at ubuntuguide.org and find smeg. Don't forget to add repositories.

The executable entry will most likely be the full path to eclipse - /home/drgreborn/eclipse/eclipse

To put one on your panel, just drag the executable onto the panel and a window will pop up. You just need to enter the Name, and add the icon from the eclipse directory.

---

### Post by drgreborn on 2005-10-04
Actualy I got the answer to my questions from different entries in the ubuntuguide.

---

### Post by drgreborn on 2005-10-05
Erm heres a new question. I accidentaly removed the menus located on my taskbar panel. The aplication menu, system menu the likes. Erm how do I recover them? Thanks you very much.

---

### Post by drgreborn on 2005-10-05
erm nevermind I figured it out. Silly me, I just had to add a custom menu item to the panel..

---

