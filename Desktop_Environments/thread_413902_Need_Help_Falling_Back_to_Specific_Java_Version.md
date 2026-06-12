---
title: "Need Help Falling Back to Specific Java Version"
date: 2007-04-19
forum: Desktop Environments
---

### Post by solderhead on 2007-04-19
I'm looking for some helpful advice on package management.  I currently have Sun Java 1.5.0_11 installed on my Feisty Fawn installation of Kubuntu, and for compatability reasons I need to fall back to Sun Java 1.5.0_10.

Can anyone tell me how to do this?

TIA

---

### Post by llamakc on 2007-04-19
sudo update-alternatives --config java

---

### Post by solderhead on 2007-04-19
thanks for posting.  that command, as far as i can tell, allows you to select the java config from installed configs on the system:, but as I understand it it doesn't allow much granular control over specific versions.  maybe i'm missing something.

```
# sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:    
```

although that command appears to provide the ability to select sun java 1.5, it doesn't appear to offer the ability to select specific subversions.  maybe i'm missing something.

i'd like to know how to: a) obtain 1.5.0_10, and b) how to set the system to use it instead of the 1.5.0_11 that is already installed.  

thanks again.

---

### Post by llamakc on 2007-04-19
No, it manages the symlink to whichever version of java you want. If you installed java from outside of the repositories, it won't help you without a little bit more work.

Why not find the version you want over at Sun's website and install that?

---

### Post by solderhead on 2007-04-20
the only Java that I have is what came with Feisty.  that's 1.5.0_11.  i haven't installed anything from outside of the repositories.  what i'd like to install is 1.5.0_10.  I have no idea if that is in the repositories or not.

regarding the option of taking the outside-of-the-repository Java from Sun and installing it manually, i am confident that if i try to do that on my own i will royally bugger up my system, as i have no clue what to do.  i slocated all of the java files in the console, and it appears that there are symlinks pointing to symlinks, and if i try to do this manually without something to follow, i'm sure that i'll be worse off than i am now.

thanks for following up.

---

