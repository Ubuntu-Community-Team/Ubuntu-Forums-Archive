---
title: "GNOME won't load anymore"
date: 2009-02-12
forum: General Help
---

### Post by quicknick_26 on 2009-02-12
I was getting this message at startup:
"User's $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $Home directory must be owned by user and not writable by other users."

I did see a nice guide here in the forum to fix this at [http://ubuntuforums.org/showthread.php?t=976610]("http://ubuntuforums.org/showthread.php?t=976610"), but not until after I tried to fix it myself (yes, I'm a moron).

It started when I thought I could share some of my home folders (music, pictures, etc.) with my wife by changing the permissions to be read/writable by group. This method of sharing never really worked quite the way I expected it to. So, after getting that message for a while, I decided to run a "sudo chmod -R 644 /home/nick". Apparently, that was a big mistake.

Now I get:
"Could not update ICEauthority file /home/nick/.ICEauthority
There is a problem with the configuration server (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)", which is also mentioned in another thread at [http://ubuntuforums.org/showthread.php?t=1066856&highlight=ICEauthority&page=2]("http://ubuntuforums.org/showthread.php?t=1066856&highlight=ICEauthority&page=2"). My problem with the solution on that thread is that I set up the Intrepid Ibex to boot without login authentication and I have no other users anyway.

My only thought at this point is that I might have to use gparted to form another partition on which to reinstall Ubuntu. Then I could copy over the data from my old home folder and delete the old hosed Ubuntu partition.

Is there a better fix?

---

### Post by kanikilu on 2009-02-12
> **quicknick_26 said:**
> My problem with the solution on that thread is that I set up the Intrepid Ibex to boot without login authentication and I have no other users anyway.

Can you not boot into recovery mode?

[http://www.psychocats.net/ubuntu/fixsudo#recoverymode](http://www.psychocats.net/ubuntu/fixsudo#recoverymode)

---

### Post by quicknick_26 on 2009-02-12
Yeah, I can get into recovery mode. Sorry, I was looking at post 13 in that thread. I see where they bring up going into recovery mode on post 14, but the person who started the thread fixed his problem elsewhere and that train of thought was never completed. I can get to the root shell prompt, but I don't know for sure what commands will undo what I have done.

---

### Post by quicknick_26 on 2009-02-12
Is there a list of files that are supposed to have specific permissions set for the operating system or are there too many to list?

---

### Post by quicknick_26 on 2009-02-13
If I knew which files needed specific permissions set, I should be able to fix this without reinstalling; shouldn't I?

---

### Post by grndslm on 2009-02-13
You should be able to login thru command line

Ctrl + Alt + [F1-F6], then login!

then type:

sudo chown -R user:user *
(just replace user with your username, and make sure "ls -l" shows that all the files in your /home dir are now owned only by you)

then go back to GDM for graphical login

Ctrl + Alt + F7

Hope that works!

---

### Post by quicknick_26 on 2009-02-13
Actually I was already the owner.

I rolled the dice and tried to fix it myself again. I went ahead and changed directory to the root of my /home/nick folder and did a "chmod -R 755 .". So far this seems to have fixed the problem. I restarted the computer and after a fresh boot there were no error messages of any sort whatsoever. I'm knocking on wood.

Thanks to everyone for your input!

---

