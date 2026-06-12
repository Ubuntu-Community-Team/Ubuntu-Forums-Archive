---
title: "help installing app?"
date: 2009-02-05
forum: General Help
---

### Post by newbux on 2009-02-05
hello can you guide me through installing something i am a previous windows user and installing is not as easy on ubuntu 8.10 intrepid. i am installing the new version of claws mail and also installing a plugin to block attachments. the new version of claws is on: [http://www.claws-mail.org/downloads.php?section=downloads](http://www.claws-mail.org/downloads.php?section=downloads) it has a funny url i dont know what to do?

and the plugin is on: [http://www.claws-mail.org/plugins.php](http://www.claws-mail.org/plugins.php)

can you please describe in detail because this is all new thanks

---

### Post by overlord.gaurav on 2009-02-05
For install Claws Mail, go to system > Administration > Software Sources.
Navigate to "Third-Party Sources" > Click on Add.
Add "deb [http://ppa.launchpad.net/claws-mail/ubuntu](http://ppa.launchpad.net/claws-mail/ubuntu) intrepid main" to the sources.
Close the window. It'll prompt you to update your repos. Hit reload.
Now:
1. Click on System > Administration > Synaptic Package Manager > Select "claws-mail" and click Apply. You're done.
OR
2. Go to the terminal, type
```
sudo apt-get install claws-mail
```
Step 2 saves time! ;)

Edit: Installing softwares on Ubuntu isn't all that tough.
Maybe [this guide]("https://help.ubuntu.com/8.10/add-applications/C/index.html") can help you!

---

### Post by N4zgu1 on 2009-02-06
you have to open a terminal and run the code 

```
deb http://ppa.launchpad.net/claws-mail/ubuntu intrepid main
```

after that

```
sudo apt-get update

```

and 

```
sudo apt-get install claws-mail
```


Explanation: the first command adds claws mail to your reppositories 

apt-get update updates the reppositories (you have to do this every time you change them)

and finally apt-get install is a command for isntalling programs


Notes: If you know spanish here is complete guide for configuring claws-mail

[http://tuxlink.wordpress.com/2008/04/20/claws-mail-y-gmail/](http://tuxlink.wordpress.com/2008/04/20/claws-mail-y-gmail/)

---

### Post by newbux on 2009-02-06
thanks i got the app installed but i dont know how to install the plugin?
could you help again?

---

### Post by overlord.gaurav on 2009-02-06
To load a plugin go to "Configuration/Plugins" and click the "Load Plugin" button. Select the plugin that you want and click "Open" button.

---

### Post by newbux on 2009-02-06
thanks again.

---

### Post by newbux on 2009-02-06
hello well i thought it was done but when i clicked plugins/add it open it to a folder called src and then i clicked open again and it went into src where their was nothing else to do? also when i clicked the plugins/add  button there was a error stating that some folder didnt exist? could you help out again? i tried to create the folder myself by right clicking and creating it but i wasnt allowed to?

---

