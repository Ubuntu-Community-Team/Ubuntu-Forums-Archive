---
title: "firefox and java"
date: 2006-01-09
forum: Desktop Environments
---

### Post by tbobo05 on 2006-01-09
I am running the latest firefox and have installed the java run-time environment seperately.  Every time i try to view a page that has java, it says  I am missing the plugin.  How do I set firefox to point to my particular installation of java?  Thanks,   
              Bobo


UPDATE:  nevermind, just saw new post that answers question, thanks anyway though

---

### Post by awi on 2006-01-29
You need to make a symbolic link from your firefox's installation dir, pointing to the plugin that came with the jre, something like this:

```
$ cd /usr/lib/mozilla-firefox/plugins/
$ sudo ln -s /usr/lib/j2re1.4-blackdown/plugin/amd64/mozilla/libjavaplugin_oji.so

```
changing to your jre's dir, and arch.
Chek the installation later, typing on the URL bar:

```
about:plugins
```

---

### Post by Il_Tuo_Nome on 2006-02-03
I re-installed java and after checked the path's which contained the symbolic links required. However, when I checked about:plugins within firfox, it did not show the plugin for that. I imagine that's why it keeps saying the plugin needs installed. Can someone please help me solve this dilema?

thank you

---

### Post by Basu on 2006-02-03
Same problem here. Please help

---

### Post by jerome bettis on 2006-02-04
search for automatix, it sets all that stuff up for you:cool:

---

### Post by Il_Tuo_Nome on 2006-02-04
assuming I do use 'automatix', will that overwrite what I have installed? And if not is there a way of uninstalling all that?


thanks

---

### Post by ilbahr on 2006-02-06
You need to know where you have installed java.

If you are using sun java the plugin should be in the following directory

/usr/lib/j2re1.5-sun/plugin/i386/ns7/

if you are using blackdown java than look for the plugin under

/usr/lib/<dir of blackdown java>/plugin/i386/

the file name to look for is libjavaplugin_oji.so

now make a symbolic link to it and name it libjavaplugin.so

ln -s 
/usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so $HOME/.mozilla/plugins/libjavaplugin.so


Ps you can also copy or link symbolically (using ln -s command) all your plugins that you used with ff 1.07 by copying them from 

/usr/lib/mozilla-firefox/plugins

to

.mozilla/plugins

this will copy flash, java, and all the other plugins you installed using apt-get or synaptic

---

### Post by Il_Tuo_Nome on 2006-02-06
I must say ilbahr,

you're a lifesaver, that worked flawlessly. Thank you very much for your help, 


thanks again :p

---

### Post by ilbahr on 2006-02-07
You are more than welcomed my friend.
I am just glad it worked for you :-D .

---

### Post by mattotoole on 2006-02-08
[QUOTE=ilbahr]You need to know where you have installed java.

If you are using sun java the plugin should be in the following directory

/usr/lib/j2re1.5-sun/plugin/i386/ns7/[/QUOTE]

Mine's actually in /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7

So if you can't find yours, look there.

---

### Post by pwrstick on 2006-02-23
I used this java:
[http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)

I ended up downloading the AMD64 (since I have an AMD64) and installed it to the /usr/java directory.

I don't see a plugin directory as a subdirectory anywhere.  What do  you think?

---

