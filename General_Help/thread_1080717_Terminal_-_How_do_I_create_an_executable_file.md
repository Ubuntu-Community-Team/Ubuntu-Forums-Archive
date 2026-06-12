---
title: "Terminal - How do I create an executable file?"
date: 2009-02-25
forum: General Help
---

### Post by ddigler on 2009-02-25
I need to create a file with a single iptable redirect command. I need it in /etc/init.d/

File to be called 'transparentproxy'

I'm assuming I have to do this from Terminal for rights.

Can anyone help me with this?

thanks!

---

### Post by taurus on 2009-02-25
Create a new file in /etc/init.d with

```
gksudo gedit /etc/init.d/transparentproxy
```
and add whatever command you want in there after this line.

```
#!/bin/bash
```
Save it and change the permissions to include an executable.

```
sudo chmod 755 /etc/init.d/transparentproxy
```

---

### Post by mb_webguy on 2009-02-25
You don't *have* to do anything in the terminal.  Just about anything you want to do can be done with GUI apps on the desktop.  It's just that some things are easier or faster in the terminal.

Ok, so I'm assuming you're wanting to run a command/script at startup, correct?  The preferred method of doing so is by doing the following...

1) Create a file called /etc/init.d/local, using the command "sudo gedit /etc/init.d/local". This is a shell script, so it should begin with:```
#! /bin/sh
```The file should also end with:```
exit 0
```Add any commands or applications you want to run at startup in the script, then save and exit.

2) Make the script executable using the command "sudo chmod a+x /etc/init.d/local".

3) Add the script to Init using the command "sudo update-rc.d local defaults 80".

You only have to do steps 2 and 3 once.  Afterwards, anything else you want to run at startup can just be added to the /etc/init.d/local file.

---

### Post by ddigler on 2009-02-25
Very helpful thanks. 

Yes, the point was to install squid w/ dansguardian for filtering. It all works EXCEPT:

I always have to restart squid after booting up to enable internet. Why?

---

