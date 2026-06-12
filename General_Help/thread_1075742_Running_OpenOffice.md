---
title: "Running OpenOffice"
date: 2009-02-20
forum: General Help
---

### Post by kogger on 2009-02-20
I had a couple complications with OpenOffice over the past few days. I installed the theme Slickness-Black, but having OpenOffice run in that theme disables a lot of things, so I was trying to get it to run in an envelope using another theme. Long story short, something screwed up, so I pretty much purged OpenOffice from my computer and re-installed it from scratch.

I'm not sure what I did exactly to make it work, but now when OpenOffice starts it does what I wanted it to, which is use a different theme inside the program to make things compatible. But, in order to start it, I have to have root privileges. It'll run if I type "sudo ooffice", but I have an icon launcher on my panel that doesn't work unless I activate root privileges through a terminal first.

How do I modify the ooffice command so that I can run it without needing root privileges? It's installed in /usr/bin, so do I need to move it to a different folder, or is there a way to modify the command itself?

---

### Post by kellemes on 2009-02-20
What's your output when you run it from terminal as user?

---

### Post by opscure on 2009-02-20
```
sudo chmod 755 /usr/bin/ooffice
```

---

### Post by kogger on 2009-02-20
I don't have any output. It just displays the prompt again.

And the chmod 755 didn't work.

---

### Post by kogger on 2009-02-21
I guess I should re-word this. I can't get open office to start unless I precede the command with sudo. If I simply type "ooffice," I don't even get a permissions error. It just shows the prompt again, and nothing happens.

How do I get it so I don't need to add "sudo"?

---

### Post by Incense on 2009-02-21
> **kogger said:**
> 

I'm not sure what I did exactly to make it work, 


That makes it kind of hard for us to sort this out as well. Have you tried to reinstall oo.o from synaptic?

---

### Post by kogger on 2009-02-21
Yeah. I uninstalled it and re-installed it, but I still need to add sudo in order to run it.

---

### Post by opscure on 2009-02-25
There is likely some part of the new theme that doesn't allow a user to execute it and therefore you may need to find where the theme is install and check the permissions and ownership of those files.

You can see your permissions by cd -ing to the theme directory (maybe in your ~/.openoffice2 directory somewhere and then doing a ls -la

To change permissions to a directory and files you can do:
```
sudo chmod -R 755 directory/
```
To change ownership of all files inside a directory you can do:
```
sudo chown -R username:group *
```

This could just be a problem with the theme.

You may also want to check you logs in /var/log/ to see if there are any errors being reported.  

There is a bug listing from a year ago here:
[https://bugs.launchpad.net/openoffice/+bug/131526]("https://bugs.launchpad.net/openoffice/+bug/131526")
but this is for gusty.  What version of ubuntu are you using?

---

### Post by kogger on 2009-02-26
Okay, for some reason I got it working. Here's what I typed:

```
sudo apt-get remove openoffice.org
```

I guess it just removed some specific part that was causing trouble. Oh well, it works now. =)

EDIT: Hm, maybe it didn't work like I thought it did. I'll keep messing with it.

---

### Post by kogger on 2009-02-26
As a quick note, I don't have this problem with OpenOffice 2.4. It only becomes apparent when I upgrade to 3.0.

---

