---
title: "java help"
date: 2005-12-15
forum: General Help
---

### Post by tanis143 on 2005-12-15
Ok, so I'm trying to make linux a viable o/s for my wife. However, she is a pogo player. I tried to go into a game on pogo under firefox, however it gives me a message that either my java is not installed or it is out of date. I want to know how to upgrade my java. I've downloaded the newest rpm from sun, but I'm having problems installing it. I tried their instructions, but they want to use a command "rpm" which Ubuntu does not recognize. 

Oh, and btw, I'm a newbie to linux myself :D I know some basic commands and file navigation, but you'll have to explain it in baby steps to me.

---

### Post by racyrefinedraj on 2005-12-15
I'm pretty solidly in newb territory too, but let me take a stab.

Alright, RPM stands for "Red hat package manager" and is a packaging system built for, you guessed it, Red hat linux and it's derivatives. 

Ubuntu doesn't recognize the command to install an RPM because it is not a red had derivative, it is a debian derivative and uses the debian packaging format (.deb). Usually, to install, say, java from the command line you'd do something like

```
sudo apt-get install java
```

apt-get is the command for aptitude, the program that handles the .deb packages. 

However, registering java with firefox is a bit trickier. The easiest way to install java for firefox is explained by 

[this page]("https://wiki.ubuntu.com/RestrictedFormats#head-ef347c277a133b64af0600bd1bf24bc64e7038b8") on the ubuntu wiki. Scroll down to java for firefox.

hope that helps.

---

### Post by hod139 on 2005-12-15
Using that same wiki page that racyrefinedraj posted, it states that the easiest wat to [get java]("https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249") is to use the package: j2re1.4.  
```

sudo apt-get install j2re1.4 

``` 
(or you can use synaptic and search for j2re1.4)

This is not Sun's version of java, but should work for most applications.  If you really need Sun's version, the next article in the above wiki also describes that.

Lastly, to get the plugin to work for firefox, follow the link in racyrefinedraj's post.

---

### Post by tanis143 on 2005-12-15
Actually, all I had to do was update the java, and that worked fine. Thanks!

---

