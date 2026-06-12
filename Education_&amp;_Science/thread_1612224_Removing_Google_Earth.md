---
title: "Removing Google Earth"
date: 2010-11-02
forum: Education &amp; Science
---

### Post by ChuckyZ28 on 2010-11-02
I have attempted to install google earth using the following method.
[http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/](http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/)

The version is not stable and will crash. However I can not uninstall. I installed it to the /opt/ directory as that is what it defaults to and I can not find it to delete it.

---

### Post by gunksta on 2010-11-03
I'm going to make some educated guesses here, so bear with me. I assume that Google Earth is the only thing you have installed that's not in the repos?

Open a command-line. I normally try to avoid command-line directions, but this time I think it may be easier actually. 
```

cd /opt
ls

```You should see something that looks like "googleearth", "GoogleEarth", etc. Not sure, but it should be pretty obvious. I will assume the directory is called "googleearth". You may have to make minor modifications to my recommendations if this is not true.

When you enter the command sequence this command you will  need to enter your user-password. Using "sudo" at the command line means that you are acting as the super-user and you full control over your system. This includes full control to delete everything on your computer and turn your system into an expensive paperweight. (You would have to re-install.) Thus, you should ALWAYS be careful when executing any command that starts with sudo. I promise, I'm not going to help you kill your computer.  :P
```

sudo rm -rf googleearth*

```Quick explanation - The command "rm" stands for 'remove'. The "-rf" part tells the computer that we know we are deleting a file folder, do it anyway. And the "*" at the end will catch anything after "googleearth". So, this command would erase a folder called "googleearth", "googleearth42", "googleearth-your-momma", etc. It would not delete "google-earth".

Finally we need to delete the link to the no-longer existing executable.
```

sudo rm /usr/local/bin/googleearth

```Again, I assumed that you didn't tweak the directions from Tombuntu. If you did, you may have to adjust these slightly.

---

### Post by ChuckyZ28 on 2010-11-03
maybe the install failed, Its still not showing up.

---

### Post by gunksta on 2010-11-03
What are the contents of /opt?

---

### Post by ChuckyZ28 on 2010-11-04
Well when I look in the opt folder it shows nothing, if it might have installed in a different directory how would I search for the folder?

---

### Post by wilee-nilee on 2010-11-04
My install is in synaptic most are have you looked there.

If you want a working google earth I have a link to a deb if needed.

---

### Post by gunksta on 2010-11-04
> **ChuckyZ28 said:**
> Well when I look in the opt folder it shows nothing, if it might have installed in a different directory how would I search for the folder?

This is just a shot in the dark, but what happens from the command line when you enter (does not matter where you are, just open a terminal):

```
googleearth
```I would also like to see the output of:

```
locate google
```and, just to be careful:

```
locate earth
```The first command should, in theory, start googleearth if it is still installed on your system. If you are told that there is no such command, that would tend to imply that it has been at least partially removed.

The second command will go through and return the location of ANY file with the word google in it. If locate finds something, we know where to look. If it comes up empty, you have removed google earth.

---

